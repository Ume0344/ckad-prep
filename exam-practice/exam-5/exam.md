### Create a PersistentVolume

Create a PersistentVolume called `pv-data` in the default Namespace.

Set the storage amount to `1Gi` and the storage class to `static`.

Use a `hostPath` to mount the host directory `/var/pvdata` with the PersistentVolume.


### Create a Pod That Consumes Storage from the PersistentVolume

Create a Pod called `pv-pod` in the default Namespace.

Use the `busybox:stable` image with the command `sh -c while true; do sleep 3600; done`.

Use the PersistentVolume to provide storage to this Pod's container at the path ` /var/data`.

If everything is set up correctly, you should be able to find some data exposed to the container by the PersistentVolume at `/var/data/data.txt`.
