

# 检查源是否存在
cat /etc/apt/sources.list.d/ros2.list

# 如果没有，标准配置流程（Humble 对应 Jammy 22.04）：
sudo apt install software-properties-common
sudo add-apt-repository universe

sudo curl -sSL https://raw.githubusercontent.com/ros/rosdistro/master/ros.key -o /usr/share/keyrings/ros-archive-keyring.gpg

echo "deb [arch=$(dpkg --print-architecture) signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] http://packages.ros.org/ros2/ubuntu $(. /etc/os-release && echo $UBUNTU_CODENAME) main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null

sudo apt update



# 1. 彻底清空旧的源文件
sudo rm -f /etc/apt/sources.list.d/ros2.list

# 2. 重新写入中科大的 ARM64 专属 Humble 软件源
echo "deb [arch=arm64 signed-by=/usr/share/keyrings/ros-archive-keyring.gpg] https://mirrors.ustc.edu.cn/ros2/ubuntu jammy main" | sudo tee /etc/apt/sources.list.d/ros2.list > /dev/null
