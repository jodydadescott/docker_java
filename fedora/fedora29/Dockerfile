FROM fedora:29
WORKDIR /
MAINTAINER jody@thescottsweb.com

RUN dnf -y install bind-utils
ADD cache/jdk.tgz /opt
RUN ln -s /opt/jdk* /opt/jdk
RUN ln -s /opt/jdk/bin/java /usr/bin/java
