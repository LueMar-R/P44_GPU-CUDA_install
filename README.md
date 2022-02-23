# P44_GPU-CUDA_install

#### affichier spec du GPU
```shell
(base) @-dell:~$ lspci | grep -i nvidia
01:00.0 3D controller: NVIDIA Corporation GM107GLM [Quadro M620 Mobile] (rev a2)
```
#### rechercher le driver corespondant 
![https://www.nvidia.fr/Download/](https://www.nvidia.fr/Download/)

purger nvidia*
```shell
@-dell:~$ sudo apt-get remove --purge '^nvidia-.*'
```
chercher la nouvelle version du driver + installer
```shell
@-dell:~$ apt search nvidia-driver
@-dell:~$ sudo apt install nvidia-driver-470
```
verif nvidia-smi. il peut être nécessaire de switcher de prime select
```shell
@-dell:~$ nvidia-smi
@-dell:~$ sudo prime-select intel
@-dell:~$ sudo prime-select nvidia
@-dell:~$ sudo reboot
```


#### ou voir la version actuelles du driver
```shell
(base) @-dell:~$ nvidia-smi
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 470.74       Driver Version: 470.74       CUDA Version: 11.4     |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|                               |                      |               MIG M. 
|===============================+======================+======================|
|   0  Quadro M620         Off  | 00000000:01:00.0 Off |                  N/A |
| N/A   50C    P8    N/A /  N/A |    507MiB /  2004MiB |      0%      Default |
|                               |                      |                  N/A |
+-------------------------------+----------------------+----------------------+
```

#### installer dans l'environnement
```shell
(monai) @-dell:~$ conda search cudnn
```
choisir la version de CuDNN/ CUDA qui matche la compute capability
```shell
(monai) @-dell:~$ conda install cudnn=8.2.1=cuda11.3_0
```

```shell
(monai) @-dell:~$ LD_LIBRARY_PATH='/home/lmaintier/miniconda3/envs/monai/lib/'
(monai) @-dell:~$ export LD_LIBRARY_PATH
(monai) @-dell:~$ python
Python 3.8.12 (default, Oct 12 2021, 13:49:34) 
[GCC 7.5.0] :: Anaconda, Inc. on linux
Type "help", "copyright", "credits" or "license" for more information.
>>> import tensorflow
>>> tensorflow.config.get_visible_devices()
2022-02-23 15:56:09.916835: I tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:936] successful NUMA node read from SysFS had negative value (-1), but there must be at least one NUMA node, so returning NUMA node zero
2022-02-23 15:56:09.932155: I tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:936] successful NUMA node read from SysFS had negative value (-1), but there must be at least one NUMA node, so returning NUMA node zero
2022-02-23 15:56:09.932568: I tensorflow/stream_executor/cuda/cuda_gpu_executor.cc:936] successful NUMA node read from SysFS had negative value (-1), but there must be at least one NUMA node, so returning NUMA node zero
[PhysicalDevice(name='/physical_device:CPU:0', device_type='CPU'), PhysicalDevice(name='/physical_device:GPU:0', device_type='GPU')]
```




#### Voir la version de cuda compilation tools
```shell
(base) user@user-dell:~$ nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2019 NVIDIA Corporation
Built on Sun_Jul_28_19:07:16_PDT_2019
Cuda compilation tools, release 10.1, V10.1.243
```
