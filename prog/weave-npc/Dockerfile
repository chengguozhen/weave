FROM alpine

LABEL maintainer "Weaveworks Inc <help@weave.works>"
LABEL works.weave.role=system \
      org.label-schema.name="Weave Net" \
      org.label-schema.description="Weave Net creates a virtual network that connects Docker containers across multiple hosts and enables their automatic discovery" \
      org.label-schema.url="https://weave.works" \
      org.label-schema.vcs-url="https://github.com/weaveworks/weave" \
      org.label-schema.vendor="Weaveworks"

RUN apk add --update \
    iptables \
    ipset \
	ulogd \
  && rm -rf /var/cache/apk/* \
  && mknod /var/log/ulogd.pcap p
COPY ./weave-npc /usr/bin/weave-npc
COPY ./ulogd.conf /etc/ulogd.conf
ENTRYPOINT ["/usr/bin/weave-npc"]
