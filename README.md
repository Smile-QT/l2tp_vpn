## Docker 搭建 VPN 服务器

1. 准备一台 CentOS 7 系统或虚拟机

安装下载软件
```sh
sudo yum install wget -y  
```

2. 下载脚本文件

```shell   
wget https://raw.githubusercontent.com/choushunn/l2tp_vpn/main/init_centos7.sh
```
安装 Docker，输入 0，执行全部操作
```shell      
bash init_centos7.sh
```
3. 下载 Docker-compose 文件

```sh
wget https://raw.githubusercontent.com/choushunn/l2tp_vpn/main/docker-compose.yml
```

4. 配置 vpn.env 文件

```sh
wget https://raw.githubusercontent.com/choushunn/l2tp_vpn/main/vpn.env
```
修改 VPN 配置文件
```
#修改预共享密钥
VPN_IPSEC_PSK=key
#修改用户名
VPN_USER=admin
# 修改密码
VPN_PASSWORD=passw0rd
VPN_DNS_SRV1=114.114.114.114
VPN_DNS_SRV2=8.8.8.8
#添加其他用户请取消注释
#VPN_ADDL_USERS=guest
#VPN_ADDL_PASSWORDS=guest1
```

5. 启动 VPN 服务器

```sh
docker-compose up -d
```

6. 查看 VPN Server 运行状态

```sh
docker logs ipsec-vpn-server 
```

6. 停止 VPN Server

```sh
docker-compose down
```

## 下一步，使用 VPN
[Windows 10 使用 VPN](https://github.com/choushunn/common_tools/blob/main/vpn/Windows%2010%20%E4%BD%BF%E7%94%A8%20VPN.md)


## 特别感谢

[docker-ipsec-vpn-server](https://github.com/hwdsl2/docker-ipsec-vpn-server)

----

