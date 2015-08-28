FROM ubuntu:trusty

MAINTAINER Mario Pitassi <mariop2000@hotmail.fr>

ENV BOOT2DOCKER_ID 1000
ENV BOOT2DOCKER_GID 50
RUN usermod -u ${BOOT2DOCKER_ID} www-data && \
    usermod -G staff www-data
RUN groupmod -g $(($BOOT2DOCKER_GID + 10000)) $(getent group $BOOT2DOCKER_GID | cut -d: -f1)
RUN groupmod -g ${BOOT2DOCKER_GID} staff

RUN apt-get update && \
    DEBIAN_FRONTEND=noninteractive apt-get -yq install \
        imagemagick \
        curl \
        wget \
        apache2 \
        libapache2-mod-php5 \
        php5-mysql \
        php5-gd \
        php5-curl \
        php-pear \
        php5-mcrypt \
        php-apc \
        php5-imagick \
        && \
    rm -rf /var/lib/apt/lists/* && \
    php5enmod mcrypt && \
    a2enmod rewrite && \
    rm /etc/apache2/sites-enabled/000-default.conf && \
    echo "ServerName localhost" >> /etc/apache2/apache2.conf && \
    service apache2 stop

ADD run.sh /run.sh
ADD conf/vhost.conf /etc/apache2/sites-enabled/
ADD php.ini /etc/php5/apache2/conf.d/30-custom.ini

VOLUME /etc/apache2/sites-enabled/
VOLUME /var/www

RUN chmod 755 /run.sh

EXPOSE 80 1500

CMD ["/run.sh"]
