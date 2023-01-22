FROM ubuntu:22.04

RUN apt-get update && apt-get install -y tzdata
# timezone setting
ENV TZ=Asia/Tokyo 

# package install
RUN apt-get update && apt-get upgrade -y \
    && apt-get install -y git \
    && apt-get install -y xz-utils \
    && apt-get install -y wget

# server-data extracting
RUN mkdir -p /opt/cfx-server/server \
    && cd /opt/cfx-server/server \
    && wget https://runtime.fivem.net/artifacts/fivem/build_proot_linux/master/6025-df07de437f9f4738383e6ff0bfd3a46e8c9df08d/fx.tar.xz \
    && tar -xf fx.tar.xz

# clone & build cfx-server
RUN mkdir -p /opt/cfx-server/server-data/resources\
    && git clone --depth 1 https://github.com/citizenfx/cfx-server-data.git /usr/src/cfx-server/
RUN cp -rf /usr/src/cfx-server/resources/* /opt/cfx-server/server-data/resources/

# txAdmin pre execute
COPY "txAdmin_settings/config.json" "/opt/cfx-server/server/txData/dev_server/"