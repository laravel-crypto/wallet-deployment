# wallet-deployment

#### Build bitcoind docker container

`cd eclair/bitcoind`

`docker build -t bitcoind . `

#### Run bitcoind docker container

`docker run -p 18332:18332 --name bitcoind bitcoind`

#### Download eclair lightning node(jar)

https://github.com/ACINQ/eclair/releases

#### Put eclair.conf file in default directory:

~/.eclair/eclair.conf

#### Run eclair lightning node with GUI

`java -jar eclair-node-gui-0.2-alpha5-a97fa39.jar`
