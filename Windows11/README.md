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
#### WSL -- install Command
- ```powershell
  wsl --install -d <Distribution Name> #WSL安装镜像使用命令格式
  wsl --list --online  #查看可用 Linux 分发版的列表
  wsl --install -d Ubuntu-20.04 #安装Ubuntu 20.04LTS
  wsl --set-default-version 2  #将 WSL2 设置为默认版本

  wsl --status   #查看更新状态，可显示 WSL 目前使用的内核版本，以及最后一次更新的时间。
  wsl --update   #WSL更新
  wsl --rollback  #回滚到上一次使用的 Linux 内核版本。
  wsl --shutdown  #关闭WSL
  ```
