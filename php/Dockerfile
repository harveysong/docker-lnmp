FROM php:7.1-fpm 
MAINTAINER harvey <harveysong@aliyun.com>

RUN apt-get update \
	&& apt-get install -y openssl libssl-dev libmemcached-dev zlib1g-dev curl libmcrypt-dev

RUN docker-php-ext-install gettext mysqli opcache pdo_mysql sockets mcrypt

RUN pecl install redis \
&& docker-php-ext-enable redis

RUN pecl install mongodb \
&& docker-php-ext-enable mongodb

RUN pecl install xdebug \
    && docker-php-ext-enable xdebug

RUN curl -L -o /tmp/memcached.tar.gz "https://github.com/php-memcached-dev/php-memcached/archive/php7.tar.gz" \
    && mkdir -p /usr/src/php/ext/memcached \
    && tar -C /usr/src/php/ext/memcached -zxvf /tmp/memcached.tar.gz --strip 1 \
    && docker-php-ext-configure memcached \
    && docker-php-ext-install memcached \
    && rm /tmp/memcached.tar.gz 

CMD ["php-fpm"]

EXPOSE 9000
