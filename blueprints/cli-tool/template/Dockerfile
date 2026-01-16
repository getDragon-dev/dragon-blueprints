# syntax=docker/dockerfile:1@sha256:b6afd42430b15f2d2a4c5a02b919e98a525b785b1aaff16747d2f623364e39b6
FROM golang:1.25.6-alpine@sha256:bc2596742c7a01aa8c520a075515c7fee21024b05bfaa18bd674fe82c100a05d AS build
WORKDIR /app
COPY . .
RUN go mod tidy && go build -o app

FROM alpine:3.23@sha256:51183f2cfa6320055da30872f211093f9ff1d3cf06f39a0bdb212314c5dc7375
WORKDIR /app
COPY --from=build /app/app /usr/local/bin/app
EXPOSE 8080
CMD ["app"]
