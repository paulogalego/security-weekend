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