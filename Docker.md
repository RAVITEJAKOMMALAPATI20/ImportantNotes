# Docker
docker image build -t 1ra4vi3/finalimage  .
### 
```
list all the available cotainers : docker container ls
```
docker inspect 
### Points
### docker images 

```
nginx default port 80
mysql
httpd -apachi  default port 80
```
```
sudo systemctl start docker
sudo systemctl is-active docker
```
### Commands
```
docker run -it -p 80:80 nginx 
docker images
docker container ls
docker container -a
docker pull nginx
-d =>detach(run in backround)
```

```
/usr/share/nginx/html
```
### SSH into Docker container
```
docker container exec -it f30ef49f6580 bash
```
### logs
```
docker containerID logs
```
### Remove Docker Container 
```
docker container rm f4cdb552c176 -f
```
### pushing image to docker hub
```
docker login
1ra4vi3
Ravi@1993
docker push 1ra4vi3/mynginx
```
### Building a docker Image
```
docker image build -t 1ra4vi3/mynginx .
```
Docker username 1ra4vi3

### Important Links

https://www.youtube.com/watch?v=Kyx2PsuwomE


### Kong
```
Kong:

sudo docker run --name kong-database -td -p 9042:9042 cassandra:2.2

sudo docker run --rm --link kong-database:kong-database -e "KONG_DATABASE=cassandra" -e "KONG_CASSANDRA_CONTACT_POINTS=kong-database" kong:0.9.9 kong migrations bootstrap

sudo docker run -d --name kong \
 --link kong-database:kong-database \
 -e "KONG_DATABASE=cassandra" \
 -e "KONG_CASSANDRA_CONTACT_POINTS=kong-database" \
 -e "KONG_PROXY_ACCESS_LOG=/dev/stdout" \
 -e "KONG_ADMIN_ACCESS_LOG=/dev/stdout" \
 -e "KONG_PROXY_ERROR_LOG=/dev/stderr" \
 -e "KONG_ADMIN_ERROR_LOG=/dev/stderr" \
 -e "KONG_ADMIN_LISTEN=0.0.0.0:8001" \
 -e "KONG_ADMIN_LISTEN_SSL=0.0.0.0:8444" \
 -p 8000:8000 \
 -p 8443:8443 \
 -p 8001:8001 \
 -p 8444:8444 \
 kong:0.9.9

curl -i -X POST \
    --url http://localhost:8001/apis/ \
    --data 'name=gumball' \
    --data 'upstream_url=http://internal-gum-1582843025.us-west-2.elb.amazonaws.com:8080/' \
    --data 'strip_request_path=true' \
    --data 'request_path=/goapi'

curl -X POST http://localhost:8001/plugins \
    --data "name=key-auth"

curl -X POST http://localhost:8001/consumers/ \
         --data "username=gumballAuth"

curl -X POST http://localhost:8001/consumers/gumballAuth/key-auth \
  --data "key=7df4616d41484445a65bcf1192ab211c"

```
```
https://stackoverflow.com/questions/42202942/how-to-run-kong-api-gateway-using-docker-containers
```



