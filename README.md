[![Build Status](https://travis-ci.org/blizzlike-org/core.svg?branch=master)](https://travis-ci.org/blizzlike-org/core)

## build instructions

### dependencies

#### debian (stretch)

    apt-get install vim git \
      build-essential gcc g++ automake \
      autoconf make patch \
      libace-dev libmysql++-dev libtool \
      libssl-dev grep binutils zlibc \
      libc6 libbz2-dev cmake libboost-dev libboost-system-dev \
      libboost-program-options-dev libboost-thread-dev libboost-regex-dev \
      libtbb-dev libcurl4-openssl-dev libutfcpp-dev 

#### ubuntu (trusty)

    apt-get install vim git software-properties-common \
      build-essential gcc g++ automake \
      autoconf make patch \
      libace-dev libmysql++-dev libtool \
      libssl-dev grep binutils zlibc \
      libc6 libbz2-dev cmake3 libboost-dev libboost-system-dev \
      libboost-program-options-dev libboost-thread-dev libboost-regex-dev \
      libtbb-dev libssl-dev libcurl4-openssl-dev libutfcpp-dev

    add-apt-repository ppa:ubuntu-toolchain-r/test
    apt-get update
    apt-get install g++-6
    update-alternatives --install /usr/bin/g++ g++ /usr/bin/g++-6 90

### compile

    mkdir build run
    cd build

    # for ubuntu trusty append the following additional arguments
    # -DCMAKE_CXX_COMPILER=g++-6
    # -DCMAKE_C_COMPILER=gcc-6
    cmake .. \
      -DUSE_ANTICHEAT=0 \
      -DCMAKE_INSTALL_PREFIX=./run \
      -DUSE_EXTRACTORS=1 \
      -DUSE_LIBCURL=1 \
      -DDEBUG=0

    make -j${X} # ${X} is the amount of cpus/threads
    make install

### database

    > mysql -h <mysql-host> -u root -p
    Enter password: 

    MariaDB [(none)]> CREATE USER 'core'@'%';
    MariaDB [(none)]> CREATE DATABASE core_characters;
    MariaDB [(none)]> CREATE DATABASE core_logon;
    MariaDB [(none)]> CREATE DATABASE core_logs;
    MariaDB [(none)]> CREATE DATABASE core_world;
    MariaDB [(none)]> GRANT ALL PRIVILEGES ON `core\_%` . * TO 'core'@'%';
    MariaDB [(none)]> ALTER USER 'core'@'%' IDENTIFIED BY '<your-password>';
    MariaDB [(none)]> FLUSH PRIVILEGES;
    MariaDB [(none)]> \q

    mysql -h <mysql-host> -u core -p core_characters < core/sql/characters.sql
    mysql -h <mysql-host> -u core -p core_logon < core/sql/logon.sql
    mysql -h <mysql-host> -u core -p core_logs < core/sql/logs.sql

    mysql -h <mysql-host> -u core -p core_world < database/sql/world_full.sql
    cd ./core/sql/migrations
    ./merge.sh
    mysql -h <mysql-host> -u core -p core_world < world_db_updates.sql
