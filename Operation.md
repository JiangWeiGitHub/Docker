###### Goal: create a new debian image which contains a 'hello world' file, then save it as a local package.

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
`quit`<p>

<p>
--------------------------Back to working console--------------------------
<p>

* Get the container ID<p>
`docker ps -l`<p>
    CONTAINER ID<p>
    2bf7a119a38f<p>
