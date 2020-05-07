FROM node:8

RUN apt-get update && apt-get install -y \
  libzmq3-dev \
  python-minimal

RUN npm install -g --unsafe-perm=true bitcore@latest
RUN bitcore create mynode

WORKDIR /mynode
RUN ls -al

RUN bitcore install insight-api
RUN bitcore install insight-ui

COPY ./bitcore-node.json /mynode

EXPOSE 3001
CMD [ "bitcore", "start" ]