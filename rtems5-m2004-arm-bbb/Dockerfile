FROM rtems5-m2004-arm-tools:latest
LABEL Description="RTEMS 5 m2004 release ARM Beaglebone Black + libbsd build"
ENV DEBIAN_FRONTEND noninteractive
ENV TERM linux

#
# Download and build a specific release of RTEMS,
# then build RTEMS for the ARM/Beaglebone Black with LibBSD support
#    This can be customized for different targets and BSPs
#   
RUN  cd /usr/src && \ 
     #
     # download RTEMS
     #
     wget https://ftp.rtems.org/pub/rtems/releases/5/5.0.0/5.0.0-m2004/sources/rtems-5.0.0-m2004.tar.xz && \
     tar Jxf rtems-5.0.0-m2004.tar.xz && \
     #
     # Build RTEMS
     #
     cd rtems-5.0.0-m2004 && \
     ./bootstrap && \
     cd .. && \
     mkdir b-arm && \
     cd b-arm && \
       ../rtems-5.0.0-m2004/configure --target=arm-rtems5 \
       --enable-rtemsbsp=beagleboneblack \
       --prefix=/opt/rtems/5.0.0-m2004 \
       --disable-networking \
       --enable-posix  && \
     make -j8 && \
     make install && \
     #
     # Clean up
     #
     cd .. && \
     rm -rf b-arm && \
     #
     # Get rtems-libbsd 
     #
     cd /usr/src && \
     wget https://ftp.rtems.org/pub/rtems/releases/5/5.0.0/5.0.0-m2004/sources/rtems-libbsd-5.0.0-m2004.tar.xz && \
     tar Jxf rtems-libbsd-5.0.0-m2004.tar.xz && \
     cd rtems-libbsd-5.0.0-m2004 && \
     ./waf configure --prefix="/opt/rtems/5.0.0-m2004" \
       --rtems-tools="/opt/rtems/5.0.0-m2004" \
       --rtems-bsps=arm/beagleboneblack \
       --buildset=buildset/default.ini && \
     ./waf && \
     ./waf install && \
     #
     # Clean up
     #
     cd .. && \
     rm -rf rtems-libbsd-5.0.0-m2004
