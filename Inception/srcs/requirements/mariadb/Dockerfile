FROM debian:buster

EXPOSE 3306

RUN apt-get update && apt-get upgrade -y \
		&& apt-get install -y mariadb-server \
		&& mkdir -p /conf && chmod 755 /conf
COPY /conf/creatDataBase.sh /conf/creatDataBase.sh
COPY /conf/my.cnf /etc/mysql/mariadb.conf.d/50-server.cnf

ENTRYPOINT ["/bin/bash", "/conf/creatDataBase.sh"]