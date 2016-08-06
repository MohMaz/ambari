FROM debian:7
RUN apt-get update && \
	apt-get -y install apt-utils curl nano ntp net-tools procps htop
RUN	curl http://public-repo-1.hortonworks.com/ambari/debian7/2.x/updates/2.2.0.0/ambari.list -o /etc/apt/sources.list.d/ambari.list
RUN	apt-key adv --recv-keys --keyserver keyserver.ubuntu.com B9733A7A07513CAD
RUN apt-get update

# Install Java.
RUN \
  echo oracle-java8-installer shared/accepted-oracle-license-v1-1 select true | debconf-set-selections && \
  add-apt-repository -y ppa:webupd8team/java && \
  apt-get update && \
  apt-get install -y oracle-java8-installer && \
  rm -rf /var/lib/apt/lists/* && \
  rm -rf /var/cache/oracle-jdk8-installer


# Define working directory.
WORKDIR /data

# Define commonly used JAVA_HOME variable
ENV JAVA_HOME /usr/lib/jvm/java-8-oracle
