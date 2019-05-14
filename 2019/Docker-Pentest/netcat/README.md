# Dockerfile to create a Netcat container.

## Usando o Docker

### Criando arquivo Dockerfile
```sh
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
```

O arquivo **init.sh** tem o seguinte valor
```sh
#!/bin/bash
set -e

# Prepend "netcat" if the first argument is not an executable
if ! type -- "$1" &> /dev/null; then
	set -- /bin/netcat "$@"
fi
echo "->>>>>> (Executing '"$@"') <<<<<<-"

exec "$@"
```


### Criando imagem do netcat
Podemos criar a imagem da seguinte forma
```sh
docker build -t "greenmind/netcat:1" .
```

### Usando a imagem
Podemos criar um serviço da seguinte forma
```sh
docker run -d -t --name=netcat -p 8182:8182 -p 9192:9192/udp -p443:443 "greenmind/netcat:1"
```

Assim que o serviço for criado podemos acessar ele das seguintes formas

A primeira
```sh
docker exec -it netcat bash
```

A segunda
```sh
docker exec -ti netcat nc -v www.businesscorp.com.br 80
```

