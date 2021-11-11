FROM rtems6-microblaze-tools:latest AS build
LABEL Description="rtems6 kcu105_qemu bsp"
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
