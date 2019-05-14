Podemos usar um cliente openssl para analisar sites com HTTPS e assim facilitando o uso em testes.

## Usando o Docker

### Criando o arquivo Dockerfile
```sh
FROM alpine
RUN apk add --no-cache openssl
ENTRYPOINT ["/usr/bin/openssl"]
```

### Criando a imagem do OpenSSL
```sh
sudo docker build -t "greenmind/openssl:1" .
```

### Usando a imagem criada
```sh
sudo docker run -it "greenmind/openssl:1" s_client -quiet -connect www.itau.com.br:443
```

E depois de conectado podemos enviar
```sh
HEAD / HTTP/1.0
Host:www.itau.com.br
```