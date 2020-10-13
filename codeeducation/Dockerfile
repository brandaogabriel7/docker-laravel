FROM golang:alpine AS builder

RUN apk update && apk add --no-cache git
WORKDIR $GOPATH/src/mypackage/myapp/
COPY . .

RUN go get -d -v

RUN GOOS=linux GOARCH=amd64 go build -ldflags="-w -s" -o /go/bin/codeeducation

FROM scratch

COPY --from=builder /go/bin/codeeducation /go/bin/codeeducation

ENTRYPOINT ["/go/bin/codeeducation"]