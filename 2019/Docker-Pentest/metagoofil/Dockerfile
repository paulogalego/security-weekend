FROM python:2
WORKDIR /opt/
RUN git clone https://github.com/laramies/metagoofil
WORKDIR /opt/metagoofil
RUN chmod +x metagoofil.py
ENTRYPOINT ["python","metagoofil.py"]