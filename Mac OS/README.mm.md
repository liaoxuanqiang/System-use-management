## Mac OS
### Hackintosh Install Steps
#### 1.Download Mac OS Image
- [macOS Monterey 12.x]()
- [macOS Big Sur 11.6.x]()
- [macOS Catalina 10.15.x]()
#### 2.Create a USB installation disk
- [Etcher](https://www.balena.io/etcher/)
- [TransMAC](https://www.acutesystems.com/scrtm.htm)
#### 3.Download Intel NUC10 Hackintosh EFI
##### OpenCore EFI
  - [`Hackintosh EFI` Intel NUC10](https://github.com/hackintosh-efi/intel-nuc10) 
  - [`Pierpaolo` INTEL-NUC10i5FNH](https://github.com/pierpaolodimarzo/INTEL-NUC10i5FNH)
  - [`MacKonsti` nuc10i7fnh](https://github.com/mackonsti/nuc10i7fnh)
  - [OpenCore Sanity Checker](https://opencore.slowgeek.com/)
#### 4.Replacing EFI in USB installation disk
#### 5.Modify BIOS configuration
- ```sh
  -SATA Mode Selection -> AHCI
  -Secure Boot -> Disabled
  ```
##### 6.Install Hackintosh
### Hackintosh EFI Configuration
- [OpenCore Configurator](https://mackie100projects.altervista.org/download-opencore-configurator/)
- [Clover Configurator](https://mackie100projects.altervista.org/download-clover-configurator/)
- [Hackintool](https://github.com/headkaze/Hackintool)
### System optimized configuration
#### 1.Remove 4-digit password restriction
- ```bash
  pwpolicy -clearaccountpolicies # 取消4位数密码限制 
  passwd # 更改密码
  ```
#### 2.Allows to install apps from any source
- ```bash
  sudo spctl --master-disable # APP安装开启任何来源
  ```
#### 3.Modify hostname and share name
- ```bash
  sudo scutil --set HostName {自定义主机名} # 修改主机名
  sudo scutil --set ComputerName {自定义电脑名} # 修改共享名称
  ```
#### 4.Install Xcode Command Line Tools
- ```bash
  xcode-select --install # 安装 xcode 命令行工具
  ```
#### 5.Decreased Dock Response Time
- ```bash
  defaults write com.apple.dock autohide-time-modifier -float 0.5 && killall Dock # 设置启动坞动画时间设置为 0.5 秒
  defaults write com.apple.dock autohide-delay -int 0 && killall Dock # 设置启动坞响应时间最短
  ```
- ```bash
  defaults delete com.apple.dock autohide-time-modifier && killall Dock # 恢复启动坞默认动画时间
  defaults delete com.apple.Dock autohide-delay && killall Dock # 恢复默认启动坞响应时间
  ```
#### 6.Modify the number of launchpad rows and columns
- ```bash
  defaults write com.apple.dock springboard-columns -int 9 # 设置列数为 9
  defaults write com.apple.dock springboard-rows -int 6 # 设置行数为 6
  killall Dock # 重启 Dock 生效
  ```
- ```bash
  defaults write com.apple.dock springboard-rows Default # 恢复默认的列数
  defaults write com.apple.dock springboard-columns Default # 恢复默认的行数
  killall Dock # 重启 Dock 生效
  ```
### Software installation and configuration
#### iTerm2
#### Homebrew
##### 安装
- ```bash
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"  # 安装命令
  ```
##### 设置代理
- ```bash
  export https_proxy=http://127.0.0.1:7890 http_proxy=http://127.0.0.1:7890 all_proxy=socks5://127.0.0.1:7890 # ClashX 代理示例
  ```
##### brew 常用命令与软件
- ```bash
  brew update # 更新 Homebrew
  brew search [关键词] # 搜索相关的包
  rew info [软件名]   # 查看包的信息
  brew list # 查看已安装的包
  brew upgrade [软件名] # 更新某个软件
  brew cleanup # 清理所有软件的旧版
  brew uninstall [软件名] # 卸载某个软件
  brew install iproute2mac # ip 命令 查看ip地址很方便
  ```
##### brew services 命令
- ```bash
  brew services list： # 查看所有服务 
  brew services run [服务名] # 单次运行某个服务
  brew services start [服务名] # 运行某个服务，并设置开机自动运行
  brew services stop [服务名] # 停止某个服务
  brew services restart # 重启某个服务
  ```
##### brew 常用配置
- ```bash
  brew install iproute2mac # ip 命令 查看ip地址很方便
  brew install cask # 安装 brew-cask
  brew install qlmarkdown # 空格预览 markdown
  brew install syntax-highlight # 空格预览代码文件
  ```
#### Oh My Zsh
##### 安装
- ```bash
  sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)" # 安装卡的话就挂代理
  ```
