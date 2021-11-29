FROM rtems6-aarch64-tools:latest AS build
LABEL Description="rtems6 A53 QEMU bsp"
ENV TERM linux
COPY config.ini /config.ini
RUN cd /usr/src && \
    git clone --depth 1 git://git.rtems.org/rtems.git rtems && \
    cd rtems && \
    mv /config.ini . && \
    ./waf configure \
    --prefix=/opt/rtems6 && \
    ./waf && \
    ./waf install
