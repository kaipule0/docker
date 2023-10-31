# docker run.sh脚本





#!/bin/bash

# 检查是否已安装Docker
if ! which docker >/dev/null; then
  echo "Docker is not installed. Installing Docker..."
  
  # 安装Docker
  curl -fsSL https://get.docker.com -o get-docker.sh
  sudo sh get-docker.sh
  sudo usermod -aG docker $$USER
  sudo systemctl enable docker
  sudo systemctl start docker
  
  echo "Docker installation completed."
else
  echo "Docker is already installed."
fi

# 拉取镜像并运行容器
echo "Pulling and running the desired Docker image..."
docker run -d -p 8080:80 --name my_container your_docker_image

echo "Docker installation and container deployment completed."