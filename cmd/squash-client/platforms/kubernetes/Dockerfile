FROM ubuntu:16.04

RUN apt-get update
RUN apt-get install --yes gdb build-essential
RUN apt-get install --yes git
RUN apt-get install --yes curl
# RUN apt-get install --yes golang-1.8-go


RUN curl https://storage.googleapis.com/golang/go1.8.linux-amd64.tar.gz | tar -C /usr/lib -xz

ENV GOROOT /usr/lib/go
ENV GOPATH /gopath
ENV GOBIN /gopath/bin
ENV PATH $PATH:$GOROOT/bin:$GOPATH/bin

RUN mkdir -p $GOPATH/src/github.com/derekparker/ && cd  $GOPATH/src/github.com/derekparker/ && git clone https://github.com/derekparker/delve/
RUN cd $GOPATH/src/github.com/derekparker/delve/ && git checkout v1.0.0-rc.1
RUN cd $GOPATH/src/github.com/derekparker/delve/cmd/dlv && go install

COPY squash-client /

EXPOSE 1234

ENTRYPOINT ["/squash-client"]
