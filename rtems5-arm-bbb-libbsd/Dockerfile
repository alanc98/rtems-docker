FROM rtems5-arm-bbb:latest AS build
LABEL Description="rtems5 bbb libbsd"
ENV TERM linux

RUN cd /usr/src && \
    git clone git://git.rtems.org/rtems-libbsd.git rtems-libbsd && \
    cd rtems-libbsd && \
    git submodule init && \
    git submodule update && \
    ./waf configure --prefix="/opt/rtems5" \
    --rtems-tools="/opt/rtems5" \
    --rtems-bsps=arm/beagleboneblack \
    --buildset=buildset/default.ini && \
    ./waf && \
    ./waf install && \
    cd .. && \
    rm -rf rtems-libbsd
