FROM python:3
WORKDIR /opt/
RUN git clone https://github.com/laramies/theHarvester
WORKDIR /opt/theHarvester
RUN pip3 install -r requirements.txt
RUN chmod +x theHarvester.py
ENTRYPOINT ["python3","theHarvester.py"]