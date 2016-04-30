FROM ubuntu:14.04

RUN apt-get update -y && \
    apt-get install -y --force-yes curl

RUN apt-get -y --force-yes install python3 python3-setuptools python3-pip python3-matplotlib cython3 zlib1g-dev  make libncurses5-dev r-base libxml2-dev

RUN apt-get install -y --force-yes tesseract-ocr  tesseract-ocr-eng  tesseract-ocr-por
# Rabbitmq client
RUN pip3 install pika==0.10.0
RUN pip3 install pymongo==3.2.0