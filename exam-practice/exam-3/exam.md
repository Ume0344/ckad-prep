Create a ConfigMap

Create a ConfigMap called `kenobi` in the `yoda` Namespace.

Store the following configuration data in the ConfigMap:

`planet: hoth`

Create a Pod That Consumes the ConfigMap as a Mounted Volume

Create a Pod called `chewie` in the yoda Namespace. Use the `nginx:stable` image.

Provide the kenobi ConfigMap data to this Pod as a mounted volume at the path `/etc/starwars`.

The volume name must be defined as `kenobi-cm`