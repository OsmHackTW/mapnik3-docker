FROM ubuntu:xenial

MAINTAINER Rex Tsai <rex.cc.tsai@gmail.com>

ENV DEBIAN_FRONTEND=noninteractive
RUN sed -e s%http://archive.ubuntu.com/ubuntu/%mirror://mirrors.ubuntu.com/mirrors.txt% -i /etc/apt/sources.list \
        && apt-get update \
        && apt-get dist-upgrade -y \
        && apt-get install -y vim

ENV MAPNIK_VERSION=3.0.9+ds-1 \
    PYTHON_MAPNIK_VERSION=1:0.0~20151125-92e79d2-1build1

RUN apt-get install -y libmapnik3.0=${MAPNIK_VERSION} mapnik-utils=${MAPNIK_VERSION} python-mapnik=${PYTHON_MAPNIK_VERSION} python3-mapnik=${PYTHON_MAPNIK_VERSION} \
        && rm -rf /var/lib/apt/lists/*
