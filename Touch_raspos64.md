# Touch_raspos64

树莓派官方64位系统安装体验

## 1.下载镜像文件

```
https://mirrors.tuna.tsinghua.edu.cn/raspbian-images/raspios_arm64/images/raspios_arm64-2020-05-28/2020-05-27-raspios-buster-arm64.zip
```

## 2. 安装配置VNC

```
sudo raspi-config
interfacing options-->VNC
```

发现跟32位版本不一样的地方在于打开VNC时需要安装相关程序，不过等它自己安装完就好了，需要联网

接下来设置分辨率

```
advanced options-->resolution
```

发现使用VNC Server进行连接时显示被拒绝连接了，输入账号密码的机会都没有

Xshell连接终端是可以的，试着安装`tightvncserver vnc4server`看看，安装成功后再次开启VNC，又提示需要卸载安装`a`,好吧，那就安装呗，终于发现之前有一个问题被我忽略了

```
/usr/bin/vncserver-x11: error while loading shared libraries: libbcm_host.so: cannot open shared object file: No such file or directory
```

