# wallet-deployment

#### Clone repo

`git clone https://github.com/BitfuryLightning/wallet-deployment`

#### Build bitcoind docker container

`cd eclair/bitcoind`

`docker build -t bitcoind . `

#### Run bitcoind docker container

`docker run -p 18332:18332 --name bitcoind bitcoind`

#### Install JRE 1.8

`apt-get install -y default-jre`

#### Download eclair lightning node(jar)

https://github.com/ACINQ/eclair/releases

#### Put eclair.conf file in default directory:

cp eclair/eclair.conf ~/.eclair/eclair.conf

#### Run eclair lightning node with GUI

`java -jar eclair-node-gui-0.2-alpha5-a97fa39.jar`
