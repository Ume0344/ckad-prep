### Configuration

```
# count docker images
docker image ls -q | wc -l

# build image
docker build -t <name>:<tag> .

# docker container run, image should be last argument
docker run -p <hostport:containerport> <image>

# to see the operating system image is built for
docker run python:3.6 cat /etc/os-release
```

- `command` in pod template overrides the entire `ENTRYPOINT` of Dockerfile. `args` in pod template overrides `CMD` of Dockerfile.
- secret can be build through cli `k create secret generic <secret_name> --from-literal=username=habiba --from-literal=password=123`
