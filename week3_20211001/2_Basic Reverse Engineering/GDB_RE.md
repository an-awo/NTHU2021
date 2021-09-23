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

### [Key Features](https://gef.readthedocs.io/en/master/)
- One single GDB script
- Entirely OS Agnostic, NO dependencies: GEF is battery-included and is installable instantly
- Fast limiting the number of dependencies and optimizing code to make the commands as fast as possible
- Provides a great variety of commands to drastically change your experience in GDB.
- Easily extensible to create other commands by providing more comprehensible layout to GDB Python API.
- Full Python3 support (Python2 support was dropped - see gef-legacy).
- Built around an architecture abstraction layer, so all commands work in any GDB-supported architecture such as x86-32/64, ARMv5/6/7,AARCH64, SPARC, MIPS, PowerPC, etc.
-Suited for real-life apps debugging, exploit development, just as much as CTF

## [安裝](https://gef.readthedocs.io/en/master/config/)
```
$ git clone https://github.com/hugsy/gef.git  # or git pull to update
$ echo 'source /path/to/gef.py' >> ~/.gdbinit
```

### ![#1589F0](https://via.placeholder.com/15/1589F0/000000?text=+)`常用指令`

```gdb
$ gdb-gef ./a.out ==> 需要設定
gef➤ gef help
gef➤ run  ==> 會開啟漂亮視窗
```
- [gef➤ checksec](https://gef.readthedocs.io/en/master/commands/checksec/)
- [gef➤ elf](https://gef.readthedocs.io/en/master/commands/elf-info/)
gef➤ vmmap -- Display a comprehensive layout of the virtual memory mapping. 
gef➤ registers

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
