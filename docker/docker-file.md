Docker File Examples
=======

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