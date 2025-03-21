### Expose an Application with a NodePort Service

There is a Deployment called `willow` in the `buffy` Namespace.

Expose this Deployment on port `8082` and target port `80` using a NodePort-type Service called `willow-svc`.


### Provide Network Access between Pods via a NetworkPolicy

There are several Pods in the `giles` Namespace. The `xander` Pod needs to be able to reach out to both `api-1` and `api-2`, but it currently cannot do so due to the NetworkPolicy setup.

Without creating, changing, or removing any existing NetworkPolicies, provide the `xander` Pod with access to `api-1` and `api-2`, but not any other Pods in the Namespace. You should be able to do this by only making changes to the `xander` Pod and no other objects.
*Solution*: `k label pod xander -n giles api-2-access=true api-1-access=true` 