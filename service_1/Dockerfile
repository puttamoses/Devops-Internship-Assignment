FROM golang:1.20

# Set GOPATH mode (disables module mode)
ENV GO111MODULE=off

# Set up GOPATH and working dir
WORKDIR /go/src/app

# Copy your source code
COPY . .

# Build using GOPATH style
RUN go build -o service1

EXPOSE 8001

CMD ["./service1"]