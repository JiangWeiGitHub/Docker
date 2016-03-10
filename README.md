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
`sudo apt-key adv --keyserver hkp://p80.pool.sks-keyservers.net:80 --recv-keys 58118E89F3A912897C070ADBF76221572C52609D`<p>

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

*** 

#### Done ^_^
