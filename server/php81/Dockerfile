#--------------------------------------------------------------------------
# 构建PHP镜像
#--------------------------------------------------------------------------
#args变量
ARG PHP_VERSION

#PHP版本
FROM php:${PHP_VERSION}

#Author
MAINTAINER Qasim <15750783791@163.com>

# php扩展
#bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd gettext gmp hash iconv imap interbase intl json ldap mbstring mysqli oci8 odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql phar posix pspell readline recode reflection session shmop simplexml snmp soap sockets sodium spl standard sysvmsg sysvsem sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zend_test zip

RUN sed -i "s@http://deb.debian.org@http://mirrors.aliyun.com@g" /etc/apt/sources.list \
  && cat /etc/apt/sources.list \
  && rm -Rf /var/lib/apt/lists/* \
  && apt-get update \
  && apt-get -y install wget \
  && docker-php-ext-install mysqli \
  && docker-php-ext-install pdo_mysql \
  && docker-php-ext-install sockets \
  && apt-get install -y --no-install-recommends libfreetype6-dev libwebp-dev libjpeg62-turbo-dev libpng-dev librabbitmq-dev \
  && docker-php-ext-configure gd --with-webp=/usr/include/webp --with-freetype=/usr/include/freetype2/ --with-jpeg=/usr/include \
  && docker-php-ext-install -j$(nproc) gd

#安装Redis、amqp、swoole
RUN pecl install -o -f redis \
  && rm -rf /tmp/pear \
  && docker-php-ext-enable redis \
  && pecl install -o -f amqp \
  && docker-php-ext-enable amqp \
  && pecl install -o -f swoole \
  && docker-php-ext-enable swoole
