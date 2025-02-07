### application-observerability-and-maintenance

#### API Deprecation Policy
- Deprecation - A process of providing advance warnings to the user of API regarding any changes in the API. This allow user to update their code 
 according to leatest API chnages.
- Important concept regarding deprecation policy;
    - apiVersion:  indicates which version of API is compatible with the object.
    - Deprecation window: Indicates how much time developers have to update their code according to latest API changes. Usually it is 12 months or 3 releases.
    - [Deprecated API migration guide](https://kubernetes.io/docs/reference/using-api/deprecation-guide/): Document on how can we migrate from deprecated API.

### Implementing Probes and Healthchecks
#### Probes
- Part of container specs which allow the user to customize how k8s detect the state of containers.
- [Examples of Liveness, readiness, startup probes](https://github.com/Ume0344/kubernetes-probes?tab=readme-ov-file)

#### Monitoring Kubernetes Applications
- Metrics API in kubernetes provide the basic data about application, pods or nodes. To get this data from Metrics API, 
we need to install Metrics Server to our cluster.
```
kubectl apply -f https://raw.githubusercontent.com/ACloudGuru-Resources/content-cka-resources/master/metrics-server-components.yaml
```
- Once it is installed, we can use kubernetes `top` command, to get metrics data;
```
kubectl top pods/nodes
```

#### Accessing container logs
- Kubernetes stores stdout/stderr console output of each container to container log.
```
kubectl logs <pod-name> -c <container-name>
```

#### Debugging in Kubernetes
- Check object status; `kubectl get`
- Check object configuration; `kubectl describe`
- Check logs; `kubectl logs`

```
kubectl get pods --all-namespaces
kubectl get pod <pod> -o yaml
```
**Cluster-Level logs**
- API server logs are present at `/var/log/containers/`.
- `kubelet` logs can be found using `journalctl` as `kubelet` runs a a service.
```
sudo journalctl -u kubelet
```
