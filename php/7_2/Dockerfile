FROM php:7.2-fpm

RUN apt-get update && apt-get install -y \
    zlib1g-dev \
    libzip-dev \
    libcurl3-dev \
    libmagickwand-dev \
    libxml2-dev

RUN docker-php-ext-install pdo_mysql mysqli zip curl soap \
    && pecl install redis-5.1.1 \
	&& pecl install xdebug-2.8.1 \
    && pecl install apcu-5.1.18 \
    && pecl install imagick \
    && docker-php-ext-enable mysqli redis xdebug apcu imagick

RUN touch /usr/local/etc/php/conf.d/uploads.ini \
    && echo "upload_max_filesize = 50M\npost_max_size = 50M\nmax_execution_time = 600\nmax_input_vars = 4000" >> /usr/local/etc/php/conf.d/uploads.ini

RUN echo "xdebug.remote_autostart=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_enable=1" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null && \
    echo "xdebug.remote_host=192.168.1.221" | tee -a /usr/local/etc/php/conf.d/docker-php-ext-xdebug.ini > /dev/null
