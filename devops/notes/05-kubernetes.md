# Kubernetes

Kubernetes is an open source project from Google

## Structure

-   Control Plane
    -   api
    -   scheduler
    -   ...
-   Node
    -   objects
    -   kubelet
    -   k-proxy

### Control Plane

The Control Plane is the brain of the Kubernetes cluster.

-   Manages all nodes
-   Solves container issues with self-healing concepts
-   Publishes new nodes
-   Ensures containers are running

#### api

The api provides services for the Nodes, which send events to the api

#### scheduler

The scheduler ???

### Node

The Node is a physical or virtual machine, it's the place where the applications will run as containers  
In AWS, it's normally an EC2 machine

It sends events to the Control Plane api

It has objects

#### Objects

-   pod: the place where the containers will run
-   replicaset: controls pod instances
-   deploy: contains configurations like: available resources for each pod, number of pod instances, etc
-   horizontal pod autoscaler
    -   Creates and kills pod replicas according to the application workload
    -   You can configure the limit of replicas to respect the limits of the Node hardware
-   vertical pod autoscaler: controls the resources by pod
-   service: manages network interfaces

#### kubelet

#### k-proxy

Network Layer of the Node

It's not common to run database services in Kubernetes because it introduces a lot of complexity and, there are other services specifically designed for this task.

## K3D

K3d is a CLI used to create Kubernetes Clusters

Create a cluster  
`k3d cluster create CLUSTER_NAME --servers NUMBER_OF_NODES`

## Kubectl

Kubectl is a CLI to communicate with the Kubernetes Cluster

Show help menu  
`kubectl`

Get the nodes of the created Cluster in default namespace  
`kubectl get nodes`

Get the pods of the created Cluster in a custom namespace  
`kubectl get pods -n NAMESPACE`

Get existing namespaces  
`kubectl get ns`

Create a namespace  
`kubectl create ns NAMESPACE`

