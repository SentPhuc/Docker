FROM ams-php-fpm-81:latest AS php81
RUN apk add git
WORKDIR /srv

FROM ams-php-fpm-74:latest AS php74
RUN apk add git
WORKDIR /srv

FROM ams-node14:latest AS node14
WORKDIR /usr
COPY ./node_src .
RUN yarn
CMD ["yarn", "start"]
WORKDIR /usr

FROM ams-node16:latest AS node16
WORKDIR /usr
COPY ./node_src .
RUN yarn
CMD ["yarn", "start"]
WORKDIR /usr