# Linux Tools for Binary Analysis

### Linux 工具集
- file 
- size 列出目的模組或檔案大小
- [strings](https://linux.die.net/man/1/strings)
- hexdump | hd

### 資訊分析工具

- [Ldd(List Dynamic Dependencies，列出動態庫依賴關係)](https://man7.org/linux/man-pages/man1/ldd.1.html)
  - root@kali:/usr/bin# ldd xxd 
- [nm - list symbols from object files](https://linux.die.net/man/1/nm)
- objdump
- [readelf](https://sourceware.org/binutils/docs-2.32/binutils/readelf.html#readelf)

### 部署階段工具
```
chrpath ==  change the rpath or runpath in binaries
patchelf == PatchELF is a simple utility for modifying existing ELF executables and libraries
strip  ==> 刪除目的檔案中的全部或者特定符號，可以減小可執行檔的大小。
ldconfig
```
### 運行時分析工具

- ltrace 命令(A library call tracer)==>顯示運行時從函數庫中調用的所有函數
  - [指令參數](https://man7.org/linux/man-pages/man1/ltrace.1.html)
- strace 工具==>不是追蹤呼叫的函數庫，而是追蹤系統呼叫。系統呼叫是你與內核對接來完成工作的。
  - [10 Strace Commands for Troubleshooting and Debugging Linux Processes](https://www.tecmint.com/strace-commands-for-troubleshooting-and-debugging-linux/) 
- GNU Debugger (GDB)
- addr2line

### 其他
- objcopy
- data duplicator (dd)
- [Evan's Debugger (EDB)](https://github.com/eteran/edb-debugger)
- [Cutter: Free and Open Source RE Platform powered by Rizin](https://cutter.re/)


## 實作練習:

## socat 與 nc
### server端Terminal
```
# server.py

import sys

def print_flag(): 
	flag_hex = [111,104,101,114,96,108,125,103,106,106,89,114,110,99,117,
	99,89,107,105,107,99,104,114,117,89,106,105,117,114,89,111,104,89,114,111,107,99,123]
	i = 0
	while ( i < 38):
		sys.stdout.write(chr(flag_hex[i] ^ 6))
		i += 1

input = input('why did you save me? ')
#input = raw_input('why did you save me? ')

if input == 'to_say_something':
	print_flag()
```
```
socat TCP-LISTEN:20000,fork EXEC:'python3 ./server.py'
```
### Clinet 端terminal
```
nc 127.0.0.1 20000
why did you save me? to_say_something
inctfj{XXXXXXXXXXXXXXXXXXXXXX}r
```
## 實作練習 strace

- [[The strace Command in Linux]](https://www.baeldung.com/linux/strace-command)
- [Kali linux:installation] apt-get install -y strace
- help ==>strace -h
- CTF : CSIE_strace
  - chmod 777 strace
  - strace ./strace
  - strace -s 1000 ./strace 



## `[實作練習|pratice|s'entraîner|üben|관행|práctica]`
- [Advanced C and C++ Compiling  Milan Stevanovic/Apress 高級C/C++編譯技術(2014)](https://www.books.com.tw/products/CN11244082)
  - ch13.Linux Toolbox 

### 實作練習導讀
- 連結過程調試 Debugging the Linking
  - LD_DEBUG=help cat

- 確定二進位檔案類型(Determining the Binary File Type)
  - file
  - readelf -h XXXXbinary | grep Type
     - EXEC (executable file) | DYN (shared object file) | REL (relocatable file)
  - objdump -f XXXXbinary
     - EXEC_P (executable file) | DYNAMIC (shared object file)
     
- 確定二進位檔案入口點(Determining the Binary File Entry Point)
  - 獲取可執行檔入口點(Determining the Binary File Entry Point)
    - readelf -h XXXXbinary | grep Entry
    - objdump -f XXXXbinary | grep start
  - 獲取動態庫入口點 Determining the Dynamic Library Entry Point

- 列出符號資訊List Symbols
  - nm
  - readelf --symbols XXXXbinary
  - readelf --dyn-syms XXXXbinary
  - objdump -t XXXXbinary
  - objdump -T XXXXbinary
  
- 查看節的信息List and Examine Sections
  - 列出所有節的資訊Listing the Available Sections
    - readelf -S XXXXbinary
    - objdump -t XXXXbinary
  - 查看節的信息Examining Specific Sections
    - Examining the Dynamic Section
      - readelf -d XXXXbinary
      - objdump -p XXXXbinary
    - Determining Whether Dynamic Library is PIC or LTR
    - Examining the Relocation Section
    - Examining the Data Section
    
 - 查看段的信息List and Examine Segments
   - readelf --segments XXXXbinary
   - objdump -p XXXXbinary
   
 - 反彙編代碼Disassembling the Code
   - 反彙編二進位檔案Disassembling the Binary File
   - 反彙編正在運行的進程Disassembling the Running Process

- 判斷是否為調試構建Identifying the Debug Build
- 查看載入時依賴項Listing Load-time Dependencies
- 查看裝載器可以找到的庫檔Listing the Libraries Known to the Loader
- 查看運行時動態連結的庫檔Listing Dynamically Linked Libraries
  - strace實用程式
  - LD_DEBUG環境變數
  - /proc/<ID>/maps文件
  - lsof實用程式
  - 通過程式設計方式查看Programmatic Way
- 創建和維護靜態程式庫Creating and Maintaining the Static Library

## LD_DEBUG=help cat
```
Valid options for the LD_DEBUG environment variable are:

  libs        display library search paths
  reloc       display relocation processing
  files       display progress for input file
  symbols     display symbol table processing
  bindings    display information about symbol binding
  versions    display version dependencies
  scopes      display scope information
  all         all previous options combined
  statistics  display relocation statistics
  unused      determined unused DSOs
  help        display this help message and exit

To direct the debugging output into a file instead of standard output
a filename can be specified using the LD_DEBUG_OUTPUT environment variable.
```
## 網路資源 : 可視時間增加自己的工具庫
- [10 ways to analyze binary files on Linux](https://opensource.com/article/20/4/linux-binary-analysis)
- [在 Linux 上分析二進位檔案的 10 種方法](https://linux.cn/article-12187-1.html)
- [[Binary analysis tools]](https://linuxsecurity.expert/security-tools/binary-analysis-tools)
- [[The Top 51 Binary Analysis Open Source Projects]](https://awesomeopensource.com/projects/binary-analysis)
- [Open-source Software Security Tools for Binary Analysis and Rewriting | GrammaTech(2019)](https://blogs.grammatech.com/open-source-tools-for-binary-analysis-and-rewriting)

## 教科書 Practical Binary Analysis
 - [[教科書Practical Binary Analysis: Build Your Own Linux Tools for Binary Instrumentation, Analysis, and Disassembly,Dennis Andriesse]](https://www.tenlong.com.tw/products/9781593279127) [[Github]](https://github.com/wilvk/practical-binary) [[官方網站:下載ova及code]](https://practicalbinaryanalysis.com/)
   - chapter 5: BASIC BINARY ANALYSIS IN LINUX
     - 5.1 Resolving Identity Crises Using file
     - 5.2 Using ldd to Explore Dependencies
     - 5.3 Viewing File Contents with xxd
     - 5.4 Parsing the Extracted ELF with readelf
     - 5.5 Parsing Symbols with nm
     - 5.6 Looking for Hints with strings
     - 5.7 Tracing System Calls and Library Calls with strace and ltrace
     - 5.8 Examining Instruction-Level Behavior Using objdump
     - 5.9 Dumping a Dynamic String Buffer Using gdb

# [Pharos Static Binary Analysis Framework](https://github.com/cmu-sei/pharos)
- The Pharos static binary analysis framework is a project of the Software Engineering Institute at Carnegie Mellon University.
- The framework is designed to facilitate the automated analysis of binary programs. 
- It uses the ROSE compiler infrastructure developed by Lawrence Livermore National Laboratory for disassembly, control flow analysis, instruction semantics, and more.
- This software is released under a BSD license.
- The current distribution is a substantial update to the previous version, and adds a variety of features including improvements to the OOAnalyzer tool, experimental path analysis code, partitioner improvements, multi-threading, and many other smaller features.

- [The Pharos Static Analysis Framework for Software Assurance](https://apps.dtic.mil/sti/pdfs/AD1084679.pdf)

	
## 使用docker
```
Pre-built Docker Images (Easiest)
The easiest way to get started with Pharos is to use our pre-built Docker images.

The first step is to download the image:

$ docker pull seipharos/pharos
	
To start an interactive session in which the host directory /dir is mapped to /dir inside your container, run the following command:

$ docker run --rm -it -v /dir:/dir seipharos/pharos

The pharos tools will be installed in /usr/local/bin.
```
## Toolsets

### OOAnalyzer Applications to Software Assurance
- OOAnalyzer can be used to:
  - Understand the design of object oriented software
  - Gain automated insight into OO library usage?
  - Compare design documents to observed OO constructs?
- Ooanalyzer –j <json output> <binary>
	
	
	
