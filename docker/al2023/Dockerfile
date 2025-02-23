FROM amazonlinux:2023
RUN dnf check-update && \
  dnf install -y tar gzip make gcc libxml2-devel bzip2-devel curl-devel readline-devel libxslt-devel openssl-devel rpm-build shadow shadow-utils gd-devel freetype-devel zlib-devel
WORKDIR /usr/local/src
ARG LIBDIR=${LIBDIR}
RUN curl -sL https://www.openssl.org/source/openssl-1.1.1u.tar.gz -o openssl-1.1.1u.tar.gz && \
  tar -xzvf ./openssl-1.1.1u.tar.gz && cd openssl-1.1.1u && \
  ./config--prefix=/usr/local/openssl
RUN curl https://www.php.net/distributions/php-7.3.33.tar.gz -o php-7.3.33.tar.gz && \
  tar zxf php-7.3.33.tar.gz
RUN cd php-7.3.33 && \
  ./configure \
  --with-mysqli \
  --enable-mysqlnd \
  --enable-mbstring \
  --with-curl \
  --enable-exif \
  --enable-bcmath \
  --enable-calendar \
  --enable-ftp \
  --with-gd \
  --with-freetype-dir=${LIBDIR} \
  --with-jpeg-dir=${LIBDIR} \
  --with-png-dir=${LIBDIR} \
  --with-webp-dir=${LIBDIR} \
  --with-xpmg-dir=${LIBDIR} \
  --with-zlib-dir=${LIBDIR} \
  --with-gmp-dir=${LIBDIR} \
  --with-gmp-dir=/${LIBDIR} \
  --with-gettext \








# RUN groupadd mock && useradd mockbuild && \
#   curl -sO https://cdn.amazonlinux.com/blobstore/6ab6ed91c84e0d6cd5364192e379e4c51d0a33d61b14e6b2d19f70cfab7ff00a/php-7.3.33-2.amzn2.src.rpm && \
#   dnf install -y aspell-devel cyrus-sasl-devel \
#       enchant-devel \
#       gcc-c++ \
#       gd-devel \
#       gmp-devel \
#       httpd-devel \
#       krb5-devel \
#       libacl-devel \
#       libdb-devel \
#       libedit-devel \
#       libicu-devel \
#       libstdc++-devel \
#       libtool \
#       libtool-ltdl-devel \
#       libzip-devel \
#       net-snmp-devel \
#       oniguruma-devel \
#       openldap-devel \
#       pam-devel \
#       pcre2-devel \
#       perl \
#       pkgconfig \
#       libsodium \
#       libsodium-devel \
#       postgresql-devel \
#       recode-devel \
#       smtpdaemon \
#       sqlite-devel \
#       systemd-devel \
#       systemd-units \
#       systemtap-sdt-devel \
#       tokyocabinet-devel \
#       unixODBC-devel
      #  && \
      # rpmbuild -ba php-7.3.33-2.amzn2.src.rpm
