## Kubernetes: Architecture.

**Nodes in Kubernetes:**

A node in Kubernetes is a machine, whether physical or virtual, where the Kubernetes system is installed. Nodes are also known as worker machines, as they execute the actual workloads of running containers managed by Kubernetes. Previously, nodes were referred to as minions. The terms "node" and "minion" are often used interchangeably.

However, relying on a single node poses a risk—if the node fails, the applications running on it go down as well. To ensure high availability and fault tolerance, Kubernetes organizes nodes into clusters. A cluster is a set of nodes grouped together, allowing applications to remain accessible even if one node fails. Additionally, having multiple nodes facilitates load sharing across the cluster.

**Master Node:**

The master node is another node in the Kubernetes cluster that hosts the control plane components responsible for managing and orchestrating the cluster's resources. It oversees the nodes in the cluster and orchestrates container deployments on worker nodes.

**Components of Kubernetes:**

When Kubernetes is installed, it includes several key components distributed across the master and worker nodes:

1. **API Server and etcd**: The API server serves as the front end for Kubernetes, handling communication with users, management devices, and command-line interfaces. Etcd is a distributed key-value store used by Kubernetes to store all data related to managing the cluster.

2. **Kubelet**: Kubelet is an agent that runs on each node in the cluster. It ensures that containers are running as expected on the nodes and communicates with the master node.

3. **Container Runtime**: The container runtime is the underlying software responsible for running containers. Docker is a commonly used container runtime in Kubernetes, although alternatives like Rocket or Cryo exist.

4. **Controllers and Schedulers**: Controllers are responsible for making decisions to maintain the desired state of the cluster. They respond to changes in nodes, containers, or endpoints by initiating actions such as bringing up new containers. Schedulers distribute work or containers across multiple nodes by assigning them to appropriate nodes.

**Distribution of Components:**

The master node hosts components such as the API server, etcd service, control manager, and scheduler. These components work together to manage the cluster and orchestrate container deployments.

On the other hand, the worker nodes host containers and include components like the kubelet agent, container runtime, and necessary supporting services. The kubelet agent interacts with the master node to provide health information and execute actions requested by the master on the worker nodes.

**kubectl Command Line Utility:**

The `kubectl` command line tool is used to interact with and manage Kubernetes clusters. It allows users to deploy and manage applications, retrieve cluster information, monitor node statuses, and execute various administrative tasks.

- `kubectl run`: Deploy an application on the cluster.
- `kubectl cluster info`: View information about the cluster.
- `kubectl get nodes`: List all nodes in the cluster.

Understanding these components and commands is crucial for setting up and managing Kubernetes clusters effectively. As you delve deeper into Kubernetes, you'll encounter additional commands and concepts that further enhance your understanding and proficiency in managing containerized applications.
