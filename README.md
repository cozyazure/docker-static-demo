# docker-static-demo
A short demo on how to use docker to serve static websites in nginx.

## Requirements

All you need is dockers installed on your machine :)

## Clone the project

```bash
$ git clone git@github.com:cozyazure/docker-static-demo.git
$ cd docker-static-demo
```

## Build the docker image.

To build the docker image, run the following command on the terminal. This will read your Dockerfile config and create the image accordingly.

```bash
docker build -t awesome-website:v1 .
```

### Explanation on `Dockerfile` 

```bash
FROM nginx:alpine
COPY . /usr/share/nginx/html
```

The first line `FROM` tells us what is our base image. Here, we will run nginx on the apline distro. 
The secondline copies everything in the current directory and place it under the directory of the container, which is `/usr/share/nginx/html`

## View Docker image

To inspect what are the images are on the host, use

```bash
docker images
```

You should see `awesome-website` is on the host:

```bash
REPOSITORY         TAG          IMAGE ID        CREATED             SIZE
awesome-website     v1           1c93a37292d0    10 seconds ago      54.28 MB
```

## Run Docker

You can now run the image to serve the static files.

```bash
docker run -d -p 3000:80 awesome-website:v1
```

The `-d` flag stands for detach, meaning it will run the container in background (and print container ID)

The `-p` flag means to publish, and it wil publish a containers port to the host port, in the format of following:

```
-p <host-port>:<container-port>.
```

## View the webpage

Just go to <a href="http://localhost:3000">localhost:3000</a> and you should see the static website running.




