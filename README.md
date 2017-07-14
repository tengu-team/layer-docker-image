# Docker-image

## What is it?

This charm wraps around a docker image. When connected via its dockerhost 
relation, the image will be deployed in the host environment. By default 
all exposed ports are opened.

## How to use

Add the layer to `layer.yaml`

    includes: ['layer:docker-image']

In your reactive file, set the state `docker-image.start` when the docker container is ready to start.
This state can be used if the docker container needs environment variables for configuration. The charm's key-value store is used to pass this information to the docker-image layer. The key is `docker-image-env` and the value should be a dictionary.
An example which adds mongodb connection info is:
```
@when('mongodb.available')
def mongodb_connected(mongodb):
    unitdata.kv().set('docker-image-env', 
                      {'mongodb': mongodb.connection_string()})
    set_state('docker-image.start')
```
    
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


