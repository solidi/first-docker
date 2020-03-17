# Learning Docker

## General

1. Makes scripting distributed systems easy.
1. Written in Go.
1. Uses "cgroups" to contain processes.
1. Uses "namespaces" to contain networks.
1. Uses "copy-on-write" file systems to build images.
1. COWs - layers are the power of docker file system.
1. Processes start with "init".
1. Boot2Docker is an old version of docker desktop.
1. host.docker.internal refers to localhost.
1. Full name structure is registry.example.com:port/organization/image-name:version-tag
1. ```docker run``` automatically runs ```docker pull```
1. Volumes "disks" share files. Persistent and ephemeral.

## Commands

```shell
docker images
docker run -ti <image> --name <name> --net <network> --link <name> bash
docker run -ti --restart centos -v <external:internal> bash
docker run -ti centos --volumes-from <ps name> bash
docker run -p (publish) internal:external/(udp)
docker ps -a or -l
# control D to exit.
docker commit <hash> <tag name>:<tagname>
docker tag <sha> <tag name>
docker run --rm
docker run -d
docker attach (ctrl q + ctrl p)
docker logs <container name>
docker kill <container name>
docker port <image tag>
docker network create <name>
docker rmi <image-id>
docker search
docker inspect --format '{{.State.Pid}}' <image name>
docker run -ti --rm --privileged=true --pid=host ubuntu bash
docker save
docker load
```

## Dockerfiles

1. Place highly changing items at the end of the file.
1. Each line is effectively a docker run and commit command.
1. ADD can uncompressed tars, and downloads urls.
1. Forms - shell -> nano notes.txt vs exec ["/bin/nano", "notes.txt"]

## Avoid Golden Build

1. Include installers in your project
1. Have a canonical build that builds everything completely from scratch.
1. Tag your builds with the git hash of the code that built it.
1. Use small base images, such as Alpine.
1. Build images you share publicly from Dockerfiles, always.

## Multistage Builds

1. Small vs complete solution.

## Links

1. [Dockerfile reference](https://docs.docker.com/engine/reference/builder)
