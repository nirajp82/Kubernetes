## Kubernetes: Architecture.

**Nodes in Kubernetes:**

**Node**: In Kubernetes, a node is a physical or virtual machine where the Kubernetes system is installed and runs your applications. Each node typically hosts multiple containers that together form your application stack. Nodes are the basic units of the Kubernetes cluster where your applications are deployed and run.

**Cluster**: A Kubernetes cluster is a collection of nodes that work together as a single entity. It consists of one or more master nodes and multiple worker nodes.

**Master Node**: The master node is the control plane of the Kubernetes cluster. It manages the cluster's overall state, scheduling, and orchestration of application workloads. The master node includes several components such as the Kubernetes API server, scheduler, controller manager, and etcd (a distributed key-value store for storing cluster data).

**Worker Node**: Also known as a minion node, the worker node is where your application containers are deployed and executed. Each worker node runs a container runtime (such as Docker or containerd) and a Kubernetes agent called kubelet, which communicates with the master node.

**Components of Kubernetes:**

When Kubernetes is installed, it includes several key components distributed across the master and worker nodes:

1. **API Server and etcd**: The API server serves as the front end for Kubernetes  that exposes the Kubernetes API. It handles requests from various Kubernetes components, users, and external clients. The API server validates and processes requests, then updates the corresponding objects in the cluster's etcd database.

2. **Kubelet**: Kubelet is an agent that runs on each node in the cluster. It ensures that containers are running as expected on the nodes and communicates with the master node.

3. **Container Runtime**: The container runtime is the underlying software responsible for running containers. Docker is a commonly used container runtime in Kubernetes, although alternatives like Rocket or Cryo exist.

4. **Controllers and Schedulers**: Controllers are responsible for making decisions to maintain the desired state of the cluster. They respond to changes in nodes, containers, or endpoints by initiating actions such as bringing up new containers. Schedulers distribute work or containers across multiple nodes by assigning them to appropriate nodes.
   
5. **etcd**: etcd is a distributed key-value store that serves as the cluster's persistent storage. It stores desired state of the cluster configuration, configuration data, state information, and metadata about the cluster's objects. The Kubernetes master components read from and write to etcd to maintain the cluster's state.

**Distribution of Components:**

The master node hosts components such as the API server, etcd service, control manager, and scheduler. These components work together to manage the cluster and orchestrate container deployments.

On the other hand, the worker nodes host containers and include components like the kubelet agent, container runtime, and necessary supporting services. The kubelet agent interacts with the master node to provide health information and execute actions requested by the master on the worker nodes.

**kubectl Command Line Utility:**

The `kubectl` command line tool is used to interact with and manage Kubernetes clusters. It allows users to deploy and manage applications, retrieve cluster information, monitor node statuses, and execute various administrative tasks.

- `kubectl run`: Deploy an application on the cluster.
- `kubectl cluster info`: View information about the cluster.
- `kubectl get nodes`: List all nodes in the cluster.

Understanding these components and commands is crucial for setting up and managing Kubernetes clusters effectively. As you delve deeper into Kubernetes, you'll encounter additional commands and concepts that further enhance your understanding and proficiency in managing containerized applications.
