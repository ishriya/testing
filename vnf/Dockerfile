FROM ubuntu:xenial
MAINTAINER Deepak Bhardwaj

#define interface names
ENV IFIN input
ENV IFOUT output1 output2

# define
ENV TCP_LISTEN_PORT 8888
ENV TCP_SERVER1 server1 40.0.0.254:80;
ENV TCP_SERVER2 server2 50.0.0.254:80;
ENV UDP_LISTEN_PORT 8888
ENV UDP_SERVER1 server1 40.0.0.254:80;
ENV UDP_SERVER2 server2 50.0.0.254:80;

RUN export DEBIAN_FRONTEND=noninteractive && apt-get update && apt-get install -y -q \
	net-tools \
	iproute \
	inetutils-ping \
	nginx \
 	python \
	python-yaml \
	python3 \
	python3-pip \
	curl

ADD start.sh start.sh
RUN chmod +x start.sh
ADD stop.sh stop.sh
RUN chmod +x stop.sh

# ADD www /var/www/html
ADD nginx.conf /etc/nginx/nginx.conf
ADD log_intf_statistics.py log_intf_statistics.py

WORKDIR /

RUN mkdir /tngbench_share

# normal entry point
CMD /bin/bash
