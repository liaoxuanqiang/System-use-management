# Ubuntu

## Ubuntu Releases
### LTS Releases
- [Ubuntu 20.04.3 LTS (Focal Fossa)](http://releases.ubuntu.com/focal/)
- [Ubuntu 18.04.6 LTS (Bionic Beaver)](http://releases.ubuntu.com/bionic/)
### Interim Releases
- [Ubuntu 21.10 (Impishell Indri)](http://releases.ubuntu.com/impishell/)
- [Ubuntu 21.04 (Hirsute Hippo)](http://releases.ubuntu.com/hirsute/)
## Ubuntu Install
#### 1.Download the Ubuntu image
#### 2.Use [Rufus](http://rufus.ie/en/) to make installation disk
#### 3.Install the system
## Mirror sources
- [USTC open source software mirror](https://mirrors.ustc.edu.cn/)
- [华为开源镜像站](https://www.huaweicloud.com/product/mirrors.html?utm_source=3.baidu.com&utm_medium=organic&utm_adplace=kapian&ticket=ST-284735-qBnErkcWHqKY2S2UabAESk14-sso)
- [阿里云镜像站](https://developer.aliyun.com/mirror/)
- [网易开源镜像站](https://mirrors.163.com/)
- [清华大学开源软件镜像站](https://mirrors.tuna.tsinghua.edu.cn/)

## Configuration
### Modify source
#### 1.Backup configuration files
- 
  ```shell
  sudo cp -a /etc/apt/sources.list /etc/apt/sources.list.bak
  ```
#### 2.Modify sources.list file
- 
  ```shell
  sudo sed -i "s@http://.*archive.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list
  sudo sed -i "s@http://.*security.ubuntu.com@http://repo.huaweicloud.com@g" /etc/apt/sources.list
  ```
- ```shell
  sudo vim /etc/apt/sources.list
  ```

#### 3.Update index&Software
- ```shell
  sudo apt-get update
  ```
- ```shell
  sudo apt-get upgrade
  ```



## Commands
### Identity rights management
#### get user identity command
- 
  ```shell
  whoami
  ```

#### su
- 
  ```shell
  su - root  #-表示切换到root用户及环境
  su -  #可以省略root用户
  ```
#### sudo
- 
  ```shell
  sudo snap install firefox  #临时获得超级用户权限,通过snap来安装frefox浏览器
  sudo password for henry :  #输入henry用户的密码
  ```
### shellutdown&Reboot
#### shellutdown
- 
  ```shell
  sudo shellutdown -h 0  #h参数表示关机,0表示0秒后关机,即立即关机,这是最为稳妥的关机方式
  sudo halt  #快速关机,因为文件系统越来越强大,因此可以直接关机
  ```
#### reboot
- 
  ```shell
  sudo shellutdown -r 0  #参数表示重启,0表示0秒后重启,即立即重启,这是 最为稳妥的重启方式
  sudo reboot  #快速重启系统
  ```
### Copy
#### copy file
- 
  ```shell
  cd 
  cp ./.bashellrc src/
  ```
#### copy directory
- 
  ```shell
  cd /etc
  cp profile ~

  cp -r ./src/Documents
  ```
## Development deployment
### 1.Install and configure [Git](https://git-scm.com/download/linux)
- ```shell
  apt-get install git #Ubuntu安装Git命令
  
  add-apt-repository ppa:git-core/ppa 
  apt update; apt install git
  
  git config --global user.email "liaoxuanqiang@live.com" # 配置邮箱
  git config --global user.name "liaoxuanqiang" # 配置用户名
  ssh-keygen -t rsa -C "liaoxuanqiang@live.com" # 创建ssh key
  cat .ssh/id_rsa.pub # 查看.ssh/id_rsa.pub文件并复制key,在GitHub设置中添加ssh key
  ssh -T git@github.com # 链接验证
  ```
### 2.Install [VSCode](https://code.visualstudio.com) and add plugins
### 3.Configure proxy
- ```shell
  git config --global http.proxy 'http://127.0.0.1:7890' #设置理端口为7890
  git config --global https.proxy 'http://127.0.0.1:7890'
  git config --global http.proxy 'socks5://127.0.0.1:7890' #设置socks5代理端口为7890
  git config --global https.proxy 'socks5://127.0.0.1:7890'
  
  git config --global --unset http.proxy #取消设置git代理
  git config --global --unset https.proxy

  git config --global --get http.proxy #查看Git代理设置
  git config --global --get https.proxy

  cat ~/.gitconfig # 查看git配置
  git config -l # 或者也可以这样查看git的配置
  ```

## Install software
#### aria2
- ```shell
  1.安装
  sudo apt -y install aria2
  sudo mkdir /etc/aria2
  sudo touch /etc/aria2/aria2.session
  sudo wget -P /etc/aria2 https://github.com/ToyoDAdoubi/doubi/blob/master/other/Aria2/dht.dat

  2.配置
  sudo vim /etc/aria2/aria2.conf

  3.新建aria2c服务
  sudo vim /etc/systemd/system/aria2c.service
  4.启动、开机自启命令
  sudo systemctl enable aria2c.service
  sudo systemctl start aria2c.service
  5.卸载aria2
  udo apt-get remove aria2
  sudo apt-get remove –purge aria2

  dpkg -l |grep ^rc|awk '{print $2}' |sudo xargs dpkg -P
  ```
#### Web server
- [Caddy](https://caddyserver.com/)
- [File Browser](https://filebrowser.org/)

#### Open Source Media Center
##### Kodi
- []()
##### Jellyfin
- [Home](https://jellyfin.org/)
- []
##### Koel
- [Home](https://docs.koel.dev/)

#### Open Source Monitoring Panel
- [Netdata](https://learn.netdata.cloud/)
- [InPanel](http://inpanel.org/)
- [aaPanel](https://www.aapanel.com/index.html)
- []()