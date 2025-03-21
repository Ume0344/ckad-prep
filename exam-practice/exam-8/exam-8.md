### Locate and Fix a Failing Liveness Probe

Somewhere in the cluster, there is a Pod that is broken due to a failing liveness probe.

Locate this Pod and record the Namespace and Pod name in the file /home/cloud_user/probe-fix/broken-pod-name.txt. Store the data in the form namespace/podname.

Next, get a list of events for the Pod's Namespace using kubectl get events. Use the wide output format to retrieve additional information. Store the output of this command in the file /home/cloud_user/probe-fix/events.txt.

Finally, fix the underlying issue with the liveness probe to get the Pod running.
#### Solution -> livenessProbe.httpGet.port was incorrect.


### Find the Pod with the Highest CPU Usage

Locate the Pod within the cpu Namespace that is using the most CPU resources.

Save the name of that Pod in the file /home/cloud_user/metrics/high-cpu-pod-name.txt
#### Solution -> Use k logs to find highest cpu usage
