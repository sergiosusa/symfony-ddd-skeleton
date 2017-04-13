FROM php:7-fpm

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
    openssh-server \
    telnet \
    php7.0-xdebug \
    git-all \
 && rm -rf /var/lib/apt/lists/*

COPY xdebug.ini       /etc/php/7.0/mods-available/xdebug.ini

RUN curl -sS https://getcomposer.org/installer | php -- --install-dir=/usr/bin --filename=composer

# SSHD daemon setup as per the official documentation
# at https://docs.docker.com/engine/examples/running_ssh_service/
RUN mkdir /var/run/sshd \
 && echo 'root:root' | chpasswd \
 && sed -i 's/PermitRootLogin without-password/PermitRootLogin yes/' /etc/ssh/sshd_config \
 && sed 's@session\s*required\s*pam_loginuid.so@session optional pam_loginuid.so@g' -i /etc/pam.d/sshd

RUN rm /etc/php/7.0/cli/conf.d/20-xdebug.ini

RUN usermod -u 1000 www-data

EXPOSE 22 9000

CMD ["/usr/sbin/sshd", "-D"]

