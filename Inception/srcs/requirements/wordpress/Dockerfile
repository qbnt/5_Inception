FROM debian:buster

RUN apt-get update -y \
		&& apt-get upgrade -y \
		&& apt-get install wget -y \
		&& apt-get install php7.3 php-fpm php-mysql mariadb-client -y \
		&& wget https://wordpress.org/wordpress-6.4.3.tar.gz -P /var/www/ \
		&& cd /var/www/ && tar -xvf wordpress-6.4.3.tar.gz && rm wordpress-6.4.3.tar.gz \
		&& chown -R root:root /var/www/wordpress \
		&& wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
		&& chmod 755 wp-cli.phar \
		&& mv wp-cli.phar /usr/local/bin/wp

COPY ./conf/wp-config.php /var/www/wordpress/

EXPOSE 9000

RUN mkdir -p /conf && chmod 755 /conf

COPY conf/php.conf /etc/php/7.3/fpm/pool.d/www.conf
COPY conf/index.html /conf/index.html
COPY conf/setup.sh /conf/setup.sh

RUN chmod +x /conf/setup.sh


ENTRYPOINT ["/bin/bash", "/conf/setup.sh"]

