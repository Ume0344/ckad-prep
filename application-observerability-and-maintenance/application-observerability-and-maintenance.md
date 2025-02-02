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
