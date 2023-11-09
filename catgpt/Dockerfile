FROM golang:1.21 AS builder
WORKDIR /app
COPY . .
COPY go.mod .
COPY go.sum .
RUN go mod download
RUN CGO_ENABLED=0 go build -o /app/myapp
FROM gcr.io/distroless/static-debian12:latest-amd64
WORKDIR /
COPY --from=builder /app/myapp .
EXPOSE 8080
CMD ["./myapp"]