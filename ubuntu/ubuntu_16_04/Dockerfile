FROM ubuntu:16.04
WORKDIR /
MAINTAINER jodyscott

# Install Java.
ADD jre-8u201-linux-x64.tar /usr/lib
RUN mv /usr/lib/jre* /usr/lib/jre
RUN ln -s /usr/lib/jre/bin/java /usr/bin/java
ENV JAVA_HOME /usr/lib/jre
