FROM openjdk:8-jdk-alpine

MAINTAINER jenkins/ant/xxx-openjdk-8-alpine

ENV HOME /home/jenkins
RUN addgroup -S -g 10000 jenkins
RUN adduser -S -u 10000 -h $HOME -G jenkins jenkins
LABEL Description="This is a base image, which provides the Jenkins agent executable (slave.jar)" Vendor="Jenkins project" Version="3.14"

ARG VERSION=3.14
ARG AGENT_WORKDIR=/home/jenkins/agent

RUN apk add --update --no-cache curl bash git openssh-client openssl tar wget\
    ca-certificates \
    unzip \
  && curl --create-dirs -sSLo /usr/share/jenkins/slave.jar https://repo.jenkins-ci.org/public/org/jenkins-ci/main/remoting/${VERSION}/remoting-${VERSION}.jar \
  && chmod 755 /usr/share/jenkins \
  && chmod 644 /usr/share/jenkins/slave.jar 

# USER jenkins
ENV AGENT_WORKDIR=${AGENT_WORKDIR}
RUN mkdir /home/jenkins/.jenkins && mkdir -p ${AGENT_WORKDIR}

VOLUME /home/jenkins/.jenkins
VOLUME ${AGENT_WORKDIR}
WORKDIR /home/jenkins


# install  ant
ENV ANT_VERSION 1.10.1
ENV ANT_HOME $HOME/apache-ant-${ANT_VERSION}/
RUN wget -q http://mirrors.hust.edu.cn/apache//ant/binaries/apache-ant-${ANT_VERSION}-bin.tar.gz && \
    tar -xzf apache-ant-${ANT_VERSION}-bin.tar.gz && \
    mv apache-ant-${ANT_VERSION} ${ANT_HOME} && \
    rm apache-ant-${ANT_VERSION}-bin.tar.gz
ENV PATH ${PATH}:${ANT_HOME}/bin

USER jenkins
