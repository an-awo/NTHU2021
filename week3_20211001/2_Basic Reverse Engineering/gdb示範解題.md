## 示範解題

- [[教科書Practical Binary Analysis: Build Your Own Linux Tools for Binary Instrumentation, Analysis, and Disassembly,Dennis Andriesse]](https://www.tenlong.com.tw/products/9781593279127) [[Github]](https://github.com/wilvk/practical-binary) [[官方網站:下載ova及code]](https://practicalbinaryanalysis.com/)
- Chpater 5.BASIC BINARY ANALYSIS IN LINUX  有趣

```
5.1 Resolving Identity Crises Using file
  
   file payload
   head payload
   base64 -d payload > decoded_payload
   file decoded_payload
   file -z decoded_payload
  
  tar xvzf decoded_payload
  ==>ctf
    67b8601

  file ctf
  file 67b8601

5.2 Using ldd to Explore Dependencies
  

   chmod +x ctf
   ./ctf ==> error
   ldd ctf
   grep 'ELF' *
  
5.3 Viewing File Contents with xxd 
  
  xxd 67b8601 | head -n 15
  dd skip=52 count=64 if=67b8601 of=elf_header bs=1
  xxd elf_header
  
5.4 Parsing the Extracted ELF with readelf
  
  readelf -h elf_header
  
  dd skip=52 count=10296 if=67b8601 of=lib5ae9b7f.so bs=1
  
  readelf -hs lib5ae9b7f.so
  
5.5 Parsing Symbols with nm 
  
  nm lib5ae9b7f.so
  
  nm -D lib5ae9b7f.so
  
  nm -D --demangle lib5ae9b7f.so
  
  export LD_LIBRARY_PATH=`pwd`
  ./ctf
  $ echo $?

  
5.6 Looking for Hints with strings 
  
  strings ctf
  ./ctf foobar
  ./ctf show_me_the_flag

5.7 Tracing System Calls and Library Calls with strace and ltrace
  
  strace ./ctf show_me_the_flag
  
  ltrace -i -C ./ctf show_me_the_flag
  
  GUESSME='foobar' ./ctf show_me_the_flag
  
  GUESSME='foobar' ltrace -i -C ./ctf show_me_the_flag

5.8 Examining Instruction-Level Behavior Using objdump 

  objdump -s --section .rodata ctf
  
  objdump -d ctf
  
5.9 Dumping a Dynamic String Buffer Using gdb
  
  gdb ./ctf
  
 (gdb) b *0x400dc8
 (gdb) set env GUESSME=foobar
 (gdb) run show_me_the_flag
 (gdb) display/i $pc
 (gdb) info registers rcx
 (gdb) info registers rax
 (gdb) x/s 0x615050
 (gdb) quit
  
  GUESSME="Crackers Don't Matter" ./ctf show_me_the_flag
  
  最後的flag 為何?
```

## 參考資料
## File magic 與 file signature
  
- [[WIKI]List of file signatures](https://en.wikipedia.org/wiki/List_of_file_signatures)  

## [Steganography](https://en.wikipedia.org/wiki/Steganography)  [[隱寫術]](https://zh.wikipedia.org/zh-hant/%E9%9A%90%E5%86%99%E6%9C%AF)

- [Steganography](https://wiki.bi0s.in/steganography/)
  - 有一些工具介紹與說明
  - audio steganalysis ==> [Audacity](https://wiki.bi0s.in/steganography/) 
- [隱寫術實作： 把小檔案藏在圖檔或文字檔裡](https://newtoypia.blogspot.com/2017/04/steganography.html)
  - cat cover.jpg secret.zip > steg.jpg
    - cover file == 用來掩護內嵌檔的 「載具」 == cover.jpg 
    - 需要隱藏/內嵌 (embed) 的機密檔 == secret.zip 
    - stegofile == 打包完的 steg.jpg 
  - 用看圖軟體去開 steg.jpg 看起來就是一張普通的圖片
  - 但用 unzip 指令去開 steg.jpg 則會將 secret.zip 的內容解出來。
  - 工具有許多: [stegsnow](http://manpages.ubuntu.com/manpages/bionic/man1/stegsnow.1.html)

- [圖像隱碼術(Steganography)與惡意程式：原理和方法 (2015, Trend Labs 趨勢科技全球技術支援與研發中心)](https://blog.trendmicro.com.tw/?cat=2123)
- [Daserf 間諜集團以「心肺復甦術」、「防災計畫」主旨信件及日文加圖像隱碼術,騙倒日本企業(2017,Trend Labs 趨勢科技全球技術支援與研發中心])](https://blog.trendmicro.com.tw/?cat=2123)
- [Python圖片隱寫術] (https://hackmd.io/@NIghTcAt/ByKr8jxGH)
- [REVIEW: Image Steganography: A Review of the Recent Advances(2021)](https://ieeexplore.ieee.org/document/9335027)

## LD_LIBRARY_PATH環境變數
- [LD_LIBRARY_PATH環境變數的設定](https://www.itread01.com/content/1549007643.html) 
- [How to set $LD_LIBRARY_PATH in Ubuntu?](https://serverfault.com/questions/201709/how-to-set-ld-library-path-in-ubuntu)
