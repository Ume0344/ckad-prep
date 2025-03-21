### Run a Job on a Schedule

In the `one` Namespace, run a Job that executes repeatedly on a schedule. Use a `CronJob` called `pwd-runner` to do this.

The Job should run the `pwd` command once every minute. Use the `busybox:stable` image. If the command takes longer than 10 seconds to execute, it should be automatically terminated.

Verify that the Job runs successfully at least once.

### Create a Deployment

Create a Deployment called `nginx-dep` in the `two` Namespace.

Use the `nginx:stable` image, and run with `3` replicas. Expose port `8081`, and add an environment variable 
to the containers called `NGINX_PORT` with the value `8081`. This will cause the nginx container to listen on port `8081`.