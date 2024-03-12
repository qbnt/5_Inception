FROM alpine

EXPOSE 9000

RUN apk update && \
    apk add --no-cache \
	curl \
    wget \
    php \
    php-fpm \
    php-mysqli \
    php-json \
    php-openssl \
    php-curl \
    php-zlib \
    php-xml \
    php-phar \
    php-intl \
    php-dom \
    php-xmlreader \
    php-ctype \
    php-session \
    php-mbstring \
    mariadb-client



COPY ./conf/www.conf /etc/php/7.3/fpm/pool.d

ADD https://wordpress.org/latest.tar.gz /var/www/latest.tar.gz

RUN cd /var/www && tar -xvf latest.tar.gz && \
	rm -rf latest.tar.gz

RUN curl https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar --output /usr/bin/wp --silent

RUN chmod +x ./usr/bin/wp

RUN mkdir /run/php

COPY ./conf/config.sh /var/www/wordpress/config.sh
RUN chmod +x /var/www/wordpress/config.sh

CMD ["bash", "/var/www/wordpress/config.sh"]