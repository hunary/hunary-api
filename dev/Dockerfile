FROM ubuntu:latest
MAINTAINER Zack Feldstein

RUN apt-get update && apt-get install -y \
     python-virtualenv \
     git
RUN mkdir -p /opt/hunary
WORKDIR /opt/hunary
RUN virtualenv -p python3 ./hunaryVenv && source /opt/hunary/hunaryVenv/bin/activate
RUN git clone https://github.com/hunary/hunary-api
RUN git clone https://github.com/hunary/hunary-cli
WORKDIR /opt/hunary/hunary-api
RUN pip install -r requirements.txt
CMD python /opt/hunary/hunary-api/main.py





