* boot2docker up
* boot2docker ip
* docker info
* docker version
* docker ps -l
* docker ps -a


* docker images
* docker pull centos
* docker search sinatra
* docker commit
* docker build -t="ouruser/sinatra:v2"
* docker push ouruser/sinatra
* docker tag 5db5f8471261 ouruser/sinatra:devel
* docker rmi training/sinatra
* docker exec -it 11d3ca70deec bash

* docker top nostalgic_morse
* docker inspect nostalgic_morse
* docker logs -f nostalgic_morse
* docker stop nostalgic_morse
* docker rm nostalgic_morse

* export DOCKER_HOST=tcp://192.168.59.103:2376
* export DOCKER_CERT_PATH=/Users/sumitarora/.boot2docker/certs/boot2docker-vm
* export DOCKER_TLS_VERIFY=1

* docker run -t -i ubuntu:14.04 /bin/bash

* docker run -t -i c3495713411d /bin/bash

* docker build -t [img] .

* -d = keep running headless
* docker run -p 49160:8080 -d [img]

* docker run -i -t node2 /bin/bash

* docker 954036e84223 -p 49160:8080

* docker run -i -t node2 -p 49160:8080 -v /Users/sumitarora/workspace/docker/docker-node-hello/abc:/abc /bin/bash

```shell
FROM ubuntu

RUN apt-get update
RUN apt-get install -y nginx
RUN echo "\ndaemon off;" >> /etc/nginx/nginx.conf

ADD /site.conf /etc/nginx/sites-available/default

VOLUME ["/website_data"]

EXPOSE 80

CMD ["nginx"]
```

```shell
FROM dockerfile/ubuntu

RUN apt-get update
RUN apt-get install nginx

EXPOSE 80

CMD ["nginx"]
-v /src/webapp: /opt/webapp //if i dnt expose and run
docker run -p 49160:8080 -d node
docker run -v /Users/wsargent/myapp/src:/src
```


```shell
FROM ubuntu

RUN apt-get update
RUN apt-get install -y nodejs
RUN apt-get install -y npm
RUN ln -s /usr/bin/nodejs /usr/bin/node


COPY . /src
RUN cd /src; npm install
EXPOSE  8080
CMD ["node", "/src/index.js"]


docker build -t node

docker run -v /Users/wsargent/myapp/src:/src

docker run -v /Users/sumitarora/Kitematic/test:/src -p 49160:8080 -d

docker run -d -P --name web -v / src / webapp: / opt / webapp training / webapp python app.py
```

https://www.youtube.com/watch?v=2Gi3qF7aM-A
