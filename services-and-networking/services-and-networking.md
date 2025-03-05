### Services-and-Networking
#### Network Policies
- Non-isolated Pods - If pod is not using any of the network policies, it will serve all traffic coming or going out of it. Such pod is non-isolated.
- Isolated Pods - If pod is selected by any of the policies, it is isolated. Means, traffic will be filtered our based on netwrok policies attached to it.

- To label a namespace; `kubectl label namespace namespace-a team=ateam`
- The scenerio is if we create a server pod in namespace-a and client pod in namespace-b, client can request server pod through server's ip address. Here, comes the art of Network policies.
