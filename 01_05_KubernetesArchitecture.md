## Kubernetes: Architecture.

**Nodes: The Foundation for Workloads**

* **Definition:** A node, physical or virtual, serves as the **worker machine** in a Kubernetes cluster. It's where containerized applications are **launched and executed**. These were previously called **minions**.
* **Importance of Multiple Nodes:** While a single node can run containers, it creates a single point of failure. If that node fails, the application goes down. To ensure **availability and redundancy**, a **cluster** is formed by **grouping multiple nodes together**. This way, even if one node fails, the application remains accessible from the others. Additionally, multiple nodes allow for **load sharing**, distributing the workload across available resources for better performance.

**The Master: Orchestrating the Cluster**

* **Function:** The **master**, a designated node with Kubernetes installed, acts as the **central control unit** for the cluster. It's responsible for **orchestrating** the entire container lifecycle on worker nodes.
* **Information Management:** The master leverages several components to manage the cluster:
    * **API Server:** The **frontend** for Kubernetes, accepting requests from users, management tools, and command-line interfaces to interact with the cluster.
    * **etcd:** A distributed **key-value store** that **stores all cluster data** in a **reliable and consistent** manner, even across multiple master nodes. It also implements **locks** to prevent conflicts between masters.
    * **Scheduler:** Analyzes and assigns **newly created containers** to appropriate nodes based on resource availability and other factors.
    * **Controllers:** The **brains** behind orchestration, continuously monitoring the cluster for issues. They **react and take corrective actions** when nodes, containers, or endpoints encounter problems, such as bringing up new containers to replace failed ones.
    * **Container Runtime:** The underlying software, like **Docker**, responsible for **running containers** on the nodes.

**Kubelet: The Agent on Each Node**

* **Function:** Each node in the cluster runs a **kubelet agent**, acting as the **local agent** for the master. It ensures that containers are **running as expected** on its node.
* **Responsibilities:**
    * **Communication:** Communicates with the master to provide **health information** about the node and **executes actions** requested by the master.
    * **Container Management:** Manages the lifecycle of containers on the node, ensuring they are **started, stopped, and restarted** as needed.

**Deployment of Components: Master vs. Worker**

* **Worker Nodes:**
    * Host **containerized applications** (e.g., Docker containers).
    * Require a **container runtime** like Docker or alternatives like Rocket or Cryo.
    * Run the **kubelet agent** to interact with the master.
* **Master Node:**
    * Distinguished by the presence of the **kube-API server**.
    * Stores cluster information in an **etcd key-value store**.
    * Runs the **scheduler, controller manager, and other components**.

**Kubectl: The Command-Line Tool**

* **Function:** `kubectl`, also known as `kube control`, is a **command-line tool** used to **deploy and manage applications** on a Kubernetes cluster.
* **Common Commands:**
    * `kubectl run`: Deploys an application on the cluster.
    * `kubectl cluster info`: Displays information about the cluster.
    * `kubectl get nodes`: Lists all nodes in the cluster.

This detailed explanation equips you with a solid understanding of the fundamental components of Kubernetes and their roles in managing containerized applications. With this knowledge, you can effectively navigate the setup, configuration, and management of your own Kubernetes infrastructure.
