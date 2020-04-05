FROM ubuntu:latest
LABEL Description="RTEMS 5 m2004 release ARM tools build"
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux

RUN apt-get update && \
    #
    # Install tools and libraries
    #
    apt-get install -y \
       apt-utils build-essential \
       vim u-boot-tools git cmake \
       bison flex texinfo bzip2 \
       xz-utils unzip python wget \
       lua5.3 liblua5.3-dev libexpat1-dev \
       libpython2.7-dev zlib1g-dev libtinfo-dev && \
     rm -rf /var/lib/apt/lists/* && \
     #
     # Download and extract RTEMS Source Builder
     # 
     cd /usr/src && \ 
     wget https://ftp.rtems.org/pub/rtems/releases/5/5.0.0/5.0.0-m2004/sources/rtems-source-builder-5.0.0-m2004.tar.xz && \
     tar Jxf rtems-source-builder-5.0.0-m2004.tar.xz && \
     #
     # build the ARM RTEMS toolchain
     #
     cd rtems-source-builder-5.0.0-m2004/rtems && \
     ../source-builder/sb-set-builder --prefix=/opt/rtems/5.0.0-m2004 5/rtems-arm && \
     #
     # Clean up
     #
     cd /usr/src && \
     rm -rf rtems-source-builder-5.0.0-m2004

ENV PATH="/opt/rtems/5.0.0-m2004/bin:${PATH}"
