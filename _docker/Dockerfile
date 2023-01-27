FROM php:7.0-fpm

RUN apt-get -qq update && apt-get -qq install libxml++2.6-dev > /dev/null
# Install dependencies
RUN apt-get update && apt-get install -y \
    jpegoptim optipng pngquant gifsicle \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    build-essential \
    libfontconfig1 \
    libxrender1 \
    libpng-dev \
    libzip-dev \
    libpq-dev \
    locales \
    unzip \
    curl \
    zip \
    vim \
    git \
    && docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/ \
    && docker-php-ext-install -j$(nproc) pdo pdo_mysql mysqli zip exif pcntl gd bcmath

# Clear cache
RUN apt-get clean && rm -rf /var/lib/apt/lists/*

#for php5.6
#RUN pecl install xdebug-2.2.5 \
#for php7.0
RUN pecl install xdebug-2.5.5 \
    && docker-php-ext-enable xdebug \

RUN yes | pecl install   \
    && echo "zend_extension=$(find /usr/local/lib/php/extensions/ -name xdebug.so)" > /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_enable=on" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_port=9000" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.idekey=PHPSTORM" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_host = host.docker.internal" >> /usr/local/etc/php/conf.d/xdebug.ini \
    && echo "xdebug.remote_log='/tmp/xdebug_log/xdebug.log'" >> /usr/local/etc/php/conf.d/xdebug.ini

RUN groupadd -g 1000 www
RUN useradd -u 1000 -ms /bin/bash -g www www

USER www