# Section 7

## Docker on Cloud

On docker Swarm the cluster is manage by a Swarm manager. The same is true with Kubernetes. However unlike Swarm, Kubernetes does not run containers by itself, they have to be encaptulate by a unit called pods.

- Pods contain containers.
- Kube Worker contain Pods.
- A Pod can have multiple containers.
- We can deploy inside a Pod two containers sharing the same IP address and the same storage volume.

- Instead of Links the communciation is enable with services (Internal for cluster communication and External with a load balancer for outside communication).


    $ kubectl create -f pod-definition.yml

    $ kubectl get pods

    $ kubectl describe pods


    #pod-definition.yml

    apiVersion: v1

    kind: pod

    metadata:
        name: my-nginx

    spec:

        containers:
            -name: nginx
             image: nginx
             ports:
                - containerPort: 80


    $ kubectl create -f pod-definition.yml

    Steps:

        1. Deploy PODs
        2. Create Services (ClusterIP)
        3. Create Services (LoadBalancer)