FROM ubuntu:22.04
RUN apt update && apt install -y wget

RUN wget -qO- https://go.dev/dl/go1.22.4.linux-amd64.tar.gz | tar xvz -C /usr/local
ENV PATH="${PATH}:/usr/local/go/bin"
WORKDIR /usr/src/app

COPY . .
RUN go build
RUN go test ./...
ENV REQUEST_ORIGIN=*
ENV PORT=8000
EXPOSE 8000
ENTRYPOINT ["./server"]
