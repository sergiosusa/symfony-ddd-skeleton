FROM php:7.0-fpm

# Get noninteractive frontend for Debian to avoid some problems:
#    debconf: unable to initialize frontend: Dialog
ENV DEBIAN_FRONTEND noninteractive

RUN echo '\n\
deb http://packages.dotdeb.org jessie all\n\
deb-src http://packages.dotdeb.org jessie all\n'\
>> /etc/apt/sources.list

RUN apt-key adv --keyserver keys.gnupg.net --recv-keys 7E3F070089DF5277 \
 && apt-get update && apt-get install -y --no-install-recommends \
    nano \
    telnet \
    php7.0-xdebug \
    php7.0-xml \
    git-all \
 && rm -rf /var/lib/apt/lists/*

RUN  rm /etc/php/7.0/cli/conf.d/20-xdebug.ini
COPY xdebug.ini       /etc/php/7.0/mods-available/xdebug.ini
RUN ln -sf /etc/php/7.0/mods-available/xdebug.ini /etc/php/7.0/cli/conf.d/20-xdebug.ini
RUN mkdir -p /etc/php/7.0/fpm/conf.d
RUN ln -sf /etc/php/7.0/mods-available/xdebug.ini /etc/php/7.0/fpm/conf.d/20-xdebug.ini
COPY cli/php.ini         /etc/php/7.0/cli/php.ini
COPY fpm/php.ini         /etc/php/7.0/fpm/php.ini
COPY fpm/pool.d/www.conf /etc/php/7.0/fpm/pool.d/www.conf

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

RUN usermod -u 1000 www-data

EXPOSE 22 9000
