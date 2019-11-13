# CentOS-SSH-Installation-And-Configuration
Step1 查看SSH是否安装。
```
rpm -qa | grep ssh
```
注：若没安装SSH则可输入:
```
yum install openssh-server
```
Step2启动SSH服务。
```
1.systemctl restart  sshd
```
```
2.systemctl start sshd
```
Step3查看是否启动22端口
```
netstat -antp | grep sshd
```
Step4设置SSH开机启动
```
systemctl enable sshd
```
# Centos-Static ip address-configuration
Step1配置静态IP地址
```
vi /etc/sysconfig/network-scripts/ifcfg-eno-网卡数字
```
Step2修改BootProto为Static，同时添加IPADDR、NETMASK、GATEWAY

Step3修改完成后，重启网络
```
service network restart
```
注：出现如下错误，直接重启Centos即可
```
Restarting network (via systemctl):  Job for network.service failed because the control process exited with error code. See "systemctl status network.service" and "journalctl -xe"
```
Step4设置DNS
```
vi /etc/resolv.conf

nameserver 8.8.8.8
nameserver 114.114.114.114
```
Step5测试
```
ping baidu.com
```
