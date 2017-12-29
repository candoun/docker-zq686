FROM python:3.6.4-alpine3.6

MAINTAINER ZZUWHJ

WORKDIR /usr/src/app

COPY requirements.txt ./
RUN pip install --upgrade --no-cache-dir -r requirements.txt
RUN set -ex;\
    find /usr/local -depth \
	\( \
	    \( -type d -a \( -name test -o -name tests \) \) \
		-o \
	    \( -type f -a \( -name '*.pyc' -o -name '*.pyo' \) \) \
	\) -exec rm -rf '{}' +; \
	rm requirements.txt