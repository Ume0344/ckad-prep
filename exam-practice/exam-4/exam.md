### Change the Rollout Settings for an Existing Deployment

There is a Deployment called fish in the `default` Namespace.

Change the `maxUnavailable` for this Deployment to 2. Change `maxSurge` to 50%. -> Just change it in deployment declaratively.

### Perform a Rolling Update

Perform a rolling update to change the image used in the `fish` Deployment to `nginx:1.21.5.` -> Just change image in deployment declaratively.


### Roll Back a Deployment to the Previous Version

Roll back the fish Deployment to the previous version. -> `k rollout undo deployment/fish`