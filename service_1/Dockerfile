FROM golang:1.22-alpine

WORKDIR /app
COPY . .
RUN go build -o app .
EXPOSE 8001
CMD ["./app"]
