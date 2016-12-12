[linuxserverurl]: https://linuxserver.io
[forumurl]: https://forum.linuxserver.io
[ircurl]: https://www.linuxserver.io/irc/
[podcasturl]: https://www.linuxserver.io/podcast/

[![linuxserver.io](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/linuxserver_medium.png)][linuxserverurl]

The [LinuxServer.io][linuxserverurl] team brings you another container release featuring easy user mapping and community support. Find us for support at:
* [forum.linuxserver.io][forumurl]
* [IRC][ircurl] on freenode at `#linuxserver.io`
* [Podcast][podcasturl] covers everything to do with getting the most from your Linux Server plus a focus on all things Docker and containerisation!

# lsioarmhf/muximux-aarch64
[![](https://images.microbadger.com/badges/version/lsioarmhf/muximux-aarch64.svg)](https://microbadger.com/images/lsioarmhf/muximux-aarch64 "Get your own version badge on microbadger.com")[![](https://images.microbadger.com/badges/image/lsioarmhf/muximux-aarch64.svg)](http://microbadger.com/images/lsioarmhf/muximux-aarch64 "Get your own image badge on microbadger.com")[![Docker Pulls](https://img.shields.io/docker/pulls/lsioarmhf/muximux-aarch64.svg)][hub][![Docker Stars](https://img.shields.io/docker/stars/lsioarmhf/muximux-aarch64.svg)][hub][![Build Status](http://jenkins.linuxserver.io:8080/buildStatus/icon?job=Dockers/LinuxServer.io-arm64/lsioarm64-muximux)](http://jenkins.linuxserver.io:8080/job/Dockers/job/LinuxServer.io-arm64/job/lsioarm64-muximux/)
[hub]: https://hub.docker.com/r/lsioarmhf/muximux-aarch64/

This is a lightweight portal to view & manage your HTPC apps without having to run anything more than a PHP enabled webserver. With Muximux you don't need to keep multiple tabs open, or bookmark the URL to all of your apps. [Muximux](https://github.com/mescon/Muximux).

[![muximux](https://raw.githubusercontent.com/linuxserver/docker-templates/master/linuxserver.io/img/muximux-icon.png)][muximuxurl]
[muximuxurl]: https://github.com/mescon/Muximux

## Usage

```
docker create \
  --name=muximux \
  -v <path to data>:/config \
  -e PGID=<gid> -e PUID=<uid>  \
  -e TZ=<timezone> -p 80:80 \
  lsioarmhf/muximux-aarch64
```

## Parameters

`The parameters are split into two halves, separated by a colon, the left hand side representing the host and the right the container side. 
For example with a port -p external:internal - what this shows is the port mapping from internal to external of the container.
So -p 8080:80 would expose port 80 from inside the container to be accessible from the host's IP on port 8080
http://192.168.x.x:8080 would show you what's running INSIDE the container on port 80.`


* `-p 80` - the port(s)
* `-v /config` - Where muximux should store its files
* `-e PGID` for GroupID - see below for explanation
* `-e PUID` for UserID - see below for explanation
* `-e TZ` for timezone setting, eg Europe/London

It is based on phusion baseimage, for shell access whilst the container is running do `docker exec -it muximux /bin/bash`.

### User / Group Identifiers

Sometimes when using data volumes (`-v` flags) permissions issues can arise between the host OS and the container. We avoid this issue by allowing you to specify the user `PUID` and group `PGID`. Ensure the data volume directory on the host is owned by the same user you specify and it will "just work" ™.

In this instance `PUID=1001` and `PGID=1001`. To find yours use `id user` as below:

```
  $ id <dockeruser>
    uid=1001(dockeruser) gid=1001(dockergroup) groups=1001(dockergroup)
```

## Setting up the application
`IMPORTANT... THIS IS THE ARM64 VERSION`

Find the web interface at `<your-ip>:80` , set apps you wish to use with muximux via the webui.
More info:- [Muximux][muximuxurl]


## Info

* Shell access whilst the container is running: `docker exec -it muximux /bin/bash`
* To monitor the logs of the container in realtime: `docker logs -f muximux`

* container version number 

`docker inspect -f '{{ index .Config.Labels "build_version" }}' muximux`

* image version number

`docker inspect -f '{{ index .Config.Labels "build_version" }}' lsioarmhf/muximux-aarch64`

## Versions

+ **12.12.16:** Initial release.