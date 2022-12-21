FROM golang AS buildando

WORKDIR /app
ADD . .
RUN go mod init v1
RUN go mod tidy
RUN go build -o meugo

FROM alpine
WORKDIR /app
COPY --from=buildando /app/meugo /app 

ENTRYPOINT ./meugo
