# Example deploying for dockerhub

Пример внутренней и внешней сборки + деплой
https://youtu.be/Lu1ziKbQYIQ?t=1054
https://github.com/drucoder/docker-site

@@ Для корректного билда в текущем ридми нужно добавить webpack

### Option 1.

Run Container
```
docker run -it --name node-dru alpine sh
/ apk add nodejs
/ node --version
/ exit
```

```
docker container ls -a | grep node-dru
```

Commit to image
```
docker commit node-dru evosandru6/node-dru:v14.17
```

```
docker images
```

Push to dockerhub
```
docker push evosandru6/node-dru:v14.17
```

Remove locally 
```
docker rmi evosandru6/node-dru:v14.17 
```

Pull image
```
docker pull evosandru6/node-dru:v14.17
```

```
docker images
```
### Option 2. (Via Dockerfile)

Build with tag defining
```
docker build -t evosandru6/node-hru:v1 -f sample.docker .
```

Run
```
docker run -it --name node-hru -p 3000:8080 evosandru6/node-hru:v1
``` 

Curl
```
curl 127.0.0.1:3000
```

Push
```
docker push evosandru6/node-hru:v1
```

Pull
```
docker pull evosandru6/node-hru:v1
```

### Option 2. (Via Dockerfile for nodejs app)

Build
```
docker build -t evosandru6/web-server-external:v1 -f ex.docker .
```

Run
```
docker run -it --name web-ex -p 3000:3000 evosandru6/web-server-external:v1
``` 

Bash (пока список файлов в рабочей папке из контейнера, можно внести в .dockerignore лишнее при копировании)
```
docker run -it --name web-ex -p 3000:3000 evosandru6/web-server-external:v1 bash
cd /opt/server
ls -al
```

