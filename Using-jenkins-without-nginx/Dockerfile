FROM jenkins/jenkins:lts-slim

USER root

RUN apt-get update && \
    apt-get -y install python3

RUN apt-get install -y python3-pip

RUN pip3 install virtualenv