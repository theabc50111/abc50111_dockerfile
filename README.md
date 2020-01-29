# opencv_dockerfile

## Get docker images:
### **There are two ways** 
### 1. docker pull abc50111/opencv:tag name
https://hub.docker.com/repository/docker/abc50111/opencv
### 2. run the Dockerfile
https://github.com/theabc50111/Opencv/blob/master/docker%20file/Dockerfile

## Set enviroment and docker run image,there are two ways: 
### **There are two ways** 
### 1. input the following code in terminal
$ xhost +local:docker

$ XSOCK=/tmp/.X11-unix

$ XAUTH=/tmp/.docker.xauth

$ xauth nlist $DISPLAY | sed -e 's/^..../ffff/' | xauth -f $XAUTH nmerge -

$ sudo docker run -it --device=/dev/video0　-e DISPLAY=$DISPLAY --env QT_X11_NO_MITSHM=1\ -v $XSOCK:$XSOCK -v $XAUTH:$XAUTH\ 
-e XAUTHORITY=$XAUTH abc50111/opencv:4.2.0_gui-complete #remember to mounted the volumes 

$ xhost -local:docker #Revoke Authority

### 2.run the setXhost
https://github.com/theabc50111/Opencv/blob/master/docker%20file/setXhost
#remember to change the mounted directory => -v /home/ywt01/Desktop/CVtoDocker:/home

