FROM alpine

EXPOSE 3306

ARG SQL_DATABASE=${SQL_DATABASE}
ARG SQL_USER=${SQL_USER}
ARG SQL_PASSWORD=${SQL_PASSWORD}
ARG SQL_ROOT_PASSWORD=${SQL_ROOT_PASSWORD}

RUN apk update && apk add --no-cache mariadb mariadb-client

RUN rm -f /etc/mysql/mariadb.conf.d/50-server.cnf

COPY ./conf/50-server.cnf /etc/mysql/mariadb.conf.d/50-server.cnf
COPY ./conf/config.sh /
RUN chmod 755 /config.sh && chmod 755 /etc/mysql/mariadb.conf.d/50-server.cnf

CMD ["./config.sh"]