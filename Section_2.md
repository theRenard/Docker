# What I've learned so far

## Dockerfile example

Dockerfile example: 

```
FROM node:14

WORKDIR /app

COPY package.json .

RUN npm install

COPY . .

EXPOSE 3000

CMD [ "node", "app.mjs" ]
```

`FROM` starting image

`WORKDIR` internal working directory (better use /app)

`COPY` copy from -> to

`RUN` run command

`COPY` copy again, because we have layers all steps before this will not be duplicated

`EXPOSE` this is obsolete, you must use `-p ext:int` ex: `docker run -p 80:3000`

`CMD` is a command into terminal, as an array, it becomes `node app.mjs` 

## Build

`docker build .` build from `Dockerfile`

`docker build -t name:tag .` build with name, ex: `myApp:v10`

## RUN

`docker run xxxxxx` where xxxx is both the id of an image or the tag

`docker run myApp:v10` we run a container from the above image

### More parameters

`docker run -p ext:int myApp:10` specify the ports

`docker run -d myApp:10` detached

`docker attach [container]` to attach to a running container

`docker run -it myApp:10` with interaction (ex python input)

`docker run --name myApp myApp:10` specify container name (to stop/start)

`docker run --rm myApp:10` remove the container once stopped

## Utils

`docker cp [path] [container]:/[path]` copy files from disk to image

`docker cp [container]:/[path] [path] ` copy files from image to disk

`docker image ls` list images

`docker rm [container name]` removes container

`docker rmi [image name]` removes image (should not be used by an existing container)