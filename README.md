# Containers

## What are containers ?

## chroot

### Ubuntu VM using docker

```
docker run -it --name docker-host --rm --privileged ubuntu:bionic

cat /etc/issue // will tell what version of Ubuntu you're using!
```

This will download the official [Ubuntu container](https://hub.docker.com/_/ubuntu) from Docker Hub and grab the version marked with the bionic tag. In this case, latest means it's the latest stable release (18.04.) You could put `ubuntu:devel` to get the latest development of Ubuntu (as of writing that'd be 19.10). `docker run` means we're going to run some commands in the container, and the `-it` means we want to make the shell interactive (so we can use it like a normal terminal.)
