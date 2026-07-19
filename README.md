# 强行写入 ROS 2 Humble 官方 ARM64 软件源
echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(source /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.p/ros2.list > /dev/null

# 再次刷新并安装
sudo apt update && sudo apt install ros-humble-gazebo-ros-pkgs -y
