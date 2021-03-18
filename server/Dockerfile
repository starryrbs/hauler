FROM golang:alpine

ENV GO111MODULE=on
ENV GOPROXY=https://goproxy.io,direct
WORKDIR /go/src/hauler

COPY server/ ./

RUN go env && go build -o server .

FROM alpine:latest

COPY --from=0 /go/src/hauler/server ./

EXPOSE 8080

ENV GIN_MODE=release

ENTRYPOINT server