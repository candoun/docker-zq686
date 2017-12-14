FROM openjdk:8-jdk-alpine
MAINTAINER jenkins/gradle/4.3.1-openjdk-8-alpine


ENV HOME /home/jenkins
RUN addgroup -S -g 10000 jenkins
RUN adduser -S -u 10000 -h $HOME -G jenkins jenkins
LABEL Description="This is a base image, which provides the Jenkins agent executable (slave.jar)" Vendor="Jenkins project" Version="3.14"

ARG VERSION=3.14
ARG AGENT_WORKDIR=/home/jenkins/agent

RUN apk add --update --no-cache curl bash git openssh-client openssl tar unzip \
  && curl --create-dirs -sSLo /usr/share/jenkins/slave.jar https://repo.jenkins-ci.org/public/org/jenkins-ci/main/remoting/${VERSION}/remoting-${VERSION}.jar \
  && chmod 755 /usr/share/jenkins \
  && chmod 644 /usr/share/jenkins/slave.jar 

# USER jenkins
ENV AGENT_WORKDIR=${AGENT_WORKDIR}
RUN mkdir /home/jenkins/.jenkins && mkdir -p ${AGENT_WORKDIR}

VOLUME /home/jenkins/.jenkins
VOLUME ${AGENT_WORKDIR}
WORKDIR /home/jenkins


# install  gradle


ENV GRADLE_HOME $HOME
ENV GRADLE_VERSION 4.3.1

ARG GRADLE_DOWNLOAD_SHA256=15ebe098ce0392a2d06d252bff24143cc88c4e963346582c8d88814758d93ac7
RUN set -o errexit -o nounset \
    && echo "Installing build dependencies" \
    \
    && echo "Downloading Gradle" \
    && wget --no-verbose --output-document=gradle.zip "https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-bin.zip" \
    \
    && echo "Checking download hash" \
    && echo "${GRADLE_DOWNLOAD_SHA256} *gradle.zip" | sha256sum -c - \
    \
    && echo "Installing Gradle" \
    && unzip gradle.zip \
    && rm gradle.zip \
    && mkdir /opt \
    && mv "gradle-${GRADLE_VERSION}" "${GRADLE_HOME}/" \
    && ln -s "${GRADLE_HOME}/gradle-${GRADLE_VERSION}/bin/gradle" /usr/bin/gradle 

    
RUN set -o errexit -o nounset \
	&& echo "Testing Gradle installation" \
	&& gradle --version

#USER jenkins