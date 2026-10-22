FROM golang:1.27-alpine@sha256:f2c872bcee949b7be9c490efd02b48a8a2fbf947cdf533f1c58525ec9d8170fd AS build
WORKDIR /src
COPY . .
RUN go mod tidy && go build -o app ./cmd/{{ .Name }}

FROM alpine:3.24@sha256:c6b073f8e9e58d881f6ffba6ebf3b9ebd60b9e7d6e8337018c0e68bb5c356873
COPY --from=build /src/app /usr/local/bin/app
ENV APP_PORT=8080
EXPOSE 8080
ENTRYPOINT ["app"]