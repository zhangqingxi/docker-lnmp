#--------------------------------------------------------------------------
# 构建PHP镜像
#--------------------------------------------------------------------------
#args变量
ARG PHP_VERSION

#PHP版本 alpine镜像
FROM php:${PHP_VERSION}

#Author
MAINTAINER Qasim <15750783791@163.com>

#修改源
RUN sed -i 's/dl-cdn.alpinelinux.org/mirrors.ustc.edu.cn/g' /etc/apk/repositories

# 安装扩展所需的依赖
RUN apk update  \
    && apk add --no-cache --virtual .build-deps \
                                autoconf \
                                gcc \
                                g++ \
                                automake \
                                libtool \
                                make \
                                libstdc++ \
                                freetype-dev \
                                libjpeg-turbo-dev \
                                libpng-dev \
                                libmcrypt-dev \
    && docker-php-ext-configure gd \
                    --with-freetype-dir=/usr/include/freetype2/freetype \
                    --with-jpeg-dir=/usr/include \
                    --with-png-dir=/usr/include \
    && docker-php-ext-install -j$(nproc) gd

#bcmath bz2 calendar ctype curl dba dom enchant exif fileinfo filter ftp gd gettext gmp hash iconv imap interbase intl json ldap mbstring mysqli oci8 odbc opcache pcntl pdo pdo_dblib pdo_firebird pdo_mysql pdo_oci pdo_odbc pdo_pgsql pdo_sqlite pgsql phar posix pspell readline recode reflection session shmop simplexml snmp soap sockets sodium spl standard sysvmsg sysvsem sysvshm tidy tokenizer wddx xml xmlreader xmlrpc xmlwriter xsl zend_test zip
#安装自带的php扩展
#ext already:iconv fileinfo
RUN docker-php-ext-install pdo_mysql opcache bcmath

#安装Redis
RUN pecl install Igbinary \
    && pecl install redis \
    && docker-php-ext-enable redis \
    && pecl clear-cache
