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
- [X] update `-v /${absolute_path_to_the_project}/OpenPCDet:/root/OpenPCDet \` in run.sh
- [X] `(sudo) bash run.sh` # this mounts this project to the container

Now, you shall enter a container

- [X] `cd /root/OpenPCDet`
- [X] `python setup.py develop`
- [X] Download KITTI data as the [original readme said](ORIGINAL_README.md)
- [X] Download models
- [X] Generate training data `python -m pcdet.datasets.kitti.kitti_dataset create_kitti_infos tools/cfgs/dataset_configs/kitti_dataset.yaml`
- [X] `cd tools & python test.py --cfg_file cfgs/pointpillar.yaml --batch_size 4 --ckpt ../ckpts/pointpillar.pth`

You shall see results in `/root/OpenPCDet/output/pointpillar/default/eval/epoch_no_number/val/default`

```
2020-09-21 04:53:02,187   INFO  Car AP@0.70, 0.70, 0.70:
bbox AP:90.7802, 89.5710, 88.1988
bev  AP:90.0862, 87.3121, 83.9497
3d   AP:87.3674, 77.2977, 74.0227
aos  AP:90.75, 89.37, 87.89
Car AP_R40@0.70, 0.70, 0.70:
bbox AP:95.9010, 92.0908, 90.7773
bev  AP:94.1856, 88.3521, 85.4229
3d   AP:88.3821, 78.4251, 74.9309
aos  AP:95.87, 91.86, 90.43
Car AP@0.70, 0.50, 0.50:
bbox AP:90.7802, 89.5710, 88.1988
bev  AP:95.3721, 90.0208, 89.1257
3d   AP:95.3044, 89.9037, 88.8997
aos  AP:90.75, 89.37, 87.89
Car AP_R40@0.70, 0.50, 0.50:
bbox AP:95.9010, 92.0908, 90.7773
bev  AP:97.2666, 94.5944, 93.5978
3d   AP:97.2260, 94.2424, 92.9334
aos  AP:95.87, 91.86, 90.43
Pedestrian AP@0.50, 0.50, 0.50:
bbox AP:60.3184, 57.2768, 54.1461
bev  AP:55.1695, 50.0249, 46.1048
3d   AP:50.5018, 45.4544, 41.0912
aos  AP:42.50, 40.33, 37.97
Pedestrian AP_R40@0.50, 0.50, 0.50:
bbox AP:60.1178, 56.4277, 53.1250
bev  AP:54.5183, 48.7809, 44.7121
3d   AP:49.0521, 43.7786, 39.1144
aos  AP:39.67, 36.77, 34.45
Pedestrian AP@0.50, 0.25, 0.25:
bbox AP:60.3184, 57.2768, 54.1461
bev  AP:66.3091, 63.0741, 59.7845
3d   AP:66.2020, 62.4316, 59.2472
aos  AP:42.50, 40.33, 37.97
Pedestrian AP_R40@0.50, 0.25, 0.25:
bbox AP:60.1178, 56.4277, 53.1250
bev  AP:66.7191, 62.8219, 59.4442
3d   AP:66.3862, 62.2832, 58.9252
aos  AP:39.67, 36.77, 34.45
Cyclist AP@0.50, 0.50, 0.50:
bbox AP:84.5649, 71.6686, 68.0017
bev  AP:81.5557, 64.4501, 61.8452
3d   AP:79.1085, 62.6828, 59.1882
aos  AP:84.28, 69.90, 66.25
Cyclist AP_R40@0.50, 0.50, 0.50:
bbox AP:87.6933, 72.7717, 68.6119
bev  AP:83.3776, 65.4307, 61.4462
3d   AP:80.3914, 62.6057, 58.7745
aos  AP:87.36, 70.83, 66.62
Cyclist AP@0.50, 0.25, 0.25:
bbox AP:84.5649, 71.6686, 68.0017
bev  AP:83.6275, 69.9468, 65.7707
3d   AP:83.6275, 69.8436, 65.7707
aos  AP:84.28, 69.90, 66.25
Cyclist AP_R40@0.50, 0.25, 0.25:
bbox AP:87.6933, 72.7717, 68.6119
bev  AP:86.7431, 70.6220, 66.3741
3d   AP:86.7431, 70.5932, 66.3730
aos  AP:87.36, 70.83, 66.62

```