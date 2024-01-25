# XSS跨站脚本攻击
???+ abstract "requests"

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