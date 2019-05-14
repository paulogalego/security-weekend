## Brute force de URL - Dirb

### Conhecendo o Dirb
O Dirb é um projeto que tem como objetivo realizar o reconhecimento de diretorios usando brute force , conta com wordlist padrão e podemos passar a nossa propria wordlist personalizada.

### Usando o Docker

#### Criando Dockerfile para o Dirb
Abaixo podemos ver o arquivo Dockerfile para criar a imagem do Dirb.
```sh
FROM debian
MAINTAINER greenmind.sec@gmail.com
WORKDIR /root
RUN apt-get update
RUN apt-get install build-essential wget -y
COPY . .
RUN tar xf dirb222.tar.gz 
WORKDIR /root/dirb222
RUN apt-get install libcurl4-gnutls-dev -y 
RUN chmod +x configure 
RUN ./configure 
RUN make 
RUN chmod +x dirb 
RUN ln -s /root/dirb222/dirb /bin/dirb
ENTRYPOINT ["/bin/dirb"]
```

#### Criando uma imagem para o Dirb
Como posso criar a imagem ?
```sh
sudo docker build -t "greenmind/dirb:1" .
```

#### Como podemos usar o Dirb.
Como usar a imagem e passar o local da wordlist.
```sh
sudo docker run --name dirb -it --rm "greenmind/dirb:1" http://site-exemplo.com.br/ /root/dirb222/wordlists/common.txt
```

> OBS: O processo não é possivel ser parado usando **Ctrl+c** , caso queira parar o processo é possivel usar o **docker rm dirb -f** ou **docker rm id-do-container**.


