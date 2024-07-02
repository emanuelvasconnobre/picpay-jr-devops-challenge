FROM golang:1.16
WORKDIR /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go
COPY . /go/src/github.com/PicPay/picpay-jr-devops-challenge/services/go

RUN go mod download
RUN go mod tidy

EXPOSE 8080
CMD ["go","run","main.go"]