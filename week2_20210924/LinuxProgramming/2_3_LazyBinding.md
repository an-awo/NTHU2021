# 2_3_LazyBinding.md


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
## relocation 重定位

- [Pwn the GOT!](https://blog.fxiao.me/got-plt/)

```c
//test.c
#include <stdio.h>
int main(){
    printf("1234");
    printf("5678");
    return 0;
}
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
