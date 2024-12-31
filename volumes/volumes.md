**Volumes**
Volumes provide external storage to containers outside of the container filesystem. There are two concepts, volumes and volumeMounts.
Volumes are defined in Pod spec and volumeMounts are defined in container spec.

**Volume Types**
Defines where and how the data storage is handled.
- hostPath: Data is stored at a specific location, directly in host filesystem on node where pod is running.
- hostPath volume types:
    - Directory - Mounts an existing host directory 
    - DirectoryOrCreate - Mounts a host directory and creates it if does not exist.
    - File - Mounts an existing host file. 
    - FileOrCreate - Mounts a file on host and creates it if does not exist. 
- emptyDir: It is a temporary ephimeral storage outside of container filesystem. Data is stored in automatically 
managed location on the host filesystem (k8s nodes). Data is destroyed when pod is deleted.
- persistentVolume: PV is a default kubernetes resource. It abstracts volume storage details away from pods and 
treat storage like a consumable resource.
- persistentVolumeClaim - Defines request for storage needed by pod. This automatically binds the persistentVolume 
that meets the requested demands. Mounted in a pod like other volumes