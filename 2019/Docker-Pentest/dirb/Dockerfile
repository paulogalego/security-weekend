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