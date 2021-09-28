# 助教示範解題


# Midterm
- 同學可以羅列你解的reverse CTF題目
- 請清單列表,並依主題分類
- 將你所完成的解答列在你的GITHUB上
- 誠信是最重要的人品,請勿抄襲同學的解答
- 參考到別人的writeup 須註明出處(也請強調自己的發現)
- 老師上課的及助教示範的不能列入解題列表(除非有新的解法)

- [HITCON in DEFCON 22 CTF Final 紀錄片(2014)](https://www.youtube.com/watch?v=XcneHvq1hbY)
- [CTF 的三十道陰影:哪個年代大大走過的路](https://ithelp.ithome.com.tw/users/20121059/ironman/2810)


## 參考列表[不必每一類型都有解過,底下只是列表供你參考用]

- 底下範例若有誤植與錯誤,請自行更正

- 基礎題 (5題)
  - picoCTF 2021 | Reverse Engineering | speeds and feeds [[解答1]](https://www.youtube.com/watch?v=_Q2Trkp8F8w)
  - [Angstrom CTF 2021 - Reverse Engineering Challenge Walkthroughs](https://www.youtube.com/watch?v=MhkVkOpj5OI)
- 使用angr或z3解題(3題)
  -  Google-ctf-2020/reversing/beginner
[[題目]](https://github.com/luker983/google-ctf-2020/tree/master/reversing/beginner)
[[解法1]](https://github.com/luker983/google-ctf-2020/tree/master/reversing/beginner)
[[解法2(youtube)(angr)]](https://www.youtube.com/watch?v=RCgEIBfnTEI&t=1641s)
[[解法3]](https://github.com/Dvd848/CTFs/blob/master/2020_GoogleCTF/Beginner.md)

- python/Java/ruby/go程式逆向題(3題)
  - python pyc
    - [CTF简单Reverse题目解法和pyc文件逆向](https://blog.fullstackpentest.com/a-pyc-reverse-writeup.html)  
    - [【CTF工具】 uncompyle6快速反编译pyc](https://www.bilibili.com/s/video/BV1Q64y1z7dh)
  - Android app逆向題
    - [ Google Capture The Flag 2021|tridroid題目](https://ctftime.org/task/16572)
  - Haskill
    - hxp CTF 2017 /wreckme  [[題目]]()  [[參考解答]](https://ctftime.org/writeup/8112)  
- 其他平台(ARM,MIPS,...)程式逆向題(1題)
  - ARM 
    - [PicoCTF2021](https://github.com/HHousen/PicoCTF-2021/tree/master/Reverse%20Engineering)
    - PicoCTF-2021|Reverse Engineering|ARMssembly 0-4
    - [ARM Instruction Set Tutorial](https://azeria-labs.com/arm-instruction-set-part-3/)
    - [Arm Architecture Reference Manual](https://developer.arm.com/documentation/ddi0487/latest) 
    - [Running ARMv8 via Linux Command Line](https://github.com/joebobmiles/ARMv8ViaLinuxCommandline)
```
sudo apt install binutils-aarch64-linux-gnu

$ aarch64-linux-gnu-as -o a.o [the name of your source file]
$ aarch64-linux-gnu-gcc -static -o [the name of the executable] a.o
```
    - QEMU to Emulate ARM: sudo apt install qemu-user-static

- 代碼混淆/packing/Anti-analysis題(1題)
  - CSAW CTF Qualification Round 2020/not_malware
    - [[ 題目]](https://github.com/acdwas/ctf/tree/master/2020/CSAW/rev/not_malware)
    - [[anti-debugging technique using ptrace範例解答pstrace/strace ]](https://ctftime.org/writeup/23357)
    - [[很好的writeup]](https://github.com/Ragnar-Security/ctf-writeups/tree/master/csaw-2020/not_malware)- 
  - JavaScript
    - [JavaScript Obfuscator Tool](https://obfuscator.io/)

- 艱難題(1題) ==> 你覺得花妳很多時間+氣力才搞懂如何解
  -  Google Capture The Flag 2020 /reversing/ sprint [[題目]](https://ctftime.org/task/12834) [[參考解答1]](https://ctftime.org/writeup/23412)
