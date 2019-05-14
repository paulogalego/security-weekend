## Analise de portas e de vulnerabilidade - Nmap & NmapNSE


NMAP é uma ferramenta muito conhecida , ela nos auxilia em diversas tarefas como por exemplo
- scan de portas
- scanner
- ataques a formularios
- E uma infinidade de soluções

Junto com o NMAP temos o NSE , ele é com o Nmap e tem um conjunto de scripts maior a cada nova versão

Site Oficial:
```sh
http://nmap.org/nsedoc/
```

Documentação:
```sh
https://nmap.org/book/nse-usage.html
```

Local Default dos scripts :
```sh
/usr/share/nmap/scripts
```

### Usando o Docker

#### Criando imagem usando o Docker
Podemos ver o codigo Dockerfile
```sh
FROM debian
MAINTAINER greenmind.sec@gmail.com
WORKDIR /root
RUN apt-get update
RUN apt-get install git -y
RUN git clone https://github.com/nmap/nmap
WORKDIR /root/nmap
RUN apt-get install gcc -y
RUN ./configure
RUN apt-get install build-essential -y
RUN make
RUN make install
ENTRYPOINT ["nmap"]
```

#### Criando a imagem do NMAP
Podemos criar ela da seguinte forma
```sh
sudo docker build -t "greenmind/nmap:1" .
```

#### Como podemos usar ela ? 
Bastar passar os argumentos , da seguinte forma
```sh
sudo docker run -it --rm "greenmind/nmap:1" -h
```

#### Usando rede host
Podemos tambem usar a rede do nosso host , dessa forma inves de realizar um teste em nosso container é realizado em nossa maquina host e podemos fazer isso usando
```sh
sudo docker run -it --rm --network host "greenmind/nmap:1" localhost
```

Para mais informações sobre network veja em
```sh
https://docs.docker.com/network/host/
```

