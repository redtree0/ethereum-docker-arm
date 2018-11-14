FROM redtree941/eth-client-go:arm

RUN echo "deb http://mirror.ox.ac.uk/sites/archive.raspbian.org/archive/raspbian stretch main contrib non-free rpi" >> /etc/apt/sources.list 
RUN echo "deb-src http://mirror.ox.ac.uk/sites/archive.raspbian.org/archive/raspbian stretch main contrib non-free rpi" >> /etc/apt/sources.list

RUN  apt-get update \
  && apt-get install --no-install-recommends -y wget \
  && rm -rf /var/lib/apt/lists/*

RUN \
  wget https://raw.githubusercontent.com/MaximilianMeister/kubernet-eth/master/scripts/start_boot.sh -O /start_boot.sh && \
  chmod +x /start_boot.sh

EXPOSE 30301

ENTRYPOINT ["/start_boot.sh"]

