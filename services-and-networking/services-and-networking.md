### Services-and-Networking
#### Network Policies
- Non-isolated Pods - If pod is not using any of the network policies, it will serve all traffic coming or going out of it. Such pod is non-isolated.
- Isolated Pods - If pod is selected by any of the policies, it is isolated. Means, traffic will be filtered out based on network policies attached to it.

- To label a namespace; `kubectl label namespace namespace-a team=ateam`
- The scenerio is if we create a server pod in namespace-a and client pod in namespace-b, client can request server pod through server's ip address. Here, comes the art of Network policies.

#### Services
- Service allows us to expose an application running across multiple pods. Clients use the Service and traffic will automatically routed to one of the pods.
- Two types of Services;
    - ClusterIP -  Exposes the application within the cluster network.
    - NodePort - Exposes the application externally by listening on an external port on each cluster node.
    ![alt text](image.png)
    - To verify nodeport service, `curl http://<worker_node_ip>:<node_port>`

#### Ingress
- An Ingress manages external access to Kubernetes applications. It routes the traffic to one or more kubernetes services
- An ingress controller is required to implement ingress functionality.
- Ingress object is created in the namespace where service exposing application is running.
