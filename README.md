# Containers

## What are containers ?

...

## chroot

...

### Ubuntu VM using docker

```
docker run -it --name docker-host --rm --privileged ubuntu:bionic

cat /etc/issue // will tell what version of Ubuntu you're using!
```

This will download the official [Ubuntu container](https://hub.docker.com/_/ubuntu) from Docker Hub and grab the version marked with the bionic tag. In this case, latest means it's the latest stable release (18.04.) You could put `ubuntu:devel` to get the latest development of Ubuntu (as of writing that'd be 19.10). `docker run` means we're going to run some commands in the container, and the `-it` means we want to make the shell interactive (so we can use it like a normal terminal.)

## Namespaces

...

## cgroups

...

## Getting Set Up with Docker

Docker is a commandline tool that made creating, updating packaging, distributing, and running containers significantly easier which in turns allowed them become very popular with not just system administraters but the programming populace at large. At its heart, it's a command line to achieve what we were doing with cgroups, namespaces, and chroot but in a much more convenient way.

## Docker Images

#### Images

These pre-made containers are called images. They basically dump out the state of the container, package that up, and store it so you can use it later.

try

```
docker run --interactive --tty alpine:3.10
// or
docker run -it alpine:3.10 // to be shorter
```

## Node.js on Docker

#### Node.js on Containers

```js
docker run -it node:12-stretch
/// Notice this drops us into the Node.js REPL which may or may not be what you want.

docker run -it node:12-stretch bash

node --version // Now we can check the node version

cat /etc/issue // and also what linux is running
```

#### Tags

[see here!](https://btholt.github.io/complete-intro-to-containers/tags)

## Docker CLI

#### pull / push

pull allows you to pre-fetch container to run. P

```
docker pull jturpin/hollywood
docker run -it jturpin/hollywood hollywood
# notice it's already loaded and cached here; it doesn't redownload it
```

push allows you to push containers to whatever registry you're connected to (probably normally Docker Hub or something like Azure Container Registry).

#### kill and kill all

```
docker kill id // kill one
docker kill $(docker ps -q) // kill all
```

... [read more](https://btholt.github.io/complete-intro-to-containers/docker-cli)

## Intro to Dockerfiles

Docker has a special file called a `Dockerfile` which allows you to outline how a container will be built. Each line in a Docker file is a new a directive of how to change your Docker container.

A big key with Docker container is that they're supposed to be disposable. You should be able to create them and throw them away as many times as necessary. In other words: adopt a mindset of making everything short-lived. There are other, better tools for long-running, custom containers.

#### The most basic Dockerfile-based Container

```docker
FROM node:12-stretch

CMD ["node", "-e", "console.log(\"hi lol\")"]
```

The first thing on each line (`FROM` and `CMD` in this case) are called instructions. They don't technically have to be all caps but it's convention to do so so that the file is easier to read. Each one of these instruction incrementally changes the container from the state it was in previously, adding what we call a layer.

Let's go ahead and build our container. Run (from inside of the directory of where your Dockerfile is)

```
docker build .
```

... [read more](https://btholt.github.io/complete-intro-to-containers/dockerfile)

## Build a Node.js App

Make a file called `index.js` and put this in there.

```js
const http = require("http");

http
  .createServer(function(request, response) {
    console.log("request received");
    response.end("omg hi", "utf-8");
  })
  .listen(3000);
console.log("server started");
```

create a `Dockerfile`

```docker
FROM node:12-stretch

COPY index.js index.js

CMD ["node", "index.js"]
```

build the docker container and run

```
docker build -t my-node-app .
docker run my-node-app
```

[read more](https://btholt.github.io/complete-intro-to-containers/build-a-nodejs-app)

## MAKING TINY CONTAINERS – MULTI STAGE BUILDS

[read more](https://btholt.github.io/complete-intro-to-containers/alpine-linux)

## Docker Compose

[read more](https://btholt.github.io/complete-intro-to-containers/docker-compose)

if you set up a node container and you want to use nodemon
run the docker compouse with the --build flag

```bash
docker-compose up --build
```
