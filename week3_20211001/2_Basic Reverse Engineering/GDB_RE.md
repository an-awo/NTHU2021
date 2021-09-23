# GDB
- [GDB簡介](#GDB簡介)
- [gdb-gef](#gdb-gef)
- [gdb-peda](#gdb-peda)
- [常用指令](#常用指令)
- [示範解題](#示範解題)
- [學習資源](#學習資源)
## 簡介

## gdb-gef
- [GEF - GDB Enhanced Features](https://gef.readthedocs.io/en/master/)
- GEF is a set of commands for X86, ARM, MIPS, PowerPC and SPARC to make GDB cool again for exploit dev. 
- aimed to be used mostly by exploit developers and reverse-engineers, to provide additional features to GDB using the Python API to assist during the process of dynamic analysis and exploit development.
- full support for both Python2 and Python3 indifferently (as more and more distros start pushing gdb compiled with Python3 support).
- [文件](https://gef.readthedocs.io/en/master/)

## [安裝](https://gef.readthedocs.io/en/master/config/)
```
$ git clone https://github.com/hugsy/gef.git  # or git pull to update
$ echo 'source /path/to/gef.py' >> ~/.gdbinit
```

## ![#1589F0](https://via.placeholder.com/15/1589F0/000000?text=+)`範例練習`

```gdb
$ gdb ./a.out

gef➤  gef help

gef➤  run  ==> 會開啟漂亮視窗
```

vmmap -- Display a comprehensive layout of the virtual memory mapping. If a filter argument, GEF will
                             filter out the mapping whose pathname do not match that filter.


```
# 64-bit 程式
gef➤  registers
$rax   : 0x0               
$rbx   : 0x0               
$rcx   : 0x0               
$rdx   : 0x00007fffffffe2b8  →  0x00007fffffffe597  →  "SHELL=/bin/bash"
$rsp   : 0x00007fffffffe168  →  0x00007ffff7e5f600  →  <puts+16> mov r13, QWORD PTR [rip+0x147941]        # 0x7ffff7fa6f48
$rbp   : 0x00007fffffffe1b0  →  0x0000555555555190  →  <__libc_csu_init+0> push r15
$rsi   : 0x00007fffffffe2a8  →  0x00007fffffffe58d  →  "/root/fmt"
$rdi   : 0x0               
$rip   : 0x00007ffff7e86846  →   movdqu xmm4, XMMWORD PTR [rax]
$r8    : 0x0               
$r9    : 0x00007ffff7fe21b0  →   push rbp
$r10   : 0xfffffffffffff28b
$r11   : 0x00007ffff7e5f5f0  →  <puts+0> push r14
$r12   : 0x0               
$r13   : 0x0               
$r14   : 0x0               
$r15   : 0x0               
$eflags: [zero CARRY parity ADJUST SIGN trap INTERRUPT direction overflow RESUME virtualx86 identification]
$cs: 0x0033 $ss: 0x002b $ds: 0x0000 $es: 0x0000 $fs: 0x0000 $gs: 0x0000 
```
```
# 32-bit 程式
gef➤  registers
$eax   : 0x0       
$ebx   : 0x0804c000  →  0x0804bf14  →  0x00000001
$ecx   : 0xffffd360  →  0x00000001
$edx   : 0x0       
$esp   : 0xffffd2ec  →  0xf7e3543f  →  <puts+31> add esp, 0x10
$ebp   : 0xffffd328  →  0xffffd348  →  0x00000000
$esi   : 0xf7faa000  →  0x001e4d6c
$edi   : 0xf7faa000  →  0x001e4d6c
$eip   : 0xf7e683a1  →   mov ecx, DWORD PTR [eax]
$eflags: [ZERO carry PARITY adjust sign trap INTERRUPT direction overflow RESUME virtualx86 identification]
$cs: 0x0023 $ss: 0x002b $ds: 0x002b $es: 0x002b $fs: 0x0000 $gs: 0x0063 
```
## [gdb-peda]
- PEDA is a Python GDB script with many handy commands to help speed up exploit development process on Linux/Unix. 
- PEDA is also a framework for writing custom interactive Python GDB commands.
- [PEDA - Python Exploit Development Assistance for GDB]()

### 安裝peda
```
git clone https://github.com/longld/peda.git ~/peda
echo "source ~/peda/peda.py" >> ~/.gdbinit
```
### Usage
    - List of available commands:
        gdb-peda$ peda help

    - Search for some commands:
        gdb-peda$ apropos <keyword>
        gdb-peda$ help <keyword>

    - Get usage manual of specific command:
        gdb-peda$ phelp <command>
        gdb-peda$ help <command>

    - Get/set config option:
        gdb-peda$ pshow option
        gdb-peda$ pset option <name> <value>
### Key Features:[資料來源:github網址](https://github.com/longld/peda)
- Enhance the display of gdb: colorize and display disassembly codes, registers, memory information during debugging.
- Add commands to support debugging and exploit development (for a full list of commands use peda help):
  - aslr -- Show/set ASLR setting of GDB
  - checksec -- Check for various security options of binary
  - dumpargs -- Display arguments passed to a function when stopped at a call instruction
  - dumprop -- Dump all ROP gadgets in specific memory range
  - elfheader -- Get headers information from debugged ELF file
  - elfsymbol -- Get non-debugging symbol information from an ELF file
  - lookup -- Search for all addresses/references to addresses which belong to a memory range
  - patch -- Patch memory start at an address with string/hexstring/int
  - pattern -- Generate, search, or write a cyclic pattern to memory
  - procinfo -- Display various info from /proc/pid/
  - pshow -- Show various PEDA options and other settings
  - pset -- Set various PEDA options and other settings
  - readelf -- Get headers information from an ELF file
  - ropgadget -- Get common ROP gadgets of binary or library
  - ropsearch -- Search for ROP gadgets in memory
  - searchmem|find -- Search for a pattern in memory; support regex search
  - shellcode -- Generate or download common shellcodes.
  - skeleton -- Generate python exploit code template
  - vmmap -- Get virtual mapping address ranges of section(s) in debugged process
  - xormem -- XOR a memory region with a key

## 常用指令
## 示範解題
## 學習資源
