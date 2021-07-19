# Example deploying for dockerhub

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
docker build -f sample.docker -t evosandru6/node-hru:v1 .
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
