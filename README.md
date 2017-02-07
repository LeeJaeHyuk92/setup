
## Ubuntu

* **NVIDIA install**


1. sudo gedit /etc/modprobe.d/blacklist.conf

		blacklist amd76x_edac #this might not be required for x86 32 bit users.
		blacklist vga16fb
		blacklist nouveau
		blacklist rivafb
		blacklist nvidiafb
		blacklist rivatv
    
2. sudo apt-get —purge remove xserver-xorg-video-nouveau
3. sudo update-initramfs -u
4. sudo reboot
5. ctrl + alt + F1
6. sudo service lightdm stop
7. sudo ./NVIDIA-Linux-x86_64 —— .run
8. sudo reboot
9. nvidia -smi, nvidia-setting


* **무한로그인(출처: http://jangjy.tistory.com/260)**


1. ctrl + alt + f1
2. sudo apt-get remove --purge nvidia*


* **한글입력**

1. sudo apt-get install ibus ibus-hangul
2. sudoreboot
3. ibus-setup -> korean(hangul)선택
4. system setting ->keyboard -> input source korean(Hangul)(Ibus) only


## Anaconda

nb_anacondacloud
새로운 환경 만들 때 jupyter 설치

## CUDA, cuDNN

* (출처: http://luke77.tistory.com/44)


* **CUDA 설치** tensorflow가 요구하는 사양맞춰 https://developer.nvidia.com/cuda-downloads


1. sudo sh cuda_7.5.18_linux.run —override


    -EULA 동의 : accept
    -You are attempting to install on an unsupported configuration. Do you with to continue? : yes
    -Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 352.39 ? no (이미 설치했음)
    -Install the CUDA 7.5 Toolkit? yes
    -Enter Toolkit Location : Enter (default)
    -Do you want to install a symbolic link at /usr/local/cuda ? yes
    -Install the CUDA 7.5 Samples? no
    -Enter CUDA Samples Location : Enter (default)
    
    
2. export LD_LIBRARY_PATH=”$LD_LIBRARY_PATH:/usr/local/cuda/lib64”
3. export CUDA_HOME=/usr/local/cuda


* **CUDNN 설치** https://developer.nvidia.com/cudnn


1. 다운로드 받은 파일을 우클릭 하여 압축 품 (CUDA 폴더 생성됨)
2. tensorflow.org -> get started -> prepare environment for Linux 메뉴얼 참조 (파일을 복사함)
3. sudo cp -P cuda/include/cudnn.h /usr/local/cuda/include
4. sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda/lib64
5. sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*


## Tensorflow 설치


1. tensorflow.org -> anaconda installation 참조
2. export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.1-cp27-none-linux_x86_64.whl 
3. pip install --ignore-installed --upgrade $TF_BINARY_URL    <<< python 2버젼

