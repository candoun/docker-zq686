

FROM alpine:3.6

LABEL maintainer="zzuwhj@126.com"



RUN apk add --no-cache \
        curl \
        #wget \
		tar \
		unzip \
    && cd /tmp 
RUN curl -fSL  https://storage.googleapis.com/kubernetes-release/release/v1.8.5/bin/linux/amd64/kubectl -o kubectl1.8.5
RUN curl -fSL https://storage.googleapis.com/kubernetes-release/release/v1.8.0/bin/linux/amd64/kubectl  -o kubectl1.8.0

RUN curl -fSL  https://storage.googleapis.com/kubernetes-release/release/stable.txt -o aa.txt
