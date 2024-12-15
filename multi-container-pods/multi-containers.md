**Building Multi-container Pods**

In this concept, two or more than 2 containers run on same pod. When containers are tightly coupled, they will be sharing same resources like network or storage etc.

Three types of design pattern when it comes to multi-container pods;

- **Sidecar containers** - A container that assist the main container. eg; main container writes some files in shared volume and sidecar container logs them out. Shares storage resources.
- **Ambassador containers** - Proxies network traffic from/to main container. Shares network resources.
- **Adaptor containers** - To re-format the data received from the main container. Like cleaning the data coming out of the nats-mq bridge container.
