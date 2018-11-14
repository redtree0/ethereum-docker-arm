FROM redtree941/golang-raspbian-docker  

ENV PATH=$PATH

RUN \
  apt-get update && apt-get upgrade -q -y && \
  apt-get install -y --no-install-recommends git make gcc libc-dev ca-certificates wget && \
  git clone --depth 1 https://github.com/ethereum/go-ethereum && \
  (cd go-ethereum && make geth) && \
  cp go-ethereum/build/bin/geth /geth && \
  apt-get remove -y git make gcc libc-dev  && apt-get autoremove &&  apt-get clean && \
 # apt-get remove -y git make gcc libc-dev && apt autoremove -y && apt-get clean && \
  rm -rf /go-ethereum

EXPOSE 8545
EXPOSE 30303

ENTRYPOINT ["/geth"]
