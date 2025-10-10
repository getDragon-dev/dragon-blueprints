# syntax=docker/dockerfile:1
FROM golang:1.25.2-alpine AS build
WORKDIR /app
COPY . .
RUN go mod tidy && go build -o app

FROM alpine:3.22@sha256:4b7ce07002c69e8f3d704a9c5d6fd3053be500b7f1c69fc0d80990c2ad8dd412
WORKDIR /app
COPY --from=build /app/app /usr/local/bin/app
EXPOSE 8080
CMD ["app"]
