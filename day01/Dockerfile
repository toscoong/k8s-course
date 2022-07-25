# parameters
ARG NODE_VER=18

# base image
FROM node:${NODE_VER}

# building the image
# create /app and cd into it
WORKDIR /app

# RUN apt update && apt install xxx

# copy app into /app
ADD main.js .
ADD package.json .
ADD package-lock.json .

# copy the folder and specify the destination folder name
ADD public public
ADD views views

# install the dependencies
RUN npm ci

# install curl
# RUN apt update && apt install curl -y

# running the imag
# set any environment variables required by the application
ENV APP_PORT=5000

# healthcheck, expect a return value 0 if successful
HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
  CMD curl http://localhost${APP_PORT}/healthz > /dev/null || exit 1

ENTRYPOINT [ "node", "main.js" ]
