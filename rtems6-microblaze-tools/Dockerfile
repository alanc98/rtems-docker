FROM rtems6-qemu-xilinx:latest AS build
LABEL Description="rtems5 Microblaze tool chain"
ENV TERM linux

RUN cd /usr/src && \
    git clone --depth 1 git://git.rtems.org/rtems-source-builder.git rsb && \
    cd /usr/src/rsb && \
    ./source-builder/sb-check && \
    cd /usr/src/rsb/rtems && \
    ../source-builder/sb-set-builder --prefix=/opt/rtems6 6/rtems-microblaze && \
    cd /usr/src && \
    rm -rf rsb

ENV PATH="/opt/rtems6/bin:${PATH}"

