FROM silphid/yey-base

#
# go
#
ARG GO_VERSION=1.16.5
ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH
RUN curl -fsL https://dl.google.com/go/go$GO_VERSION.linux-amd64.tar.gz \
    | tar xzv -C /usr/local && \
    mkdir -p "$GOPATH/src" "$GOPATH/bin" && \
    chmod -R 777 "$GOPATH"
