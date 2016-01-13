FROM ubuntu:14.04

RUN apt-get update
EXPOSE 8080 22

RUN apt-get install -y unzip ssh wget openjdk-7-jdk
RUN useradd wg && echo wg:Aa1 | chpasswd

RUN cd /opt && wget --content-disposition http://sitewhere13.chinacloudapp.cn/softs/sitewhere-server-1.4.0.tar.gz && unzip sitewhere-server-1.4.0.tar.gz && echo "1"
ENV CATALINA_BASE="/opt/sitewhere-server-1.4.0" CATALINA_HOME="/opt/sitewhere-server-1.4.0"
COPY sitewhere-server.xml /opt/sitewhere-server-1.4.0/conf/sitewhere/sitewhere-server.xml
COPY sitewhere-tenant.xml /opt/sitewhere-server-1.4.0/conf/sitewhere/sitewhere-tenant.xml
COPY default-tenant.xml /opt/sitewhere-server-1.4.0/conf/sitewhere/default-tenant.xml
RUN ln -s /opt/sitewhere-server-1.4.0 /opt/sitewhere && useradd -d /opt/sitewhere sitewhere && chown -R sitewhere.sitewhere /opt/sitewhere-server-1.4.0 && chown -R sitewhere.sitewhere /opt/sitewhere && cd /opt/sitewhere && chmod +x /opt/sitewhere-server-1.4.0/bin/*.sh 
CMD nohup /opt/sitewhere/bin/startup.sh & echo 'Starting SiteWhere...' && while ! [ -f /opt/sitewhere/logs/catalina.out ]; do sleep 1; done && tail -f /opt/sitewhere/logs/catalina.out
