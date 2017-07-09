# docker run -it --rm go

# Pull base image.
FROM amazonlinux

RUN yum update -y && yum install -y \
    wget \
    procps \
    git \
# gcc for cgo
    gcc \
  && yum clean all

# Install Go
ENV GOLANG_VERSION 1.8.1

RUN set -eux; \
    url="https://golang.org/dl/go${GOLANG_VERSION}.linux-amd64.tar.gz"; \
    wget -O go.tgz "$url"; \
    echo 'a579ab19d5237e263254f1eac5352efcf1d70b9dacadb6d6bb12b0911ede8994 *go.tgz' | sha256sum -c -; \
    tar -C /usr/local -xzf go.tgz; \
    rm go.tgz; \
    export PATH="/usr/local/go/bin:$PATH"; \
    go version

ENV GOPATH /go
ENV PATH $GOPATH/bin:/usr/local/go/bin:$PATH

RUN mkdir -p "$GOPATH/src" "$GOPATH/bin" && chmod -R 777 "$GOPATH"
WORKDIR $GOPATH

# Define default command.
CMD ["bash"]
