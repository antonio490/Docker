# Section 4

## Docker Service

First we learn how to run an application o a docker host using:

    $ docker run my-web-server

Then we have learned how to monitorized a cluster with docker Swarm. Docker service is the key of docker orchestration. This we can automate the process running multiple nodes .

    $ docker service create --replicas=3 --name web-server //MANAGER NODE

        - web-server1
        - web-server2
        - web-server3

We have just runned 3 instances of my-web-server on a cluster.

### Global services 

- One instances but on every node

    $ docker service create --mode global my-monitor-agent

### Service update

Add a new instance of a service.

    $ docker service update --replicas=4 web-server


### DEMO

    $ docker service create nginx //MASTER

    $ docker service ls // List services

    $ docker service ps  // List the task of one or more services

    $ docker service update >CONTAINER ID> --publish-add 5000:80 //MASTER

    $ docker service create --replicas 2 --name nginx nginx

    $ docker node update --availability drain docker-master // Disable availability of master node to be a nginx worker. 

