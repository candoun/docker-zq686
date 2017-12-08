

FROM alpine:3.6

LABEL maintainer="zzuwhj@126.com"



RUN apk add --no-cache \
        curl \
        wget \
		tar \
		unzip \
    && cd /tmp \
	&& curl -LO https://storage.googleapis.com/kubernetes-release/release/$(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt)/bin/linux/amd64/kubectl \
    && curl $(curl -s https://storage.googleapis.com/kubernetes-release/release/stable.txt) \
    && curl -LO https://storage.googleapis.com/kubernetes-release/release/v1.8.0/bin/linux/amd64/kubectl 


