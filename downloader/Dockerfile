FROM ubuntu:18.04

VOLUME ["/apt"]

RUN mkdir -p /apt

WORKDIR /apt

RUN export DEBIAN_FRONTEND=noninteractive

RUN apt-get -y update 

RUN apt-get install -y systemd 

ARG PACKAGES="systemd curl git"

RUN apt-get download $(apt-cache depends --recurse --no-recommends --no-suggests \
    --no-conflicts --no-breaks --no-replaces --no-enhances \
    --no-pre-depends ${PACKAGES} | grep "^\w")

RUN apt-get install -y --download-only ${PACKAGES} 
