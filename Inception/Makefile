# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Makefile                                           :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: qbanet <qbanet@student.42perpignan.fr>     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2024/03/02 10:18:05 by qbanet            #+#    #+#              #
#    Updated: 2024/03/25 09:53:23 by qbanet           ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

NAME = inception
CONFIGS_FOLDER = ./srcs/requirements
COMPOSE_FILE = ./srcs/docker-compose.yml
ENV = ./srcs/.env
BASEYML = ./srcs/tools/base.yml
LOGIN = $(shell whoami)

all: build start

build:
	mkdir -p ~/data/mariadb
	mkdir -p ~/data/wordpress
	sudo docker-compose -f $(COMPOSE_FILE) build
	@echo "\n\nInception is ready to be launched."

start:
	sudo docker-compose -f $(COMPOSE_FILE) up -d
	@echo "\n\nInception is now running on https://qbanet.42.fr."

stop:
	sudo docker-compose -f $(COMPOSE_FILE) stop

clean: stop
	sudo docker-compose -f $(COMPOSE_FILE) down -v

fclean: clean
	@if [ -n "$$(sudo docker ps -a -q)" ]; then sudo docker rm -f $$(sudo docker ps -a -q); fi
	@if [ -n "$$(sudo docker images -q)" ]; then sudo docker rmi -f $$(sudo docker images -q); fi
	@if [ -n "$$(sudo docker volume ls -q)" ]; then sudo docker volume prune -f; fi
	sudo rm -rf ~/data/*

prune:
	@docker system prune -a

re: fclean all