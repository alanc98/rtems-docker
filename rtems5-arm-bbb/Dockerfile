FROM rtems5-arm-tools:latest AS build
LABEL Description="rtems5 bbb"
ENV TERM linux

RUN cd /usr/src && \
    git clone --depth 1 git://git.rtems.org/rtems.git rtems && \
    cd rtems && \
    ./bootstrap && \
    cd .. && \
    mkdir b-arm && \
    cd b-arm && \
    ../rtems/configure --target=arm-rtems5 \
    --enable-rtemsbsp=beagleboneblack \
    --prefix=/opt/rtems5 \
    --disable-networking \
    --enable-posix  && \
    make -j8 && \
    make install && \
    cd .. && \
    rm -rf b-arm 

