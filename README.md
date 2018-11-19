# 秋水逸冰写的脚本
- https://teddysun.com/
- https://github.com/teddysun
## 脚本索引

* [***代理相关***](#代理相关)
  * [Shadowsocks Python版一键安装脚本](#Shadowsocks Python版一键安装脚本)
  * [Shadowsocks-go一键安装脚本](#Shadowsocks-go一键安装脚本)
  * [ShadowsocksR一键安装脚本](#ShadowsocksR一键安装脚本)
  * [Shadowsocks 一键安装脚本(四合一)](#Shadowsocks 一键安装脚本(四合一))
  * [Debian下shadowsocks-libev一键安装脚本](#Debian下shadowsocks-libev一键安装脚本)
  * [L2TP/IPSec一键安装脚本](#L2TP/IPSec一键安装脚本)
  * [haproxy中转Shadowsocks流量一键安装脚本](#haproxy中转Shadowsocks流量一键安装脚本)
  * [一键安装KMS服务脚本](#一键安装KMS服务脚本)
  
---

## 代理相关

## Shadowsocks Python版一键安装脚本

- 脚本说明: ShadowsocksR 一键安装/管理脚本，支持单端口/多端口切换和管理
- 系统支持: Auto Install Shadowsocks(Python) Server for CentOS/Debian/Ubuntu
- 使用方法: https://teddysun.com/342.html

#### 下载安装:
``` bash
wget --no-check-certificate -O shadowsocks.sh https://raw.githubusercontent.com/heweiye/teddysunBackup/shadowsocks_install/master/shadowsocks.sh
chmod +x shadowsocks.sh
./shadowsocks.sh 2>&1 | tee shadowsocks.log
```

#### 卸载方法:
``` bash
./shadowsocks.sh uninstall
```
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status
配置文件路径：/etc/shadowsocks.json
单用户配置文件示例
``` bash
{
    "server":"0.0.0.0",
    "server_port":your_server_port,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"your_password",
    "timeout":300,
    "method":"your_encryption_method",
    "fast_open": false
}
```
多用户多端口配置文件示例
``` bash
{
    "server":"0.0.0.0",
    "local_address":"127.0.0.1",
    "local_port":1080,
    "port_password":{
         "8989":"password0",
         "9001":"password1",
         "9002":"password2",
         "9003":"password3",
         "9004":"password4"
    },
    "timeout":300,
    "method":"your_encryption_method",
    "fast_open": false
}
```

---
## Shadowsocks-go一键安装脚本

- 脚本说明: Shadowsocks-go一键安装脚本
- 系统支持: CentOS，Debian，Ubuntu
- 使用方法: https://teddysun.com/392.html

#### 下载安装:
``` bash
wget --no-check-certificate -O shadowsocks-go.sh https://raw.githubusercontent.com/heweiye/teddysunBackup/shadowsocks_install/master/shadowsocks-go.sh
chmod +x shadowsocks-go.sh
./shadowsocks-go.sh 2>&1 | tee shadowsocks-go.log
```
#### 卸载方法:
``` bash
./shadowsocks-go.sh uninstall
```

#### 使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status
配置文件路径：/etc/shadowsocks/config.json
多用户多端口配置文件示例：
``` bash
{
    "port_password":{
         "8989":"password0",
         "9001":"password1",
         "9002":"password2",
         "9003":"password3",
         "9004":"password4"
    },
    "method":"your_encryption_method",
    "timeout":600
}
```
可选 9 种加密方式
``` bash
aes-256-cfb
aes-192-cfb
aes-128-cfb
aes-256-ctr
aes-192-ctr
aes-128-ctr
chacha20-ietf
chacha20
rc4-md5
```

---
## ShadowsocksR一键安装脚本

- 脚本说明: Brook 一键安装脚本
- 系统支持: CentOS，Debian，Ubuntu
- 使用方法: https://shadowsocks.be/9.html

#### 下载安装:
``` bash
wget --no-check-certificate https://raw.githubusercontent.com/heweiye/teddysunBackup/shadowsocks_install/master/shadowsocksR.sh
chmod +x shadowsocksR.sh
./shadowsocksR.sh 2>&1 | tee shadowsocksR.log
```
使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
状态：/etc/init.d/shadowsocks status

日志文件路径：/var/log/shadowsocks.log
代码安装目录：/usr/local/shadowsocks
配置文件路径：/etc/shadowsocks.json
多用户配置示例：
``` bash
{
"server":"0.0.0.0",
"server_ipv6": "[::]",
"local_address":"127.0.0.1",
"local_port":1080,
"port_password":{
    "8989":"password1",
    "8990":"password2",
    "8991":"password3"
},
"timeout":300,
"method":"aes-256-cfb",
"protocol": "origin",
"protocol_param": "",
"obfs": "plain",
"obfs_param": "",
"redirect": "",
"dns_ipv6": false,
"fast_open": false,
"workers": 1
}
```
可选 15 种加密方式的其中之一（none 是不加密）
none
aes-256-cfb
aes-192-cfb
aes-128-cfb
aes-256-cfb8
aes-192-cfb8
aes-128-cfb8
aes-256-ctr
aes-192-ctr
aes-128-ctr
chacha20-ietf
chacha20
salsa20
xchacha20
xsalsa20
rc4-md5
可选 11 种协议（protocol）
origin
verify_deflate
auth_sha1_v4
auth_sha1_v4_compatible
auth_aes128_md5
auth_aes128_sha1
auth_chain_a
auth_chain_b
auth_chain_c
auth_chain_d
auth_chain_e
auth_chain_f
可选 9 种混淆（obfs）
plain
http_simple
http_simple_compatible
http_post
http_post_compatible
tls1.2_ticket_auth
tls1.2_ticket_auth_compatible
tls1.2_ticket_fastauth
tls1.2_ticket_fastauth_compatible


---
## Shadowsocks 一键安装脚本(四合一)

- 脚本说明: Shadowsocks 一键安装脚本(四合一)
- 系统支持: CentOS 6+，Debian 7+，Ubuntu 12+
- 使用方法: https://teddysun.com/486.html

#### 下载安装:
``` bash
wget --no-check-certificate -O shadowsocks-all.sh https://raw.githubusercontent.com/heweiye/teddysunBackup/shadowsocks_install/master/shadowsocks-all.sh
chmod +x shadowsocks-all.sh
./shadowsocks-all.sh 2>&1 | tee shadowsocks-all.log
```
卸载方法
``` bash
./shadowsocks-all.sh uninstall
```
Shadowsocks-Python 版：
/etc/init.d/shadowsocks-python start | stop | restart | status

ShadowsocksR 版：
/etc/init.d/shadowsocks-r start | stop | restart | status

Shadowsocks-Go 版：
/etc/init.d/shadowsocks-go start | stop | restart | status

Shadowsocks-libev 版：
/etc/init.d/shadowsocks-libev start | stop | restart | status

各版本默认配置文件
Shadowsocks-Python 版：
/etc/shadowsocks-python/config.json

ShadowsocksR 版：
/etc/shadowsocks-r/config.json

Shadowsocks-Go 版：
/etc/shadowsocks-go/config.json

Shadowsocks-libev 版：
/etc/shadowsocks-libev/config.json

可选 16 种加密方式的其中之一（Python 和 libev 版）
aes-256-gcm
aes-192-gcm
aes-128-gcm
aes-256-ctr
aes-192-ctr
aes-128-ctr
aes-256-cfb
aes-192-cfb
aes-128-cfb
camellia-128-cfb
camellia-192-cfb
camellia-256-cfb
chacha20-ietf-poly1305
chacha20-ietf
chacha20
rc4-md5

可选 9 种加密方式的其中之一（Go 版）
aes-256-cfb
aes-192-cfb
aes-128-cfb
aes-256-ctr
aes-192-ctr
aes-128-ctr
chacha20-ietf
chacha20
rc4-md5
可选 15 种加密方式的其中之一（none 是不加密，ShadowsocksR 版）
none
aes-256-cfb
aes-192-cfb
aes-128-cfb
aes-256-cfb8
aes-192-cfb8
aes-128-cfb8
aes-256-ctr
aes-192-ctr
aes-128-ctr
chacha20-ietf
chacha20
salsa20
xchacha20
xsalsa20
rc4-md5
可选 7 种协议（protocol）的其中之一（仅限 ShadowsocksR 版）
origin
verify_deflate
auth_sha1_v4
auth_sha1_v4_compatible
auth_aes128_md5
auth_aes128_sha1
auth_chain_a
auth_chain_b
可选 9 种混淆（obfs）的其中之一（仅限 ShadowsocksR 版）
plain
http_simple
http_simple_compatible
http_post
http_post_compatible
tls1.2_ticket_auth
tls1.2_ticket_auth_compatible
tls1.2_ticket_fastauth
tls1.2_ticket_fastauth_compatible




---
## Debian下shadowsocks-libev一键安装脚本

- 脚本说明: Debian下shadowsocks-libev一键安装脚本
- 使用方法: https://teddysun.com/358.html

#### 下载安装:
``` bash
wget --no-check-certificate -O shadowsocks-libev-debian.sh https://raw.githubusercontent.com/heweiye/teddysunBackup/shadowsocks_install/master/shadowsocks-libev-debian.sh
chmod +x shadowsocks-libev-debian.sh
./shadowsocks-libev-debian.sh 2>&1 | tee shadowsocks-libev-debian.log
```
卸载方法
``` bash
./shadowsocks-libev-debian.sh uninstall
```
使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
查看状态：/etc/init.d/shadowsocks status
修改配置文件 /etc/shadowsocks-libev/config.json 同时启用 IPv4 与 IPv6 支持
``` bash
{
    "server":["[::0]","0.0.0.0"],
    "server_port":your_server_port,
    "local_address":"127.0.0.1",
    "local_port":1080,
    "password":"your_password",
    "timeout":600,
    "method":"aes-256-cfb"
}
```


---
## CentOS下shadowsocks-libev一键安装脚本

- 脚本说明: CentOS下shadowsocks-libev一键安装脚本
- 系统支持: CentOS7 / Debian7+ / Ubuntu14+
- 使用方法: https://teddysun.com/357.html

#### 下载安装:
``` bash
wget --no-check-certificate -O shadowsocks-libev.sh https://raw.githubusercontent.com/heweiye/teddysunBackup/shadowsocks_install/master/shadowsocks-libev.sh
chmod +x shadowsocks-libev.sh
./shadowsocks-libev.sh 2>&1 | tee shadowsocks-libev.log
```
卸载方法：
``` bash
./shadowsocks-libev.sh uninstall
```
使用命令：
启动：/etc/init.d/shadowsocks start
停止：/etc/init.d/shadowsocks stop
重启：/etc/init.d/shadowsocks restart
查看状态：/etc/init.d/shadowsocks status
可选 16 种加密方式的其中之一
aes-256-gcm
aes-192-gcm
aes-128-gcm
aes-256-ctr
aes-192-ctr
aes-128-ctr
aes-256-cfb
aes-192-cfb
aes-128-cfb
camellia-128-cfb
camellia-192-cfb
camellia-256-cfb
chacha20-ietf-poly1305
chacha20-ietf
chacha20
rc4-md5


---

## L2TP/IPSec一键安装脚本

- 脚本说明: L2TP/IPSec一键安装脚本
- 系统支持: CentOS6+，Debian7+，Ubuntu12+
- 使用方法: https://teddysun.com/448.html
- 写在前面：基于 OpenVZ 虚拟化技术的 VPS 需要开启TUN/TAP才能正常使用

#### 下载安装:
``` bash
wget --no-check-certificate https://raw.githubusercontent.com/heweiye/teddysunBackup/across/master/l2tp.sh
chmod +x l2tp.sh
./l2tp.sh
```
使用命令：
l2tp -a 新增用户
l2tp -d 删除用户
l2tp -m 修改现有的用户的密码
l2tp -l 列出所有用户名和密码
l2tp -h 列出帮助信息
ipsec status （查看 IPSec 运行状态）
ipsec verify （查看 IPSec 检查结果）
/etc/init.d/ipsec start|stop|restart|status （CentOS6 下使用）
/etc/init.d/xl2tpd start|stop|restart （CentOS6 下使用）
systemctl start|stop|restart|status ipsec （CentOS7 下使用）
systemctl start|stop|restart xl2tpd （CentOS7 下使用）
service ipsec start|stop|restart|status （Debian/Ubuntu 下使用）
service xl2tpd start|stop|restart （Debian/Ubuntu 下使用）
---
## haproxy中转Shadowsocks流量一键安装脚本

- 脚本说明: haproxy中转Shadowsocks流量一键安装脚本
- 系统支持: CentOS，Debian，Ubuntu
- 使用方法: https://shadowsocks.be/10.html

#### 下载安装:
``` bash
wget --no-check-certificate https://raw.githubusercontent.com/heweiye/teddysunBackup/shadowsocks_install/master/haproxy.sh
chmod +x haproxy.sh
./haproxy.sh
```
卸载方法：
使用 root 用户登录，Debian 或 Ubuntu 系统运行以下命令：
``` bash
apt-get -y remove haproxy
```
CentOS 系统运行如下命令：
``` bash
yum -y remove haproxy
```
然后再删除 haproxy 的配置文件目录即可，命令如下：
``` bash
rm -rf /etc/haproxy
```
使用命令：
启动：service haproxy start
停止：service haproxy stop
重启：service haproxy restart
状态：service haproxy status
配置文件路径：/etc/haproxy/haproxy.cfg

---
## 一键安装KMS服务脚本

- 脚本说明: 一键安装KMS服务脚本
- 系统支持: CentOS 6+，Debian 7+，Ubuntu 12+
- 使用方法: https://teddysun.com/530.html

#### 下载安装:
``` bash
wget --no-check-certificate https://github.com/heweiye/teddysunBackup/across/raw/master/kms.sh && chmod +x kms.sh && ./kms.sh
```
使用命令：
启动：/etc/init.d/kms start
停止：/etc/init.d/kms stop
重启：/etc/init.d/kms restart
状态：/etc/init.d/kms status
卸载方法：
``` bash
./kms.sh uninstall
```


---
