###### Goal: create a new debian image which contains a 'hello world' file, then save it as a local package.

References: [**One**](https://segmentfault.com/a/1190000002766882); [**Two**](https://segmentfault.com/a/1190000000586840)

* Get default debian image from docker hub<p>
`docker pull debian`<p>

* Use default image to run a new container<p>
`docker run -it debian /bin/bash`<p>
  *PS:*<p>
    *-i: Keep STDIN open even if not attached*<p>
    *-t: Allocate a pseudo-TTY*<p>

<p>
--------------------------In container--------------------------
<p>

* Create a new file with contents of 'hello world'<p>
`echo "hello world > /message.txt"`<p>

* Quit from this container<p>
`exit`<p>

<p>
--------------------------Back to working console--------------------------
<p>

* Get the container ID<p>
`docker ps -l`<p>
  *Just like:*

        CONTAINER ID ...
        2bf7a119a38f ...

* Save image<p>
`docker commit -a "john" -m "added a hello world file" 1193bac93767 debian/hello:v0.0.1`<p>
  *PS:*<p>
    *-a: Author*<p>
    *-m: Commit message*<p>
    *Usage:	docker commit -a "yourName" -m "yourCommit" containerID repositoryOldName/yourNewName:tag*<p>

* Export image<p>
`docker save debian/hello:v0.0.1 > ./hello.tar`<p>

* Import image<p>
`docker load < ./hello.tar`<p>
