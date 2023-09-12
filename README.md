# 介绍

使用 Multistrap 工具制作根文件系统，Multistrap是一个工具，可以用来构建一个完整的、可启动的、根文件系统。这个根文件系统可以被 Docker 和 WSL 使用。


# 使用

yangtze.multistrap 是配置文件。

```bash
bash build.sh
sudo tar -cf yangtze-rootfs.tar -C /yangtze-rootfs .
```

方法二：

在新位置导入WSL。
将openkylin.tar复制到C盘，并在C盘建名为：openkylin的文件夹
执行：wsl --import openkylin c:\openkylin c:\openkylin.tar --version 2
默认密码：35785214
Root密码：35785214

# 声明

参考 deepin-docker 制作
[deepin-docker](https://github.com/BLumia/deepin-docker)
