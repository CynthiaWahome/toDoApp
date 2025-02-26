# filepath: auth-api/Dockerfile
FROM golang:1.21-alpine AS builder

WORKDIR /app

COPY go.mod go.sum ./

RUN go mod download && go mod verify

COPY . .

RUN CGO_ENABLED=0 GOOS=linux GOARCH=amd64 \
    go build -ldflags="-w -s" -o auth-api

FROM alpine:latest AS runtime

RUN apk add --no-cache ca-certificates

WORKDIR /app

COPY --from=builder /app/auth-api .

EXPOSE 8081

CMD ["./auth-api"]