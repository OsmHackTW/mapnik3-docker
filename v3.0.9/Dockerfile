FROM osmtw/ubuntu:xenial
MAINTAINER Rex Tsai "https://about.me/chihchun"

ENV MAPNIK_VERSION=3.0.9+ds-1 \
    PYTHON_MAPNIK_VERSION=1:0.0~20151125-92e79d2-1build1

# Verify that Mapnik has been installed correctly
RUN apt-get update \
 && apt-get install -y \
            libmapnik3.0=${MAPNIK_VERSION} \
            libmapnik-dev=${MAPNIK_VERSION} \
            mapnik-utils=${MAPNIK_VERSION} \
            python-mapnik=${PYTHON_MAPNIK_VERSION} \
            python3-mapnik=${PYTHON_MAPNIK_VERSION} \
     && python -c 'import mapnik'

# Install nik2img
RUN apt-get install -y python-setuptools \
 && easy_install -U nik2img

# Clean up APT when done
RUN apt-get clean \
 && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/*
