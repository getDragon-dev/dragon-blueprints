FROM golang:1.25-alpine@sha256:26111811bc967321e7b6f852e914d14bede324cd1accb7f81811929a6a57fea9 AS build
WORKDIR /src
COPY . .
RUN go mod tidy && go build -o app ./cmd/{{ .Name }}

FROM alpine:3.23@sha256:51183f2cfa6320055da30872f211093f9ff1d3cf06f39a0bdb212314c5dc7375
COPY --from=build /src/app /usr/local/bin/app
ENV APP_PORT=8080
EXPOSE 8080
ENTRYPOINT ["app"]