# What I've learned so far

## Create Docker Image

``` docker build -t feedback-node . ``` 

Create an image based on Dockerfile on give directory `.` with a tag name of `feedback-node`.
## Create Docker Container

``` docker run -p 3000:80 -d --name feeback-app --rm feedback-node ``` 

Run a container in detached mode (`-d`) based on `feedback-node` image with the name of `feedback-app`, expose internal port `80` to external port `3000` and remove that container once stopped (`--rm`)

## Volumes

Are folders in host machine which are mounted into containers.

`docker volume ls` to list volumes

### Anonymous Volume

In Dockerfile add `VOLUMES ["path"]

### Named Volume

In docker run command add `-v name:path` ex: `-v feedback:/app/feedback`. This will exist even when container is removed

## Bind Mounts 

Run command -v "local-path:/remote-path" or this shortcut `-v $(pwd):/app`