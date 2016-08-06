FROM debian:7
RUN apt-get update && \
	apt-get -y install apt-utils curl nano ntp net-tools procps htop wget ca-certificates
RUN	curl http://public-repo-1.hortonworks.com/ambari/debian7/2.x/updates/2.2.0.0/ambari.list -o /etc/apt/sources.list.d/ambari.list
RUN	apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B9733A7A07513CAD
RUN apt-get update

# Install Java.
RUN apt-get update && \
    wget --header "Cookie: oraclelicense=accept-securebackup-cookie" http://download.oracle.com/otn-pub/java/jdk/8u102-b14/jdk-8u102-linux-x64.tar.gz && \
	mkdir /opt/jdk/ && \
	mv jdk-8u102-linux-x64.tar.gz /opt/jdk/ && \
	cd /opt/jdk/ && \
	tar -zxf jdk-8u102-linux-x64.tar.gz && \
	update-alternatives --install /usr/bin/java java /opt/jdk/jdk1.8.0_102/bin/java 100 && \
	update-alternatives --install /usr/bin/javac javac /opt/jdk/jdk1.8.0_102/bin/javac 100
	
# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /opt/jdk/jdk1.8.0_102/
