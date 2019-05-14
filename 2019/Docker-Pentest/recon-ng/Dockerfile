FROM python:2
WORKDIR /opt/
RUN git clone https://LaNMaSteR53@bitbucket.org/LaNMaSteR53/recon-ng.git
WORKDIR /opt/recon-ng
RUN pip install -r REQUIREMENTS
RUN chmod +x recon-ng
ENTRYPOINT ["python","recon-ng"]