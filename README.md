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
@-dell:~$ sudo apt install nvidia-driver-390
```
verif nvidia-smi. il peut être nécessaire de switcher de prime select
@-dell:~$ nvidia-smi
@-dell:~$ sudo prime-select intel
@-dell:~$ sudo prime-select nvidia
@-dell:~$ sudo reboot






#### voir les versions actuelles de cuda, du driver,... 
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

#### Voir la version de cuda compilation tools
```shell
(base) user@user-dell:~$ nvcc -V
nvcc: NVIDIA (R) Cuda compiler driver
Copyright (c) 2005-2019 NVIDIA Corporation
Built on Sun_Jul_28_19:07:16_PDT_2019
Cuda compilation tools, release 10.1, V10.1.243
```
