# Intellij IDE in a Docker container

[![](https://images.microbadger.com/badges/image/openkbs/intellij-docker.svg)](https://microbadger.com/images/openkbs/intellij-docker "Get your own image badge on microbadger.com") [![](https://images.microbadger.com/badges/version/openkbs/intellij-docker.svg)](https://microbadger.com/images/openkbs/intellij-docker "Get your own version badge on microbadger.com")
* INTELLIJ VERSION=ideaIC-2018.2

# Requirements
* Docker 1.13.1+ or latest 17.12.1-ce 
* An X11 server socket enabled (e.g. xhost+)

# Run (Recommended for easy startup)
```
./run.sh
```
## Guide: Install Scala
During starting up Intellij first time, one of the options will allow you to install "Scala". 
Remember to install that. If not, you still can add inside the Intellij IDE later.
```
firefox ./guide/Intellij-guide-install-Scala-option.png
```

# Stop
```
./stop.sh
```

# Build (Optional)
```
./build.sh
```

# Configure - (Optional) Making plugins persist between sessions
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
# See Also - Docker-based IDE
* [openkbs/docker-atom-editor](https://hub.docker.com/r/openkbs/docker-atom-editor/)
* [openkbs/eclipse-photon-docker](https://hub.docker.com/r/openkbs/eclipse-photon-docker/)
* [openkbs/eclipse-oxygen-docker](https://hub.docker.com/r/openkbs/eclipse-oxygen-docker/)
* [openkbs/intellj-docker](https://hub.docker.com/r/openkbs/intellij-docker/)
* [openkbs/netbeans9-docker](https://hub.docker.com/r/openkbs/netbeans9-docker/)
* [openkbs/netbeans](https://hub.docker.com/r/openkbs/netbeans/)
* [openkbs/papyrus-sysml-docker](https://hub.docker.com/r/openkbs/papyrus-sysml-docker/)
* [openkbs/pycharm-docker](https://hub.docker.com/r/openkbs/pycharm-docker/)
* [openkbs/scala-ide-docker](https://hub.docker.com/r/openkbs/scala-ide-docker/)
* [openkbs/sublime-docker](https://hub.docker.com/r/openkbs/sublime-docker/)
* [openkbs/webstorm-docker](https://hub.docker.com/r/openkbs/webstorm-docker/)

# See Also - Docker-based SQL GUI
* [Mysql-Workbench at openkbs/mysql-workbench](https://hub.docker.com/r/openkbs/mysql-workbench/)
* [PgAdmin4 for PostgreSQL at openkbs/pgadmin-docker](https://hub.docker.com/r/openkbs/pgadmin-docker/)
* [Sqlectron SQL GUI at openkbs/sqlectron-docker](https://hub.docker.com/r/openkbs/sqlectron-docker/)

# Reference
* https://download.jetbrains.com/idea
* https://www.jetbrains.com/idea/

# Display X11 Issue
More resource in X11 display of Eclipse on your host machine's OS, please see
* [X11 Display problem](https://askubuntu.com/questions/871092/failed-to-connect-to-mir-failed-to-connect-to-server-socket-no-such-file-or-di)
* [X11 Display with Xhost](http://www.ethicalhackx.com/fix-gtk-warning-cannot-open-display/)

# Other possible Issues
You might see the warning message in the launching xterm console like below, you can just ignore it. I googles around and some blogs just suggested to ignore since the IDE still functional ok.
```
** (eclipse:1): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-wrKH8o5rny: Connection refused
** (java:7): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-wrKH8o5rny: Connection refused
```


