FROM ubuntu:trusty

MAINTAINER Rex Tsai <rex.cc.tsai@gmail.com>

ENV DEBIAN_FRONTEND=noninteractive
RUN sed -e s%http://archive.ubuntu.com/ubuntu/%mirror://mirrors.ubuntu.com/mirrors.txt% -i /etc/apt/sources.list \
        && apt-get update \
        && apt-get dist-upgrade -y \
        && apt-get install -y vim

ENV MAPNIK_VERSION=2.2.0+ds1-6build2 \
    PYTHON_MAPNIK_VERSION=2.2.0+ds1-6build2

# Verify that Mapnik has been installed correctly
RUN apt-get install -y \
            libmapnik2.2=${MAPNIK_VERSION} \
            libmapnik-dev=${MAPNIK_VERSION} \
            mapnik-utils=${MAPNIK_VERSION} \
            python-mapnik=${PYTHON_MAPNIK_VERSION} \
 && python -c 'import mapnik'

# Install Cascadenik
RUN apt-get install -y git python-cssutils python-imaging \
 && git clone --depth 1 https://github.com/mapnik/Cascadenik.git \
 && cd Cascadenik \
 && python setup.py install \
 && cd - \
 && rm -r Cascadenik

# Clean up APT when done
RUN apt-get autoremove -y --purge build-essential \
 && apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
