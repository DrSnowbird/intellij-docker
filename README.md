# Intellij IDE in a Docker container

[![](https://images.microbadger.com/badges/image/openkbs/intellij-docker.svg)](https://microbadger.com/images/openkbs/intellij-docker "Get your own image badge on microbadger.com")
[![](https://images.microbadger.com/badges/version/openkbs/intellij-docker.svg)](https://microbadger.com/images/openkbs/intellij-docker "Get your own version badge on microbadger.com")
* INTELLIJ VERSION=ideaIC-2018.1

## Requirements
* Docker 1.13.1+ or latest 17.12.1-ce 
* An X11 server socket enabled (e.g. xhost+)

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
           -v $HOME/.ideaIC-2018.1:/home/developer/.ideaIC-2018.1 \
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


## Other docker-based IDE
* [openkbs/eclipse-oxygen-docker](https://hub.docker.com/r/openkbs/eclipse-oxygen-docker/)
* [openkbs/netbeans](https://hub.docker.com/r/openkbs/netbeans/)
* [openkbs/scala-ide-docker](https://hub.docker.com/r/openkbs/scala-ide-docker/)

## Reference
* https://download.jetbrains.com/idea
