# Build Polkadot in a stock builder container
FROM alpine:edge AS builder
LABEL description="This is the build stage for Polkadot. Here we create the binary."
WORKDIR /usr/src/app

RUN apk add build-base \
    cmake \
    linux-headers \
    openssl-dev \
    cargo \
    clang \
    clang-libs \
    git

# v0.3 branch = Alexander testnet
# 'Riot chat consensus' on version 0.3.2 as commit b328153695d1a48771e92eca07a942479c6f83ef (no tag yet)
# when build : polkadot v0.3.2 = branch v0.3 at commit b328153695d1a48771e92eca07a942479c6f83ef
ARG VERSION=v0.3
ARG PROFILE=release

RUN git clone -b $VERSION https://github.com/paritytech/polkadot.git && cd polkadot && \
    cargo build --$PROFILE

# Pull Polkadot into a second stage deploy alpine container
FROM alpine:edge
LABEL description="This is the 2nd stage: a very small image where we copy the Polkadot binary."
ARG PROFILE=release

RUN apk add --no-cache ca-certificates \
    libstdc++ \
    openssl

COPY --from=builder /usr/src/app/polkadot/target/$PROFILE/polkadot /usr/local/bin

RUN rm -rf /usr/lib/python* && \
	mkdir -p /root/.local/share/Polkadot && \
	ln -s /root/.local/share/Polkadot /data

ENTRYPOINT polkadot --chain alex --ws-external $EXTRA_OPTS
