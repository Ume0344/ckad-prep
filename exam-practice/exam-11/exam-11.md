### Create a ConfigMap to Store an `haproxy` Config File

Create a ConfigMap called haproxy-config in the default Namespace to store the haproxy configuration for an haproxy ambassador container.

In the ConfigMap, store the following config file in a key called haproxy.cfg:

frontend ambassador
  bind *:7171
  default_backend api_svc
backend api_svc
  server svc api-svc:8181

### Update a Service to Serve on a New Port.

In the default Namespace, there is a Service called api-svc. This Service serves an API that is accessed by the client Pod.

Change the Service's exposed port to 8181. This will temporarily break the client Pod's communication with the Service since the client Pod is still using the old port.


### Re-configure a Pod to use an haproxy ambassador container.

In the default Namespace, there is a Pod called client. This Pod should be unable to reach the api-svc Service since the Service's port was changed. Fix this issue by adding an ambassador container to the client Pod that uses haproxy to forward traffic to the Service's new port.

You can find manifest file for this Pod at /home/cloud_user/client.yml. Note that you may need to delete and re-create the Pod in order to make certain changes.

First, modify the command of the client Pod's main container so that it reaches out to localhost instead of api-svc. Do not change the port number that is used within this command.

Add an haproxy ambassador container to the client Pod using the haproxy:2.4 image. Mount the haproxy-config ConfigMap to the ambassador container at /usr/local/etc/haproxy/. This will cause the ConfigMap's haproxy configuration data to configure haproxy in the ambassador container.

Once this is done, the client Pod's main container should be able to contact the api-svc successfully again. You can check the container's logs with kubectl logs client -c main.