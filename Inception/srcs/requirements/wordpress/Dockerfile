# Utilisation de l'image de base Debian Buster
FROM debian:buster

# Mettre à jour les références des paquets et mettre à niveau
RUN apt-get update -y \
		&& apt-get upgrade -y \
		&& apt-get install wget -y \
		&& apt-get install php7.3 php-fpm php-mysql mariadb-client -y \
		&& wget https://wordpress.org/wordpress-6.0.tar.gz -P /var/www/ \
		&& cd /var/www/ && tar -xvf wordpress-6.0.tar.gz && rm wordpress-6.0.tar.gz \
		&& chown -R root:root /var/www/wordpress \
		&& wget https://raw.githubusercontent.com/wp-cli/builds/gh-pages/phar/wp-cli.phar \
		&& chmod 755 wp-cli.phar \
		&& mv wp-cli.phar /usr/local/bin/wp
COPY ./conf/wp-config.php /var/www/wordpress/

RUN mkdir -p /conf && chmod 755 /conf


# Copier le fichier de configuration PHP-FPM
COPY conf/php.conf /etc/php/7.3/fpm/pool.d/www.conf

# Copier le fichier index.html dans /conf (Assurez-vous qu'il est présent dans le contexte de construction)
COPY conf/index.html /conf/index.html
COPY conf/setup.sh /conf/setup.sh
RUN chmod +x /conf/setup.sh


# Définir l'entrée principale du conteneur pour exécuter le script setup.sh
ENTRYPOINT ["/bin/bash", "/conf/setup.sh"]

# Exposer le port 9000 (utilisé pour PHP-FPM, ne garantit pas l'accès depuis l'extérieur)
EXPOSE 9000
