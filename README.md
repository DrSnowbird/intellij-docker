# Intellij IDE in a Docker container

* INTELLIJ VERSION=ideaIC-2017.3

## Requirements
* Docker 1.13.1+ 
* An X11 socket

## Build
```
./build.sh
```

## Run
```
./run.sh
```

## Making plugins persist between sessions

Intellij configurations are kept on `$HOME/.ideaIC-2017.2` inside the container, so if you
want to keep them around after you close it, you'll need to share it with your
host.

For example: (Version might be different - use run.sh instead)

```sh
docker run -ti --rm \
           -e DISPLAY=$DISPLAY \
           -v /tmp/.X11-unix:/tmp/.X11-unix \
           -v $HOME/.ideaIC-2017.3:/home/developer/.ideaIC-2017.3 \
           -v `pwd`:/home/developer/workspace \
           openkbs/intellij-docker
```

## Help! I started the container but I don't see the X11 screen

You might have an issue with the X11 socket permissions since the default user
used by the base image has an user and group ids set to `1000`, two options:
* Create your own base image with the appropriate ids or 
* Or, at the host, run
```
`xhost +` 
```
try again.

## Reference
* https://download.jetbrains.com/idea
