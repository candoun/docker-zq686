FROM centos:7
WORKDIR /usr/src/app

ENV NGINX_VERSION tengine-2.1.1
ADD http://tengine.taobao.org/download/${NGINX_VERSION}.tar.gz   tengine.tar.gz
RUN yum install -y\
 gcc gcc-c++ autoconf automake make pcre pcre-devel  \
 openssl openssl-devel  \
 libpcre3-dev \
 zlib1g-dev \
 libgeoip-dev \
 libxslt1-dev \
 libgd2-dev \
 build-essential \
 libc6 \
 libexpat1 \
 libgd2-xpm-dev \
 libgeoip1 \
 libgeoip-dev \
 libpam0g \
 libssl1.0.0 \
 libxml2 \
 libxslt1.1 \
 zlib1g \
 openssl \
 liblua5.1-0-dev \
 lua5.1 \
 libgd2-xpm-dev \
 libgeoip-dev \
 libxslt1-dev \
 libpcre++0 \
 libpcre++-dev \
 libperl-dev \
 wget \
 curl && \
tar -zxvf tengine.tar.gz > /dev/null && \
cd ${NGINX_VERSION} && \
./configure \
	--with-pcre \
	--with-pcre-jit && \
make && make install && \
yum clean all -y && \
rm -rf /var/cache/yum tengine*

