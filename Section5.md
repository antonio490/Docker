
# Section 5

## Docker networking

### Bridge

Default network a docker is attached to. It a private internal network created in the docker. The containers can access each other by this network.


### Host

The host network takes out any islation between the container and the host. Same ports are accesible on the host. We will not be able to run multiple containers on the same port since it will be occupied.

### Overlay network

We can create a new network overlay. This way we can communicate all of our containers in the overlay network we have created.

    $ docker network crate --dirver overlay --subnet 10.0.0.9/24 my-overlay-network
    
    $ docker service create --replicas 2 --network my-overlay-network nginx

### Ingress network

Once we create a docker swarm it automatically also creates an ingress network. This ingress network has a load balancer that redirects traffic into the right port. There is not configuration needed.

