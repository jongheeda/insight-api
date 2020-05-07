FROM node:8

RUN apt-get update && apt-get install -y \
  libzmq3-dev \
  python-minimal

RUN npm install -g --unsafe-perm=true litecore-node@latest
RUN litecore-node create mynode

WORKDIR /mynode
RUN ls -al

RUN litecore-node install insight-lite-api
RUN litecore-node install insight-lite-ui

COPY ./litecore-node.json /mynode

EXPOSE 3001
CMD [ "litecore-node", "start" ]

