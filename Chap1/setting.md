# 파티션 확장

lsblk

sudo growpart /dev/mmcblk0 1

sudo resize2fs /dev/mmcblk0p1

df -h

# 6.1.2

remotectl1.sh
remotectl2.sh
testapp.py
np.py
test.txt
CHECK folder

# pip install

sudo apt-get install python3-pip

# 그 외 설치

pip3 install --user --upgrade Jetson.GPIO Adafruit-Blinka adafruit-circuitpython-neopixel-spi playsound

sudo udevadm control --reload-rules && sudo udevadm trigger

pip3 install --user adafruit-circuitpython-led-animation

pip3 install adafruit-circuitpython-ssd1306

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

# ultralyitcs 준비

pip3 uninstall opencv-python opcv-contrib-python

pip3 install 'numpy<2'

pip3 uninstall -y torch torchvision torchaudio

sudo apt-get install -y libopenblas-base libopenmpi-dev libomp-dev


pip3 install ./torch/*.whl

sudo dpkg -i cudss-local-tegra-repo-ubuntu2204-0.7.1_0.7.1-1_arm64.deb

sudo cp /var/cudss-local-tegra-repo-ubuntu2204-0.7.1/cudss-*-keyring.gpg /usr/share/keyrings/

sudo apt-get update

sudo apt install -y cudss

wget https://developer.download.nvidia.com/compute/cusparselt/0.8.1/local_installers/cusparselt-local-tegra-repo-ubuntu2204-0.8.1_0.8.1-1_arm64.deb

sudo dpkg -i cusparselt-local-tegra-repo-ubuntu2204-0.8.1_0.8.1-1_arm64.deb

sudo cp /var/cusparselt-local-tegra-repo-ubuntu2204-0.8.1/cusparselt-*-keyring.gpg /usr/share/keyrings/

sudo apt-get update

sudo apt-get -y install cusparselt


pip3 install ./onnx/*.whl

```python
python3 -c "import torch; import torchvision)"
```

# opencv-python

sudo apt install -y libatlas-base-dev


pip3 install ./opencv/*.whl


sudo apt install -y libtesseract4 tesseract-ocr



* 확인
```python
python3 -c "import cv2; print('CUDA 사용 가능 GPU 개수:', cv2.cuda.getCudaEnabledDeviceCount())"
```


# ultralyitcs 설치


pip3 install 'numpy<2' --force-reinstall

pip3 install pyyaml tqdm matplotlib requests psutil pandas seaborn

pip3 install ultralytics==8.4.0 --no-deps


#ros


# rospkgs

sudo apt install ros-humble-dynamixel-sdk

sudo apt install ros-humble-xacro

sudo apt install ros-humble-cartographer ros-humble-cartographer-ros ros-humble-navigation2 ros-humble-nav2-bringup ros-humble-nav2-map-server

sudo apt install -y ros-humble-image-transport ros-humble-image-transport-plugins ros-humble-compressed-image-transport

sudo apt install ros-humble-rosbridge-suite

ros2_app_ws

rssaem_ws


colcon build

# bash.rc

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
