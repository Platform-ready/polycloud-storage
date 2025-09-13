FROM golang:1.21 as builder
WORKDIR /app
COPY . .
RUN go mod tidy && go build -o service ./cmd/service

FROM gcr.io/distroless/base
COPY --from=builder /app/service /service
ENTRYPOINT ["/service"]
