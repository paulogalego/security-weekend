## Usando o Docker

### Criando arquivo Dockerfile
```sh
FROM debian:9-slim
RUN apt-get update 
RUN apt-get install ftp -y
ENTRYPOINT ["ftp"]
```

### Criando imagem
```sh
sudo docker build -t "greenmind/ftp:1" .
```

### Usando a imagem
```sh
sudo docker run -it --rm "greenmind/ftp:1" -h
```