FROM dockcross/bare-arm:latest
MAINTAINER Brooks Prumo <brooks@prumo.org>

RUN apt-get update && apt-get install -y \
	python3 \
	python3-dev \
	python3-pip \
	mercurial

RUN pip3 install -U mbed-cli
ENV PATH=~/.local/bin:$PATH
RUN unset AS AR CC CPP CXX LD && pip3 install -U -r https://raw.githubusercontent.com/ARMmbed/mbed-os/master/requirements.txt
RUN mbed toolchain --global GCC_ARM

ENV DEFAULT_DOCKCROSS_IMAGE dockcross/mbed-arm

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
