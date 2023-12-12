FROM ubuntu:20.04

RUN apt-get update \
    && apt-get -y install apt-transport-https lsb-core lsb-release net-tools netcat-openbsd sudo \
    && touch /usr/bin/firewall-cmd \
    && chmod +x /usr/bin/firewall-cmd \
    && useradd -m expedition \
    && chmod 755 /root

COPY ./setup /setup
WORKDIR /setup

ENV TERM=xterm

RUN ./initSetup.sh \
    && rm -rf /var/lib/apt/lists/* /tmp/* /var/tmp/* \
    && apt-get clean

WORKDIR /

COPY start.sh /
CMD ["/start.sh"]
