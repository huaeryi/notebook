# Midnight Sun CTF

???+ abstract

    将于赛后收录和复现Midnight Sun CTF中的一些题

    ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
    ![](https://img.shields.io/badge/-Crypto-red?style=flat-square)
    ![](https://img.shields.io/badge/-Web-blueviolet?style=flat-square)
    ![](https://img.shields.io/badge/-Reverse-violet?style=flat-square)
    ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)
    ![](https://img.shields.io/badge/-AI-brown?style=flat-square)
 
    * 本note更新时间在赛后
    * 🚧施工中>>>

### speeda ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)
- one_gadget


### speedb ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)


### speedc ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)

### speedd ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)

### speede ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)

### roborop ![](https://img.shields.io/badge/-Pwn-grey?style=flat-square)

### minus10 ![](https://img.shields.io/badge/-Reverse-violet?style=flat-square)
- gcc-msp430-4.6.3
- MSP430系列单片机是美国德州仪器（TI）1996年开始推向市场的一种16位超低功耗、具有精简指令集（RISC）的混合信号处理器（Mixed Signal Processor）。
- .sr文件

???+ abstract "exp"

    === "Python"

        ``` python linenums="1"
        s = [0xbf, 0xbe, 0xb8, 0x8f, 0x8f, 0x8c, 0x98, 0x81, 0x81, 0x88, 0x65, 0x7b, 0x63, 0x76, 0x7c, 0x42, 0x57, 0x57, 0x73, 0x5e, 0x58, 0x64, 0x0d, 0x16, 0x1a, 0x7b, 0x67, 0x69, 0x23]
        for i in range(len(s)):
            s[i] = (s[i] ^ (i * 5 - 0x2e)) % 256
        flag = ''.join(chr(i) for i in s)
        print(flag)
        ```
- [ ] midnight{warmed_up_on_MSP430}
### rockyoudle ![](https://img.shields.io/badge/-Misc-informational?style=flat-square)
- wordle带字典
