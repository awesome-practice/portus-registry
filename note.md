1. 文件./registry/init 的换行符要保证为linux的

2. run compose
```shell script
docker-compose -f docker-compose.yml   up  -d 
docker-compose ps 

```
在portus web中配置registry的hostname为REGISTRY_AUTH_TOKEN_SERVICE的值

2. docker login registry
```shell script
docker login host.docker.internal
docker login host.docker.internal:5000
#username: portus
#password: portus
```


3. docker push image
```shell script
docker images
docker tag  eureka-server:1.0  host.docker.internal/eureka-server:1.0
docker push host.docker.internal/eureka-server:1.0

docker tag  eureka-server:1.0  host.docker.internal:5000/eureka-server:1.0
docker push host.docker.internal:5000/eureka-server:1.0
```

4. 于portus web上查看image, 需要一阵时间后才能看到

# 问题解决
##  error authorizing context: insufficient scope
registry中的log
解决： 
在portus web中将registry的hostname配置为REGISTRY_AUTH_TOKEN_SERVICE的值