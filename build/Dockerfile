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

# v0.3.4 tag = Alexander testnet
ARG VERSION=v0.3.4
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

RUN rm -rf /usr/lib/python*

ENTRYPOINT polkadot --chain alex --ws-external $EXTRA_OPTS
