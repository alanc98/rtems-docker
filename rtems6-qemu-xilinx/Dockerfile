FROM ubuntu:20.04
LABEL Description="RTEMS xilinx qemu"
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux

#
# Setup repos, install a TON of deps, then download, and build xilinx qemu
#
# Probably needs to be cleaned up and possibly included with the Xilinx tools image.
#
RUN    echo "deb-src http://archive.ubuntu.com/ubuntu/ focal main restricted" >> /etc/apt/sources.list \
    && echo "deb-src http://archive.ubuntu.com/ubuntu/ focal-updates main restricted" >> /etc/apt/sources.list \
    && apt-get update \
    && apt build-dep -y qemu \
    && apt-get install -y \
       apt-utils build-essential \
       vim u-boot-tools git cmake \
       bison flex texinfo bzip2 \
       xz-utils unzip python3 \
       libexpat1-dev zlib1g-dev libtinfo-dev \
       python3-dev python-is-python3 \
    && cd /usr/src && \
       git clone --depth 1 git://git.rtems.org/rtems-source-builder.git rsb && \
       cd /usr/src/rsb \
    && ./source-builder/sb-check \
    && cd /usr/src/rsb/bare \
    && ../source-builder/sb-set-builder --prefix=/opt/rtems6 devel/qemu-xilinx \
    && cd /usr/src \
    && rm -rf rsb \
    && rm -rf /var/lib/apt/lists/*

ENV PATH="/opt/rtems6/bin:${PATH}"

