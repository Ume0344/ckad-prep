### application-environment-configuration-security

#### Custom Resource Definitions (CRDs)
An extension to Kubernetes API. These are defined through CRDs and controlled through custom controllers.

#### Service Accounts
- A service account allow processes within the containers to authenticate with kubernetes API server. So, if any process within a container wants to interact with k8s api server (performing any action on k8s cluster), they can use service accounts.
- Service accounts work with RBAC (Role Based Access control) to define the permissions.
- Every pod by default gets a `default` service account.

#### Kubernetes Auth
Kubernetes have two kinds of users to be authenticated or authorized.
- Users
- Service Accounts

![Alt text](users-vs-service-accounts.png)

#### RBAC 
It is a system for managing authorization. This allows us to define what users are allowed to do within the k8s cluster.
- Role - To define the permissions [verbs (list, get) and resources (pods, services)]. It is namespaced. We can create cluster roles which will be cluster-scoped
- Role Binding - This object binds a service account, user or group to a role.

#### Admission Controller 
Admission controller checks the requests coming to API server after authentication/authorization but before perssiting the request to datastore (etcd). 
We can have multiple admission controllers turned on for our cluster by updating pod manifest of API server at `/etc/kubernetes/manifests/kube-apiserver.yaml` at
the flag  `--enable-admission-plugins`.
Forexample, `NamespaceAutoProvision` is an admission controller to create namespaces used by resources if namespace is not present.

#### ConfigMaps and Secrets
- ConfigMaps and secrets can be configured to pods as volumeMounts or environment variables. ()

#### Security Context
- We can define security context at pod level as well as container level.
- A container's SecurityContext allows us to control advanced security-related settings for the container.
- We can set the container's user ID (UID) and group ID (GID) with `securitContext.runAsUser` and `securityContext.runAsGroup`.
- Enable or disable privilege escalation with `securityContext.allowPrivilegeEscalation`.
- Make the container root filesystem read-only with `securityContext.readOnlyRootFilesystem`. If we try to write to any file inside container, it will fail as filesystem is read-only. i.e, `kubectl exec securitycontext-pod -- sh -c "echo hi > test.txt"` will throw error; `sh: can't create test.txt: Read-only file system`
