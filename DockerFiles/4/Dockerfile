FROM golang

WORKDIR /app
ADD . .
RUN go mod init v1
RUN go mod tidy
RUN go build -o meugo
ENTRYPOINT ./meugo
