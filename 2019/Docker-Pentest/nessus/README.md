## Analise de vulnerabilidade - Nessus
Podemos usar o Docker para criar uma imagem do Nessus , isso pode nos ajudar muito já que o Nessus não vai ficar instalado em nossa maquina e assim mantendo a segurança de nossa maquina.

Pontos positivos
- Não é instalado em nossa maquina
- Podemos criar mais de uma maquina

Pontos negativos
- Podemos ser prejudicados devida a performance

### Criando maquina Nessus usando Docker
Para ele funcionar em nossa maquina precisamos de alguns requisitos minimos:
- Docker
- Docker-compose
- Git

#### Clonando o projeto
Vamos usar um projeto chamado
```sh
https://github.com/praveendhac/nessus-docker
```

Vamos clonar ele
```sh
git clone https://github.com/praveendhac/nessus-docker
```

Depois vamos entrar no diretorio
```sh
cd nessus-docker
```

Pronto , estamos no diretorio do projeto e agora vamos subir a nossa maquina usando o **docker-compose**.

#### Criando imagem
Já estamos no diretorio do projeto , em seguida vamos subir o projeto usando **docker-compose**.
```sh
docker-compose -f docker-compose.yaml up
```

Agora nossa imagem esta sendo criada e depois vamos podemos acessar ela no endereço.
```sh
https://127.0.0.1:9934
```

E já vamos criar nossa conta , igual na versão instalada no Debian/Kali.

Agora vamos precisamos passar o codigo obtido em **02 - Conhecendo versões e realizando conta**.


#### Logando no serviço
Podemos agora logar no serviço usando a porta **9934**.
```sh
https://127.0.0.1:9934
```

Como é um certificado auto assinado devemos aceitar.

#### Após carregar os plugins
Já vai ser possivel usar o Nessus.

