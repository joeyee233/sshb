# SSH Bastionhost 

连接[奇安信网神运维审计系统](https://www.qianxin.com/product/detail/pid/385)堡垒机，自动完成：

- 2FA两步验证（需要配合`sshenc`）
- 跳转到指定资源
- 执行命令

## 🔧 安装

拉取Git仓库到本地

```bash
git clone git@github.com:joeyee233/sshb.git
```

将命令添加到本地

```bash
sudo cp sshb/sshb* /usr/local/bin/ 
```

## ⚙️ 使用

连接堡垒机资源

```bash
# sshb -h 堡垒机地址 -r 主机地址 -k 'TOTP秘钥' -c 执行命令
sshb -h 127.0.0.1 -r 10.10.0.1 -k '~/.totp/bastionhost.key' -c pwd
```

```bash
spawn ssh bastionhost-feihe
Welcome to SSHD

请选择多因子认证方式:
  [1] 短信验证码
  [2] 手机令牌OTP
  [x] English
  [e] 退出
> 2

请输入手机令牌OTP: ******
验证成功!

user login success

SSH资源(767) :
  [1] root@10.10.0.1  (测试资源)
  --输入'l'显示更多--

Telnet资源(0) :

Rlogin资源(0) :

操作命令:
  [l] 显示SSH资源列表
  [i] 显示Telnet资源列表
  [r] 显示Rlogin资源列表
  [s] 搜索资源，根据IP/name/account/label
  [k] 显示历史会话列表
  [x] English
  [n] encoding UTF8
  [h] 显示帮助
  [e] 退出

>
输入搜索关键字: 10.10.0.1

共1条结果:
 [1] root@10.10.0.1  (测试资源)

> 1
正在连接测试资源...

资源已被管控，一切操作将被记录
验证成功!
Last login: Wed Oct 16 17:15:04 2024 from 10.10.255.20

Welcome to Alibaba Cloud Elastic Compute Service !

[root@10.10.0.1]#pwd
/root
[root@10.10.0.1]#
```

