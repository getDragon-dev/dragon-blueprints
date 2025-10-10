# syntax=docker/dockerfile:1
FROM golang:1.25.2-alpine AS build
WORKDIR /app
COPY . .
RUN go mod tidy && go build -o app

FROM alpine:3.20
WORKDIR /app
COPY --from=build /app/app /usr/local/bin/app
EXPOSE 8080
CMD ["app"]
