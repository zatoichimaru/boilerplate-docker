FROM node:16-alpine as base

LABEL maintainer "William Tenório da Silva <contato@williamtenorio.com.br>"

WORKDIR /usr/src/app/

COPY package*.json ./

RUN apk update \
    && apk --no-cache --update add git python3 build-base \
    && npm install -g npm  \
    && npm install \
    && npm cache clean --force

COPY . .

FROM base as local
CMD ["npm", "run", "local"]

FROM base as development
CMD ["npm", "run", "dev"]

FROM base as test
CMD ["npm", "run", "test"]

FROM base as production
CMD ["npm", "run", "start"]