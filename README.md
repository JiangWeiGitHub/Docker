## The installation procedure for Docker

### Prerequisites

  Official Links: [*Docker*](https://docs.docker.com/engine/installation/linux/ubuntulinux/)

  My Platform: Ubuntu 14.04 64bit

#### Update your apt sources

+ Open a terminal window.<p>
  *Update package information, ensure that APT works with the https method, and that CA certificates are installed.*<p>
`sudo apt-get update`<p>
`sudo apt-get install apt-transport-https ca-certificates`<p>

+ Add the new *GPG* key.<p>
`sudo apt-key adv --recv-keys --keyserver hkp://keyserver.ubuntu.com:80 AAAD1D3563E5A736A4F561EE884D6308E89713C4`<p>

+ Create & Edit the /etc/apt/sources.list.d/docker.list<p>
`vim /etc/apt/sources.list.d/docker.list`<p>
  Add the following sentence to this file.<p>
`deb https://apt.dockerproject.org/repo ubuntu-trusty main`<p>

+ Update the *APT* package index.<p>
`sudo apt-get update`<p>

+ Purge the old repo if it exists.<p>
`sudo apt-get purge lxc-docker`<p>

+ Verify that *APT* is pulling from the right repository.<p>
`sudo apt-cache policy docker-engine`<p>

#### Prerequisites by Ubuntu Version
+ Update your package manager.<p>
`sudo apt-get update`<p>

+ Install the recommended package.<p>
`sudo apt-get install linux-image-extra-$(uname -r) apparmor`<p>

  *Go ahead and install Docker.*<p>

#### Install
+ Update your *APT* package index.<p>
`sudo apt-get update`<p>

+ Install *Docker*.<p>
`sudo apt-get install docker-engine`<p>

+ Start the docker daemon.<p>
`sudo service docker start`<p>

+ Verify docker is installed correctly.<p>
`sudo docker run hello-world`<p>
  *This command downloads a test image and runs it in a container. When the container runs, it prints an informational message. Then, it exits.*<p>

#### Upgrade Docker
`sudo apt-get upgrade docker-engine`<p>

#### Uninstallation
`sudo apt-get purge docker-engine`<p>

To uninstall the Docker package and dependencies that are no longer needed:<p>
`sudo apt-get autoremove --purge docker-engine`<p>

The above commands will not remove images, containers, volumes, or user created configuration files on your host. If you wish to delete all images, containers, and volumes run the following command:<p>
`rm -rf /var/lib/docker`<p>

  *You must delete the user created configuration files manually.*<p>

#### Copy file & folder from host to container or oppositely
file: `docker cp foo.txt [container-id]:/foo.txt`<p>
file: `docker cp [container-id]:/foo.txt foo.txt`<p>
folder: `docker cp foo [container-id]:/foo`<p>
folder: `docker cp [container-id]:/foo foo`<p>

#### Come back to the previous container
`docker start -ia [container-id]`<p>

#### Enter a running docker
`docker exec -it [container-id] bash`<p>

*** 

#### Done ^_^
