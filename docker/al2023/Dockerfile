FROM amazonlinux:2023
RUN dnf check-update && \
  dnf install -y tar gzip make gcc libxml2-devel bzip2-devel curl-devel readline-devel libxslt-devel openssl-devel && \
  cd /usr/local/src && curl https://www.php.net/distributions/php-7.3.31.tar.gz -o php-7.3.31.tar.gz && \
  tar -xzvf php-7.3.31.tar.gz