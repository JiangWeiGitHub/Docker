# Usage for different platforms

### Project

[**fruitmix-desktop**](https://github.com/wisnuc/fruitmix-desktop)


### Docker Document

[**Official API**](https://docs.docker.com/engine/api/v1.26/)


### Linux Kernel Capabilities

[**Reference**](https://linux.die.net/man/7/capabilities)


### X86 Normal -> Ubuntu 16.04.1 amd64

+ api

`docker -H tcp://127.0.0.1:1688 run --volume /a:/media/share --volume /b:/media/timemachine --net "host" --env AVAHI=1 cptactionhank/netatalk:latest`


### X86 215I -> Ubuntu 16.04.1 amd64

+ api

`docker -H tcp://127.0.0.1:1688 run --cap-add SYS_RESOURCE --volume /a:/media/share --volume /b:/media/timemachine --net "host" --env AVAHI=1 cptactionhank/netatalk:latest`


### Miscellaneous

`--volume` -> [*wisnuc/appifi-recipes reference*](https://github.com/wisnuc/appifi-recipes/blob/release/doc/customizationParameters.md)

`--net` -> API `HostConfig -> NetworkMode`

`--cap-add` -> API `HostConfig -> CapAdd`

`--env` -> API `Env`
