# Andocker device image development Dockerfile

## Usage
To build device docker image, we need _/var/run/docker.sock_ being mounted into container. To setup permissions correctly, there are several docker build arguments available. By default, it creates a normal user _andocker_ with uid _1000_. Gid for host docker daemon is also required, which cannot have a default value because it varies with per system setup. So,

* To build: `docker build -t andocker/devel:stretch --build-arg GROUP_DOCKER_GID=$(cat /etc/group | grep ^docker | cut -d: -f3) .`
* To run: `docker run --tty --interactive --volume /home:/home --volume /var/run/docker.sock:/var/run/docker.sock andocker/devel:stretch /bin/bash`

Then you may begin checking out source & build device images inside.
