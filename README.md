# P44_GPU-CUDA_install


lspci | grep -i nvidia


#### voir les versions actuelles de cuda, du driver,... 
```shell
nvidia-smi
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
