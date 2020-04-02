FROM rtems4.11-i386-tools:latest AS build
LABEL Description="rtems4.11-pc686 kernel environment"
ENV TERM linux

WORKDIR /usr/src
RUN cd /usr/src && \
    git clone --branch 4.11 --depth 1 git://git.rtems.org/rtems.git rtems && \
    cd /usr/src/rtems && \
    ./bootstrap && \
    cd /usr/src && \
    mkdir b-pc686 && \
    cd /usr/src/b-pc686 && \
    ../rtems/configure --target=i386-rtems4.11 \
       --enable-rtemsbsp=pc686 \
       --prefix=/opt/rtems4.11 \
       --enable-networking \
       --enable-cxx \
       --disable-posix \
       --disable-deprecated \
       BSP_ENABLE_VGA=0 \
       CLOCK_DRIVER_USE_TSC=1 \
       USE_COM1_AS_CONSOLE=1 \
       BSP_PRESS_KEY_FOR_RESET=0 \
       BSP_RESET_BOARD_AT_EXIT=1 && \
    make -j8 && \
    make install && \
    cd /usr/src && \
    rm -rf rtems && \
    rm -rf b-pc686
