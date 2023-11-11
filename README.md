# P400-Jellyfin

nano /etc/apt/sources.list

```ajoutez contrib non-free aux dépots```

```apt-get update```

```apt-get upgrade```

```apt install nvidia-driver nvidia-support firmware-misc-nonfree```

apt install curl

curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg   && curl -s -L https://nvidia.github.io/libnvidia-container/stable/deb/nvidia-container-toolkit.list |     sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' |     sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list   &&     sudo apt-get update

sudo apt-get install -y nvidia-container-toolkit
sudo nvidia-ctk runtime configure --runtime=docker
sudo systemctl restart docker
sudo nvidia-ctk runtime configure --runtime=containerd
sudo systemctl restart containerd
sudo nvidia-ctk runtime configure --runtime=crio
sudo systemctl restart crio

sudo apt-get install nvidia-driver libnvcuvid1 libnvidia-encode1 libcuda1 nvidia-smi

aptitude install nvidia-opencl-icd
sudo apt search linux-headers-$(uname -r)
sudo apt install linux-headers-$(uname -r)

distribution=$(. /etc/os-release;echo $ID$VERSION_ID) \
      && curl -fsSL https://nvidia.github.io/libnvidia-container/gpgkey | sudo gpg --dearmor -o /usr/share/keyrings/nvidia-container-toolkit-keyring.gpg \
      && curl -s -L https://nvidia.github.io/libnvidia-container/$distribution/libnvidia-container.list | \
            sed 's#deb https://#deb [signed-by=/usr/share/keyrings/nvidia-container-toolkit-keyring.gpg] https://#g' | \
            sudo tee /etc/apt/sources.list.d/nvidia-container-toolkit.list
            
sudo apt-get update

apt install -t buster-backports nvidia-docker2
apt install -t buster-backports libnvidia-encode1
apt install -t buster-backports nvidia-smi
apt install -t buster-backports nvidia-container-runtime
sudo apt update && sudo apt install -y libnvcuvid1 libnvidia-encode1
sudo apt update && sudo apt install -y libnvidia-decode libnvidia-encode

sudo apt-get install aptitude
aptitude install nvidia-opencl-icd

docker run --gpus 0 nvidia/cuda:11.1.1-base nvidia-smi
