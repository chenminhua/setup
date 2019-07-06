# setup ubuntu 1904

### 安装系统

如果在下载一些依赖的时候很慢，可以先跳过。默认选择登录不用输入密码。

### 先装个 vim

```
sudo apt install vim
```

### 换源 (此处为 19.04，其他版本注意替换变量)

```
cd /etc/apt
sudo cp -p sources.list sources.list.bak


#阿里云源
deb http://mirrors.aliyun.com/ubuntu/ disco main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ disco main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ disco-security main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ disco-security main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ disco-updates main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ disco-updates main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ disco-backports main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ disco-backports main restricted universe multiverse
deb http://mirrors.aliyun.com/ubuntu/ disco-proposed main restricted universe multiverse
deb-src http://mirrors.aliyun.com/ubuntu/ disco-proposed main restricted universe multiverse
#中科大源
deb https://mirrors.ustc.edu.cn/ubuntu/ disco main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ disco main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ disco-updates main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ disco-updates main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ disco-backports main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ disco-backports main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ disco-security main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ disco-security main restricted universe multiverse
deb https://mirrors.ustc.edu.cn/ubuntu/ disco-proposed main restricted universe multiverse
deb-src https://mirrors.ustc.edu.cn/ubuntu/ disco-proposed main restricted universe multiverse
#163源
deb http://mirrors.163.com/ubuntu/ disco main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ disco-security main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ disco-updates main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ disco-proposed main restricted universe multiverse
deb http://mirrors.163.com/ubuntu/ disco-backports main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ disco main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ disco-security main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ disco-updates main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ disco-proposed main restricted universe multiverse
deb-src http://mirrors.163.com/ubuntu/ disco-backports main restricted universe multiverse
#清华源
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-updates main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-updates main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-backports main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-backports main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-security main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-security main restricted universe multiverse
deb https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-proposed main restricted universe multiverse
deb-src https://mirrors.tuna.tsinghua.edu.cn/ubuntu/ disco-proposed main restricted universe multiverse
```

```
sudo apt update
sudo apt upgrade
```

### 显卡驱动

```
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt update
ubuntu-drivers devices
sudo apt install nvidia-driver-430
# 此处应该需要重启
nvidia-smi  #若出现电脑GPU列表，即安装成功
或者
nvidia-settings #显示你的显卡信息

```

### 关闭 screen lock

### shadowsocks

### teamviewer

### ngrok

```
wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
./ngrok authtoken <token>
```

### anaconda

```
# 安装后记得换源 https://mirror.tuna.tsinghua.edu.cn/help/anaconda/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --set show_channel_urls yes
```

### tensorflow, opencv

```
conda install tensorflow-gpu=1.12.0

conda config --add channels conda-forge
conda install opencv
```

### 输入法


### 其他软件

terminator， vscode

```
sudo apt install terminator
```
