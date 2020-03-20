# Section 3 

## Docker Swarm

Docker Swarm takes care of redistribution of docker host to maintain disponibility. 
It is useful in production environments.


Manager

- Master node where cluster is initiated.
- Responsible for maintaining cluster state.
- Adding/Removing workers.
- There is usually multiple manager nodes to prevent failure.


Let's create a cluster with two nodes:

    $ docker swarm join-token-worker //MASTER

    $ docker swarm init //MASTER

    $ docker swarm join --token xxxx ip:2377 //NODE

    $ docker node -ls // MASTER

Let's do the same but with two masters:

    $ docker swarm join-token-manager //MASTER

    $ docker swarm join --token xxxx ip:2377 //MASTER_2

    $ docker swarm join --token xxxx ip:2377 //NODE

    $ docker node promote $NODE //MASTER 