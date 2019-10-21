FROM php:7.2-fpm 
MAINTAINER harvey <harveysong@aliyun.com>

RUN apt-get update \
	&& apt-get install -y openssl libssl-dev libmemcached-dev zlib1g-dev curl libmcrypt-dev libjpeg62-turbo-dev libpng-dev libfreetype6-dev \
	&& docker-php-ext-configure gd --with-freetype-dir=/usr/include/  --with-jpeg-dir=/usr/include/ \
	&& docker-php-ext-install -j$(nproc) gd

RUN docker-php-ext-install gettext mysqli  opcache pdo_mysql sockets exif

RUN pecl install mcrypt-1.0.1 \
&& docker-php-ext-enable mcrypt

RUN pecl install redis \
&& docker-php-ext-enable redis

#RUN pecl install mongodb \
#&& docker-php-ext-enable mongodb

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
