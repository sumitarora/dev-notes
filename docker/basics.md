Commands
=======

|  Command | Description  |
|---|---|---|---|---|
| boot2docker up  |  -- |
| boot2docker ip  |  -- |
| docker info  |  -- |
| docker version  |  -- |
| docker ps -l  |  -- |
| docker ps -a  |  -- |
| docker images  |  -- |
| docker pull <image>  |  -- |
| docker search <name>  |  -- |
| docker commit  |  -- |
| docker build -t="ouruser/sinatra:v2"  |  -- |
| docker push ouruser/sinatra  |  -- |
| docker tag 5db5f8471261 ouruser/sinatra:devel  |  -- |
| docker rmi training/sinatra  |  -- |
| docker exec -it 11d3ca70deec bash  |  -- |
| docker top nostalgic_morse  |  -- |
| docker inspect nostalgic_morse  |  -- |
| docker logs -f nostalgic_morse  |  -- |
| docker stop nostalgic_morse  |  -- |
| docker rm nostalgic_morse  |  -- |
| export DOCKER_HOST=tcp://192.168.59.103:2376  |  -- |
| export DOCKER_CERT_PATH=/Users/sumitarora/.boot2docker/certs/boot2docker-vm  |  -- |
| export DOCKER_TLS_VERIFY=1  |  -- |
| docker run -t -i ubuntu:14.04 /bin/bash  |  -- |
| docker run -t -i c3495713411d /bin/bash  |  -- |
| docker build -t [img] .  |  -- |
| docker run -p 49160:8080 -d [img]  |  -- |
