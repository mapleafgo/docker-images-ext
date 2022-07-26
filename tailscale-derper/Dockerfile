FROM bitnami/golang:latest AS builder
RUN GOPROXY=https://goproxy.cn go install tailscale.com/cmd/derper@main

FROM debian:stable-slim
WORKDIR /app
COPY --from=builder /go/bin/derper /app
EXPOSE 3478 443
CMD ["/app/derper"]
