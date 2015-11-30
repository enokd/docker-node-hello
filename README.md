# Node.js Hello World

Node.js Hello World on CentOS using [docker][].

## Prerequisites

- [Node.js & npm][node-js-download]

## Getting Started

-   Start Ubuntu virtual machine using Vagrant (required to run docker):

        vagrant up

-   SSH into virtual machine:

        vagrant ssh

-   Install dependencies:

        cd /vagrant
        make install

-   Build docker image:

        make build
        # docker build -t gasi/centos-node-hello .


-   Run app:

        make run-container
        # docker run -p 49160:8080 -d gasi/centos-node-hello

-   Install `curl`:

        sudo apt-get install curl

-   Get mapped port (last column) using, e.g. 49160:

        docker ps

        > # Example
        > ID                  IMAGE                           COMMAND              CREATED             STATUS              PORTS
        > ecce33b30ebf        gasi/centos-node-hello:latest   node /src/index.js   10 seconds ago      Up 9 seconds        49160->8080

-   Test app using the port in previous step, e.g. 49160:

        curl localhost:<port>

        # Example
        # curl localhost:49163

    It should print `Hello World` to the console.
    
    If you use Docker on OS X, the port is actually mapped to the Docker host VM, and you should use the following command:
    
        curl `docker-machine $DOCKER_MACHINE_NAME ip`:<port>

## Acknowledgements

Many thanks to @shykes and @unclejack for their support on IRC as well as the
@dotCloud team for docker.


[node-js-download]: http://nodejs.org/download/
[docker]: http://docker.io
