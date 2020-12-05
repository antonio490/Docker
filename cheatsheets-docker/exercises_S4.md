
### Exercises Docker services Section 4

    $ docker service create --name vote voting-app

    $ docker service create --replicas 3 --name vote voting-app

    $ docker service create --replicas 3 --name vote -p 8080:80 voting-app

    $ docker service create --replicas 3 --name vote -p 8080:80 --network front-end voting-app

    $ docker service update --replicas=6 vote
