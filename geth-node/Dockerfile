#FROM ethereum/client-go:stable
FROM redtree941/eth-client-go:arm
USER root
RUN apt-get update && apt-get install curl -y
RUN mkdir -p /home/eth-node
WORKDIR /home/eth-node
ADD runGeth.sh /home/eth-node/runGeth.sh

ENTRYPOINT ["bash", "runGeth.sh"]


