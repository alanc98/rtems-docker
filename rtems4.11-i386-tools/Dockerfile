FROM rtems-essential:latest AS build
LABEL Description="rtems4.11 i386 basic tool set"
ENV TERM linux

RUN cd /usr/src && \
    git clone --branch 4.11 --depth 1 git://git.rtems.org/rtems-source-builder.git rsb && \
    cd /usr/src/rsb && \
    ./source-builder/sb-check && \
    cd /usr/src/rsb/rtems && \
    ../source-builder/sb-set-builder --prefix=/opt/rtems4.11 4.11/rtems-i386 && \
    cd /usr/src && \
    rm -rf rsb

ENV PATH="/opt/rtems4.11/bin:${PATH}"
