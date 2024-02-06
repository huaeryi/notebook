### 反编译工具
* `apktool` 资源文件获取，可以提取出图片文件和布局文件进行使用查看  
* `dex2jar` 将apk反编译成java源码（classes.dex转化成jar文件）
* `jd-gui` 查看APK中classes.dex转化成出的jar文件，即源码文件
* `JEB`集成工具
* `jadx`

### APK
* apk文件也是一种zip文件，可以通过解压缩获取内部文件

### Java
* 处理得到的jar文件中可能含有外部调用的函数
* `native`表示这个Java文件可能调用了c语言写的函数库或其他动态链接库
