# 1. Aşama: Go uygulamasını derle
FROM golang:1.22.1 AS builder

WORKDIR /app

# Go mod dosyalarını kopyala ve bağımlılıkları indir
COPY go.mod go.sum ./
RUN go mod download

# Uygulama dosyalarını kopyala ve derle
COPY . .
RUN go build -o main.exe .

# 2. Aşama: Küçük ve optimize bir imaj oluştur
FROM alpine:latest

WORKDIR /root/

# Önceki aşamada derlenen dosyayı kopyala
COPY --from=builder /app/main.exe .

# Container çalıştırıldığında bu komutu kullan
CMD ["./main.exe"]
