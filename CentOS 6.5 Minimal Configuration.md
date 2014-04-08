CentOS 6.5 Minimal Configuration
================================

#### 配置网络

```
#setup eth0
/etc/sysconfig/network-scripts/ifcfg-eth0
DEVEICE=eth0
ONBOOT=yes
BOOTPROTO=static
IPADDR=192.168.254.65
PREFIX=24
GATEWAY=192.168.254.254
DNS1=202.96.64.68
DNS2=114.114.114.114
```

#### 配置多个IP

```
#cp /etc/sysconfig/network-scripts/ifcfg-eth0 /etc/sysconfig/network-scripts/ifcfg-eth0:0

#vi /etc/sysconfig/network-scripts/ifcfg-eth0:0
DEVEICE=eth0:0
ONBOOT=yes
BOOTPROTO=static
IPADDR=10.4.11.65
PREFIX=24
NAME="System eth0:0"
```

#### 配置静态路由

```
#vi /etc/sysconfig/network-scripts/route-eth0:0
10.0.0.0/8 via 10.4.11.254 dev eth0:0
```

#### 重新启动网路
```
#service network restart
```

#### 检查SSHD 服务是否启动
```
#checkcfg
```

