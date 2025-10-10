# syntax=docker/dockerfile:1
FROM golang:1.25.2-alpine AS build
WORKDIR /app
COPY . .
RUN go mod tidy && go build -o app

FROM alpine:3.21@sha256:5405e8f36ce1878720f71217d664aa3dea32e5e5df11acbf07fc78ef5661465b
WORKDIR /app
COPY --from=build /app/app /usr/local/bin/app
EXPOSE 8080
CMD ["app"]
