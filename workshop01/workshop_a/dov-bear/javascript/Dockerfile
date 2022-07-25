FROM node:18

WORKDIR /app

ADD main.js .
ADD package.json .
ADD package-lock.json .
ADD public public
ADD views views

RUN npm ci

ENV PORT=5000
ENV INSTANCE_NAME="We Bare Bears"
ENV INSTANCE_HASH="5js2"

ENTRYPOINT [ "node", "main.js" ]
