FROM ubuntu:latest
MAINTAINER Zack Feldstein

RUN apt-get update && apt-get install -y \
     python-virtualenv \
     git \
     python-pip \
     python3-dev
RUN mkdir -p /opt/hunary
WORKDIR /opt/hunary
RUN virtualenv -p python3 ./hunaryVenv 
RUN /bin/bash -c "source  /opt/hunary/hunaryVenv/bin/activate"

RUN git clone https://github.com/hunary/hunary-api
RUN git clone https://github.com/hunary/hunary-cli

WORKDIR /opt/hunary/hunary-api

RUN /bin/bash -c "git fetch; git checkout docker"
RUN /opt/hunary/hunaryVenv/bin/pip install https://github.com/timClicks/slate/archive/master.zip
RUN /opt/hunary/hunaryVenv/bin/pip install spacy Flask pymongo requests
RUN /opt/hunary/hunaryVenv/bin/pip install utils
RUN /opt/hunary/hunaryVenv/bin/python -m spacy download en_core_web_sm
RUN mkdir -p ./uploads/docs/acct_01

CMD /opt/hunary/hunaryVenv/bin/python main.py

