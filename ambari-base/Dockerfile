FROM debian:7
RUN apt-get update && \
	apt-get -y install apt-utils curl 
RUN	curl http://public-repo-1.hortonworks.com/ambari/debian7/2.x/updates/2.2.0.0/ambari.list -o /etc/apt/sources.list.d/ambari.list
RUN	apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B9733A7A07513CAD
RUN apt-get update