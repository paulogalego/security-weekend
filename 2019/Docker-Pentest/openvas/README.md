## Analise de vulnerabilidade - OpenVas
### Criando imagem Docker para o OpenVas

 Pre requisitos
- Docker
- Docker-compose
- Git


#### Clonando projeto
Podemos criar a imagem da seguinte forma.
```sh
git clone https://github.com/mikesplain/openvas-docker
```

#### Subindo imagem
Podemos entrar no diretorio
```sh
cd openvas-docker
```

Depois podemos criar a imagem com o **docker-compose**.
```sh
sudo docker run -d -p 443:443 -p 9390:9390 --name openvas mikesplain/openvas
```

Podemos acessar a maquina via shell da seguinte forma
```sh
docker exec -it openvas bash
```

#### Atualizando NVTs
Depois de ter acesso a maquina e ter acesso root podemos criar um script da seguinte forma.
```sh
apt-get update
apt-get install nano
```

Em seguida podemos criar um script , ele se chama **reload.sh**.

Vou criar usando o nano
```sh
nano reload.sh
```

Agora vou inserir isso no arquivo **reload.sh**.
```sh
greenbone-nvt-sync
openvasmd --rebuild --progress
greenbone-certdata-sync
greenbone-scapdata-sync
openvasmd --update --verbose --progress

/etc/init.d/openvas-manager restart
/etc/init.d/openvas-scanner restart
```

Em seguida vou sair e dar permissão de execução.
```sh
chmod +x reload.sh
```

