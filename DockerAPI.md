# Goal<p>
Use docker's API to connect docker's daemon from docker's client in LAN environment.<p>

# Prerequisite<p>
+ owncloud (docker image)<p>
+ curl (cmdline tool on Ubuntu 16.04 64bit)<p>
+ postman (visualization tool on Windows 7 Ultimate 64bit)<p>

# Reference
(**Docker Remote API v1.23**)<https://docs.docker.com/engine/reference/api/docker_remote_api_v1.23/>

# Precedure<p>
+ **service docker stop**<p>
PS: Stop docker service.<p>

+ **docker daemon -H tcp://0.0.0.0:2375**<p>
PS: Rerun docker daemon, point the service to listen to tcp protocol on port 2375. Need not to restart docker again, it ran already.<p>

+ **docker -H tcp://0.0.0.0:2375 run -d -p 80:80 owncloud**<p>
PS: Use another console to run owncloud with tcp protocol.<p>

+ **docker -H tcp://0.0.0.0:2375 ps**<p>
  ```
  CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS              PORTS                    NAMES
  4b08169385e3        owncloud            "/entrypoint.sh apach"   20 seconds ago      Up 17 seconds       0.0.0.0:80->80/tcp       sick_hopper
  ```
  PS: Check the situation.<p>

+ **curl -X GET http://localhost:2375/containers/json?all=1**<p>
  ```
  [{"Id":"4b08169385e3d63a7dff6a591ed03979fa3ecbebbb0c19233ac06864f5de380f","Names":["/sick_hopper"],"Image":"owncloud","ImageID":"sha256:3649079a26be73d26a897455d36dde6dc749f9bfbffe6e4000ed4b5bd3b5473e","Command":"/entrypoint.sh apache2-foreground","Created":1461655546,"Ports":[{"IP":"0.0.0.0","PrivatePort":80,"PublicPort":80,"Type":"tcp"}],"Labels":{},"State":"running","Status":"Up 16 minutes","HostConfig":{"NetworkMode":"default"},"NetworkSettings":{"Networks":{"bridge":{"IPAMConfig":null,"Links":null,"Aliases":null,"NetworkID":"","EndpointID":"f2d0226af15562da26acfb909e19f9920d3a1b35fbc01016518743810e4ce3c5","Gateway":"172.17.0.1","IPAddress":"172.17.0.3","IPPrefixLen":16,"IPv6Gateway":"","GlobalIPv6Address":"","GlobalIPv6PrefixLen":0,"MacAddress":"02:42:ac:11:00:03"}}},"Mounts":[{"Name":"67ebec35b20f4016001b6886223ac7314601acf55b6e6b71237c659f72a1fb30","Source":"/var/lib/docker/volumes/67ebec35b20f4016001b6886223ac7314601acf55b6e6b71237c659f72a1fb30/_data","Destination":"/var/www/html","Driver":"local","Mode":"","RW":true,"Propagation":""}]},{"Id":"397deebcfb75137e7190296b213952707e9ef71c6e2bb7298499a9759afb661a","Names":["/backstabbing_knuth"],"Image":"owncloud","ImageID":"sha256:3649079a26be73d26a897455d36dde6dc749f9bfbffe6e4000ed4b5bd3b5473e","Command":"/entrypoint.sh apache2-foreground","Created":1461577061,"Ports":[],"Labels":{},"State":"exited","Status":"Exited (0) 22 minutes ago","HostConfig":{"NetworkMode":"default"},"NetworkSettings":{"Networks":{"bridge":{"IPAMConfig":null,"Links":null,"Aliases":null,"NetworkID":"","EndpointID":"","Gateway":"","IPAddress":"","IPPrefixLen":0,"IPv6Gateway":"","GlobalIPv6Address":"","GlobalIPv6PrefixLen":0,"MacAddress":""}}},"Mounts":[{"Name":"a5d5329c2b8d1c0c843c5fcb45cb0134de7b9161313ac803786af40f1e132325","Source":"/var/lib/docker/volumes/a5d5329c2b8d1c0c843c5fcb45cb0134de7b9161313ac803786af40f1e132325/_data","Destination":"/var/www/html","Driver":"local","Mode":"","RW":true,"Propagation":""}]},{"Id":"ac548fc9d02ebc06610cccbaddcc0f1c46f67396312067634b7e59e9e13be13f","Names":["/registry"],"Image":"registry:2","ImageID":"sha256:88ecdbb5a908bd1bdbb921110a6134d6916f962680da0c4628102ff0691b38b3","Command":"/bin/registry serve /etc/docker/registry/config.yml","Created":1461575624,"Ports":[{"IP":"0.0.0.0","PrivatePort":5000,"PublicPort":5000,"Type":"tcp"}],"Labels":{},"State":"running","Status":"Up 19 minutes","HostConfig":{"NetworkMode":"default"},"NetworkSettings":{"Networks":{"bridge":{"IPAMConfig":null,"Links":null,"Aliases":null,"NetworkID":"","EndpointID":"d68547a1da72fb84828a977bcc9598bbdeef9255a64b9b98990f5155497f9071","Gateway":"172.17.0.1","IPAddress":"172.17.0.2","IPPrefixLen":16,"IPv6Gateway":"","GlobalIPv6Address":"","GlobalIPv6PrefixLen":0,"MacAddress":"02:42:ac:11:00:02"}}},"Mounts":[{"Source":"/home/wenshang/Downloads","Destination":"/var/lib/registry","Mode":"","RW":true,"Propagation":"rprivate"}]}]
  ```
  PS: Use "curl" to get information from API.<p>
  
+ You can use Postman on Windows, input *http://192.168.5.179:2375/containers/json?all=1*<p>
  ```
  [
    {
      "Id": "4b08169385e3d63a7dff6a591ed03979fa3ecbebbb0c19233ac06864f5de380f",
      "Names": [
        "/sick_hopper"
      ],
      "Image": "owncloud",
      "ImageID": "sha256:3649079a26be73d26a897455d36dde6dc749f9bfbffe6e4000ed4b5bd3b5473e",
      "Command": "/entrypoint.sh apache2-foreground",
      "Created": 1461655546,
      "Ports": [
        {
          "IP": "0.0.0.0",
          "PrivatePort": 80,
          "PublicPort": 80,
          "Type": "tcp"
        }
      ],
      "Labels": {},
      "State": "running",
      "Status": "Up 17 minutes",
      "HostConfig": {
        "NetworkMode": "default"
      },
      "NetworkSettings": {
        "Networks": {
          "bridge": {
            "IPAMConfig": null,
            "Links": null,
            "Aliases": null,
            "NetworkID": "",
            "EndpointID": "f2d0226af15562da26acfb909e19f9920d3a1b35fbc01016518743810e4ce3c5",
            "Gateway": "172.17.0.1",
            "IPAddress": "172.17.0.3",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "MacAddress": "02:42:ac:11:00:03"
          }
        }
      },
      "Mounts": [
        {
          "Name": "67ebec35b20f4016001b6886223ac7314601acf55b6e6b71237c659f72a1fb30",
          "Source": "/var/lib/docker/volumes/67ebec35b20f4016001b6886223ac7314601acf55b6e6b71237c659f72a1fb30/_data",
          "Destination": "/var/www/html",
          "Driver": "local",
          "Mode": "",
          "RW": true,
          "Propagation": ""
        }
      ]
    },
    {
      "Id": "397deebcfb75137e7190296b213952707e9ef71c6e2bb7298499a9759afb661a",
      "Names": [
        "/backstabbing_knuth"
      ],
      "Image": "owncloud",
      "ImageID": "sha256:3649079a26be73d26a897455d36dde6dc749f9bfbffe6e4000ed4b5bd3b5473e",
      "Command": "/entrypoint.sh apache2-foreground",
      "Created": 1461577061,
      "Ports": [],
      "Labels": {},
      "State": "exited",
      "Status": "Exited (0) 22 minutes ago",
      "HostConfig": {
        "NetworkMode": "default"
      },
      "NetworkSettings": {
        "Networks": {
          "bridge": {
            "IPAMConfig": null,
            "Links": null,
            "Aliases": null,
            "NetworkID": "",
            "EndpointID": "",
            "Gateway": "",
            "IPAddress": "",
            "IPPrefixLen": 0,
            "IPv6Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "MacAddress": ""
          }
        }
      },
      "Mounts": [
        {
          "Name": "a5d5329c2b8d1c0c843c5fcb45cb0134de7b9161313ac803786af40f1e132325",
          "Source": "/var/lib/docker/volumes/a5d5329c2b8d1c0c843c5fcb45cb0134de7b9161313ac803786af40f1e132325/_data",
          "Destination": "/var/www/html",
          "Driver": "local",
          "Mode": "",
          "RW": true,
          "Propagation": ""
        }
      ]
    },
    {
      "Id": "ac548fc9d02ebc06610cccbaddcc0f1c46f67396312067634b7e59e9e13be13f",
      "Names": [
        "/registry"
      ],
      "Image": "registry:2",
      "ImageID": "sha256:88ecdbb5a908bd1bdbb921110a6134d6916f962680da0c4628102ff0691b38b3",
      "Command": "/bin/registry serve /etc/docker/registry/config.yml",
      "Created": 1461575624,
      "Ports": [
        {
          "IP": "0.0.0.0",
          "PrivatePort": 5000,
          "PublicPort": 5000,
          "Type": "tcp"
        }
      ],
      "Labels": {},
      "State": "running",
      "Status": "Up 19 minutes",
      "HostConfig": {
        "NetworkMode": "default"
      },
      "NetworkSettings": {
        "Networks": {
          "bridge": {
            "IPAMConfig": null,
            "Links": null,
            "Aliases": null,
            "NetworkID": "",
            "EndpointID": "d68547a1da72fb84828a977bcc9598bbdeef9255a64b9b98990f5155497f9071",
            "Gateway": "172.17.0.1",
            "IPAddress": "172.17.0.2",
            "IPPrefixLen": 16,
            "IPv6Gateway": "",
            "GlobalIPv6Address": "",
            "GlobalIPv6PrefixLen": 0,
            "MacAddress": "02:42:ac:11:00:02"
          }
        }
      },
      "Mounts": [
        {
          "Source": "/home/wenshang/Downloads",
          "Destination": "/var/lib/registry",
          "Mode": "",
          "RW": true,
          "Propagation": "rprivate"
        }
      ]
    }
  ]
  ```
