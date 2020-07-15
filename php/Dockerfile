FROM php:7.4.2-fpm

RUN apt-get update \
  #&& apt-get upgrade -y \
  #&& apt-get install -y libcurl4-openssl-dev \
  && apt-get install -y libzip-dev zip unzip \
  && docker-php-ext-install pdo_mysql mysqli zip pcntl \
  && apt-get install -y vim \
  && apt-get install -y libmemcached-dev zlib1g-dev libonig-dev \
  && pecl install memcached \
  && docker-php-ext-enable memcached \
  && pecl install redis \
  && docker-php-ext-enable redis \
  && apt-get install --assume-yes --no-install-recommends --quiet libfreetype6-dev libjpeg-dev libpng-dev \
  && docker-php-ext-configure gd --with-freetype --with-jpeg \
  && docker-php-ext-install -j$(nproc) gd \
  && docker-php-ext-enable gd \
  && curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/local/bin --filename=composer \
  && composer global require laravel/installer \
  #&& apt-get install -y git-core curl build-essential openssl libssl-dev \
  #&& git clone https://github.com/nodejs/node.git \
  #&& cd node \
  #&& ./configure \
  #&& make \
  #&& sudo make install
  && apt-get install -y curl software-properties-common \
  && curl -sL https://deb.nodesource.com/setup_12.x | bash - \
  && apt-get install -y nodejs

ENV LANG C.UTF-8
ENV LC_ALL C.UTF-8
ENV PATH="$PATH:/root/.composer/vendor/bin"

WORKDIR /var/www/html
EXPOSE 9000
