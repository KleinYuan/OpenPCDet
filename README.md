# How to run it

## Host Machine Setup (Tested)

- [X] ubuntu 18.04
- [X] NVIDIA 440, CUDA 10.2, CUDNN 8

## Docker

- [X] Install docker CE
- [X] Install nvidia-docker2

## Github

- [X] `git clone git@github.com:KleinYuan/OpenPCDet.git & cd OpenPCDet`
- [X] `git checkout v0.1` # lol
- [X] `cd docker`
- [X] `(sudo) bash build.sh`
- [X] `(sudo) bash run.sh` # this mounts this project to the container

Now, you shall enter a container

- [X] `cd /root/OpenPCDet`
- [X] Download KITTI data as the [original readme said](ORIGINAL_README.md)
- [X] Download models
- [X] Generate training data `python -m pcdet.datasets.kitti.kitti_dataset create_kitti_infos tools/cfgs/dataset_configs/kitti_dataset.yaml`
