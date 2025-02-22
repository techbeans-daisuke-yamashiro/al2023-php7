FROM amazonlinux:2023
RUN dnf check-update && \
  dnf install -y tar gzip make gcc libxml2-devel bzip2-devel curl-devel readline-devel libxslt-devel openssl-devel && \
  cd /usr/local/src && curl https://cdn.amazonlinux.com/blobstore/6ab6ed91c84e0d6cd5364192e379e4c51d0a33d61b14e6b2d19f70cfab7ff00a/php-7.3.33-2.amzn2.src.rpm && \
  tar -xzvf php-7.3.31.tar.gz
