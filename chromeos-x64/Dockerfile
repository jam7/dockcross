FROM jam7/base:latest
MAINTAINER Kazushi (Jam) Marukawa "jam@pobox.com"

RUN apt-get install -y \
  libcurl3 \
  liblzma5

# RUN ln -s /lib/x86_64-linux-gnu/ld-2.19.so /lib64
RUN ln -s /lib/x86_64-linux-gnu/libc.so.6 /lib64
RUN ln -s /lib/x86_64-linux-gnu/libpthread.so.0 /lib64

#ENV CROSS_TRIPLE x86_64-linux-gnu
#ENV CROSS_ROOT /usr/bin
#ENV AS=/usr/bin/${CROSS_TRIPLE}-as \
#    AR=/usr/bin/${CROSS_TRIPLE}-ar \
#    CC=/usr/bin/${CROSS_TRIPLE}-gcc \
#    CPP=/usr/bin/${CROSS_TRIPLE}-cpp \
#    CXX=/usr/bin/${CROSS_TRIPLE}-g++ \
#    LD=/usr/bin/${CROSS_TRIPLE}-ld \
ENV LD_LIBRARY_PATH=/usr/local/lib:/usr/local/lib64:/lib/x86_64-linux-gnu

#COPY ${CROSS_TRIPLE}-noop.sh /usr/bin/${CROSS_TRIPLE}-noop
#COPY Toolchain.cmake /usr/lib/${CROSS_TRIPLE}/
#ENV CMAKE_TOOLCHAIN_FILE /usr/lib/${CROSS_TRIPLE}/Toolchain.cmake

ENV DEFAULT_DOCKCROSS_IMAGE jam7/chromeos-x64

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
