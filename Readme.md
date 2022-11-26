
# CheFilmServer

## Setup instructions

```bash
docker build -t chefilm-server -f Dockerfile.server .
docker build -t chefilm-redis -f Dockerfile.redis .


docker run -d --name chr1 --cpus 0.5 --memory 512m chefilm-redis

docker run -itd --name chs1 -p 80:8000 --cpus 0.5 --memory 512m -v $PWD:/code  chefilm-server 
docker exec -it chs1 bash

```

## just Help


docker run -d --name test1 --cpus 0.5 --memory 512m -e MYSQL_ALLOW_EMPTY_PASSWORD=TRUE mysql
docker run -d --name test1 --cpus 0.5 --memory 512m -e MYSQL_ROOT_PASSWORD=root1 mysql
docker exec -it test1 mysql -uroot -p
docker exec -it test1 bash
docker inspect test1 | grep IP

docker run -itd --name test5  --cpus 0.5 --memory 512m nginx
docker cp nginx.conf test5:/etc/nginx/nginx.conf
docker exec -it test5 nginx -s reload



docker run -itd --name test4  -v $PWD/client/build:/usr/share/nginx/html --cpus 0.5 --memory 512m nginx
docker cp nginx.conf test4:/etc/nginx/nginx.conf
docker exec -it test4 nginx -s reload


docker run -itd --name test3  -v $PWD/client/build:/code --cpus 0.5 --memory 512m node
docker exec -it test3 bash
npm i serve -g
serve -s code/ -l 80


docker run -itd --name chefilm -p 80:5000 -v $PWD:/code --cpus 0.5 --memory 512m --workdir /code python
pip3 install -r requirements.txt
pip3 install mysqlclient
python3 manage.py runserver 0:80


pip install pipreqs
pipreqs .


docker rm $(docker ps -aq) --force
docker rm test3 --force


celery -A appserver worker --loglevel=info