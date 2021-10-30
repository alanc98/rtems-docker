FROM rtems5-sparc-tools:latest AS build
LABEL Description="rtems5 SPARC Leon3 bsp"
ENV TERM linux

RUN cd /usr/src && \
    git clone --branch 5 --depth 1 git://git.rtems.org/rtems.git rtems && \
    cd rtems && \
    ./bootstrap && \
    cd .. && \
    mkdir b-sparc && \
    cd b-sparc && \
    ../rtems/configure --target=sparc-rtems5 \
    --enable-rtemsbsp=leon3 \
    --prefix=/opt/rtems5 \
    --enable-networking \
    --enable-posix  && \
    make -j8 && \
    make install && \
    cd .. && \
    rm -rf b-sparc

