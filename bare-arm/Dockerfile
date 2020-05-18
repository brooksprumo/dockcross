FROM dockcross/base:latest
MAINTAINER Brooks Prumo <brooks@prumo.org>

RUN apt-get update && apt-get install -y \
	tar \
	bzip2 \
	curl

ENV ARM_GCC_VERSION 9-2019-q4-major
ENV CROSS_TRIPLE arm-none-eabi
ENV CROSS_ROOT /opt/gcc-${CROSS_TRIPLE}-${ARM_GCC_VERSION}

RUN curl https://armkeil.blob.core.windows.net/developer/Files/downloads/gnu-rm/9-2019q4/gcc-${CROSS_TRIPLE}-${ARM_GCC_VERSION}-x86_64-linux.tar.bz2 | tar -xjC /opt

ENV AS=${CROSS_ROOT}/bin/${CROSS_TRIPLE}-as \
    AR=${CROSS_ROOT}/bin/${CROSS_TRIPLE}-ar \
    CC=${CROSS_ROOT}/bin/${CROSS_TRIPLE}-gcc \
    CPP=${CROSS_ROOT}/bin/${CROSS_TRIPLE}-cpp \
    CXX=${CROSS_ROOT}/bin/${CROSS_TRIPLE}-g++ \
    LD=${CROSS_ROOT}/bin/${CROSS_TRIPLE}-ld

ENV PATH=${CROSS_ROOT}/bin:$PATH
ENV DEFAULT_DOCKCROSS_IMAGE dockcross/bare-arm

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
