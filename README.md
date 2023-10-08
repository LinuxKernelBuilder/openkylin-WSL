# 介绍

使用 Multistrap 工具制作根文件系统，Multistrap是一个工具，可以用来构建一个完整的、可启动的、根文件系统。这个根文件系统可以被 Docker 和 WSL 使用。


# 使用

## 安装

首先需要下载 Linux 内核更新包，参考：[旧版 WSL 的手动安装步骤 | Microsoft Learn](https://learn.microsoft.com/zh-cn/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package) 

![1696769272977](C:\Users\XXTXT\Desktop\Gitee\openkylin-wsl\README.assets\1696769272977.png)

## 将 WSL 2 设置为默认版本

打开 PowerShell，然后在安装新的 Linux 发行版时运行以下命令，将 WSL 2 设置为默认版本：

```
wsl --set-default-version 2
```

### 方法一
yangtze.multistrap 是配置文件。

```bash
bash build.sh
sudo tar -cf yangtze-rootfs.tar -C /yangtze-rootfs .
```

### 方法二

在新位置导入WSL。
选一个存放虚拟磁盘的文件夹，起名为openkylin。  
将openkylin.tar复制到上面的文件夹里面，比如复制到了`c:\openkylin`，然后执行下面的命令：
```powershell
cd c:\openkylin
wsl --import openkylin .\ .\openkylin.tar --version 2
```
上面的openkylin是容器名，可以自定义，但是自己改完之后后面修改默认用户会比较麻烦。    

默认密码：35785214  
Root密码：35785214

## 新增用户
可以使用`wsl -d openkylin`进入系统中，此时进入的是root账户。  
1. 使用`passwd root`可以修改`root`账户密码。    
2. 新增用户xxxx到sudo组：`useradd -g sudo xxxx`
3. 修改xxxx密码：`passwd xxxx`
4. 添加家目录：`mkdir /home/xxxx`
5. 设置家目录权限：`chmod 777 -R ~`（本来应该设置755，但一些程序运行不对劲，所以这里改777了）

## 设置默认登陆用户
现在已经有了账户，但默认登陆还是root。  
如果想改成上面的xxxx，可以随便找一个wsl的安装程序，比如`deepin.exe`，用他来快速配置：
1. 把`deepin.exe`拷贝到`c:\openkylin`并改名成`openkylin.exe`
2. 执行`.\openkylin.exe config --default-user xxxx`如果不报错，默认用户就变成xxxxx了


# 声明

参考 deepin-docker 制作
[deepin-docker](https://github.com/BLumia/deepin-docker)
