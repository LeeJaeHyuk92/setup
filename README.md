Ubuntu

NVIDIA install
sudo gedit /etc/modprobe.d/blacklist.conf
blacklist amd76x_edac #this might not be required for x86 32 bit users.
blacklist vga16fb
blacklist nouveau
blacklist rivafb
blacklist nvidiafb
blacklist rivatv
sudo apt-get —purge remove xserver-xorg-video-nouveau
sudo update-initramfs -u
sudo reboot
ctrl + alt + F1
sudo service lightdm stop
sudo ./NVIDIA-Linux-x86_64 —— .run
sudo reboot
nvidia -smi, nvidia-setting
무한로그인(출처: http://jangjy.tistory.com/260)
ctrl + alt + f1
sudo apt-get remove —purge nvidia*
한글입력
sudo apt-get install ibus ibus-hangul
reboot
ibus-setup -> korean(hangul)선택
system setting ->keyboard -> input source korean(Hangul)(Ibus) only
Anaconda

nb_anacondacloud
새로운 환경 만들 때 jupyter 설치
tensorflow

gpu 설치 (출처: http://luke77.tistory.com/44)
CUDA 설치 tensorflow가 요구하는 사양맞춰 https://developer.nvidia.com/cuda-downloads
sudo sh cuda_7.5.18_linux.run —override
-EULA 동의 : accept
-You are attempting to install on an unsupported configuration. Do you with to continue? : yes
-Install NVIDIA Accelerated Graphics Driver for Linux-x86_64 352.39 ? no (이미 설치했음)
-Install the CUDA 7.5 Toolkit? yes
-Enter Toolkit Location : Enter (default)
-Do you want to install a symbolic link at /usr/local/cuda ? yes
-Install the CUDA 7.5 Samples? no
-Enter CUDA Samples Location : Enter (default)
export LD_LIBRARY_PATH=”$LD_LIBRARY_PATH:/usr/local/cuda/lib64” , export CUDA_HOME=/usr/local/cuda
CUDNN 설치 https://developer.nvidia.com/cudnn
다운로드 받은 파일을 우클릭 하여 압축 품 (CUDA 폴더 생성됨)
tensorflow.org -> get started -> prepare environment for Linux 메뉴얼 참조 (파일을 복사함)
sudo cp -P cuda/include/cudnn.h /usr/local/cuda/include
sudo cp -P cuda/lib64/libcudnn* /usr/local/cuda/lib64
sudo chmod a+r /usr/local/cuda/include/cudnn.h /usr/local/cuda/lib64/libcudnn*
Tensorflow 설치
a. anaconda installation 참조
b. export TF_BINARY_URL=https://storage.googleapis.com/tensorflow/linux/gpu/tensorflow_gpu-0.12.1-cp27-none-linux_x86_64.whl 
c. pip install --ignore-installed --upgrade $TF_BINARY_URL    <<< python 2버젼젼
