### 搜索
* Google
* Chatgpt

### 文件类型
* `file <文件名>` 识别不带后缀的文件格式
* 16进制编辑器（winhex、010editer）查看文件头可以得到文件类型
* 文件头缺失，用编辑器补全

#### .sav
* 游戏存档文件
  
### 文件分离
* `binwalk <文件名>` 分析文件由其他文件合并
* `binwalk -e <文件名>` 分离文件
* `foremost <文件名> -o <输出文件名>` 分离文件
* `dd if=<源文件> of=<目标文件> bs=每块字节数<> count=<取多少块> skip=<跳过多少块>`
* winhex手动分离
* `strings`获取特定字符串

### 文件合并
* `cat c1 c2 c3 > c` 合并文件到c
* `cat c* > c` 同样效果
* `md5sum <文件名>`linux md5完整性检测
* `copy /B c1+c2+c3 c` windows下合并

### 图片隐写
#### PNG
* 文件开头`89 50 4E 47 0D 0A 1A 0A`

#### JPG

#### GIF

#### 细微颜色差别

#### 盲水印
* BlindWaterMark-master

#### gif多帧隐藏
* firework

#### Exif信息隐藏
* 显示一些图片的定位等信息
* 右键-属性
* `exiftool <图片>` 查看exif信息 

#### Unix时间戳
* Unix 时间戳是从1970年1月1日（UTC/GMT的午夜）开始所经过的秒数，不考虑闰秒
* 格式`1984:08:03 18:41:46` `+08:00` 换算时区

#### 图片修复
* stegsolve xor add sub运算

#### 最低有效位LSB隐写
* zteg
* wbstego4
* python脚本
* stegsolve

#### 图片加密
* TweakPNG可以打开文件头正常却CRC校验出错的文件
* 也可以用python爆破脚本检测CRC正常却长宽错误的文件
* bftools在win下解密图片信息
* silenteye用于隐藏文字和文件到图片
* stegdetect专门用于jpg图像加密，可识别如下隐写算法
  * Jphide
  * Outguess
  * F5
* 二维码扫描工具CQR


### 压缩文件
#### ZIP
* 文件开头`50 4B 03 04`
##### 暴力破解
* Windows下暴力破解ARCHPR，ziperello
* Linux下的命令行工具fcrackzip
##### 明文攻击
* Windows下ARCHPR
* Linux下PKCrack
##### 伪加密
* zip文件是否加密是通过标识符来显示的，0000代表未加密
* deflag这一位为1代表已经加密，可以利用这一点造成伪加密

#### RAR
* 文件开头`52 61 72 21 1A 07 00`
##### 暴力破解
* Linux下RarCrack
##### 伪加密
* PASSWORD_ENCRYPTED这一位为1代表已经加密

* 压缩文件可能解压后缺失，有人恶意写文件头，原本的文件头应当以0x74结尾
* NTFS数据流

### 流量取证
#### 借助wireshark抓取流量
* .pcap文件
* 过滤ip `ip.src eq xxxx or ip.dst eq xxxx`
* 过滤端口 `tcp.port == 80`
* 过滤协议 `tcp udp`
* 过滤MAC地址 `eth.dst`
* 过滤长度
* http模式过滤
* http和tcp流汇聚

#### 数据提取
* 导出http对象
* 导出分组对象

#### wifi流量破解
* `aircrack-ng <xxx.cap> -w dict.txt`
* `hashcat -m 22000`

#### USB流量包
* 导出csv
* `tshark`
* 键盘流量
* 鼠标流量

### 音频隐写
#### MP3隐写
* Mp3Stego
#### SSTV
* 慢扫描电视（Slow-scan television 简称SSTV）是业余无线电爱好者的一种主要图片传输方法，慢扫描电视通过无线电传输和接收单色或彩色静态图片。
* 使用工具：MMSSTV接收图片 e2eSoft虚拟声卡
* 文件类型：wav

### img
* 回环设备
* `sudo mount -o loop a.img /img` img挂载
* `sudo umount /img` 解除挂载

### ntfs数据流
* window下的文件系统，ntfs隐写
  * NtfsStreamsEditor
  * AlternateStreamView

### QR二维码
* QR research

### 0宽隐写
* [解码工具](http://330k.github.io/misc_tools/unicode_steganography.html)

### pyc反编译
* uncompyle6
* [在线工具](https://tool.lu/pyc/)

### git回滚
* `git log`
* `git reflog`
* `git reset --hard xxxxxx`

