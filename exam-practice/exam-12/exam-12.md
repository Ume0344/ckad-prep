### Create a Dockerfile

Create a Dockerfile for an application.

There is a project directory at /home/cloud_user/buzz. All the necessary files are in this directory. Create a Dockerfile in /home/cloud_user/buzz.

Use the busybox:1.34.1 image as the baseline for your new image.

Configure the Dockerfile to place data1.txt from the buzz directory into the resulting container image at /etc/data/mainData.txt.

Add data2.txt to the container image at /etc/data/data2.txt, and add data3.txt to the container image at /etc/data/data3.txt.


### Build and Save a Container Image

Build a container image using your Dockerfile located at /home/cloud_user/buzz/Dockerfile. Install Docker on the CLI server, and you can use the service to build the image.

Give this image the tag buzz:1. You do not need to run a container using this image or push it to any remote repository.

Save a copy of the image to an archive file located at /home/cloud_user/buzz_1.tar.

*Solution:* 
```
docker build -t buzz:1 .
docker image save -o /home/cloud_user/buzz_1.tar buzz:1
```