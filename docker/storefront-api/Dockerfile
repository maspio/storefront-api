FROM node:10-alpine3.11

RUN apk update && apk upgrade

RUN apk add --no-cache curl git

RUN apk add --no-cache --virtual .build-deps ca-certificates wget nasm bash && apk del .build-deps

ENV VS_ENV dev

WORKDIR /var/www

COPY package.json ./
COPY yarn.lock ./

RUN yarn install --frozen-lockfile --no-cache && yarn cache clean --force

RUN yarn global add nodemon

CMD ["yarn", "dev"]
