FROM  --platform=$TARGETOS/$TARGETARCH ubuntu:22.04

LABEL author="TemaFlux" maintainer="artem.prozapas@gmail.com"

ENV   DEBIAN_FRONTEND noninteractive

## add container user
RUN   useradd -m -d /home/container -s /bin/bash container

## update base packages
RUN   apt update && apt upgrade -y

## install dependencies
RUN   apt install -y build-essential gcc g++ libgcc1 libc++-dev gdb libc6 libasan5 git wget curl tar zip unzip binutils xz-utils liblzo2-2 cabextract iproute2 net-tools netcat telnet libatomic1 libsdl1.2debian libsdl2-2.0-0 \
        autotools-dev libfontconfig icu-devtools libunwind8 sqlite3 libsqlite3-dev libzip4 locales apt-transport-https init-system-helpers \
        libcurl3-gnutls libboost-all-dev liblua5.1-0 libluajit-5.1-2 libsqlite3-0 bzip2 zlib1g libevent-dev libmariadb-dev-compat libmariadb-dev libssl-dev \
	libfluidsynth-dev libmariadb-dev libicu-dev libbz2-dev libssl3 libduktape207 libjsoncpp-dev libleveldb1d libncurses5 libncursesw5 libpython2.7 libatlas3-base psmisc

RUN   wget https://raw.githubusercontent.com/TemaFlux/yolks/main/libs/libboost-1.70.tar.gz
RUN   tar xf libboost-1.70.tar.gz -C /usr/local/lib && rm libboost-1.70.tar.gz && chown root:root /usr/local/lib/libboost_* && chmod 755 /usr/local/lib/libboost_*

## configure locale
RUN   update-locale lang=en_US.UTF-8 \
        &&   dpkg-reconfigure --frontend noninteractive locales

WORKDIR /home/container

COPY  ./entrypoint.sh /entrypoint.sh
CMD   [ "/bin/bash", "/entrypoint.sh" ]
