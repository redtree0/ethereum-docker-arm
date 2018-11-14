FROM resin/armhf-alpine:edge-20180718

RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
        ca-certificates \
    && update-ca-certificates 2>/dev/null || true

RUN \
  apk add --update git go make gcc musl-dev linux-headers openssl bash && \
  git clone https://github.com/ethereum/go-ethereum                                    && \
  (cd go-ethereum && git checkout release/1.7  && make geth)                            && \
  cp go-ethereum/build/bin/geth /bin/geth                                              && \
  cp go-ethereum/build/bin/geth /usr/local/bin/                                        && \
  apk del git go make gcc musl-dev linux-headers                                       && \
  rm -rf /go-ethereum && rm -rf /var/cache/apk/*

EXPOSE 8545 8546 30303 30303/udp
ENTRYPOINT ["geth"]
