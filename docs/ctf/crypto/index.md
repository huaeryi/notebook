# Crypto

### 密码学工具
* [cyberchef](https://icyberchef.com/)
* [在线工具包](http://www.hiencode.com/)
* [md5解密](https://www.cmd5.com/)
* [质因数分解factordb](http://www.factordb.com/)
* 质因数分解yafu
* [词频分析quipqiup](https://quipqiup.com/)
* gmpy2
* sage

### 常见编码
#### ASCII
* ASCII (American Standard Code for Information Interchange)：美国信息交换标准代码
#### Latin-1
* Latin-1也即ISO-8859-1编码是单字节编码，向下兼容ASCII，其编码范围是0x00-0xFF，0x00-0x7F之间完全和ASCII一致，0x80-0x9F之间是控制字符，0xA0-0xFF之间是文字符号

#### Unicode
* 统一的编码标准，下述编码是它的实现方式
* 16位含 \uxxxx
* `&#124`

???+ info "字节序"

    * 对于多字节编码而言，字节序有大端小端之分，字节序指的是多字节编码中以字节为单位排布的顺序，即8bit为一组，字节内部的顺序是不变的 大端法的`2F 45 3A 0D` 小端法就是`0D 3A 45 2F`

##### UTF-8
* UTF-8编码规则：如果只有一个字节则其最高二进制位为0；如果是多字节，其第一个字节从最高位开始，连续的二进制位值为1的个数决定了其编码的字节数，其余各字节均以10开头
  * `0xxxxxxx`：单字节编码形式;
  * `110xxxxx 10xxxxxx`：双字节编码形式;
  * `1110xxxx 10xxxxxx 10xxxxxx`：三字节编码形式;
  * `11110xxx 10xxxxxx 10xxxxxx 10xxxxxx`：四字节编码形式
##### UTF-16
* UTF-16是UNICODE编码实现方式之一，该编码长度既是可变，亦是固定：采用存储的字节长度，要么是2Byte ，要么是4Byte。
##### UTF-32
* 每个字符都采用 4byte 字节来存储，容易造成存储空间的浪费

#### GB系列
##### GB 1312
* 1980 年，中国发布了第一个汉字编码标准，也即 GB2312 ，全称 《信息交换用汉字编码字符集·基本集》，通常简称 GB （“国标”汉语拼音首字母）， 共收录了 6763 个常用的汉字和字符，此标准于次年5月实施，它满足了日常 99% 汉字的使用需求
* GB2312 把每个汉字都编码成两个字节，第一个字节是高位字节，第二个字节是低位字节

##### GBK
* GBK 也是双字节编码，为了向下兼容 GB2312， GBK 使用了 GB2312 没有用到的编码区域，总的编码范围是: 第一个字节 0x81–0xFE，第二个字节 0x40–0xFE

##### GB18030
* 与 GBK 不同的是，GB18030 是变长多字节字符集，每个字或字符可以由一个，两个或四个字节组成，所以它的编码空间是很大的，最多可以容纳 161 万个字符，由于需要兼容 GBK，四个字节的前两个字节和 GBK 编码保持一致

#### Base64
* 3 * 8 -> 4 * 6
* 扩充为八位后按对照表输出字节流

#### URL编码
* ASCII码的十六进制，加上%

#### 摩斯电码

#### JS混淆 

#### jsfuck
* 特征`[][(![]+[])`
* 很有趣的javascript加密

#### Brainfuck和Ook!
* 特征`+++++ +++++ [->++ +++++ +++<]`
* 特征`Ook!`
* [在线工具](https://www.splitbrain.org/services/ook)

### 古典密码
#### Caesar凯撒密码
* 也称ROT
#### 维吉尼亚密码


#### Rail Fence Cipher栅栏密码

#### 思科的Type 7加密形式
* [在线工具](http://www.atoolbox.net/Tool.php?Id=992)

#### Enigma密码机

### 加密算法
#### 对称加密
* 加密和解密密钥相同
* DES、3DES、IDEA、AES

#### 非对称加密
* 加密和解密密钥不同，即公钥和私钥
* RSA、ECC、EIGamal



### 摘要算法（哈希算法）
* 验证数据完整性
* MD5、SHA