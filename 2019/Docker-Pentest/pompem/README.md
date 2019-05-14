## Buscando por exploits publicos
Podemos usar diversos sites publicos para buscar exploits , alguns deles são.
- Packet Storm Security (https://packetstormsecurity.com/search/?q=2019&s=files)
- cxsecurity (https://cxsecurity.com/search/cve/DESC/AND/2019.1.19.1999.1.1/0/10/2019/)
- vulners (https://www.vulners.com/search?query=CVE-2019)
- National Vulnerability Database (https://nvd.nist.gov/vuln/search/results?form_type=Basic&results_type=overview&query=CVE-2019&search_type=all)
- WPVulnDB (https://wpvulndb.com/search?utf8=%E2%9C%93&text=CVE-2019)

### Conhecendo o Pompem
O Pompem é um projeto desenvolvido em Python que auxilia na busca de exploits publicos e atualmente pode buscar por exploits publicos em

- PacketStorm security
- CXSecurity
- ZeroDay
- Vulners
- National Vulnerability Database
- WPScan Vulnerability Database 

### Usando o Docker

#### Antes de criar a imagem
Vamos usar como exemplo um projeto que se chama 
```sh
https://github.com/rfunix/Pompem
```
Criei um fork do projeto e vou criar uma imagem desse projeto usando o Docker.

Podemos ver o projeto em
```sh
https://github.com/greenmind-sec/Pompem
```

#### Criando Dockerfile para o Pompem
Vamos clonar e criar um arquivo **Dockerfile**.
```sh
#A imagem usada
FROM python:3
# Responsavel em criar a imagem Docker
MAINTAINER greenmind.sec@gmail.com
# Indo até o diretorio /root
WORKDIR /root
# Clonando o projeto oficial
RUN git clone https://github.com/rfunix/Pompem
# Indo para o diretorio do projeto
WORKDIR /root/Pompem
# Dando permissão de execução
RUN chmod +x pompem.py
# Instalando requisitos
RUN pip3 install requests
# Criando link simbolico
RUN ln -s /root/Pompem /bin/pompem
# Dando permissão de execução
RUN chmod +x /bin/pompem/pompem.py
# Criando entrypoint
ENTRYPOINT ["python3","/bin/pompem/pompem.py"]
CMD ["--help"]
```


#### Criando uma imagem para o Pompem
Podemos criar a imagem da seguinte forma
```sh
sudo docker build -t "greenmind/pompem:1" .
```

#### Usando a imagem criada
Alem disso podemos executar nossa imagem da seguinte forma
```sh
sudo docker run -it --rm "greenmind/pompem:1" -s "CVE-2019"
```


