# Web

!!! abstract

    * web作为一种常见题型，包含以下的几种类型
    * 网页隐藏信息查找
    * 脚本执行
    * 代码审计php,js
    * 代码注入
    * 特定框架web漏洞
    * CVE漏洞库

### Web工具
#### 靶场搭建
* phpstudy搭建本地容器
* Dvwa集成了常用攻击手段的测试容器
#### Chorme开发人员工具和插件
* 右键`检查`或`Crtl + Shift + I`或`F12`打开开发人员工具
* Hackbar插件集成了常用的web请求、攻击手段和编码绕过
#### 集成工具
* Burpsuite
* sqlmap

### RCE拿到shell之后
* `cat flag`
* `./flag`执行可执行文件拿到flag


### 网页信息查找
#### 敏感文件
* `robots.txt`
* `index.php`
* `index.php~`
* `.index.php.swap`

### 文件泄露
#### git泄露
* `./scrabble <url>` 探测源代码中的git泄露
#### vim泄露


### 常用框架

#### flask

#### Nginx

#### Apache

#### tomcat弱口令
* tomcat - tomcat 
* shell.jsp
* shell.jsp压缩为shell.zip再改名为shell.war
* 上传shell.war获取shell



### CSRF跨站请求伪造
* CSRF，全名 Cross Site Request Forgery，跨站请求伪造



### WAF绕过

### Web夺权模板
#### 信息探测
* `nmap -sV ip` 挖掘开放服务信息
* `nmap -A -v -T4 ip` 探测靶场全部信息
* `nmap -O ip` 探测靶场操作系统类型与版本
* `nikto -host ip:port` 挖掘敏感信息
* `dirb http://ip:port/` 对服务隐藏文件探测



#### 漏洞扫描
* web漏洞扫描器 owasp-zap

#### nc端口监听
* `nc ip port` 监听端口

#### 浏览器
* 浏览器查看敏感页面源代码

### SSH协议
* ssh（Secure Shell） 22端口
#### 基于口令认证
* 通过账号和口令登录到远程主机
* 弱口令暴力破解获取用户名和密码，不一定获取root权限
#### 基于密钥的安全认证
* `id_rsa` 私钥
* `id_rsa.pub` 公钥
* `chmod 600 id_rsa`
* `ssh -i id_rsa 用户名@主机地址` 登陆服务器
#### 信息探测
* `nmap -sV ip` 挖掘开放服务信息
* `nmap -A -v ip` 探测靶场全部信息
* `nmap -O ip` 探测靶场操作系统类型与版本

#### 分析探测结果，挖掘敏感信息
* ssh22端口考虑暴力破解和私钥泄露
* http服务80端口考虑浏览器访问和探测工具
* `dirb http://ip:port/` 对服务隐藏文件探测
* `nikto -host ip` 挖掘敏感信息

#### 登录主机
* `ssh -i id_rsa name@ip` 以name身份登录ip主机
* `find / -perm -4000 2>/dev/null` 查找具有root权限的文件

#### 权限提升
* `whoami`查看用户
* `id`查看权限
* `msfconsole`集成的攻击框架
* `/etc/crontab` 定时执行的文件
* `nc ip port` 监听端口
* `python -c "import pty;pty.spawn('/bin/bash')"` 优化shell

### SMB泄露
* SMB 139 445端口
* `smbclient -L ip` 

### FTP后门
* msf查看版本号获取漏洞代码

### shiro框架漏洞
* Apache Shiro 是一个Java安全框架
* [shiro反序列化漏洞利用工具](https://github.com/j1anFen/shiro_attack)
