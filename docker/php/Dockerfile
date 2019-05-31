FROM php:7.3.5-fpm

RUN apt-get update \
    && apt-get install \
    git \
    zip \
    unzip \
    libjpeg62-turbo-dev \
    libfreetype6-dev \
    libpng-dev \
    -y

# create php.ini
COPY ./docker/php/php.ini /usr/local/etc/php/php.ini

# create www.conf
COPY ./docker/php/www.conf /usr/local/etc/php-fpm.d/www.conf

RUN docker-php-ext-install pdo_mysql mysqli bcmath sockets

RUN docker-php-ext-configure gd --with-freetype-dir=/usr/include/ --with-jpeg-dir=/usr/include/
RUN docker-php-ext-install -j$(nproc) gd

# install composer
RUN curl https://getcomposer.org/installer | php \
    && mv composer.phar /usr/local/bin/composer

# install mongodb extension
RUN pecl install mongodb \
    && echo "extension=mongodb.so" >> /usr/local/etc/php/php.ini

RUN composer install
