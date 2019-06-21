# DAppNodePackage-polkadot-alexander

Dappnode package providing polkadot alexander testnet chain 

It was generated using [DAppNodeSDK](https://github.com/dappnode/DAppNodeSDK)

No Aragon Package Manager Repo yet.

build_0.0.8 of polkadot v0.4.4
```
  DNP (DAppNode Package) built and uploaded
  Manifest hash : /ipfs/QmZCmU26M25MNN7ekHpxuKcVLApqXKq9ono3SVJpSUbiHK
  Install link  : http://my.dappnode/#/installer/%2Fipfs%2FQmZCmU26M25MNN7ekHpxuKcVLApqXKq9ono3SVJpSUbiHK
```
## DEMO 


<p align="center"><img src="/img/DappNodeAvadoSetup.gif?raw=true"/></p>

or can use this package without installing it in your DAppNode following these instructions:

## Prerequisites

- git

   Install [git](https://git-scm.com/book/en/v2/Getting-Started-Installing-Git) commandline tool.

- docker

   Install [docker](https://docs.docker.com/engine/installation). The community edition (docker-ce) will work. In Linux make sure you grant permissions to the current user to use docker by adding current user to docker group, `sudo usermod -aG docker $USER`. Once you update the users group, exit from the current terminal and open a new one to make effect.

- docker-compose

   Install [docker-compose](https://docs.docker.com/compose/install)
   
**Note**: Make sure you can run `git`, `docker ps`, `docker-compose` without any issue and without sudo command.


## Buidling

`docker-compose build`

## Running

### Start

`docker-compose up -d`

Watch if your node start syncing at [Polkadot telemetry](https://telemetry.polkadot.io/#/Alexander)

### View logs

`docker-compose logs -f`

### Stop

`docker-compose down`

## Extra options

You can write extra options on the adminui or edit the `docker-compose.yml` and add extra options, such as:
```
 - EXTRA_OPTS=--name 'alexander-dappnode-package-tester'
```

## License

This project is licensed under the GNU General Public License v3.0 - see the [LICENSE](LICENSE) file for details

