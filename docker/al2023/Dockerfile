#ビルド用ベースイメージ
FROM amazonlinux:2023 AS base
RUN dnf check-update && \
  dnf install -y tar gzip make gcc libxml2-devel bzip2-devel libzip-devel curl-devel readline-devel libxslt-devel openssl-devel rpm-build shadow shadow-utils gd-devel freetype-devel zlib-devel perl && \
  dnf clean all
#ソースを収集
FROM alpine:latest AS collector
WORKDIR /usr/local/src
RUN apk update && apk add --no-cache curl tar && \
  curl -sLO https://www.openssl.org/source/openssl-1.1.1u.tar.gz && \
  tar xzf ./openssl-1.1.1u.tar.gz && mv openssl-1.1.1u openssl && \
  curl -sLO https://www.php.net/distributions/php-7.3.33.tar.gz && \
  tar zxf php-7.3.33.tar.gz && mv php-7.3.33 php

#OpenSSL1.xをビルド
FROM base AS openssl
COPY --from=collector /usr/local/src/openssl/ /usr/local/src/openssl
WORKDIR /usr/local/src/openssl
RUN ls && ./config --prefix=/root/lib/openssl && make && make install

FROM base AS php
ARG LIBDIR=/usr/lib64
COPY --from=openssl /root/lib/openssl/ /usr/local/openssl/ 
COPY --from=collector /usr/local/src/php/ /usr/local/src/php/ 
WORKDIR /usr/local/src/php
RUN ./configure \
  --with-mysqli \
  --enable-mysqlnd \
  --enable-mbstring \
  --with-curl \
  --with-gzip \
  --with-bz2 \
  --with-xsl \
  --with-zlib \
  --enable-pcntl \
  --enable-exif \
  --enable-wddx \ 
  --enable-sockets \
  --enable-bcmath \
  --enable-calendar \
  --enable-ftp \
  --with-libzip \
  --with-readline \
  --with-pdo-mysql \
  --disable-posix \
  --with-gd=/usr \
  --with-freetype-dir=${LIBDIR} \
  --with-jpeg-dir=${LIBDIR} \
  --with-png-dir=${LIBDIR} \
  --with-webp-dir=${LIBDIR} \
  --with-zlib-dir=${LIBDIR} \
  --with-gmp-dir=${LIBDIR} \
  --with-xpm-dir=${LIBDIR} \
  --with-gettext \
  --with-openssl=/usr/local/openssl \
  --with-openssl-dir=/usr/local/openssl && \
  make install && make clean
