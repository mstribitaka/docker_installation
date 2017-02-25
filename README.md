# docker_installation
Notes on installing docker images on ubuntu machine

## Installed docker: 

Followed instructions at https://docs.docker.com/engine/installation/linux/ubuntu/

## Installed nvidia-docker:

Instructions at https://github.com/NVIDIA/nvidia-docker/

Added myself to docker group:

```sudo groupadd docker
```
```sudo usermod -aG docker <my_username>
```
Log out then log back in to take effect.

Went into nvidia/cuda image:

```docker run -it ... /bin/bash
```
Inside did:

```apt-get update
```

Downloaded Anaconda binary:

https://www.continuum.io/downloads#linux

Then:

```bash Anaconda2-4.3.0-Linux-x86_64.sh
```

Installed Keras:

```pip install keras
```

Installed tensorflow:

```pip install tensorflow-gpu
```


