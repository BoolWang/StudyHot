# HotRaspberry

树莓派的常用操作

## 1. 设置有线静态ip

```bash
nano  /etc/dhcpcd.conf
```

末尾添加：

```bash
#有线
interface eth0

static ip_address=192.168.0.10/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1

#无线
interface wlan0

static ip_address=192.168.0.200/24
static routers=192.168.0.1
static domain_name_servers=192.168.0.1
```

然后重启生效

## 2. 关闭防火墙

