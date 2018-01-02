FROM python:3.6.4-alpine3.6

MAINTAINER ZZUWHJ


WORKDIR /usr/src/app
RUN apk add --no-cache \
    curl \
	wget \
	vim \
	&& apk update && apk add tzdata \
	&& cp /usr/share/zoneinfo/Asia/Shanghai /etc/localtime
	
COPY requirements.txt \
	 Dockerfile \
	 ./
COPY kubectl1.7.0 \
	 kubectl1.8.0 \
	 kubectl1.8.5 \
	 /usr/local/bin/

RUN apk add --no-cache --virtual .build-deps \
		py-pip postgresql-dev gcc g++ mariadb-dev \
		freetds-dev freetds  \
	&& pip install Cython  \
	&& pip install -r requirements.txt \
	&& pip install uwsgi && \
	&& set -ex;\
		find /usr/local -depth \
		\( \
			\( -type d -a \( -name test -o -name tests \) \) \
			-o \
			\( -type f -a \( -name '*.pyc' -o -name '*.pyo' \) \) \
		\) -exec rm -rf '{}' +; \
		rm requirements.txt \
	&& apk del .build-deps \
	&& chmod 777 /usr/local/bin/kubectl* \
	&& ln -s /usr/local/bin/kubectl1.7.0  /usr/local/bin/kubectl \
	&& rm -rf /usr/share/zoneinfo/
