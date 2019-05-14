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