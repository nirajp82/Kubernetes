## Kubernetes: Architecture.

**Nodes in Kubernetes:**

**Node**: In Kubernetes, a node is a physical or virtual machine where the Kubernetes system is installed and runs your applications. Each node typically hosts multiple containers that together form your application stack. Nodes are the basic units of the Kubernetes cluster where your applications are deployed and run.

**Cluster**: A Kubernetes cluster is a collection of nodes that work together as a single entity. It consists of one or more master nodes and multiple worker nodes.

**Master Node**: The master node is the control plane of the Kubernetes cluster. It manages the cluster's overall state, scheduling, and orchestration of application workloads. The master node includes several components such as the Kubernetes API server, scheduler, controller manager, and etcd (a distributed key-value store for storing cluster data).

**Worker Node**: Also known as a minion node, the worker node is where your application containers are deployed and executed. Each worker node runs a container runtime (such as Docker or containerd) and a Kubernetes agent called kubelet, which communicates with the master node.

**Components of Kubernetes:**

When Kubernetes is installed, it includes several key components distributed across the master and worker nodes:

1. **API Server and etcd**: The API server serves as the front end for Kubernetes  that exposes the Kubernetes API. It handles requests from various Kubernetes components, users, and external clients. The API server validates and processes requests, then updates the corresponding objects in the cluster's etcd database.

2. **Kubelet**: Kubelet is an agent that runs on each node in the cluster. It ensures that containers are running as expected on the nodes and communicates with the master node. It receives pod specifications from the API server, ensures that the containers described in the pod specifications are running and healthy, and reports the node's status back to the master.

3. **Container Runtime**: The container runtime is the underlying software responsible for running containers. Docker is a commonly used container runtime in Kubernetes, although alternatives like Rocket or Cryo exist.
   
4. **Controller Manager**: The controller manager runs various controllers that regulate the state of the cluster. Controllers continuously monitor the cluster's desired state, compare it with the actual state, and take corrective actions to ensure that the desired state is maintained. Examples of controllers include the Replication Controller, ReplicaSet Controller, and Deployment Controller.

5. **Controllers**: Controllers are responsible for making decisions to maintain the desired state of the cluster. They respond to changes in nodes, containers, or endpoints by initiating actions such as bringing up new containers.
  
6. **Schedulers**: distribute work or containers across multiple nodes by assigning them to appropriate nodes. The scheduler is responsible for assigning pods (a group of one or more containers) to nodes in the cluster based on resource requirements, node capacity, and other constraints. It ensures that workloads are spread evenly across the cluster.
   
7. **etcd**: etcd is a distributed key-value store that serves as the cluster's persistent storage. It stores desired state of the cluster configuration, configuration data, state information, and metadata about the cluster's objects. The Kubernetes master components read from and write to etcd to maintain the cluster's state.

8. **Pods**: The fundamental unit of deployment in Kubernetes, representing a group of one or more containers that share storage and network resources.
   
9. **kube-proxy**: Manages network traffic for pods within the cluster, implementing service discovery and load balancing. 

**Example:**

1. You deploy a web application as a deployment object in Kubernetes. This information is sent to the kube-apiserver.

2. The kube-apiserver stores the deployment details in etcd and informs the kube-controller-manager.

3. The kube-controller-manager creates a corresponding replica set to manage the desired number of pods for the application.

4. The kube-scheduler identifies suitable nodes based on resource availability and pod requirements.

5. The kube-scheduler instructs the kubelet on each node to create and run the pod, which in turn utilizes the container runtime to launch the application containers.

6. The kube-proxy automatically configures networking for the pods, enabling communication and access to the application.

This simplified example demonstrates how different components collaborate to manage and run containerized applications within a Kubernetes cluster.

**Distribution of Components:**

The master node hosts components such as the API server, etcd service, control manager, and scheduler. These components work together to manage the cluster and orchestrate container deployments.

On the other hand, the worker nodes host containers and include components like the kubelet agent, container runtime, and necessary supporting services. The kubelet agent interacts with the master node to provide health information and execute actions requested by the master on the worker nodes.

**kubectl Command Line Utility:**

The `kubectl` command line tool is used to interact with and manage Kubernetes clusters. It allows users to deploy and manage applications, retrieve cluster information, monitor node statuses, and execute various administrative tasks.

- `kubectl run`: Deploy an application on the cluster.
- `kubectl cluster info`: View information about the cluster.
- `kubectl get nodes`: List all nodes in the cluster.

Understanding these components and commands is crucial for setting up and managing Kubernetes clusters effectively. As you delve deeper into Kubernetes, you'll encounter additional commands and concepts that further enhance your understanding and proficiency in managing containerized applications.
