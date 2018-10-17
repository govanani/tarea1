############# TALLER 1 - TAREA 1

FROM node:6.14.4-alpine
ENV HOME /usr/src
WORKDIR $HOME/app

RUN apk add --update tini

COPY package.json $HOME/app/

RUN chown -R node:node $HOME/*

RUN npm config set registry http://registry.npmjs.org \
    && npm install \
    && npm cache clean


COPY . /tmp/app
RUN chown -R node:node /tmp/app \
    && cp -rp /tmp/app $HOME \
    && rm -rf /tmp/app

EXPOSE 80


# Tini is installed at /sbin/tini
ENTRYPOINT ["/sbin/tini", "--", "node", "./bin/www"]
