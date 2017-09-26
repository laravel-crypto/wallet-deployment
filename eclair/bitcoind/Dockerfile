FROM ubuntu:16.04
# TODO(evg): add maintainer

# Install some basic utilities
RUN apt-get update && \
    apt-get install -y git nano vim net-tools inetutils-ping

# Dependency Build Instructions: Ubuntu & Debian
# For more details see https://github.com/bitcoin/bitcoin/blob/master/doc/build-unix.md
RUN apt-get install -y build-essential libtool autotools-dev automake \
                       pkg-config libssl-dev libevent-dev bsdmainutils

RUN apt-get install -y libboost-system-dev libboost-filesystem-dev libboost-chrono-dev \
                       libboost-program-options-dev libboost-test-dev libboost-thread-dev

RUN apt-get install -y libzmq3-dev

# Ubuntu and Debian have their own libdb-dev and libdb++-dev packages, but these will
# install BerkeleyDB 5.1 or later, which break binary wallet compatibility with the
# distributed executables which are based on BerkeleyDB 4.8.
RUN apt-get install -y software-properties-common
RUN add-apt-repository ppa:bitcoin/bitcoin
RUN apt-get update
RUN apt-get install -y libdb4.8-dev libdb4.8++-dev

# Clone bitcoin
RUN git clone https://github.com/bitcoin/bitcoin
WORKDIR bitcoin

# To Build
RUN ./autogen.sh
RUN ./configure
RUN make
RUN make install # optional

# Eclair
RUN apt-get install -y default-jre
RUN mkdir /eclair
ADD eclair-node-0.2-alpha5-a97fa39.jar /eclair/

# Launch bitcoind in regtest mode
RUN mkdir lol4
ADD bitcoin.conf /root/.bitcoin/bitcoin.conf
CMD bitcoind

