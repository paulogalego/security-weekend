FROM debian:jessie

MAINTAINER Roger CARHUATOCTO <chilcano at intix dot info>

RUN DEBIAN_FRONTEND=noninteractive apt-get update
RUN DEBIAN_FRONTEND=noninteractive apt-get install -yq --no-install-recommends netcat
RUN apt-get clean && rm -rf /var/cache/apt/* /var/lib/apt/lists/*
# Allocate the 8182 and 9192 port to listen for TCP and UDP traffic
# Port 443 for reverse shell
RUN apt-get update
RUN apt-get install net-tools -y
EXPOSE 8182 9192 443
COPY init.sh /
RUN chmod +x /init.sh
ENTRYPOINT ["/init.sh"]