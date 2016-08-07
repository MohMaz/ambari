FROM quay.io/digikala/ambari-base
# Installing Packages
RUN apt-get -y install\
	ambari-agent \
	dnsutils \
	systemd systemd-sysv \


# Modifying 
COPY ambari.list /etc/apt/sources.list.d/
RUN apt-get update

# configuring Host Name Issues:
COPY public-hostname.sh /etc/ambari-agent/conf/public-hostname.sh
COPY internal-hostname.sh /etc/ambari-agent/conf/internal-hostname.sh
RUN sed -i "/\[agent\]/ a public_hostname_script=\/etc\/ambari-agent\/conf\/public-hostname.sh" /etc/ambari-agent/conf/ambari-agent.ini
RUN sed -i "/\[agent\]/ a hostname_script=\/etc\/ambari-agent\/conf\/internal-hostname.sh" /etc/ambari-agent/conf/ambari-agent.ini

# do not use the docker0 interface
RUN sed -i "s/\"ifconfig\"/\"ifconfig eth0\"/" /usr/lib/python2.6/site-packages/ambari_agent/Facter.py

# init agent
COPY init/init-agent.sh /opt/ambari-agent/init-agent.sh
RUN chmod u+x /opt/ambari-agent/init-agent.sh

COPY init/ambari-agent.service /etc/systemd/system/ambari-agent.service

RUN systemctl enable ambari-agent
