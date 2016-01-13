FROM ubuntu:14.04

RUN apt-get update
EXPOSE 8080 22
RUN apt-get install -y unzip ssh wget openjdk-7-jdk
RUN useradd wg && echo wg:Aa1 | chpasswd
RUN cd /opt && wget --content-disposition http://sitewhere13.chinacloudapp.cn/softs/apache-activemq-5.12.1-bin.tar.gz && unzip apache-activemq-5.12.1-bin.tar.gz && echo "1"
CMD nohup /opt/apache-activemq-5.12.1/bin/activemq start & echo 'Starting ActiveMQ...'
