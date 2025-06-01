## Exam prep

### Create resource imperatively
```
kubectl run nginx -n mynamespace --image=nginx
k run redis --image=redis:alpine --labels="tier=db"

# with running command env
kubectl run busybox --image=busybox --command --restart=Never -- env

# create namespace yaml without creating namespace
kubectl create ns myns -o yaml --dry-run=client

# get pods of all namespace
kubectl get pods -A

# expose a pod
k expose pod redis --port=6379 --name=redis-service --type=ClusterIP # port here is container port

# create deployment
k create deploy webapp --image=kodekloud/webapp-color --replicas=3 -n dev-ns
```