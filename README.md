# Docker
Practice the docker

#To build the docker image
docker image build -t webanalyzer

#To run the docker web
docker container run -it --rm --name webanalyzer -p 5000:5000  -e FLASK_APP=app.py -e FLASK_DEBUG=1 -e WEB2_COUNTER_MSG="The Docker visitors are " -v $PWD:/app --net firstnetwork webanalyzer

#To create the network
docker network create --driver bridge firstnetwork

#To create the volume
docker volume create web2_redis

#To run the redis container
docker container run -it --rm --name redis -p 6379:6379 -d --net firstnetwork -v web2_redis:/data --volumes-from web2 redis:3.2-alpine

#To build the docker COMPOSE
docker-compose build

#To run the docker COMPOSE
docker-compose up

#Both build and run
docker-compose up --build -d 
