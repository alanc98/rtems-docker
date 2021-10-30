FROM rtems-essential:latest AS build
LABEL Description="rtems5 ARM tool set"
ENV TERM linux

RUN cd /usr/src && \
    git clone --branch 5 --depth 1 git://git.rtems.org/rtems-source-builder.git rsb && \
    cd /usr/src/rsb && \
    ./source-builder/sb-check && \
    cd /usr/src/rsb/rtems && \
    ../source-builder/sb-set-builder --prefix=/opt/rtems5 5/rtems-arm && \
    cd /usr/src && \
    rm -rf rsb

ENV PATH="/opt/rtems5/bin:${PATH}"

