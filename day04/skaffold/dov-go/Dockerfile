ARG GO_VER="1.18-alpine3.16"
ARG ALPINE_VER="3.16"

# build stage
FROM golang:${GO_VER} AS builder

WORKDIR /app

# add files, sequence matter from less likely change to most frequent change
ADD go.mod .
ADD go.sum .
ADD main.go .

# build the app
RUN go build -o main .


# runtime stage
FROM alpine:${ALPINE_VER} AS final

RUN apk --no-cache add curl

WORKDIR /app

COPY --from=builder /app/main /app/main

# copy runtime files
ADD public public
ADD templates templates

USER 1000

ENV PORT=5000
ENV INSTANCE_NAME="We Gogo Bears"
ENV INSTANCE_HASH="5go2"

HEALTHCHECK --interval=30s --timeout=5s --start-period=5s --retries=3 \
  CMD curl http://localhost:${PORT}/healthz > /dev/null || exit 1 

ENTRYPOINT [ "./main" ]
