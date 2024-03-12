FROM alpine

EXPOSE	443

RUN apk update && \
    apk add --no-cache nginx vim && \
    mkdir -p /etc/nginx/ssl


RUN apk add openssl --no-cache
RUN openssl req -x509 -days 365 -nodes -newkey rsa:4096 \
	-keyout /etc/nginx/ssl/inception.key \
	-out /etc/nginx/ssl/inception.crt -sha256 -subj "/CN=qbanet.42.fr"

RUN mkdir -p /var/run/nginx

COPY ./conf/nginx.conf /etc/nginx/sites-available/default

RUN mkdir -p /var/www/html && chmod 755 /var/www/html

RUN adduser -u 82 -D -S -G www-data www-data

RUN chown -R www-data:www-data /var/www/html

CMD [ "nginx", "-g", "daemon off;" ]