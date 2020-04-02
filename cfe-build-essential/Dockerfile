FROM ubuntu:latest
LABEL Description="CFE basic code build image"
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux

# Standard build dependencies
RUN apt-get update \
    && apt-get install -y \
       apt-utils build-essential \
       vim u-boot-tools git cmake \
       bison flex texinfo bzip2 \
       xz-utils unzip python \
       lua5.3 liblua5.3-dev libexpat1-dev \
       libpython2.7-dev zlib1g-dev libtinfo-dev \
    && rm -rf /var/lib/apt/lists/*

