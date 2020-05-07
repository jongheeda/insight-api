FROM node:8.15

RUN apt-get update && apt-get install -y \
  cmake \
  libzmq3-dev \
  python-minimal \
  git \
  wget curl \
  build-essential libtool autotools-dev automake pkg-config libssl-dev libevent-dev bsdmainutils dh-autoreconf \
  libboost-system-dev libboost-filesystem-dev libboost-chrono-dev libboost-program-options-dev libboost-test-dev libboost-thread-dev



RUN wget https://github.com/dashpay/dash/releases/download/v0.15.0.0/dashcore-0.15.0.0-x86_64-linux-gnu.tar.gz
RUN tar -xvzf dashcore-0.15.0.0-x86_64-linux-gnu.tar.gz
RUN rm dashcore-0.15.0.0-x86_64-linux-gnu.tar.gz

#RUN cp -R /dash/depends/x86_64-pc-linux-gnu/. /usr/local/.
# RUN apk --no-cache --update add libstdc++ bash


RUN npm install -g --unsafe-perm=true @dashevo/dashcore-node
RUN dashcore-node create mynode

WORKDIR /mynode
RUN ls -al

RUN dashcore-node install @dashevo/insight-api
RUN dashcore-node install @dashevo/insight-ui

COPY ./dashcore-node.json /mynode

EXPOSE 3001
CMD [ "dashcore-node", "start" ]
