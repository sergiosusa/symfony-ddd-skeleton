FROM debian:jessie

# Get noninteractive frontend for Debian to avoid some problems:
#    debconf: unable to initialize frontend: Dialog
ENV DEBIAN_FRONTEND noninteractive

RUN echo "\nexport TERM=xterm" >> /etc/bash.bashrc \
 && apt-get update && apt-get install -y --no-install-recommends \
    apt-utils

RUN echo '\n\
deb http://packages.dotdeb.org jessie all\n\
deb-src http://packages.dotdeb.org jessie all\n'\
>> /etc/apt/sources.list

RUN apt-key adv --keyserver keys.gnupg.net --recv-keys 7E3F070089DF5277 \
 && apt-get update && apt-get install -y --no-install-recommends \
    ca-certificates \
    curl \
    git \
    libfcgi0ldbl \
    php7.0-apcu \
    php7.0-bcmath \
    php7.0-bz2 \
    php7.0-cli \
    php7.0-curl \
    php7.0-fpm \
    php7.0-gd \
    php7.0-intl \
    php7.0-mcrypt \
    php7.0-mbstring \
    php7.0-mysql \
    php7.0-pgsql \
    php7.0-xml \
    php7.0-readline \
    php7.0-redis \
    php7.0-sqlite3 \
    php7.0-soap \
    php7.0-ssh2 \
    php7.0-xml \
    php7.0-zip \
    php7.0-xdebug \
    nano \
 && rm -rf /var/lib/apt/lists/*


COPY cli/php.ini         /etc/php/7.0/cli/php.ini
COPY fpm/php.ini         /etc/php/7.0/fpm/php.ini
COPY fpm/pool.d/www.conf /etc/php/7.0/fpm/pool.d/www.conf

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

# FPM child processes run as root
RUN sed -i 's@user = www-data@user = root@' /etc/php/7.0/fpm/pool.d/www.conf \
 && sed -i 's@group = www-data@group = root@' /etc/php/7.0/fpm/pool.d/www.conf \
 && rm /etc/php/7.0/cli/conf.d/20-xdebug.ini

COPY start.sh /start.sh
RUN chmod +x /start.sh

EXPOSE 9000

CMD ["/start.sh"]