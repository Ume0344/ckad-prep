### Create a Pod with Resource Requests

Create a Pod in the `dev` Namespace called `apple`. Use the `nginx:stable` image.

Configure this Pod's container with resource requests for `256Mi` memory and `250m` CPU.


### Create and Consume a Secret

In the `secure` Namespace, create a Secret called `secret-code`.

You can get a a base64-encoded string for the Secret data via:

`echo trustno1 | base64`
Add the following key-value data to the Secret:

`code: [insert the base64-encoded string here]`
In the same Namespace, create a Pod called `secret-keeper`. Use the `busybox:stable` image. Configure the container to run the command `sh -c echo $SECRET_STUFF; sleep 3600`.

Provide the Secret's `code` key to the container as an environment variable called `SECRET_STUFF` If done correctly, the container's log should show the Secret data, `trustno1`