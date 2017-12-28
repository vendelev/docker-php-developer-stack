FROM node:alpine

ENV TIMEZONE=Europe/Moscow

RUN apk update \
    && apk add tzdata \
    && cp /usr/share/zoneinfo/${TIMEZONE} /etc/localtime \
    && echo "${TIMEZONE}" > /etc/timezone \
    && apk del tzdata \
    && rm -frv /var/cache/apk/*