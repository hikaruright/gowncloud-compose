FROM golang:latest

LABEL maintener="hikaruright"

RUN mkdir -p $GOPATH/src/github.com/gowncloud
RUN cd $GOPATH/src/github.com/gowncloud
RUN git clone https://github.com/gowncloud/gowncloud.git
RUN cd gowncloud
RUN go generate
RUN go build

RUN echo './gowncloud -c [client_id] -s [client_secret] --db "[database_driver]://[database_user]@[database_url]:[database_port]?sslmode=disable"' > ~/run.sh
RUN chomod +x ~/run.sh

ENTRYPOINT [ "~/run.sh" ]
