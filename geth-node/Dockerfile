FROM resin/armhf-alpine:edge-20180718


RUN apk update \
    && apk upgrade \
    && apk add --no-cache \
        ca-certificates \
    && update-ca-certificates 2>/dev/null || true

RUN \
  apk add --update git go make gcc musl-dev linux-headers openssl bash && \
  git clone https://github.com/ethereum/go-ethereum                                    && \
  (cd go-ethereum && git checkout release/1.7  && make all)                            && \
  cp go-ethereum/build/bin/bootnode /bootnode                                          && \
  cp go-ethereum/build/bin/geth /geth                                                  && \
  apk del git go make gcc musl-dev linux-headers                                       && \
  rm -rf /go-ethereum && rm -rf /var/cache/apk/*

RUN \
  wget https://raw.githubusercontent.com/MaximilianMeister/kuberneteth/master/scripts/start_boot.sh -O /start_boot.sh && \
  chmod +x /start_boot.sh

EXPOSE 30303

ENTRYPOINT ["/start_boot.sh"]


