DIR = /home/${USER}

all: inception

inception:
	chmod +x /home/lps/inception/srcs/requirements/mariadb/tools/docker_entry.sh
	chmod +x /home/lps/inception/srcs/requirements/wordpress/tools/docker_entry.sh
	mkdir -p ${DIR}/data/mariadb
	mkdir -p ${DIR}/data/wordpress
	docker-compose -f ./srcs/docker-compose.yml up --build -d

clean:
	docker-compose -f ./srcs/docker-compose.yml down --rmi all -v --remove-orphans 2>/dev/null || true

fclean: clean
	sudo rm -rf ${DIR}/data/*
	sudo docker rmi -f $$(docker images -a -q) 2> /dev/null || true
	sudo docker volume prune -f

re: fclean all

.PHONY: all clean fclean re
