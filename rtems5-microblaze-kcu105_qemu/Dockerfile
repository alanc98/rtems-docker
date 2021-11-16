FROM rtems5-microblaze-tools:latest AS build
LABEL Description="rtems5 Microblaze KCU105_QEMU bsp"
ENV TERM linux

RUN cd /usr/src && \
    git clone --branch 5 --depth 1 git://git.rtems.org/rtems.git rtems && \
    cd rtems && \
    ./bootstrap && \
    cd .. && \
    mkdir b-microblaze && \
    cd b-microblaze && \
    ../rtems/configure --target=microblaze-rtems5 \
    --enable-rtemsbsp=kcu105_qemu \
    --prefix=/opt/rtems5 \
    --enable-networking \
    --enable-posix  && \
    make -j8 && \
    make install && \
    cd .. && \
    rm -rf b-microblaze

