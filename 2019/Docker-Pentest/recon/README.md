## Realizando o reconhecimento usando o Docker

- Nmap 7.40
- host 9.10.3-P4-Debian
- DNSRato v1.0
- Whois 5.2.17
- Netcat 1.10-41+b1
- FPing 3.15
- Xprobe2 v.0.3
- tcpdump 4.9.2
- libpcap 1.8.1
- OpenSSL 1.0.2l
- HPing3 3.0.0-alpha-2
- Traceroute 2.1.0
- Shodan 1.7.5
- Fierce 1.2.0
- Dirb 2.22
- Google 1.9.3
- DNSRecon 0.8.11
- TheHarvester 2.7.1

### Docker Recon

#### Clonando o repositório
Podemos clonar e construir a imagem.
```sh
git clone https://github.com/greenmind-sec/recon
```

Podemos ir até o projeto baixado.
```sh
cd recon
```

Não podemos esquecer de criar o nosso diretorio **recon** , ele vai ser nossa ponte para enviar arquivos para maquina.

#### Contruindo imagem
Nesse caso a minha imagem se chamara **recon**.
```sh
sudo docker build -t recon .
```

#### Usando a imagem
Depois de criar a nossa imagem **recon** podemos subir ela e destruir sempre que precisar.
```sh
docker run -ti --rm recon bash
```

E assim toda vez que sair da imagem ela é destruida.