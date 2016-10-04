# Liveblog
[Download](https://github.com/liveblog/liveblog/archive/master.zip) •
[Fork](https://github.com/liveblog/liveblog) •
[License](https://github.com/liveblog/liveblog/blob/master/LICENSE) •
[Documentation](http://sourcefabric.booktype.pro/live-blog-30-for-journalists/what-is-live-blog/) •
*Version 3.0.9*

[![Build Status](https://travis-ci.org/liveblog/liveblog.svg?branch=master)](https://travis-ci.org/liveblog/liveblog)

## Up to date installation

How to run Liveblog in a full docker environment

Remove older database and packages

```
cd ~/code/liveblog
sudo rm -rf data/ client/node_modules client/.tmp
```

We need to create the configuration file for the frontend:

```
cp client/config.sample.js client/config.js
```

Run docker

``
cd ~/code/liveblog
docker-compose -p liveblog -f docker/docker-compose-dev.yml up
``

SSh into the superdesk docker container:

``
docker exec -i -t `docker ps | grep liveblog_superdesk | awk '{print $1}'` /bin/bash
python3 manage.py users:create -u admin -p admin -e 'admin@example.com' --admin ;
python3 manage.py register_local_themes ;
python3 manage.py schema:migrate ;
```

## Old installation

### Installation

Use [docker-compose](http://fig.sh "") and the config from `docker` folder or build docker images manually from the [Dockerfile](./Dockerfile).

##### install docker

```sh
$ sudo apt-get install docker.io
```

and make sure you can run [docker without sudo](http://askubuntu.com/questions/477551/how-can-i-use-docker-without-sudo).

##### create python virtualenv

```sh
$ sudo apt-get install python-virtualenv
$ virtualenv env
```

##### install docker compose and run app

```sh
$ . env/bin/activate
$ pip install -r docker/requirements.txt
$ ./scripts/docker-local-demo.sh
```
