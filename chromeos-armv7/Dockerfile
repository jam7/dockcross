FROM jam7/base:latest
MAINTAINER Kazushi (Jam) Marukawa "jam@pobox.com"

# Add the cross compiler sources
RUN echo "deb http://emdebian.org/tools/debian/ jessie main" >> /etc/apt/sources.list && \
  dpkg --add-architecture armhf && \
  curl http://emdebian.org/tools/debian/emdebian-toolchain-archive.key | apt-key add -

RUN apt-get update && apt-get install -y \
  crossbuild-essential-armhf \
  gfortran-arm-linux-gnueabihf \
  qemu-user \
  qemu-user-static \
  libbz2-dev:armhf \
  libexpat1-dev:armhf \
  ncurses-dev:armhf \
  libssl-dev:armhf

RUN apt-get install -y \
  libcurl3:armhf \
  liblzma5:armhf

# RUN ln -s /lib/arm-linux-gnueabihf/ld-2.19.so /lib
RUN ln -s /lib/arm-linux-gnueabihf/libc.so.6 /lib
RUN ln -s /lib/arm-linux-gnueabihf/libpthread.so.0 /lib

#ENV CROSS_TRIPLE arm-linux-gnueabihf
#ENV CROSS_ROOT /usr/${CROSS_TRIPLE}
#ENV AS=/usr/bin/${CROSS_TRIPLE}-as \
#    AR=/usr/bin/${CROSS_TRIPLE}-ar \
#    CC=/usr/bin/${CROSS_TRIPLE}-gcc \
#    CPP=/usr/bin/${CROSS_TRIPLE}-cpp-4.9 \
#    CXX=/usr/bin/${CROSS_TRIPLE}-g++ \
#    LD=/usr/bin/${CROSS_TRIPLE}-ld
ENV LD_LIBRARY_PATH=/usr/local/lib:/lib/arm-linux-gnueabihf

ENV DEFAULT_DOCKCROSS_IMAGE jam7/chromeos-armv7

# Note: Toolchain file support is currently in debian Experimental:
# https://wiki.debian.org/CrossToolchains#In_jessie_.28Debian_8.29
#COPY Toolchain.cmake /usr/lib/${CROSS_TRIPLE}/
#ENV CMAKE_TOOLCHAIN_FILE /usr/lib/${CROSS_TRIPLE}/Toolchain.cmake

# Build-time metadata as defined at http://label-schema.org
ARG BUILD_DATE
ARG IMAGE
ARG VCS_REF
ARG VCS_URL
LABEL org.label-schema.build-date=$BUILD_DATE \
      org.label-schema.name=$IMAGE \
      org.label-schema.vcs-ref=$VCS_REF \
      org.label-schema.vcs-url=$VCS_URL \
      org.label-schema.schema-version="1.0"
