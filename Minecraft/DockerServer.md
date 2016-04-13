## How to deploy Minecraft-server on docker
Related Reference: [*Click*](https://hub.docker.com/r/itzg/minecraft-server/)

##### Precondition:
+ Windows:<p>
  Minecraft Client: 1.7.2<p>
+ Linux:<p>
  Ubuntu 14.04 64bit & Docker<p>

##### Procedure:
+ Download origin docker image<p>
`docker pull itzg/minecraft-server`<p>

+ Run image<p>
`docker run -ti -e EULA=TRUE --privileged -p 25565:25565 -e VERSION=1.7.2 itzg/minecraft-server /bin/bash`<p>

+ Install sshuttle<p>
`apt-get install sshuttle`<p>
*PS: The reason of installing sshuttle is that TIANCHAO's network is shit!*<p>

+ Run sshuttle<p>
`sshuttle -r root@?.?.?.? 0/0 --dns`<p>
*PS: Use your own server ip.*<p>

+ Open another docker console<p>
  - Find the docker container's ID<p>
  `docker ps`<p>
  - Go into this running container<p>
  `docker exec -it *container's ID* bash`<P>
  - Go into *data* folder<p>
  `cd /data`<p>
  - First run server<p>
  `/start-minecraft`<p>
  *PS: There'll create some new fils which include eula.txt*<P>
  - Edit *eula.txt* file<p>
  `nano /data/eula.txt`<p>
  *Change EULA=false to EULA=TRUE*<p>
  - Quit sshuttle
  *Go into the first console, ctrl + c to quit the server, then go back to the second console.*<p>
  - Rerun server<p>
  `/start-minecraft`<p>
  
          Checking version information.
          Checking type information.
          Downloading minecraft_server.1.7.2.jar ...
          [09:04:31] [Server thread/INFO]: Starting minecraft server version 1.7.2
          [09:04:31] [Server thread/INFO]: Loading properties
          [09:04:31] [Server thread/INFO]: Default game type: SURVIVAL
          [09:04:31] [Server thread/INFO]: Generating keypair
          [09:04:32] [Server thread/INFO]: Starting Minecraft server on *:25565
          [09:04:32] [Server thread/WARN]: Failed to load operators list: java.io.FileNotFoundException: ./ops.txt (No such file or directory)
          [09:04:32] [Server thread/WARN]: Failed to load white-list: java.io.FileNotFoundException: ./white-list.txt (No such file or directory)
          [09:04:32] [Server thread/INFO]: Preparing level "world"
          [09:04:32] [Server thread/INFO]: Preparing start region for level 0
          [09:04:33] [Server thread/INFO]: Preparing spawn area: 6%
          [09:04:34] [Server thread/INFO]: Preparing spawn area: 11%
          [09:04:35] [Server thread/INFO]: Preparing spawn area: 18%
          [09:04:36] [Server thread/INFO]: Preparing spawn area: 24%
          [09:04:37] [Server thread/INFO]: Preparing spawn area: 31%
          [09:04:38] [Server thread/INFO]: Preparing spawn area: 39%
          [09:04:39] [Server thread/INFO]: Preparing spawn area: 48%
          [09:04:40] [Server thread/INFO]: Preparing spawn area: 58%
          [09:04:41] [Server thread/INFO]: Preparing spawn area: 68%
          [09:04:42] [Server thread/INFO]: Preparing spawn area: 79%
          [09:04:43] [Server thread/INFO]: Preparing spawn area: 93%
          [09:04:44] [Server thread/INFO]: Done (11.786s)! For help, type "help" or "?"

  
