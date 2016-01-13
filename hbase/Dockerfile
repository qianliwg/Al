FROM ubuntu:14.04

RUN apt-get update
EXPOSE 2181 22

RUN apt-get install -y unzip ssh wget openjdk-7-jdk
RUN useradd wg && echo wg:Aa1 | chpasswd

RUN cd /opt && wget --content-disposition http://sitewhere13.chinacloudapp.cn/softs/hbase-1.1.2-bin.tar.gz && unzip hbase-1.1.2-bin.tar.gz && echo "1"
ENV JAVA_HOME="/usr/lib/jvm/java-1.7.0-openjdk-amd64"
COPY hbase-site.xml /opt/hbase-1.1.2/conf/hbase-site.xml
RUN  
CMD nohup /opt/hbase-1.1.2/bin/start-hbase.sh & echo 'Starting Hbase...' 
