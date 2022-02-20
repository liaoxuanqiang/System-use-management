## Windows11

### System installation
#### 1.Check the latest Windows11 system version information
- [ChangeWindows](https://changewindows.org/)
#### 2.Download Windows11 OS image
- [Windows Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewiso)
#### 3.Use [EasyU](https://www.itsk.com/forum.php?mod=viewthread&tid=422456) tool to make PE boot disk
#### 4.After entering the PE system, partition the disk and install the system

### System optimized configuration
#### 1.Enable excellent performance mode
- ```powershell
  powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61
  ```
#### 2.Turn off hibernate
- ```powershell
  powercfg -h off
  ```
#### 3.Turn off VBS
- ```powershell
  bcdedit /set hypervisorlaunchtype off
  bcdedit /set hypervisorlaunchtype auto
  ```
#### 4.Turn off virtual memory
#### 5.Modify Group Policy (gpedit.msc) to disable broadband reservation

### Development environment
#### Set up a WSL development environment
##### 1.Get started
- ```powershell
  wsl --install
  ```
##### 2.Set up your Linux username and password
##### 3.Update and upgrade packages
- ```bash
  sudo apt update && sudo apt upgrade
  ```
#### Get started using Visual Studio Code with Windows Subsystem for Linux
##### 1.Install VS Code and the [Remote WSL extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.vscode-remote-extensionpack)
##### 2.Update your Linux distribution
- ```bash
  sudo apt-get update
  sudo apt-get install wget ca-certificates #添加 wget和 ca 证书
  ```
##### 3.Open a WSL project in Visual Studio Code
- ```powershell
  code .
  ```
#### Get started using Git on Windows Subsystem for Linux
##### 1.Git can be installed on Windows AND on WSL
##### 2.Installing Git
- ```bash
  sudo apt-get install git
  ```
##### 3.Git config file setup
- ```bash
  git config --global user.name "liaoxuanqiang"
  git config --global user.email "liaoxuanqiang@live.com"
  ```
##### 4.Git Credential Manager setup
- ```bash
  git config --global credential.helper "/mnt/c/Program\ Files/Git/mingw64/libexec/git-core/git-credential-manager-core.exe"
  ```
#### Get started with databases on Windows Subsystem for Linux
##### Install MySQL
- ```bash
  sudo apt update #更新 Ubuntu 包
  sudo apt install mysql-server #安装 MySQL
  mysql --version #确认安装并获取版本号
  ```
##### Install PostgreSQL
- ```bash
  sudo apt update #更新 Ubuntu 包
  sudo apt install postgresql postgresql-contrib #安装 PostgreSQL（和 -contrib 包，其中包含一些有用的实用程序）
  psql --version #确认安装并获取版本号
  ```
##### Install MongoDB
- ```bash
  cd ~ #转到主目录
  sudo apt update #Ubuntu 包
  wget -qO - https://www.mongodb.org/static/pgp/server-5.0.asc | sudo apt-key add - #导入 MongoDB 包管理系统使用的公钥
  echo "deb [ arch=amd64,arm64 ] https://repo.mongodb.org/apt/ubuntu focal/mongodb-org/5.0 multiverse" | sudo tee /etc/apt/sources.list.d/mongodb-org-5.0.list #为 MongoDB 创建一个列表文件
  sudo apt-get update #重新加载本地包数据库
  sudo apt-get install -y mongodb-org #安装 MongoDB 包
  mongod --version #确认安装并获取版本号
  mkdir -p ~/data/db #创建用于存储数据的目录
  sudo mongod --dbpath ~/data/db #运行 Mongo 实例
  ps -e | grep 'mongod' #检查 MongoDB 实例是否正在运行
  若要退出 MongoDB Shell，请使用快捷键：Ctrl + C
  ```
##### Install Microsoft SQL Server
##### Install SQLite
- ```bash
  sudo apt update #更新 Ubuntu 包
  sudo apt install sqlite3 #安装 SQLite3
  sqlite3 --version #确认安装并获取版本号
  ```
##### Install Redis
- ```bash
  sudo apt update #更新 Ubuntu 包
  sudo apt install redis-server #安装 Redis
  redis-server --version #确认安装并获取版本号
  ```
#### Get started with Docker remote containers on WSL 2
##### 1.Install Docker Desktop
##### 2.Develop in remote containers using VS Code
- [Install the VS Code Remote-WSL extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-wsl)
- [Install the VS code Remote-Containers extension](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-containers)
- [Install the VS Code Docker extension](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)

### Development tools
##### WSL
###### Basic commands
- ```powershell
  wsl --install #安装 WSL 和 Linux 的 Ubuntu 发行版
  wsl --install -d <Distribution Name> #安装特定的 Linux 发行版
  wsl --list --online #列出可用的 Linux 发行版
  wsl --list --verbose #列出已安装的 Linux 发行版
  wsl --set-version <distribution name> <versionNumber> #将 WSL 版本设置为 1 或 2
  wsl --set-default-version <Version> #设置默认 WSL 版本
  wsl --set-default <Distribution Name> #设置默认 Linux 发行版
  wsl ~ #将目录更改为主页
  wsl --distribution <Distribution Name> --user <User Name> #通过 PowerShell 或 CMD 运行特定的 Linux 发行版
  wsl --update #更新 WSL
  wsl --status #检查 WSL 状态
  wsl --help #Help 命令
  wsl -u <Username>`, `wsl --user <Username> #以特定用户的身份运行
  <DistributionName> config --default-user <Username> #更改发行版的默认用户
  wsl --shutdown #关闭
  wsl --unregister <DistributionName> #注销或卸载 Linux 发行版
  wsl --mount <DiskPath> #装载磁盘或设备
  ```
###### Run Linux GUI apps on WSL
- ```bash
  sudo apt update #更新发行版中的包
  sudo apt install gedit -y #安装 Gedit，若要在编辑器中启动 bashrc 文件，请输入：gedit ~/.bashrc
  sudo apt install gimp -y #安装 GIMP，若要启动，请输入：gimp
  sudo apt install nautilus -y #安装 Nautilus，若要启动，请输入：nautilus
  sudo apt install vlc -y #安装 VLC，若要启动，请输入：vlc
  sudo apt install x11-apps -y #安装 X11 应用，若要启动，请输入要使用的工具的名称。 例如：xcalc, xclock, xeyes
  ```
###### Install Google Chrome on WSL
- ```bash
  cd /tmp #将目录更改为 temp 文件夹
  udo wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb #使用 wget 下载Google Chrome
  sudo dpkg -i google-chrome-stable_current_amd64.deb #获取当前稳定版本
  sudo apt install --fix-broken -y #修复包
  sudo dpkg -i google-chrome-stable_current_amd64.deb #配置包
  若要启动，请输入：google-chrome
  ```
###### Install Microsoft Teams on WSL
- ```bash
  cd /tmp #将目录更改为 temp 文件夹
  sudo curl -L -o "./teams.deb" "https://teams.microsoft.com/downloads/desktopurl?env=production&plat=linux&arch=x64&download=true&linuxArchiveType=deb" #使用 curl 下载包
  sudo apt install ./teams.deb -y #使用 apt 安装Microsoft Teams
  若要启动，请输入：teams
  ```
###### Install Microsoft Edge browser on WSL
###### Install Node.js on WSL
- ```bash
  sudo apt-get install curl #安装 cURL（用于在命令行中从 Internet 下载内容的工具）
  curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.39.1/install.sh | bash #安装 nvm
  command -v nvm #验证安装
  nvm ls #列出当前安装的 Node 版本
  nvm install --lts #安装 Node.js 的当前稳定的 LTS 版本
  nvm install node #安装 Node.js 的当前版本
  nvm ls #列出安装的 Node 版本
  node --version #验证 Node.js 是否已安装，以及是否为当前默认版本
  npm --version #验证是否也有 npm
  ```
##### Windows Terminal
##### Windows Package Manager
###### 
##### PowerToys
##### Git
###### install configuration
- ```powershell
  winget install --id Git.Git -e --source winget #使用winget tool工具安装Git

  git config --global user.email "liaoxuanqiang@live.com" # 配置邮箱
  git config --global user.name "liaoxuanqiang" # 配置用户名
  ssh-keygen -t rsa -C "liaoxuanqiang@live.com" # 创建ssh key
  cat .ssh/id_rsa.pub # 查看.ssh/id_rsa.pub文件并复制key,在GitHub设置中添加ssh key
  ssh -T git@github.com # 链接验证
  ```
###### Configure proxy
- ```powershell
  git config --global http.proxy 'http://127.0.0.1:1080' #设置理端口为1080
  git config --global https.proxy 'http://127.0.0.1:1080'
  git config --global http.proxy 'socks5://127.0.0.1:1080' #设置socks5代理端口为1080
  git config --global https.proxy 'socks5://127.0.0.1:1080'

  git config --global --unset http.proxy #取消设置git代理
  git config --global --unset https.proxy

  git config --global --get http.proxy #查看Git代理设置
  git config --global --get https.proxy

  cat ~/.gitconfig # 查看git配置
  git config -l # 或者也可以这样查看git的配置
  ```
##### Databases
###### MySQL
- ```bash
  sudo /etc/init.d/mysql start #启动 MySQL 服务器
  sudo mysql_secure_installation #启动安全脚本提示符
  sudo mysql #打开 MySQL 提示符
  SHOW DATABASES; # 在MySQL 提示符查看可用的数据库
  CREATE DATABASE database_name; #在MySQL 提示符创建新数据库
  DROP DATABASE database_name; #在MySQL 提示符删除数据库
  ```
###### PostgreSQL
- ```bash
  sudo service postgresql status #检查数据库的状态
  sudo service postgresql start #开始运行数据库
  sudo service postgresql stop #停止运行数据库

  sudo passwd postgres #为默认管理员用户 postgres 分配的密码
  ```
###### MongoDB
- ```bash
  https://raw.githubusercontent.com/mongodb/mongo/master/debian/init.d | sudo tee /etc/init.d/mongodb >/dev/null #下载 MongoDB 的 init.d 脚本
  sudo chmod +x /etc/init.d/mongodb #分配该脚本可执行权限
  sudo service mongodb status #检查数据库的状态
  sudo service mongodb start #开始运行数据库
  sudo service mongodb stop #停止运行数据库
  mongo --eval 'db.runCommand({ connectionStatus: 1 })' #诊断命令验证你是否已连接到数据库服务器
  ```
###### SQLite
- ```bash
  sqlite3 example.db #创建名为“example.db”的测试数据库
  .databases #查看 SQLite 数据库列表
  .dbinfo ?DB? #查看数据库的状态
  .exit #退出 SQLite 提示符
  ```
###### Redis
- ```bash
  sudo service redis-server start #开始运行 Redis 服务器
  redis-cli ping #检查 redis 是否正常工作（redis-cli 是与 Redis 对话的命令行接口实用程序）
  sudo service redis-server stop #停止运行 Redis 服务器
  ```
##### Docker
- ```bash
  docker #列出 Docker CLI 中可用的命令
  docker <COMMAND> --help #列出特定命令的信息
  docker image ls --all #列出计算机上的 docker 映像
  docker container ls --all #列出计算机上的容器
  docker ps -a #如果没有 -a 显示全部标志，则仅显示正在运行的容器
  docker info #列出有关 Docker 安装的系统范围的信息
  ```
### Install software
#### Office
- [Office.2013-2021.C2R](https://cracksurl.com/office-2013-2021-c2r-install/)
#### WeChat、QQ
#### v2rayN
### System commands
#### Powercfg command-line options
- ```powershell
  powercfg /? #查看详细使用方法
  Powercfg -s <GUID> #使用命令格式
  Powercfg -l #获取<GUID>
  Powercfg /q #显示当前活动方案的内容

  电源方案 GUID:381b4222-f694-41f0-9685-ff5bb260df2e (平衡)
  电源方案 GUID:8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c (高性能) *
  电源方案 GUID:a1841308-3541-4fab-bc81-f71556f20b4a (节能)
  Power Scheme GUID: e9a42b02-d5df-448d-aa00-03f14749eb61  (Ultimate Performance)
  eg:
  Powercfg -s 8c5e7fda-e8bf-4a96-9a85-a6e23a8c635c #切换电源方案为高性能模式

  注册表路径为\HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Control\Power\PowerSettings
  ```

