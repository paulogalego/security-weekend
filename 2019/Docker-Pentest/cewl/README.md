## Criando wordlists personalizadas usando CeWL

### Conhecendo o CeWL
O CeWL é um projeto que tem como meta auxiliar na criação de wordlists personalisadas e podemos encontrar o projeto no github.
```sh
https://github.com/digininja/CeWL/
```

### Usando o Docker
Ele é um projeto em Ruby , vamos criar um **Dockerfile** para o projeto e agilizar o uso dessa ferramenta.

#### Criando arquivo Dockerfile.
Arquivo **Dockerfile**.
```sh
FROM ruby:2.5
WORKDIR /usr/src/app
RUN git clone https://github.com/digininja/CeWL/ 
WORKDIR /usr/src/app/CeWL
RUN gem install bundler
RUN bundle install
RUN gem source -c
RUN gem install --user-install spider http_configuration mini_exiftool zip mime-types
RUN RUBYOPT="rubygems"
ENTRYPOINT ["/usr/src/app/CeWL/cewl.rb"]
```

#### Criando imagem CeWL
Criando uma imagem no Docker.
```sh
sudo docker build -t "greenmind/cewl:1" .
```

#### Usando a imagem criada
Usando a imagem criada
```sh
sudo docker run -it --rm "greenmind/cewl:1" http://site-a-ser-testado.com
```

Salvando saida
```sh
docker run -it --rm "greenmind/cewl:1" http://businesscorp.com.br > ${PWD}/teste.txt
```