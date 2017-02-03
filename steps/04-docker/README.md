# docker


```

alias d='sudo docker'

# information about docker

d info


# run container test-1 with ubuntu

d run --name=test-1 -i -t ubuntu /bin/bash

> hostname
> cat /etc/hosts
> ip a
> # rm -rf /
> # detach from container
> ctrl-p ctrl-q


# list all running containers
d ps 

# list all containers
d ps -a

# https://docs.docker.com/engine/reference/commandline/ps/

# attach to container
d attach test-1

# stop container
d stop test-1

# start container
d start test-1


# remove container
d rm test-1


# run detached container
d run --name=noisy -d ubuntu /bin/bash -c 'while true; do date; sleep 5; done'

# see container logs
d logs noisy

d logs -f noisy

# see processes in container
d top noisy

# container attributes (metadata)
d inspect noisy

# get specific attribute
d inspect  -f '{{.NetworkSettings.IPAddress}}' noisy

d stop noisy

# run container with node
# docker registry
d run --rm -i -t node:5 /bin/bash


# search images
d search node

# download images
d pull node

# list images
d images node
d images ubuntu

d images

# tree view for images
d run --rm -v /var/run/docker.sock:/var/run/docker.sock nate/dockviz images -t

# Dockerfile

d build -t=myapp .
d images myapp
d run --rm myapp node /index.js

# how container was built
d history myapp

# work with ports
d run --name nginx -p 80 -d nginx

d ps | grep nginx
d port nginx 80

curl 127.0.0.1:<port>

curl $(d inspect -f '{{.NetworkSettings.IPAddress}}' nginx)


# postgresql container and links
d run --name pg -e POSTGRES_PASSWORD=mysecretpassword -d postgres
d run --rm --link pg:db -it ubuntu /bin/bash 

# how links work
> cat /etc/hosts
> env | grep DB

d run --rm --link pg:postgres -it postgres  sh -c 'exec psql -h "$POSTGRES_PORT_5432_TCP_ADDR" -p "$POSTGRES_PORT_5432_TCP_PORT" -U postgres'

# volumes
d run --rm  --volumes-from pg -it ubuntu /bin/bash

```
