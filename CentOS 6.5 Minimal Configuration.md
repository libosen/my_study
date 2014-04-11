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

#### 更新系统
```
yum update
```

#### 检查SSHD 服务是否启动
```
#chkconfig
```



#### 安装FTP，设置
查看是否已经安装vsftpd
```
rpm -qa | grep vsftpd
```
如果没有，就安装，并设置开机启动
```
yum install vsftpd
chkconfig vsftpd on
```

修改配置文件

打开/etc/vsftpd/vsftpd.conf，做如下配置
```
anonymous_enable=NO //设定不允许匿名访问
local_enable=YES //设定本地用户可以访问。
chroot_local_user=YES  //本地所有帐户都只能在自家目录
```

##### 设置防火墙

打开/etc/sysconfig/iptables, 添加
```
-A INPUT -m state --state NEW -m tcp -p tcp --dport 21 -j ACCEPT
```
然后保存，并关闭该文件，在终端内运行下面的命令，刷新防火墙配置：
```
service iptables restart
```

##### 设置 SELINUX 规则
```
#getsebool -a | grep ftp //查看是否 ftp_home_dir -> off
#setsebool ftp_home_dir 1 //打开 ftp_home_dir 规则,每次开机规则复位
OR
#setsebool -P ftp_home_dir 1 //保存规则
```

OK，运行“service vsftpd start”，你就可以访问你的FTP服务器了。

##### 配置PASV模式
vsftpd默认没有开启PASV模式，现在FTP只能通过PORT模式连接，要开启PASV默认需要通过下面的配置
```
pasv_enable=YES   //开启PASV模式
pasv_min_port=40000   //最小端口号
pasv_max_port=40080   //最大端口号
pasv_promiscuous=YES
```
在防火墙配置内开启40000到40080端口 /etc/sysconfig/iptables
```
-A INPUT m state --state NEW m tcp p dport 40000:40080 j ACCEPT
```
重启iptabls和vsftpd
```
service iptables restart
service vsftpd restart
```