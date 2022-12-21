## Docker Tips

ps -ef

docker container ls

docker container ls -a - Lista containers tanto em execuçaõ quanto deletados

CTRL + C = Sao dp docker matando o processo

CTRL + P + Q sair sem matar processo

docker container run -ti ubuntu - Terminal interatividade

docker container attach containerID - volta ao container

docker container run -d  roda como deamon, pra rodar em segundo plano, nao roda como terminal e nem trava o terminal

Executar comandos em um container que nao seja terminal interativo

docker container exec -ti a267999622c9 ls /

docker container exec -ti a267999622c9 bash

docker container stop 7e395798573b

docker container start 7e395798573b

docker container restart 7e395798573b


docker container inspect 7e395798573b

docker container pause 7e395798573b

docker container unpause 7e395798573b

docker container logs -f 7e395798573b - Puxa logs em tempo real


sudo docker container rm -f  - remover container


BC - bash calculator

docker container run -d -m 128M nginx --cpus 0.5 - executa container com limite de memoria e de cores de CPU

 sudo docker container update --cpus 0.5 --memory 64M - atualiza recursos do docker 


sudo docker container run -ti --mount type=bind,src=/opt/girodocker,dst=/girodocker debian

Monta imagem e carrega volume indicando a entrada e onde será montado dentro da imagem docker

sudo docker container run -ti --mount type=bind,src=/opt/girodocker,dst=/girodocker,ro debian

Faz a mesma coisa que o comando anterior mas adiciona a opção de Ready only

sudo docker volume create girodocker
Cria volume

docker volume inspect ttrss-docker_backups 
Inspeciona o volume mostrando aonde está salvo na maquina

sudo docker container run -ti --mount type=volume,src=nomedovolume,dst=/girodocker debian

montar volume ja criado

docker volume prune 
docker container prune

remove todo volume/container que estiver parado 


docker container run -d -p 5433:5432 --name pgsql2 --mount type=volume,src=dbdados,dst=/data -e POSTGRESQL_USER=docker -e POSTGRESQL_PASS=docker -e POSTGRESQL_DB=docker kamui/postgresql



sudo docker container run -ti --mount type=volume,src=dbdados,dst=/data --mount type=bind,src=/opt/backup,dst=/backup debian tar -cvf /backup/bkp-banco.tar /data

Faz backup de volumes no docker


sudo docker image build -t meu_apache:2.0.0 .

Criar imagens do apache com base no arquivo Dockerfile

sudo docker image build -t meu_apache:2.0.0 . --no-cache

Cria imagens cmo base no Dockerfile porém sem utilzar cache


Pesquisar depois = health check docker 

docker commit -m "Ubuntu com vim e curl" 298a121307fa
Cria imagem de docker baseado em container que já está em execução


docker image tag 3fc5f5c6d379 ubuntu-vim-curl:1.0

nomeia imagem que veio como <none>



