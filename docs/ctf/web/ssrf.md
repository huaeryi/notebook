# SSRF服务端请求伪造
???+ abstract "requests"

    * SSRF，Server-Side Request Forgery，服务端请求伪造
    * 当服务器请求一个传入的url但未过滤时，传入的恶意url将会对内网进行攻击

### url中伪协议的类型
* file:///
* dict://
* sftp://
* ldap://
* tftp://
* gopher://

### DNS rebinding
* 通过低ttl的域名重绑定混淆目标，达到绕过的效果
