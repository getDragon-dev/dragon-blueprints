FROM golang:1.27-alpine@sha256:d200d2dd76b03a99b52651fd1325aff7dcd35422c35c01bac56571b0507f3deb AS build
WORKDIR /src
COPY . .
RUN go mod tidy && go build -o app ./cmd/{{ .Name }}

FROM alpine:3.24@sha256:3f4d6b32e26703c6082839234f43769d5046b3ac7c910033911d1e71d8cd630a
COPY --from=build /src/app /usr/local/bin/app
ENV APP_PORT=8080
EXPOSE 8080
ENTRYPOINT ["app"]