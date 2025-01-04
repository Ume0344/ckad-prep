**Application Deployment**

#### Scaling
To scale deployments, we have multiple options;
- Change the number of replicas by editing the deployment.
```
apiVersion: apps/v1
kind: Deployment
metadata:
  name: nginx-deployment
spec:
  replicas: 2 --> 4
```
- Change the replicas through cli;
```
kubectl scale deployment/<deployment-name> --replicas=<replicas-number>
```

#### Rolling updates
To rollout updates gradually (one by one pod will be replaced, contrary to normal deployment behaviour where pods are replaced simultaneously). 
- Use `kubectl rollout status deployment/<deployment-name>` to check the status of a rolling update.
- Use `kubectl rollout undo deployment/<deployment-name>` to rollback to previous deployment version (eg, latest deployment uses image-1.4, undo will rollback it to deployment that uses image-1.3)
- Execute gradual rollouts can be achieved by changing the image of the container, either through .yaml file or cli.
```
kubectl set image deployment.v1.apps/<deployment-name> <container-name>=<image-name:<tag>>
```

#### Blue/Green Deployments
Two production environments serving different version of applications to ensure no downtime for customers.
- Blue - The production environment running current version of application and serving the customer traffic.
- Green - Another production environment which runs the newer version of application. Once this environment is tested thoroughly,
the customer traffic is routed to this environment or deployment. After, this environment is monitored extensively. If any issue comes up,
the customers can be routed back to blue environment until green is fixed.
- In kubernetes, the switching between two environments is achieved through deployment `matchLabels` in deployment specs and `labels` in pod template.

#### Canary Deployments
Canary env is where only small number of user traffic is directed to new version of application.
- It can be managed through adjusting replicas of two different deployments (managing old and new version of application)
