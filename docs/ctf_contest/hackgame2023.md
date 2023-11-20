将于**赛后**收录Hackergame2023的好题

![](https:/img.shields.io/badge/-Misc-informational?style=flat-square)
![](https://img.shields.io/badge/-Crypto-red?style=flat-square)
![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
![](https://img.shields.io/badge/-Reverse-violet?style=flat-square)
![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)
![](https://img.shields.io/badge/-Blockchain-darkorange?style=flat-square)
![](https://img.shields.io/badge/-Android-green?style=flat-square)
![](https://img.shields.io/badge/-OSINT-informational?style=flat-square)

* 本note更新时间在赛后
* 施工中>>>

### Hackergame 启动 ![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
* 首先大喊Hackergame启动，url栏末尾出现`/?similarity=`
* 修改`/?similarity=100`即可获取flag

### 猫咪小测 ![](https://img.shields.io/badge/-OSINT-informational?style=flat-square)
Q1 想要借阅世界图书出版公司出版的《A Classical Introduction To Modern Number Theory 2nd ed.》，应当前往中国科学技术大学西区图书馆的哪一层？

* 搜索`中国科学技术大学西区图书馆`发现网页[西区图书馆简介](https://lib.ustc.edu.cn/%E6%9C%AC%E9%A6%86%E6%A6%82%E5%86%B5/%E5%9B%BE%E4%B9%A6%E9%A6%86%E6%A6%82%E5%86%B5%E5%85%B6%E4%BB%96%E6%96%87%E6%A1%A3/%E8%A5%BF%E5%8C%BA%E5%9B%BE%E4%B9%A6%E9%A6%86%E7%AE%80%E4%BB%8B/)
* 因此外文图书在**12**层

Q2 今年 arXiv 网站的天体物理版块上有人发表了一篇关于「可观测宇宙中的鸡的密度上限」的论文，请问论文中作者计算出的鸡密度函数的上限为 10 的多少次方每立方秒差距？

* 搜索`可观测宇宙中的鸡的密度上限`答案**23**在这个[知乎回答](https://www.zhihu.com/question/20337132/answer/3023506910)里

Q3 为了支持 TCP BBR 拥塞控制算法，在编译 Linux 内核时应该配置好哪一条内核选项？

* 搜索`TCP BBR Linux kernel config`，即得到答案**CONFIG_TCP_CONG_BBR**


Q4 🥒🥒🥒：「我……从没觉得写类型标注有意思过」。在一篇论文中，作者给出了能够让 Python 的类型检查器 MyPY mypy 陷入死循环的代码，并证明 Python 的类型检查和停机问题一样困难。请问这篇论文发表在今年的哪个学术会议上？

* 参考网站(https://ccf.atom.im/)中下拉找到`软件工程/系统软件/程序设计语言`类的会议，手动爆破得到会议名为**ECOOP**

### 更深更暗 ![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
* `Crtl + a` `Crtl + c` `Crtl + v`粘贴即可获得flag

### 旅行照片 3.0(2/3) ![](https://img.shields.io/badge/-OSINT-informational?style=flat-square)
#### 神秘奖牌
* 含有奖牌的图中是诺贝尔物理学奖和诺贝尔化学奖奖牌，根据题意，学长是东京大学学生，因此搜索东京大学诺贝尔奖得主，发现符号条件且出生最晚是`梶田隆章 1959.3 东京大学`，研究所名为**ICRR**，东京大学宇宙射线研究所

* 对暑假6 7 8 9月的日期爆破，得到日期**2023.8.10**
#### 这是什么活动？
* 第一问搜索`東京 上野公園 "2023.8.10"`，发现是[梅酒节](https://umeshu-matsuri.jp/tokyo_ueno/)，其中含有[【ボランティアSTAFF募集】](https://umeshu-matsuri.jp/tokyo_staff/)，发现编号为**S495584522**
* 第二问爆破，最后发现是**0**

#### 后会有期，学长！
* 第一问卡了一年还是没做出来，以后要仔细看看图片里的文字了（statphys28），答案是**安田讲堂**
* 第二问**熊猫-秋田犬**，搜索`ボタン＆カフリンクス 上野`，答案**熊猫**在这个[网站](https://www.instagram.com/explore/tags/%E3%83%9C%E3%82%BF%E3%83%B3%E3%82%A2%E3%83%B3%E3%83%89%E3%82%AB%E3%83%95%E3%83%AA%E3%83%B3%E3%82%AF%E3%82%B9/?ref=9472)
* 由后面的马里奥推测是涉谷任天堂旗舰店，搜索`涉谷 3d`即得到答案**秋田犬**

### 赛博井字棋 ![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
* 和ai下一子
* F12打开控制台修改ai下的位置如`board[1][1] = 0`然后即可覆盖ai下的地方
* 轻松拿下游戏，重振人类井字棋荣光！

### 奶奶的睡前 flag 故事 ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* 根据题目中 **谷歌的『亲儿子』连系统都没心思升级 截图 在最后**几个关键词googl搜索
* 发现google亲儿子系列pixel存在截图漏洞（事实上早期windows也存在）
* pixel acropalypse截图漏洞
* [检查工具](https://lordofpipes.github.io/acropadetect/)
* [恢复工具](https://acropalypse.app/)
* 由于**连系统都没心思升级**，尝试低版本pixel，在系统为pixel3时就恢复成功了

### 组委会模拟器 ![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
* 可以进化成为高频率星人后再申请组委会
* 如果进化失败，可以使用人类的javascript脚本
```js
setInterval(function() {
  var x = document.getElementsByClassName("fakeqq-message__bubble");
  for (var i = 0; i < x.length; i++) {
    var content = x[i].textContent;
    if (content.search(/hack\[/) != -1) {
      console.log(content);
      x[i].click();    
    }
  }
}, 1500);
```

### 虫 ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* SSTV:慢扫描电视（Slow-scan television）是业余无线电爱好者的一种主要图片传输方法，慢扫描电视通过无线电传输和接收单色或彩色静态图片。
* 推荐的工具MMSSTV，e2eSoft来读取.wav文件

### JSON ⊂ YAML(1/2) ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* 这题没有真正读懂文档，乱试出来了第一题（赛后一定好好学习文档

### Git? Git! ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* 根据题意猜测是git回滚
* `git reflog`查看提交历史记录
* `git reset --hard 505e1a3`回滚到含flag的版本，读取readme.md中的flag

### HTTP 集邮册 ![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
* [参考资料](https://http.dev/)
* 尝试了各种请求例子得到十二个状态码
* 无状态码：去掉http协议

### Docker for Everyone ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* `docker run -v /:/mnt -it alpine`挂载根目录
* 在mnt中寻找flag
* 发现`flag -> /dev/shm/flag`目录下
* `cat dev/shm/flag`读取 

### 惜字如金 2.0 ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* 根据代码后面提示，每行应有24个字符，而原来每行只有23个，说明被惜字如金优化了

```py
    cod_dict += ['nymeh1niwemflcir}echaet']
    cod_dict += ['a3g7}kidgojernoetlsup?h']
    cod_dict += ['ulw!f5soadrhwnrsnstnoeq']
    cod_dict += ['ct{l-findiehaai{oveatas']
    cod_dict += ['ty9kxborszstguyd?!blm-p']
```

* 根据`flag{}`的格式恢复数据

```py
    cod_dict += ['nymeh1niwemflcir}echaete']
    cod_dict += ['a3g7}kidgojernoetlsup?he']
    cod_dict += ['ulw!ff5soadrhwnrsnstnoeq']
    cod_dict += ['ctt{l-findiehaai{oveatas']
    cod_dict += ['ty9kxborszstgguyd?!blm-p']
```

* 运行得到flag

### 🪐 高频率星球 ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* `asciinema play asciinema_restore.rec >> flag.js`
* 查找删除多余的数据
* `nodejs flag.js`得到flag

### 🪐 小型大语言模型星球（2/4） ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
#### You Are Smart
* 输入`Am I smart?`

#### Accepted
* Python脚本随机爆破七位英文字母或六位英文字母

```py
from transformers import AutoModelForCausalLM, AutoTokenizer, GenerationConfig

model = AutoModelForCausalLM.from_pretrained("roneneldan/TinyStories-33M")

tokenizer = AutoTokenizer.from_pretrained("EleutherAI/gpt-neo-125M")

import random

def generate_random_str(randomlength=16):
  random_str =''
  base_str ='abcdefghigklmnopqrstuvwxyz'
  length =len(base_str) -1
  for i in range(randomlength):
    random_str +=base_str[random.randint(0, length)]
  return random_str

if __name__ == '__main__':

    for i in range(10000):
        prompt = generate_random_str(6)
        # prompt = "Am I smart?"
        input_ids = tokenizer.encode(prompt, return_tensors="pt")

        # Generate completion
        output = model.generate(input_ids, max_length = 1000, num_beams=1)

        # Decode the completion
        output_text = tokenizer.decode(output[0], skip_special_tokens=True)

        # Print the generated text
        if "accepted" in output_text:
            print(i, "-> OK")
            print("prompt: ", prompt)
            print("output: ", output_text)
            break
        else:
            print(i, "-> no")
            print("prompt: ", prompt)
```

* 运气好爆破成功了，爆破出来的结果应该不尽相同
prompt:  vffwmi
output:  accepted the cone and was so happy. She thanked the man and ran off with her cone.
The cone was so delicious and she was so
### 🪐 流式星球 ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* Python脚本读取二进制到flag.mp4

```py
import cv2
import numpy as np
import time

for w in range(1500, 2000):
    print("w = ", w)
    h = w
    num = int(135146688 / w / h / 3)
    # 打开二进制文件
    f = open('video.bin', 'rb')

    # 创建VideoWriter对象
    out = cv2.VideoWriter('output.mp4', cv2.VideoWriter_fourcc(*"mp4v"), num, (w, h), True)

    # 循环读取二进制数据，并转换为图像
    for i in range(0, num):
    # 读取一帧的字节数
        data = f.read(w*h*3)
        # 如果没有数据，则退出循环
        if not data:
            break
        # 将字节数据转换为一维数组
        arr = np.frombuffer(data, dtype=np.uint8)
        # 将一维数组转换为三维图像
        img = arr.reshape(w, h, 3)
        # 将图像写入视频文件
        out.write(img)

    # 释放资源
    f.close()
    out.release()

    time.sleep(3)
```

* 先尝试几个宽和高，失败后人肉调频发现w=1708，h=1708时出现了4列多行的画面
* 于是w=1708/4=427得到正常一帧图片的宽，最后在视频中得到flag
### 🪐 低带宽星球(1/2) ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
* 第一问扔一个压缩网站里面就好了

### 为什么要打开 /flag 😡(1/2) ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)
* 想过打包main和动态链接库（但没用）
* 想过在根目录写入动态链接库（但Read Only）
* 想过运行时改变环境变量LD_PRELOAD（但已经迟了）
* 最后居然是静态链接直接绕过了函数

```c
#include<stdio.h>
#include<stdlib.h>

int is_flag(const char *pathname) {
    return 0;
}

int main()
{
  // Read Only, open flag  
  printf("where is flag:");
  FILE *fp;
  char buffer[100];

  fp = fopen("/flag", "rw");

  if (fp == NULL) {
      printf("no\n");
      return;
  }

  while (fgets(buffer, 100, fp) != NULL) {
      printf("%s", buffer);
  }

  fclose(fp);  

  return 0;
}
```

### 异星歧途 ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)
* 会就玩，不会就枚举！
* 一个个试出来的，话说这真的是"二进制"题吗？

### 总结
* 第一次打hackergame，最后也拿到了自己十分满意的成绩`当前分数：3750， 总排名：142 / 2386`
* 感谢hackergame幕后的工作人员，也感谢这七天疯狂烧脑互相陪伴的大家，下次还来！
