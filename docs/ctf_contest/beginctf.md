# BeginCTF2024

???+ abstract

    将于赛后收录BeginCTF中一些尝试过的题

    ![](https:/img.shields.io/badge/-Misc-informational?style=flat-square)
    ![](https://img.shields.io/badge/-Crypto-red?style=flat-square)
    ![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
    ![](https://img.shields.io/badge/-Reverse-violet?style=flat-square)
    ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)

    
    * 本note更新时间在赛后
    * 🚧施工中>>>

* 拿了自由赛道30名，3501分，很高兴有进步！
## Misc
### 问卷
- [x] begin{Thank5_F0r_Your_P@rt1c1pa7ion}
### real check in
- Base32解码得到flag
- [x] begin{WELCOMe_to_B3GinCTF_2024_H0Pe_YOU_wiL1_11ke_i7}

### Tupper
- python脚本读取文件得到
- `14278193432728026049298574575557534321062349352543562656766469704092874688354679371212444382298821342093450398907096976002458807598535735172126657504131171684907173086659505143920300085808809647256790384378553780282894239751898620041143383317064727136903634770936398518547900512548419486364915399253941245911205262493591158497708219126453587456637302888701303382210748629800081821684283187368543601559778431735006794761542413006621219207322808449232050578852431361678745355776921132352419931907838205001184`
- 利用网站解密 [https://tuppers-formula.ovh/](https://tuppers-formula.ovh/)
- [x] begin{T4UUPER!}

### devil's word
* 温州话!
```
1   
2  lia
3  sa
4  sii
5  ng
6  leu
7  cai
8  bo
9  jau
0  leng`
```
- 得到hex编码`626567696e7b7930755f6b6e30775f77336e7a686f755f6469346c6563747d`
- [x] begin{y0u_kn0w_w3nzhou_di4lect}
### cccc
- Null

### 下一站上岸
- 010查看文件末尾得到`5o+Q56S6OuaRqeaWr+WvhueggQ==`
- base一下得到提示:摩斯密码
- 交点个数`012`分别对应`<空格>.-`
- 221022201122120220111011110222012101
- [x] begin{go_shore}

### where is crazyman v1.0
- begin{秋叶原}
### where is crazyman v2.0
- [ ] begin{Tokyo Disneysea}
- [ ] begin{Tokyo Disneyland}
- [ ] begin{Shanghai Disneyland}
- [x] begin{Boulevard World}
### where is crazyman v3.0
- Boudl Apart Hotels
- Boudl Al Sahafa Hotel
- 没找出来

### 中国文化
- 先base32解密再八卦解密得到社会主义核心价值观编码
- base32中间有些数据丢失了，需要手工恢复
- bce-7bee8e3d808fcged-2ef94f}i{a7-18-12n81ce
- 栅栏密码
- [x] begin{eec8da87-ee32-11ed-8f8c-907841e2ffbc}


## Reverse
### xor
- upx脱壳
- 耐心分析逆向xor过程
- flag{Virus_gonna_be_terminated!}
- [x] begin{Virus_gonna_be_terminated!}

###  superguess
- 动态调试？

### baby xor
???+ abstract "baby_xor"

    === "Python"

        ```py linenums="1"
        secert = [7, 31, 56, 25, 23, 15, 91, 21, 49, 15, 33, 88, 26, 48, 60, 58, 4, 86, 36, 64, 23, 54, 63, 0, 54, 22, 6, 55, 59, 38, 108, 39, 45, 23, 102, 27, 11, 56, 32, 0, 82, 24]

        s = "ez_python_xor_reverse"
        flag = ""
        for i in range(42):
            flag += chr(secert[i]^ord(s[i%21]))

        print(flag)
        ```
- [x] begin{3z_PY7hoN_r3V3rSE_For_TH3_Be9inNEr!}


### 俄语学习
???+ abstract "俄语学习"

    === "Python"

        ```py linenums="1"
        s5 = [0xA7, 0xDF, 0xA7, 0xD6, 0xA7, 0xE9, 0xA7, 0xD6, 0xA7, 0xD4,
              0xA7, 0xE0, 0xA7, 0xDF, 0xA7, 0xD6, 0xA7, 0xE9, 0xA7, 0xD6,
              0xA7, 0xD4, 0xA7, 0xE0, 0xA7, 0xDF, 0xA7, 0xD6, 0xA7, 0xE9,
              0xA7, 0xD6, 0xA7, 0xD4, 0xA7, 0xE0, 0x00]

        print(hex(len(s5)))

        s4 = []
        for i in range(len(s5)):
            s4.append(s5[i]-114)

        print(s4)
        s3 = s4

        # s2 = SS + s3 - 112
        s1 = "+i&[@Y:g8[&l$f8S8v$Y&e>{"
        print(len(s1))
        s2 = s1
        flag = ""
        for i in range(24):
            flag += chr(ord(s2[i])+112-s3[i])
        print(flag)
        ```
- [x] flag{Russian_is_so_easy}

### 红白机
- [在线运行](https://codediy.github.io/nes-zh/easy6502/index.html)
- flag{6502_I_LOVE_u}
- [x] begin{6502_I_LOVE_u}

### 真龙之力
- jadx打开，两段加密，找不到key（说在lib库里）
```
utivnlgebet{liNe
a }lf o_ei i fc 

utivnlgebet{liNe
begin{veuetlltNi

ueginiN{bevllett
aioff}cie_l     

begin{Nlittleuve

begin{Neuvillett
e_official}     
```
- 猜测flag
- [x] begin{Neuvillette_official}

### ezpython
- 打包工具: PyInstaller
- PyInstaller Extractor
- uncompyle6
- 魔改的SM4加密

### arc
- python混淆

## Crypto
### fake_n
- python爆破p和q
???+ abstract "fake_n"

    === "Python"

        ```py linenums="1"
        import libnum
        from Crypto.Util.number import *

        li = [2215221821, 2290486867, 2333428577, 2361589081, 2446301969, 2507934301, 2590663067, 3107210929, 3278987191, 3389689241, 3417707929, 3429664037, 3716624207, 3859354699, 3965529989, 4098704749, 4267348123]
        e= 65537
        c= 6451324417011540096371899193595274967584961629958072589442231753539333785715373417620914700292158431998640787575661170945478654203892533418902
        # 3389689241 3859354699
        faken = 178981104694777551556050210788105224912858808489844293395656882292972328450647023459180992923023126555636398409062602947287270007964052060975137318172446309766581
        for i in range(len(li)):
            for j in range(i+1,len(li)):
                com = li[i]*li[j]
                print(li[i],li[j])
                n = faken//com

                phi_n = 1
                for k in range(len(li)):
                    if k != i and k != j:
                        # print(li[k])
                        phi_n = phi_n*(li[k]-1)
                d = libnum.invmod(e, phi_n)
                m = pow(c, d, n)
                # print(m)
                flag = long2str(m)
                print(flag)
        ```
- 分别为3389689241 3859354699


- begin{y0u_f1nd_th3_re4l_n}
### OEIS2
- 被9整除
- https://oeis.org/A244060

## Web
### zupload
- 直接读flag文件
- http://101.32.220.189:30635/?action=/flag
- [x] begin{jus7_r3aD_da6d2a4df700}
http://101.32.220.189:31609/?action=uploads/shell.zip

### zupload pro
- js前端认证，用F12控制台删除前端认证函数，下面题目也是一样
- shell.php
- [x] begin{Is_7h1s_a_We6sHEIl_0a3a490eb923}
### zupload-pro-plus
- 后缀名检查
- shell.zip.php
- [x]  begin{Str4NGE_5U1Fix_dd7c02498f7a}
### zupload-pro-plus-max
- http://101.32.220.189:32444/?action=uploads/test2.zip
- 压缩包附加一句话木马，文件包含漏洞
- [x] begin{3ViL_2lP_aa357893ca00}

### POPgadget
php反序列化

## 取证
### 逆向工程(reverse)入门指南 
- 全选`ctrl+a` `ctrl+c`
- [x] begin{0kay_1_thiNK_YoU_Ar3_a1Re@DY_rE4D_6uiDe8ooK_AnD_9OT_FL46}


### beginner_Forensics!!!!
- 混淆工具解密后
```
@echo off
echo catf1y:your flag is already deleted by me.
set find_me_pls = b@TcH_O8FU$c@T1on_15_e@SY_70_SO1vE
echo crazyman:no no no no no no !!!!! i need flag.
echo Attention:can you help crazyman to find the flag?
echo Attention:Submit the info you are looking for on begin{*}
```
- [x] begin{b@TcH_O8FU$c@T1on_15_e@SY_70_SO1vE}
### 学习取证
- vol的安装和使用
- 学习一下linux软链接`sudo ln -s /usr/local/lib/python2.7/dist-packages/usr/lib/libyara.so /usr/lib/libyara.so`
#### 历史命令
```
Cmd #0 @ 0x2445d0: echo flag{Cmd_1in3_109_i5_imp0rt@nt}
```

- [x] begin{Cmd_1in3_109_i5_imp0rt@nt}

#### 浏览器记录
- [x] begin{Y0v_c@n_g3t_th3_i3hi5t0ry}
#### 计算机名
```
Values:
REG_SZ                        : (S) mnmsrvc
REG_SZ        ComputerName    : (S) VVHATI5Y0VRNAM3
```

- [x] begin{VVHATI5Y0VRNAM3}
#### 用户口令爆破
```
Volatility Foundation Volatility Framework 2.6.1
Administrator:500:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
Guest:501:aad3b435b51404eeaad3b435b51404ee:31d6cfe0d16ae931b73c59d7e0c089c0:::
yuren:1000:aad3b435b51404eeaad3b435b51404ee:e1f04701b92c3bc1e06f3d0aa68471b3:::
```

- flag{Mimikatz_0r_j0hn}
- [x] begin{Mimikatz_0r_j0hn}

#### 敏感文件读取
- dump文件下来
```
\Device\HarddiskVolume1\Users\yuren\Desktop\机密文件.docx
0x000000001e742dd0
```

- flag{Y0v_c@n_d0vvn_th3_fi13}
- [x] begin{Y0v_c@n_d0vvn_th3_fi13}
#### 敏感程序逆向分析
- 一个文件`flag_is_here.exe`逆向过程
???+ abstract "枚举异或的值"

    === "Python"

        ```py linenums="1"
        s = [ 31,21,24,30,2,32,73,15,38,17,57,15,74,38,21,74,57,11,23,
              74,29,38,17,73,15,15,38,13,73,38,31,73,11,74,23,76,
              16,26,76,4]
        print(len(s))

        for k in range(128):
            flag = ""
            for i in range(len(s)):
                flag += chr(s[i]^k)

            print(k , ":",flag)
        # k = 121
        ```

- flag{Y0v_h@v3_l3@rn3d_h0vv_t0_f0r3n5ic5}
- [x] begin{Y0v_h@v3_l3@rn3d_h0vv_t0_f0r3n5ic5}