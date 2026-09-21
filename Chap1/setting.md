# 6.1.2 이미지 로 부팅

# 파티션 확장

lsblk

sudo growpart /dev/mmcblk0 1

sudo resize2fs /dev/mmcblk0p1

df -h

# 파일 카피

remotectl.sh
remote_gui.sh
testapp.py
np.py
oled.py
CHECK folder

# pip install

```bash
sudo apt-get install python3-pip
```

# 그 외 설치

```bash
pip3 install --user --upgrade Jetson.GPIO Adafruit-Blinka adafruit-circuitpython-neopixel-spi playsound

sudo udevadm control --reload-rules && sudo udevadm trigger

pip3 install --user adafruit-circuitpython-led-animation

pip3 install adafruit-circuitpython-ssd1306
```

## test

```bash
python3 np.py

python3 oled.py
```

# rc.local np.py 등록

```bash
sudo vi /etc/rc.local

#!/bin/bash

# Your custom commands go here
sleep 3
su - rssaem -c "/bin/python3 /home/rssaem/oled.py" &
sleep 2
su - rssaem -c "/bin/python3 /home/rssaem/np.py"
exit 0
```
# 배경화면 설정

wallpaper.png

# ultralyitcs 준비

```bash
pip3 uninstall opencv-python opcv-contrib-python

pip3 install 'numpy<2'

pip3 uninstall -y torch torchvision torchaudio

sudo apt-get install -y libopenblas-base libopenmpi-dev libomp-dev

# torch 
pip3 install ./torch/*.whl

# cudss 
sudo dpkg -i cudss-local-tegra-repo-ubuntu2204-0.7.1_0.7.1-1_arm64.deb

#dpkg 설치 후 가장 마지막에 나온 cp 명령문을 복사하여 붙혀넣고 실행시킨다.

sudo apt-get update

sudo apt install -y cudss

# cusparselt 
sudo dpkg -i cusparselt-local-tegra-repo-ubuntu2204-0.8.1_0.8.1-1_arm64.deb

#dpkg 설치 후 가장 마지막에 나온 cp 명령문을 복사하여 붙혀넣고 실행시킨다.

sudo apt-get update

sudo apt-get -y install cusparselt

# onnx
pip3 install ./onnx/*.whl
```bash

## test
```python
python3 -c "import torch; import torchvision"
```

# opencv-python
```bash
sudo apt install -y libatlas-base-dev

pip3 install ./opencv/*.whl

sudo apt install -y libtesseract4 tesseract-ocr
```

## 확인
```python
python3 -c "import cv2; print('CUDA 사용 가능 GPU 개수:', cv2.cuda.getCudaEnabledDeviceCount())"
```


# ultralyitcs 설치

```bash
pip3 install 'numpy<2' --force-reinstall

pip3 install pyyaml tqdm matplotlib requests psutil pandas seaborn

pip3 install ultralytics==8.4.0 --no-deps
```

## opencv, camera, ultralyitcs 설치 테스트
```bash
cd
cd CHECK
python3 opencvtest.py
python3 pi-camera_test.py
python3 yolov26trt_test_camera.py

```

# ROS2 humble 설치

```bash
cd
chmod +x *.sh
./install_ros.sh
```

## 확인
```bash
ros2 --version
```

## rospkgs 추가 설치

sudo apt install ros-humble-dynamixel-sdk

sudo apt install ros-humble-xacro

sudo apt install ros-humble-cartographer ros-humble-cartographer-ros ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-nav2-map-server

sudo apt install -y ros-humble-image-transport ros-humble-image-transport-plugins ros-humble-compressed-image-transport

sudo apt install ros-humble-rosbridge-suite

## 기본 패키지 빌드

```bash
cd 
cd ros2_app_ws
colcon build

cd
cd rssaem_ws
colcon build
```

# bash.rc 편집

source /opt/ros/humble/setup.bash

export PATH=/usr/local/cuda-12.6/bin:$PATH
export LD_LIBRARY_PATH=/usr/local/cuda-12.6/lib64:$LD_LIBRARY_PATH

export RMW_IMPLEMENTATION=rmw_fastrtps_cpp
source ~/ros2_app_ws/install/setup.bash
source /home/rssaem/rssaem_ws/install/setup.bash

export ROS_DOMAIN_ID=30
export RSSAEM_MODEL=rssaem
export LDS_MODEL=LDS-04

alias cbs='colcon build --symlink-install'


# jtop

sudo -v
curl -LsSf https://raw.githubusercontent.com/rbonghi/jetson_stats/master/scripts/install_jtop_torun_without_sudo.sh | bash

sudo usermod -aG jtop rssaem

newgrp jtop

jtop
