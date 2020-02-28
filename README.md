# 1.This repository include two images:
- ## OpenCV:4.2.0
  - include OpenCV4.2.0 with customized settings by compiled by my self

- ## OpenCV:4.2.0-dlib-face_rec-cuda
  - include OpenCV4.2.0 with customized settings by compiled by my self
  - include objective dlib
  - include face-recognition(***python package***) which can be execuated by CUDA
  ##### before using OpenCV:4.2.0-dlib-face_rec-cuda,***remember install nvidia-container-runtime(https://github.com/NVIDIA/nvidia-container-runtime)***

- ### There are two ways to get docker images: 
  #### 1. pull image from dockerhub
  - https://hub.docker.com/repository/docker/abc50111/opencv
  #### 2. build the image by Dockerfile
  - OpenCV:4.2.0 => https://github.com/theabc50111/opencv_dockerfile/blob/master/opencv:4.2.0/Dockerfile
  - OpenCV:4.2.0-dlib-face_rec-cuda =>https://github.com/theabc50111/opencv_dockerfile/blob/master/opencv:4.2.0-dlib-face_rec-cuda/Dockerfile


# 2.There are two ways to set enviroment and create container: 
  - ## 1. input the following code in terminal
    ```$ xhost +local:docker
    $ XSOCK=/tmp/.X11-unix
    $ XAUTH=/tmp/.docker.xauth
    $ xauth nlist $DISPLAY | sed -e 's/^..../ffff/' | xauth -f $XAUTH nmerge -
    $ sudo docker run -it --device=/dev/video0　-e DISPLAY=$DISPLAY --env QT_X11_NO_MITSHM=1 -v $XSOCK:$XSOCK -v $XAUTH:$XAUTH -e XAUTHORITY=$XAUTH abc50111/opencv:tag(*choose what you need*) command`
    $ xhost -local:docker #Revoke Authority
  - ## 2. input the following code in terminal
    ```- xhost +local:root 
    - docker run -it --net=host --env="DISPLAY" --volume="$HOME/.Xauthority:/root/.Xauthority:rw" abc50111/opencv:tag command

  - ### ***if you are using "OpenCV:4.2.0-dlib-face_rec-cuda"***<br>
    - ***install nvidia-container-runtime(https://github.com/NVIDIA/nvidia-container-runtime)***<br>
    - ***remember to add --gpus all in docker run command***
  - ### set enviromen example :　(*it's an exectable file, execute it will automatically create container*)
    - OpenCV:4.2.0
      - https://github.com/theabc50111/opencv_dockerfile/blob/master/opencv:4.2.0/4.2.0_docker_run-set_env
    - OpenCV:4.2.0-dlib-face_rec-cuda
      - https://github.com/theabc50111/opencv_dockerfile/blob/master/opencv:4.2.0-dlib-face_rec-cuda/4.2.0-dlib-face_rec-cuda_docker_run-set_env
    - ***remember to change the mounted directory : -v /home/ywt01/Desktop/CVtoDocker:/home***
