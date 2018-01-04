FROM python:3.6.4-alpine3.6

MAINTAINER ZZUWHJ

WORKDIR /usr/src/app

COPY requirements.txt \
	 Dockerfile \
	 ./
COPY kubectl1.7.0 \
	 kubectl1.8.0 \
	 kubectl1.8.5 \
	 /usr/local/bin/

RUN apk add --no-cache --virtual .build-deps \
		py-pip gcc g++ \
		git \
		linux-headers musl-dev \
	&& apk add --no-cache \
		uwsgi \
		curl \
		wget \
		vim \
		bash \
		tzdata \
		freetds-dev freetds \
		mariadb-dev \
		postgresql-dev \
	&& cp -r -f /usr/share/zoneinfo/Asia/Shanghai /etc/localtime \
	&& pip install Cython  \
	&& pip install git+https://github.com/pymssql/pymssql.git@3bc299936fe2d35196dd4c9ebc8a22777f0c97e6 \
	&& pip install -r requirements.txt \
	&& set -ex;\
		find /usr/local -depth \
		\( \
			\( -type f -a \( -name '*.pyc' -o -name '*.pyo' \) \) \
		\) -exec rm -rf '{}' +; \
		rm -rf /usr/share/zoneinfo/ \
	&& apk del .build-deps \
	&& chmod 777 /usr/local/bin/kubectl* && ln -s /usr/local/bin/kubectl1.7.0  /usr/local/bin/kubectl \

