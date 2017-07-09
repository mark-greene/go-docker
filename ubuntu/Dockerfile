# docker run -it --rm go

# Pull base image.
FROM ubuntu

RUN apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    tzdata \
    curl \
    wget \
    procps \
    openssh-client \
    git \
  && rm -rf /var/lib/apt/lists/*

RUN ln -fs /usr/share/zoneinfo/US/Eastern /etc/localtime && dpkg-reconfigure -f noninteractive tzdata

# gcc for cgo
RUN apt-get update && apt-get install -y --no-install-recommends \
    g++ \
    gcc \
    libc6-dev \
    make \
    pkg-config \
  && rm -rf /var/lib/apt/lists/*

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
