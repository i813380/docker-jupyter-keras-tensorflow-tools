# Build
```
docker build -t i813380/jupyter-keras-tensorflow-tools:tf-1.4.0-devel-py3 .
docker build -t i813380/jupyter-keras-tensorflow-tools-sshd:tf-1.4.0-devel-py3 -f Dockerfile_ssh .

sudo nvidia-docker build -t i813380/jupyter-keras-tensorflow-tools:tf-1.4.0-devel-gpu-py3 -f Dockerfile_gpu .
sudo nvidia-docker build -t i813380/jupyter-keras-tensorflow-tools-sshd:tf-1.4.0-devel-gpu-py3 -f Dockerfile_ssh .
```

# Run
```
## Jupyter
docker rm -f keras; docker run --name keras -v $(pwd):/notebooks -p 8888:8888 -p 6006:6006 -t i813380/jupyter-keras-tensorflow-tools:tf-1.4.0-devel-py3

docker rm -f keras; docker run --name keras -v $(pwd):/notebooks -p 8888:8888 -p 6006:6006 -t i813380/jupyter-keras-tensorflow-tools:tf-1.4.0-devel-py3 jupyter lab --allow-root --no-browser

## Bash
docker rm -f keras; docker run --name keras -i -v $(pwd):/notebooks -p 8888:8888 -p 6006:6006 -t i813380/jupyter-keras-tensorflow-tools:tf-1.4.0-devel-py3 bash

## Interactive shell
docker exec -it keras bash
```

# SSH
```
docker rm -f keras; docker run -d --name keras -p 23:22 -p 8888:8888 -p 6006:6006 -v $(pwd):/notebooks -w /notebooks -t i813380/jupyter-keras-tensorflow-tools-sshd:tf-1.4.0-devel-py3

docker rm -f keras; docker run --name keras -p 23:22 -p 8888:8888 -p 6006:6006 -v $(pwd):/notebooks -w /notebooks -it i813380/jupyter-keras-tensorflow-tools-sshd:tf-1.4.0-devel-py3 bash

docker rm -f keras; docker run --name keras -p 23:22 -p 8888:8888 -p 6006:6006 -v $(pwd):/notebooks -w /notebooks -it i813380/jupyter-keras-tensorflow-tools-sshd:tf-1.4.0-devel-py3 jupyter lab --allow-root --no-browser

# First time access may be slow
sudo nvidia-docker rm -f keras; sudo nvidia-docker run --name keras -p 23:22 -p 8888:8888 -p 6006:6006 -v $(pwd):/notebooks -w /notebooks -it i813380/jupyter-keras-tensorflow-tools-sshd:tf-1.4.0-devel-gpu-py3 jupyter lab --allow-root --no-browser

nvidia-docker rm -f keras; nvidia-docker run --name keras -p 23:22 -p 8888:8888 -p 6006:6006 -v /homes1/aluna/docker-jupyter-keras-tensorflow-tools:/notebooks -w /notebooks -it i813380/jupyter-keras-tensorflow-tools-sshd:tf-1.4.0-devel-gpu-py3 jupyter lab --allow-root --no-browser

docker exec -it keras bash
ssh -p 23 root@localhost
```

# AWS Instructions

Instructions for AWS instance setup instructions

## CUDA Installation
```
See https://github.com/cannin/aws-cuda-docker-install
```
