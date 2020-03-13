
# Section 2 

## Docker Compose

 Lets imagine we want to develop a voting application with the following services:

 - voting-app : python
 - in-memory DB: Redis
 - worker: .NET
 - db: postgreSQL
 - result-app: NodeJS

We see there are multiple services and diverse applications. We can put together all of this inside a docker container.

    $ docker run -d --name=redis redis

    $ docker run -d --name=db postgres:9.4

    $ docker run -d --name=vote -p 5000:80 --lin redis:redis voting-app

    $ docker run -d --name=result -p 5000:80 --link db:db result-app

    $ docker run -d --name=worker --link db:db --link redis:redis worker

* We also need to indicate links between docker machines.

Now we put all this together into docker-compose.yaml
There are multiple versionss of docker-compose. We have used version 1.

In version one we dont need to use links since all machines are in the same network.
