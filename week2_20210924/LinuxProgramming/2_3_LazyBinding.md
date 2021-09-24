# LazyBinding.md
- [Lazy binding](https://rafaelchen.wordpress.com/2017/09/25/pwn%E7%9A%84%E4%BF%AE%E7%85%89%E4%B9%8B%E8%B7%AF-lazy-binding/)
- [PIC GOT PLT OMG: how does the procedure linkage table work in linux?(2020)](https://www.youtube.com/watch?v=Ss2e6JauS0Y)
- [NTHU 廖子慶(DuckLL)的演講](https://slide.duckll.tw/2018/hitcon/#/)


- Linux 的 ELF 使用了 lazy binding 的方式來處理 dynamic linking
- 如果一個函式未被使用到，則它就不會被 binding
- 函式第一次被使用時再做 binding
- dynamic linking 比較慢，原因有二，一是它透過 GOT 做間接跳轉的動作。二是它在 run-time 時必需做符號搜尋及位址重定的動作。

- GOT == Global Offset Table
- 位於資料(.data)之前
- 區段為可讀,可寫(r,w)(default RELRO)
- 是一個 function pointer array
- GOT中涵蓋幾個部分。
- 前三個有特殊用途
  - got[0] = address of .dynamic
  - got[1] = link_map
  - got[2] = dl_runtime_resolve
  - .got 儲存全域變數的位置
  - .got.plt，儲存其他library中函式的位置。[拿到函式位置的關鍵]
    - address of .dynamic：他會存取原來GOT中.dynamic的位置
    - link_map：將會用到的library用linked_list串起來
    - dl_runtime_resolve：找出函式位置
Gobal Offset Table


每個外部 function 都有一個對應的 GOT
預設儲存 plt+6 的位置(填入 GOT 並執行)
存放 function 在 libc 的位置

- 實作方面: ELF 使用 procedure linkage table(PLT)
- 呼叫外部函式時不使用 GOT 跳轉，而是使用 PLT 跳轉。
- 呼叫函式時就等於呼叫 PLT 中某一項位址所指向的函式。
- 每個外部 function 都有一個對應的 plt
- 每個 plt 都有兩個功能
  - 跳到 GOT 的值 (plt['puts'])
  - 填入 GOT 的值並執行 (plt['puts']+6)

- Lazy-binding幫我們省了很多時間和成本，但這個機制需要GOT能夠被寫入的權限
- 存在GOT HIJACKING的攻擊 
  - [NTHU 廖子慶(DuckLL)的演講](https://slide.duckll.tw/2018/hitcon/#/)
- RELRO保護機制[GOT 守門員] ==>Full RELRO 可以抵擋 GOT Hijacking


PLT
Procedure Linkage Table
位於主程式(.text)之前
區段為可讀,可執行(r,x)
第一個 plt 是 call dl_runtime_resolve
每個外部 function 都有一個對應的 plt


```
.got
This is the GOT, or Global Offset Table. This is the actual table of offsets as filled in by the linker for external symbols.

.plt
This is the PLT, or Procedure Linkage Table. These are stubs that look up the addresses in the .got.plt section, and either jump to the right address, or trigger the code in the linker to look up the address. (If the address has not been filled in to .got.plt yet.)

.got.plt
This is the GOT for the PLT. It contains the target addresses (after they have been looked up) or an address back in the .plt to trigger the lookup. Classically, this data was part of the .got section.

.plt.got
It seems like they wanted every combination of PLT and GOT! 
This just seems to contain code to jump to the first entry of the .got. I’m not actually sure what uses this. 
(If you know, please reach out and let me know! In testing a couple of programs, this code is not hit, but maybe there’s some obscure case for this.)
```
## 範例說明

- [實作參考資料Pwn the GOT!](https://blog.fxiao.me/got-plt/)

```c
//test.c
#include <stdio.h>
int main(){
    printf("1234");   
    printf("5678");
    return 0;
}
```
## 
```linux
gcc -o test test.c -g

objdump -S -j .text -M intel test --no-show-raw-insn
```

```
0000000000001135 <main>:
#include <stdio.h>
int main(){
    1135:	push   rbp
    1136:	mov    rbp,rsp
    printf("1234");   
    1139:	lea    rdi,[rip+0xec4]        # 2004 <_IO_stdin_used+0x4>
    1140:	mov    eax,0x0
    1145:	call   1030 <printf@plt>    
    printf("5678");
    114a:	lea    rdi,[rip+0xeb8]        # 2009 <_IO_stdin_used+0x9>
    1151:	mov    eax,0x0
    1156:	call   1030 <printf@plt>
    return 0;
    115b:	mov    eax,0x0
}
    1160:	pop    rbp
    1161:	ret    
    1162:	nop    WORD PTR cs:[rax+rax*1+0x0]
    116c:	nop    DWORD PTR [rax+0x0]

```
## 使用GBD檢視GOT PLT
```
gdb-peda test
  
gdb-peda$ b main
Breakpoint 1 at 0x1139: file test.c, line 3.

```
## 使用GBD檢視GOT PLT
- []()
```c
#include <unistd.h>
#include <stdio.h>
 
int main()
   {
     char * args[] = {"/bin/ls", NULL};
     printf("pid: %d\n", getpid());
     
     //sleep(60);
```
