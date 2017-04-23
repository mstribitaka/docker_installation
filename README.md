# docker_installation
Notes on installing docker images on ubuntu machine

## Installed docker: 

Followed instructions at [https://docs.docker.com/engine/installation/linux/ubuntu/]

## Installed nvidia-docker:

Instructions at [https://github.com/NVIDIA/nvidia-docker/]

### Note: problem running nvidia-docker a few months after first installing

Had to do:

```
sudo apt-get purge nvidia-*
sudo apt-get update
sudo apt-get install nvidia-375
sudo apt-get install nvidia-modprobe
```
Then followed installation instructions at nvidia-docker link above.


Added myself to docker group:

```shell
sudo groupadd docker
```
```shell
sudo usermod -aG docker <my_username>
```
Log out then log back in to take effect.

## nvidia_anaconda3

nvidia-docker image with Anaconda3 installed (no keras, tensorflow).

## nvidia_ktf

nvidia-docker image built on Anaconda nvidia_anaconda with Keras 2.0 and Tensorflow 1.0 (GPU).

## nvidia_anaconda

Went into nvidia/cuda image:

```shell
nvidia-docker run -it ... /bin/bash
```
Inside did:

```python
apt-get update
```

Downloaded Anaconda binary:

[https://www.continuum.io/downloads#linux]

Then:

```shell
bash Anaconda2-4.3.0-Linux-x86_64.sh
```

Installed Keras:

```shell
pip install keras
```
## nvidia_tfv1.0

Installed tensorflow:

```shell
pip install tensorflow-gpu
```

Downloaded Cuda DNN library from [https://developer.nvidia.com/rdp/cudnn-download]

Gunzipped and untarred file. 

Then inside nvidia-docker image:

```docker
cp cuda/include/cudnn.h /usr/local/cuda/include/

cp cuda/lib64/libcudnn* /usr/local/cuda/lib64/

chmod a+r /usr/local/cuda/include/cudnn.h

chmod a+r /usr/local/cuda/lib64/libcudnn*

export CUDA_HOME="/usr/local/cuda-8.0"

export PATH="${CUDA_HOME}/bin:$PATH"

export LD_LIBRARY_PATH="${CUDA_HOME}/lib64:$LD_LIBRARY_PATH"

```

Tried 
```shell
nvidia-smi
```
to test if GPU working. 

