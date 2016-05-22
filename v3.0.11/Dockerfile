FROM ubuntu:xenial

MAINTAINER Rex Tsai <rex.cc.tsai@gmail.com>

ENV DEBIAN_FRONTEND=noninteractive
RUN sed -e s%http://archive.ubuntu.com/ubuntu/%mirror://mirrors.ubuntu.com/mirrors.txt% -i /etc/apt/sources.list \
        && apt-get update \
        && apt-get dist-upgrade -y \
        && apt-get install -y vim

ENV MAPNIK_VERSION=v3.0.11

RUN apt-get build-dep -y libmapnik3.0 \
    && apt-get install -y git ca-certificates \
    && git clone --depth 1 --branch $MAPNIK_VERSION https://github.com/mapnik/mapnik.git \
    && cd mapnik \
    && git submodule update --init \
    && ./configure \
    && make \
    && make install \
    && cd - \
    && rm -r mapnik \
    && apt-get autoremove -y --purge git build-essential \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

