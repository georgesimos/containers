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
