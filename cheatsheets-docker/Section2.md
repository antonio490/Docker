
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

    $ git clone https://github.com/dockersamples/example-voting-app.git

    $ docker build . -t voting-app

    $ docker run -d --name=redis redis

    $ docker run -d -p 5000:80 --link redis:redis voting-app

Now we have python web application with a redis database. Lets continue with the rest of containers.

    $ docker run --name db -e POSTGRES_PASSWORD=password -h db -d postgres:9.4

Deploy the worker
    
    $ docker build . -t worker-app 

    $ docker run --link redis:redis --link db:db -h db -u root worker-app //.NET

Last container the result-app

    $ docker build . -t result-app

    $ docker run -d -p 5001:80 --link db:db result-app // Node.js

We are going to do the same thing but using docker-compose.yml which is basically a script that automates the process.

    $ docker-compose up
