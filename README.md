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
If you use "./run.sh", you can ignore this section!

Intellij configurations are kept on `$HOME/.ideaIC-2018.1` inside the container, so if you
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
## Similar docker-based IDE
* [openkbs/eclipse-oxygen-docker](https://hub.docker.com/r/openkbs/eclipse-oxygen-docker/)
* [openkbs/netbeans](https://hub.docker.com/r/openkbs/netbeans/)
* [openkbs/scala-ide-docker](https://hub.docker.com/r/openkbs/scala-ide-docker/)
* [openkbs/pycharm-docker](https://hub.docker.com/r/openkbs/pycharm-docker/)
* [openkbs/webstorm-docker](https://hub.docker.com/r/openkbs/webstorm-docker/)
* [openkbs/intellj-docker](https://hub.docker.com/r/openkbs/intellij-docker/)

## Reference
* https://download.jetbrains.com/idea
* https://www.jetbrains.com/idea/
# Display X11 Issue

More resource in X11 display of Eclipse on your host machine's OS, please see
* [X11 Display problem](https://askubuntu.com/questions/871092/failed-to-connect-to-mir-failed-to-connect-to-server-socket-no-such-file-or-di)
* [X11 Display with Xhost](http://www.ethicalhackx.com/fix-gtk-warning-cannot-open-display/)

# Other possible Issues
You might see the warning message in the launching xterm console like below, you can just ignore it. I googles around and some blogs just suggested to ignore since the Eclipse IDE still functional ok.
```
** (eclipse:1): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-wrKH8o5rny: Connection refused

** (java:7): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-wrKH8o5rny: Connection refused

```


