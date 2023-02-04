# Basics of Kubernetes

Kubernetes (also known as K8s) is an open-source container orchestration system for automating the deployment, scaling, and management of containerized applications. It was originally developed by Google and is now maintained by the Cloud Native Computing Foundation (CNCF).

Kubernetes allows you to define how your applications should be deployed, including the number of replicas of each application, the resources required for each replica, and the network connections between components. It then automates the deployment, scaling, and management of these applications.

Kubernetes is designed to be highly scalable and can run on a large number of physical or virtual machines. It has a large and active community of users and developers and has become the de facto standard for container orchestration in the cloud.

Some key features of Kubernetes include:

* Self-healing: Kubernetes can automatically restart failed containers or replace them with new ones.
    
* Auto-scaling: Kubernetes can automatically scale the number of replicas of an application up or down based on demand.
    
* Load balancing: Kubernetes can automatically distribute incoming traffic across multiple replicas of an application.
    
* Service discovery: Kubernetes can automatically create DNS records for the different components of your application, making it easier for them to discover and communicate with each other.
    

## Components of a Kubernetes system

### Master

The Kubernetes Master is the central control plane of a Kubernetes cluster. It consists of a number of components that are responsible for managing the cluster and interacting with the nodes.

The main components of the Kubernetes Master include:

* **kube-apiserver**: The Kubernetes API server is the central way that other components interact with the Kubernetes cluster. It exposes a RESTful API that allows you to create, update, and delete various resources in the cluster, such as pods, services, and replication controllers.
    
* **etcd**: etcd is a distributed key-value store that is used to store the configuration data for the Kubernetes cluster. It is used by the API server to store and retrieve the state of the cluster.
    
* **kube-scheduler**: The Kubernetes scheduler is responsible for deciding which nodes in the cluster should run which pods. It takes into account factors such as the resource requirements of the pods, the resource usage of the nodes, and any constraints or affinity rules that have been specified.
    
* **kube-controller-manager**: The Kubernetes controller manager is responsible for running various controllers that handle tasks such as replicating pods, handling service discovery, and reacting to changes in the cluster.
    

The Kubernetes Master is typically run on one or more dedicated machines, and communicates with the nodes in the cluster through the Kubernetes API. It is responsible for enforcing the desired state of the cluster and reconciling any discrepancies that may arise.

The Kubernetes Master can be run in a highly available configuration to ensure that it is always available and able to respond to requests from the nodes. This is typically done by running multiple instances of the API server and etcd, and using a load balancer to distribute traffic between them.

### Pods

Each pod is assigned a unique IP address within the cluster, and can host one or more containers. The containers within a pod are meant to be tightly coupled and share resources such as networking and storage. For example, if you have a web server and a database that need to communicate with each other, you might put them in the same pod so that they can communicate over [localhost](http://localhost).

Pods are managed by the Kubernetes control plane, which ensures that the desired number of replicas of a pod are running at any given time. If a pod fails or is deleted, the control plane will create a new replica to replace it.

Pods are a useful abstraction because they allow you to treat a group of containers as a single entity when it comes to deployment and scaling. For example, you can create a deployment that manages a group of replicas of a pod, and use the deployment to perform a rolling update to the pod.

Pods are also useful for hosting stateful applications, such as databases. Because the pods are ephemeral, you can use them to store data on a persistent volume that is attached to the pod. When the pod is deleted and recreated, the data on the persistent volume will still be available.

### Nodes

Nodes are the worker machines in the cluster. They run the container runtime and the kubelet, which communicates with the Kubernetes master to receive instructions and report the status of the node and its containers. Each node runs a number of components, including:

* **kubelet**: The kubelet is the primary agent that runs on each node. It is responsible for ensuring that containers are running and healthy on the node. It communicates with the Kubernetes master to receive instructions and report the status of the node and its containers.
    
* **kube-proxy**: The Kubernetes proxy is a network proxy that runs on each node. It is responsible for routing traffic to the appropriate container within the cluster.
    
* **Container runtime**: A container runtime is responsible for actually running the containers on the node. Kubernetes supports a number of container runtimes, including Docker, rkt, and containerd.
    

Nodes are managed by the Kubernetes master, which is responsible for scheduling pods onto nodes and ensuring that the desired number of replicas of each pod are running at any given time.

When you create a Kubernetes cluster, you typically need to specify the number and type of nodes that you want to include in the cluster. You can then use the Kubernetes API or command-line tools to deploy your applications onto the nodes.

One of the key benefits of using Kubernetes is that it abstracts away the underlying infrastructure, so you can focus on deploying and managing your applications rather than the individual machines that they run on. This makes it easier to scale your applications up or down and deploy them onto different types of hardware or cloud environments.

Some common use cases for nodes in Kubernetes include:

* **Running stateless applications**: Nodes are well-suited for running stateless applications that do not store any data locally. Examples of stateless applications include web servers, API servers, and worker processes.
    
* **Running stateful applications**: Nodes can also be used to run stateful applications that store data locally, such as databases or message brokers. However, in this case, it is often necessary to use persistent volumes and other storage solutions to ensure that the data is retained even if the nodes fail or are rescheduled onto different machines.
    
* **Running batch jobs**: Nodes can be used to run batch jobs that have a defined start and end time, such as data processing or machine learning tasks. Kubernetes provides features such as job scheduling and resource limits that can be used to manage these types of workloads.
    
* **Running big data applications**: Nodes can be used to run big data applications that require a large number of machines to process and analyze data. Kubernetes provides features such as auto-scaling and resource quotas that can be used to manage these types of workloads.
    

### Volumes

In Kubernetes, a volume is a persistent storage component that can be mounted into a pod. Volumes are used to store data that needs to be persisted across the lifetime of a pod, even if the pod is deleted and recreated.

There are many types of volumes that you can use in Kubernetes, including:

* **EmptyDir**: An empty directory that is created when the pod is started, and deleted when the pod is removed. This is useful for storing temporary data that is not needed once the pod is terminated.
    
* **HostPath**: A directory on the node's file system that is mounted into the pod. This is useful for storing data that needs to be shared between pods on the same node.
    
* **GCEPersistentDisk**: A Google Compute Engine persistent disk that is mounted into the pod. This is useful for storing data that needs to be persisted across the lifetime of the pod, and can be used with Google Cloud Platform (GCP) clusters.
    
* **AWSElasticBlockStore**: An Amazon Web Services Elastic Block Store volume that is mounted into the pod. This is useful for storing data that needs to be persisted across the lifetime of the pod, and can be used with Amazon Elastic Container Service for Kubernetes (EKS) clusters.
    
* **NFS**: An NFS volume that is mounted into the pod. This is useful for storing data that needs to be shared between pods on multiple nodes.
    
* **ConfigMap**: A ConfigMap that is mounted into the pod as a volume or injected into the pod as environment variables. This is useful for storing configuration data that is not sensitive and does not contain binary data.
    

To use a volume in a pod, you first need to create the volume and then mount it into the pod. Here is an example of a pod configuration that mounts an empty directory as a volume:

```yaml
Copy codeapiVersion: v1
kind: Pod
metadata:
  name: my-pod
spec:
  containers:
  - name: my-container
    image: my-image
    volumeMounts:
    - name: data-volume
      mountPath: /var/data
  volumes:
  - name: data-volume
    emptyDir: {}
```

In this example, the volume is mounted into the `/var/data` directory of the container. The application can then read and write data to this directory, and the data will be persisted across the lifetime of the pod.

### Services

In Kubernetes, a Service is a logical abstraction that represents a group of pods that work together to provide a service. A Service exposes a stable, virtual IP address and DNS name, and can be used to load balance traffic to the pods it represents.

Services are useful for a number of reasons:

* They provide a stable endpoint for clients to access, even if the pods themselves are ephemeral and may come and go.
    
* They can be used to load balance traffic across a group of replicas of a pod, improving the availability and scalability of the service.
    
* They can be used to expose internal services to other components within the cluster, or to external clients.
    

There are several types of Services in Kubernetes, each with different characteristics and use cases:

* **ClusterIP**: A ClusterIP Service is the default type of Service. It exposes the Service within the cluster, and is not accessible from outside the cluster.
    
* **NodePort**: A NodePort Service exposes the Service on a specific port of each node in the cluster. It allows external clients to access the Service by connecting to the IP address of the node and the specified port.
    
* **LoadBalancer**: A LoadBalancer Service is similar to a NodePort Service, but it also creates a load balancer in the cloud provider's infrastructure that distributes incoming traffic to the nodes in the cluster.
    
* **ExternalName**: An ExternalName Service is used to map a Service to an external DNS name. This can be useful for accessing external services, or for exposing services in one cluster to another cluster.
    

Here is an example of how you might define a Service in a YAML configuration file:

```yaml
Copy codeapiVersion: v1
kind: Service
metadata:
  name: my-service
spec:
  selector:
    app: my-app
  ports:
  - protocol: TCP
    port: 80
    targetPort: 8080
  type: ClusterIP
```

In this example, the Service is of type `ClusterIP`, and it exposes a TCP port on port 80 that maps to the `8080` port of the pods that are selected by the `app=my-app` label. The `spec.selector` field is used to specify the pods that the Service should route traffic to.

### Deployment

In Kubernetes, a deployment is a resource that manages the rollout and rollback of a set of replicas of a pod. A deployment ensures that a specified number of replicas of a pod are running at any given time, and can be used to perform rolling updates to the pods.

Here is a simple example of deployment in Kubernetes:

```yaml
Copy codeapiVersion: apps/v1
kind: Deployment
metadata:
  name: my-deployment
spec:
  replicas: 3
  selector:
    matchLabels:
      app: my-app
  template:
    metadata:
      labels:
        app: my-app
    spec:
      containers:
      - name: my-container
        image: my-image:latest
        ports:
        - containerPort: 80
```

In this example, the deployment manages a set of three replicas of a pod that runs a container with the `my-image` image. The deployment uses a label selector to identify the pods that it manages, and specifies the container image and port that the pod should run.

To create the deployment, you can use the `kubectl apply` command:

```plaintext
Copy codekubectl apply -f my-deployment.yaml
```

This will create the deployment in your Kubernetes cluster. You can then use the `kubectl rollout` command to perform rolling updates to the deployment. For example, to update the deployment to use a new version of the container image, you can run:

```plaintext
Copy codekubectl set image deployment/my-deployment my-container=my-image:new-version
```

This will update the deployment to use the `new-version` of the `my-image` container image. Kubernetes will then perform a rolling update to the deployment, replacing the old replicas with new ones that use the updated image.