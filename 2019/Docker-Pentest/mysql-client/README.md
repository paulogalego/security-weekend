Podemos usar uma imagem com o cliente mysql para se conectar a um banco ou enumerar serviços e assim não tendo a necessidade de instalar em nossa maquina host.

## Usando o Docker

### Criando arquivo Dockerfile
```sh
FROM alpine
RUN apk add --no-cache mariadb-client
ENTRYPOINT ["/usr/bin/mysql"]
```

### Criando imagem
```sh
sudo docker build -t "greenmind/mysql-client:1" .
```

### Usando a imagem
```sh
sudo docker run -it --rm "greenmind/mysql-client:1" --help
```