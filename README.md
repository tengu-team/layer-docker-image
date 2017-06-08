# Docker-image

## What is it?

This charm wraps around a docker image. When connected via its dockerhost 
relation, the image will be deployed in the host environment. By default 
all exposed ports are opened.

## How to use

Deploy docker

    juju deploy cs:~tengu-team/docker-host

Deploy the docker-image charm

    juju deploy cs:~tengu-team/docker-image

Set which docker image needs to be deployed

    juju config docker-image image=ibcndevs/limeds

Add relation between the docker engine and the docker image

    juju add-relation docker-image docker

Check the deployment status (press <kbd>ctrl</kbd>-<kbd>c</kbd> to exit)

    watch -c juju status --color

# Contact Information

## Authors

This software was created in the [IDLab research group](https://www.ugent.be/ea/idlab) 
of [Ghent University](https://www.ugent.be) in Belgium. This software is used in 
[Tengu](https://tengu.io), a project that aims to make experimenting with data 
frameworks and tools as easy as possible.

 - Gregory Van Seghbroeck <gregory.vanseghbroeck@ugent.be>

