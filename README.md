# opencv_dockerfile

## Get docker images:
### **There are two ways** 
### 1. docker pull abc50111/opencv:tag name
- https://hub.docker.com/repository/docker/abc50111/opencv
### 2. run the Dockerfile
#### 1.OpenCV:4.2.0-gui
- https://github.com/theabc50111/opencv_dockerfile/tree/master/opencv:4.2.0-gui
#### 2.OpenCV:4.2.0-gui-face_rec-cuda
- https://github.com/theabc50111/opencv_dockerfile/tree/master/opencv:4.2.0-gui-face_rec-cuda
## Set enviroment and docker run image,there are two ways: 
### **There are two ways** 
### 1. input the following code in terminal
- $ xhost +local:docker

- $ XSOCK=/tmp/.X11-unix

- $ XAUTH=/tmp/.docker.xauth

- $ xauth nlist $DISPLAY | sed -e 's/^..../ffff/' | xauth -f $XAUTH nmerge -

- $ sudo docker run -it --device=/dev/video0　-e DISPLAY=$DISPLAY --env QT_X11_NO_MITSHM=1\ -v $XSOCK:$XSOCK -v $XAUTH:$XAUTH\ 
-e XAUTHORITY=$XAUTH abc50111/opencv:4.2.0_gui-complete <br>
***1.remember to mounted the volumes***<br>
***2.if you are using "OpenCV:4.2.0-gui-face_rec-cuda"***<br>
***- install nvidia-container-runtime(https://github.com/NVIDIA/nvidia-container-runtime)***<br>
***- remember to add --gpus all --runtime=nvidia***
- $ xhost -local:docker ***(Revoke Authority)***

### 2.run the  	docker_run-set_env_gui_faceRec_cuda|docker_run-set_env_gui
- https://github.com/theabc50111/opencv_dockerfile/tree/master/opencv:4.2.0-gui
- https://github.com/theabc50111/opencv_dockerfile/tree/master/opencv:4.2.0-gui-face_rec-cuda
***remember to change the mounted directory : -v /home/ywt01/Desktop/CVtoDocker:/home***

