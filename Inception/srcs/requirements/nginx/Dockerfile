FROM debian:buster


RUN apt-get update && apt-get upgrade -y \
		&& apt-get install -y nginx \
		&& apt-get install -y openssl \
		&& mkdir -p /etc/nginx/ssl/private \
		&& mkdir -p /etc/nginx/ssl/certs \
		&& mkdir -p /var/run/nginx && \
		openssl req -newkey rsa:4096 -days 42 -nodes -x509 -out /etc/nginx/ssl/certs/inception.crt -keyout /etc/nginx/ssl/private/inception.key -subj "/C=FR/ST=Paris/L=Paris/O=42/OU=42Paris/CN=qbanet.42.fr/UID=qbanet"

COPY conf/nginx.conf /etc/nginx/nginx.conf

RUN chmod 755 /var/www/html \
		&& chown -R www-data:www-data /var/www/html


CMD ["nginx", "-g", "daemon off;"]