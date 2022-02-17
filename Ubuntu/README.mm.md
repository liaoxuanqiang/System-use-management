## Ubuntu
### Ubuntu Install
#### 1.Download the Ubuntu image
- [Ubuntu Releases](http://releases.ubuntu.com)
#### 2.Use [Rufus](http://rufus.ie/en/) to make installation disk
#### 3.Install the system
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
### Install software
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
