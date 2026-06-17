FROM golang:1.26-alpine@sha256:f1ddd9fe14fffc091dd98cb4bfa999f32c5fc77d2f2305ea9f0e2595c5437c14 AS build
WORKDIR /src
COPY . .
RUN go mod tidy && go build -o app ./cmd/{{ .Name }}

FROM alpine:3.24@sha256:28bd5fe8b56d1bd048e5babf5b10710ebe0bae67db86916198a6eec434943f8b
COPY --from=build /src/app /usr/local/bin/app
ENV APP_PORT=8080
EXPOSE 8080
ENTRYPOINT ["app"]