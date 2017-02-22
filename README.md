## Ubuntu gdm3 setup

1. sudo apt-get install ubuntu-gnome-desktop
2. sudo dpkg-reconfigure gdm


first : https://zapary.blogspot.kr/2014/08/ubuntu-recovery-mode.html

second : http://ishuca.tistory.com/entry/Ubuntu-1404-%EC%97%90%EC%84%9C-%EC%95%84%EB%82%98%EC%BD%98%EB%8B%A4%EC%97%90-Tensorflow-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0


## Ubuntu

* **NVIDIA install**( https://zapary.blogspot.kr/2014/08/ubuntu-recovery-mode.html)


1. sudo gedit /etc/modprobe.d/blacklist.conf

		blacklist amd76x_edac #this might not be required for x86 32 bit users.
		blacklist vga16fb
		blacklist nouveau
		blacklist rivafb
		blacklist nvidiafb
		blacklist rivatv
    
2. -- do not!!! sudo apt-get —purge remove xserver-xorg-video-nouveau 
3. sudo update-initramfs -u
4. sudo reboot
5. ctrl + alt + F1
6. sudo service lightdm stop
7. sudo sh NVIDIA-Linux-x86_64 —— .run
8. sudo reboot
9. nvidia -smi, nvidia-setting


* **무한로그인(출처:http://unix.stackexchange.com/questions/341920/fix-nvidia-drivers-in-ubuntu-16-04-when-getting-the-stopping-user-manager-for-u or http://man-about-town.tistory.com/45 or http://m.blog.naver.com/dusrb2003/220549096442)**

1. NVIDIA, CUDA uninstall
2. grub - advanced...mode
3. reinstall nvidia
4. reboot

* **한글입력**

1. sudo apt-get install ibus ibus-hangul
2. sudoreboot
3. ibus-setup -> korean(hangul)선택
4. system setting ->keyboard -> input source korean(Hangul)(Ibus) only


## Anaconda

nb_anacondacloud
새로운 환경 만들 때 jupyter 설치

## CUDA, cuDNN

* (출처: http://ishuca.tistory.com/entry/Ubuntu-1404-%EC%97%90%EC%84%9C-%EC%95%84%EB%82%98%EC%BD%98%EB%8B%A4%EC%97%90-Tensorflow-%EC%84%A4%EC%B9%98%ED%95%98%EA%B8%B0 or http://luke77.tistory.com/44)


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

