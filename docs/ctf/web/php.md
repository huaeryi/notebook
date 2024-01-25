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
- r = 4; w = 2; x = 1;
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
- 过滤关键字的绕过
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


### PHP反序列化
* 序列化serialize()将变量转化为字符串
* 反序列化unserialize()
* POP 面向属性编程(Property-Oriented Programing) 

### PHP文件上传
- 经常和文件包含结合

### PHP文件包含
- [文件包含漏洞](https://cdn.zjusec.com/PHP%E6%96%87%E4%BB%B6%E5%8C%85%E5%90%AB%E6%BC%8F%E6%B4%9E%E6%80%BB%E7%BB%93.html)
- 本地文件包含 相对于被攻击服务器的本地文件
- 远程文件包含 相对于被攻击服务器的远程文件
#### php伪协议
- `file://`


- `php://input`用于把input内容当作php代码执行
    * 在协议头输入： ?/file=php://input
    * `?/file=php://input%00`可以用作截断
    * 在请求体输入：<?PHP system("ls /"); ?>`


#### 00截断
- payload后加上`%00`

#### 长度截断