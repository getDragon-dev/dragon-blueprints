FROM golang:1.25-alpine AS build
WORKDIR /src
COPY . .
RUN go mod tidy && go build -o app ./cmd/{{ .Name }}

FROM alpine:3.22@sha256:4b7ce07002c69e8f3d704a9c5d6fd3053be500b7f1c69fc0d80990c2ad8dd412
COPY --from=build /src/app /usr/local/bin/app
ENV APP_PORT=8080
EXPOSE 8080
ENTRYPOINT ["app"]