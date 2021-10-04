
    1000:	f3 0f 1e fa          	endbr64 
    1004:	48 83 ec 08          	sub    rsp,0x8
    1008:	48 8b 05 d9 2f 00 00 	mov    rax,QWORD PTR [rip+0x2fd9]        # 3fe8 <__gmon_start__>
    100f:	48 85 c0             	test   rax,rax
    1012:	74 02                	je     1016 <_init+0x16>
    1014:	ff d0                	call   rax
    1016:	48 83 c4 08          	add    rsp,0x8
    101a:	c3                   	ret    

.plt 區段的反組譯：

0000000000001020 <.plt>:
    1020:	ff 35 82 2f 00 00    	push   QWORD PTR [rip+0x2f82]        # 3fa8 <_GLOBAL_OFFSET_TABLE_+0x8>
    1026:	f2 ff 25 83 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f83]        # 3fb0 <_GLOBAL_OFFSET_TABLE_+0x10>
    102d:	0f 1f 00             	nop    DWORD PTR [rax]
    1030:	f3 0f 1e fa          	endbr64 
    1034:	68 00 00 00 00       	push   0x0
    1039:	f2 e9 e1 ff ff ff    	bnd jmp 1020 <.plt>
    103f:	90                   	nop
    1040:	f3 0f 1e fa          	endbr64 
    1044:	68 01 00 00 00       	push   0x1
    1049:	f2 e9 d1 ff ff ff    	bnd jmp 1020 <.plt>
    104f:	90                   	nop
    1050:	f3 0f 1e fa          	endbr64 
    1054:	68 02 00 00 00       	push   0x2
    1059:	f2 e9 c1 ff ff ff    	bnd jmp 1020 <.plt>
    105f:	90                   	nop
    1060:	f3 0f 1e fa          	endbr64 
    1064:	68 03 00 00 00       	push   0x3
    1069:	f2 e9 b1 ff ff ff    	bnd jmp 1020 <.plt>
    106f:	90                   	nop

.plt.got 區段的反組譯：

0000000000001070 <__cxa_finalize@plt>:
    1070:	f3 0f 1e fa          	endbr64 
    1074:	f2 ff 25 7d 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f7d]        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    107b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

.plt.sec 區段的反組譯：

0000000000001080 <puts@plt>:
    1080:	f3 0f 1e fa          	endbr64 
    1084:	f2 ff 25 2d 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f2d]        # 3fb8 <puts@GLIBC_2.2.5>
    108b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001090 <__stack_chk_fail@plt>:
    1090:	f3 0f 1e fa          	endbr64 
    1094:	f2 ff 25 25 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f25]        # 3fc0 <__stack_chk_fail@GLIBC_2.4>
    109b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

00000000000010a0 <printf@plt>:
    10a0:	f3 0f 1e fa          	endbr64 
    10a4:	f2 ff 25 1d 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f1d]        # 3fc8 <printf@GLIBC_2.2.5>
    10ab:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

00000000000010b0 <gets@plt>:
    10b0:	f3 0f 1e fa          	endbr64 
    10b4:	f2 ff 25 15 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f15]        # 3fd0 <gets@GLIBC_2.2.5>
    10bb:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

.text 區段的反組譯：

00000000000010c0 <_start>:
    10c0:	f3 0f 1e fa          	endbr64 
    10c4:	31 ed                	xor    ebp,ebp
    10c6:	49 89 d1             	mov    r9,rdx
    10c9:	5e                   	pop    rsi
    10ca:	48 89 e2             	mov    rdx,rsp
    10cd:	48 83 e4 f0          	and    rsp,0xfffffffffffffff0
    10d1:	50                   	push   rax
    10d2:	54                   	push   rsp
    10d3:	4c 8d 05 b6 01 00 00 	lea    r8,[rip+0x1b6]        # 1290 <__libc_csu_fini>
    10da:	48 8d 0d 3f 01 00 00 	lea    rcx,[rip+0x13f]        # 1220 <__libc_csu_init>
    10e1:	48 8d 3d c1 00 00 00 	lea    rdi,[rip+0xc1]        # 11a9 <main>
    10e8:	ff 15 f2 2e 00 00    	call   QWORD PTR [rip+0x2ef2]        # 3fe0 <__libc_start_main@GLIBC_2.2.5>
    10ee:	f4                   	hlt    
    10ef:	90                   	nop

00000000000010f0 <deregister_tm_clones>:
    10f0:	48 8d 3d 19 2f 00 00 	lea    rdi,[rip+0x2f19]        # 4010 <__TMC_END__>
    10f7:	48 8d 05 12 2f 00 00 	lea    rax,[rip+0x2f12]        # 4010 <__TMC_END__>
    10fe:	48 39 f8             	cmp    rax,rdi
    1101:	74 15                	je     1118 <deregister_tm_clones+0x28>
    1103:	48 8b 05 ce 2e 00 00 	mov    rax,QWORD PTR [rip+0x2ece]        # 3fd8 <_ITM_deregisterTMCloneTable>
    110a:	48 85 c0             	test   rax,rax
    110d:	74 09                	je     1118 <deregister_tm_clones+0x28>
    110f:	ff e0                	jmp    rax
    1111:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]
    1118:	c3                   	ret    
    1119:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

0000000000001120 <register_tm_clones>:
    1120:	48 8d 3d e9 2e 00 00 	lea    rdi,[rip+0x2ee9]        # 4010 <__TMC_END__>
    1127:	48 8d 35 e2 2e 00 00 	lea    rsi,[rip+0x2ee2]        # 4010 <__TMC_END__>
    112e:	48 29 fe             	sub    rsi,rdi
    1131:	48 89 f0             	mov    rax,rsi
    1134:	48 c1 ee 3f          	shr    rsi,0x3f
    1138:	48 c1 f8 03          	sar    rax,0x3
    113c:	48 01 c6             	add    rsi,rax
    113f:	48 d1 fe             	sar    rsi,1
    1142:	74 14                	je     1158 <register_tm_clones+0x38>
    1144:	48 8b 05 a5 2e 00 00 	mov    rax,QWORD PTR [rip+0x2ea5]        # 3ff0 <_ITM_registerTMCloneTable>
    114b:	48 85 c0             	test   rax,rax
    114e:	74 08                	je     1158 <register_tm_clones+0x38>
    1150:	ff e0                	jmp    rax
    1152:	66 0f 1f 44 00 00    	nop    WORD PTR [rax+rax*1+0x0]
    1158:	c3                   	ret    
    1159:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

0000000000001160 <__do_global_dtors_aux>:
    1160:	f3 0f 1e fa          	endbr64 
    1164:	80 3d a5 2e 00 00 00 	cmp    BYTE PTR [rip+0x2ea5],0x0        # 4010 <__TMC_END__>
    116b:	75 2b                	jne    1198 <__do_global_dtors_aux+0x38>
    116d:	55                   	push   rbp
    116e:	48 83 3d 82 2e 00 00 	cmp    QWORD PTR [rip+0x2e82],0x0        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1175:	00 
    1176:	48 89 e5             	mov    rbp,rsp
    1179:	74 0c                	je     1187 <__do_global_dtors_aux+0x27>
    117b:	48 8b 3d 86 2e 00 00 	mov    rdi,QWORD PTR [rip+0x2e86]        # 4008 <__dso_handle>
    1182:	e8 e9 fe ff ff       	call   1070 <__cxa_finalize@plt>
    1187:	e8 64 ff ff ff       	call   10f0 <deregister_tm_clones>
    118c:	c6 05 7d 2e 00 00 01 	mov    BYTE PTR [rip+0x2e7d],0x1        # 4010 <__TMC_END__>
    1193:	5d                   	pop    rbp
    1194:	c3                   	ret    
    1195:	0f 1f 00             	nop    DWORD PTR [rax]
    1198:	c3                   	ret    
    1199:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

00000000000011a0 <frame_dummy>:
    11a0:	f3 0f 1e fa          	endbr64 
    11a4:	e9 77 ff ff ff       	jmp    1120 <register_tm_clones>

00000000000011a9 <main>:
    11a9:	f3 0f 1e fa          	endbr64 
    11ad:	55                   	push   rbp
    11ae:	48 89 e5             	mov    rbp,rsp
    11b1:	48 83 ec 70          	sub    rsp,0x70
    11b5:	64 48 8b 04 25 28 00 	mov    rax,QWORD PTR fs:0x28
    11bc:	00 00 
    11be:	48 89 45 f8          	mov    QWORD PTR [rbp-0x8],rax
    11c2:	31 c0                	xor    eax,eax
    11c4:	48 8d 3d 39 0e 00 00 	lea    rdi,[rip+0xe39]        # 2004 <_IO_stdin_used+0x4>
    11cb:	b8 00 00 00 00       	mov    eax,0x0
    11d0:	e8 cb fe ff ff       	call   10a0 <printf@plt>
    11d5:	48 8d 45 90          	lea    rax,[rbp-0x70]
    11d9:	48 89 c7             	mov    rdi,rax
    11dc:	b8 00 00 00 00       	mov    eax,0x0
    11e1:	e8 ca fe ff ff       	call   10b0 <gets@plt>
    11e6:	48 8d 3d 27 0e 00 00 	lea    rdi,[rip+0xe27]        # 2014 <_IO_stdin_used+0x14>
    11ed:	b8 00 00 00 00       	mov    eax,0x0
    11f2:	e8 a9 fe ff ff       	call   10a0 <printf@plt>
    11f7:	48 8d 45 90          	lea    rax,[rbp-0x70]
    11fb:	48 89 c7             	mov    rdi,rax
    11fe:	e8 7d fe ff ff       	call   1080 <puts@plt>
    1203:	b8 00 00 00 00       	mov    eax,0x0
    1208:	48 8b 55 f8          	mov    rdx,QWORD PTR [rbp-0x8]
    120c:	64 48 33 14 25 28 00 	xor    rdx,QWORD PTR fs:0x28
    1213:	00 00 
    1215:	74 05                	je     121c <main+0x73>
    1217:	e8 74 fe ff ff       	call   1090 <__stack_chk_fail@plt>
    121c:	c9                   	leave  
    121d:	c3                   	ret    
    121e:	66 90                	xchg   ax,ax

0000000000001220 <__libc_csu_init>:
    1220:	f3 0f 1e fa          	endbr64 
    1224:	41 57                	push   r15
    1226:	4c 8d 3d 73 2b 00 00 	lea    r15,[rip+0x2b73]        # 3da0 <__frame_dummy_init_array_entry>
    122d:	41 56                	push   r14
    122f:	49 89 d6             	mov    r14,rdx
    1232:	41 55                	push   r13
    1234:	49 89 f5             	mov    r13,rsi
    1237:	41 54                	push   r12
    1239:	41 89 fc             	mov    r12d,edi
    123c:	55                   	push   rbp
    123d:	48 8d 2d 64 2b 00 00 	lea    rbp,[rip+0x2b64]        # 3da8 <__do_global_dtors_aux_fini_array_entry>
    1244:	53                   	push   rbx
    1245:	4c 29 fd             	sub    rbp,r15
    1248:	48 83 ec 08          	sub    rsp,0x8
    124c:	e8 af fd ff ff       	call   1000 <_init>
    1251:	48 c1 fd 03          	sar    rbp,0x3
    1255:	74 1f                	je     1276 <__libc_csu_init+0x56>
    1257:	31 db                	xor    ebx,ebx
    1259:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]
    1260:	4c 89 f2             	mov    rdx,r14
    1263:	4c 89 ee             	mov    rsi,r13
    1266:	44 89 e7             	mov    edi,r12d
    1269:	41 ff 14 df          	call   QWORD PTR [r15+rbx*8]
    126d:	48 83 c3 01          	add    rbx,0x1
    1271:	48 39 dd             	cmp    rbp,rbx
    1274:	75 ea                	jne    1260 <__libc_csu_init+0x40>
    1276:	48 83 c4 08          	add    rsp,0x8
    127a:	5b                   	pop    rbx
    127b:	5d                   	pop    rbp
    127c:	41 5c                	pop    r12
    127e:	41 5d                	pop    r13
    1280:	41 5e                	pop    r14
    1282:	41 5f                	pop    r15
    1284:	c3                   	ret    
    1285:	66 66 2e 0f 1f 84 00 	data16 nop WORD PTR cs:[rax+rax*1+0x0]
    128c:	00 00 00 00 

0000000000001290 <__libc_csu_fini>:
    1290:	f3 0f 1e fa          	endbr64 
    1294:	c3                   	ret    

.fini 區段的反組譯：

0000000000001298 <_fini>:
    1298:	f3 0f 1e fa          	endbr64 
    129c:	48 83 ec 08          	sub    rsp,0x8
    12a0:	48 83 c4 08          	add    rsp,0x8
    12a4:	c3
    
```


``` c
#include <stdio.h>

int main(void)
{
	int n;
	int mul = 1;
	int i;

	scanf("%d", &n);
	
	i = 1;
	while(i <= n)
	{
		mul *= i;
		i++;
	};

	printf("the result is %d\n", mul);

	return 0;
}
```
* objdump -S -M intel test2.s
```

test2.s      檔案格式 elf64-x86-64


.init 區段的反組譯：

0000000000001000 <_init>:
    1000:	f3 0f 1e fa          	endbr64 
    1004:	48 83 ec 08          	sub    rsp,0x8
    1008:	48 8b 05 d9 2f 00 00 	mov    rax,QWORD PTR [rip+0x2fd9]        # 3fe8 <__gmon_start__>
    100f:	48 85 c0             	test   rax,rax
    1012:	74 02                	je     1016 <_init+0x16>
    1014:	ff d0                	call   rax
    1016:	48 83 c4 08          	add    rsp,0x8
    101a:	c3                   	ret    

.plt 區段的反組譯：

0000000000001020 <.plt>:
    1020:	ff 35 8a 2f 00 00    	push   QWORD PTR [rip+0x2f8a]        # 3fb0 <_GLOBAL_OFFSET_TABLE_+0x8>
    1026:	f2 ff 25 8b 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f8b]        # 3fb8 <_GLOBAL_OFFSET_TABLE_+0x10>
    102d:	0f 1f 00             	nop    DWORD PTR [rax]
    1030:	f3 0f 1e fa          	endbr64 
    1034:	68 00 00 00 00       	push   0x0
    1039:	f2 e9 e1 ff ff ff    	bnd jmp 1020 <.plt>
    103f:	90                   	nop
    1040:	f3 0f 1e fa          	endbr64 
    1044:	68 01 00 00 00       	push   0x1
    1049:	f2 e9 d1 ff ff ff    	bnd jmp 1020 <.plt>
    104f:	90                   	nop
    1050:	f3 0f 1e fa          	endbr64 
    1054:	68 02 00 00 00       	push   0x2
    1059:	f2 e9 c1 ff ff ff    	bnd jmp 1020 <.plt>
    105f:	90                   	nop

.plt.got 區段的反組譯：

0000000000001060 <__cxa_finalize@plt>:
    1060:	f3 0f 1e fa          	endbr64 
    1064:	f2 ff 25 8d 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f8d]        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    106b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

.plt.sec 區段的反組譯：

0000000000001070 <__stack_chk_fail@plt>:
    1070:	f3 0f 1e fa          	endbr64 
    1074:	f2 ff 25 45 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f45]        # 3fc0 <__stack_chk_fail@GLIBC_2.4>
    107b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001080 <printf@plt>:
    1080:	f3 0f 1e fa          	endbr64 
    1084:	f2 ff 25 3d 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f3d]        # 3fc8 <printf@GLIBC_2.2.5>
    108b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

0000000000001090 <__isoc99_scanf@plt>:
    1090:	f3 0f 1e fa          	endbr64 
    1094:	f2 ff 25 35 2f 00 00 	bnd jmp QWORD PTR [rip+0x2f35]        # 3fd0 <__isoc99_scanf@GLIBC_2.7>
    109b:	0f 1f 44 00 00       	nop    DWORD PTR [rax+rax*1+0x0]

.text 區段的反組譯：

00000000000010a0 <_start>:
    10a0:	f3 0f 1e fa          	endbr64 
    10a4:	31 ed                	xor    ebp,ebp
    10a6:	49 89 d1             	mov    r9,rdx
    10a9:	5e                   	pop    rsi
    10aa:	48 89 e2             	mov    rdx,rsp
    10ad:	48 83 e4 f0          	and    rsp,0xfffffffffffffff0
    10b1:	50                   	push   rax
    10b2:	54                   	push   rsp
    10b3:	4c 8d 05 d6 01 00 00 	lea    r8,[rip+0x1d6]        # 1290 <__libc_csu_fini>
    10ba:	48 8d 0d 5f 01 00 00 	lea    rcx,[rip+0x15f]        # 1220 <__libc_csu_init>
    10c1:	48 8d 3d c1 00 00 00 	lea    rdi,[rip+0xc1]        # 1189 <main>
    10c8:	ff 15 12 2f 00 00    	call   QWORD PTR [rip+0x2f12]        # 3fe0 <__libc_start_main@GLIBC_2.2.5>
    10ce:	f4                   	hlt    
    10cf:	90                   	nop

00000000000010d0 <deregister_tm_clones>:
    10d0:	48 8d 3d 39 2f 00 00 	lea    rdi,[rip+0x2f39]        # 4010 <__TMC_END__>
    10d7:	48 8d 05 32 2f 00 00 	lea    rax,[rip+0x2f32]        # 4010 <__TMC_END__>
    10de:	48 39 f8             	cmp    rax,rdi
    10e1:	74 15                	je     10f8 <deregister_tm_clones+0x28>
    10e3:	48 8b 05 ee 2e 00 00 	mov    rax,QWORD PTR [rip+0x2eee]        # 3fd8 <_ITM_deregisterTMCloneTable>
    10ea:	48 85 c0             	test   rax,rax
    10ed:	74 09                	je     10f8 <deregister_tm_clones+0x28>
    10ef:	ff e0                	jmp    rax
    10f1:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]
    10f8:	c3                   	ret    
    10f9:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

0000000000001100 <register_tm_clones>:
    1100:	48 8d 3d 09 2f 00 00 	lea    rdi,[rip+0x2f09]        # 4010 <__TMC_END__>
    1107:	48 8d 35 02 2f 00 00 	lea    rsi,[rip+0x2f02]        # 4010 <__TMC_END__>
    110e:	48 29 fe             	sub    rsi,rdi
    1111:	48 89 f0             	mov    rax,rsi
    1114:	48 c1 ee 3f          	shr    rsi,0x3f
    1118:	48 c1 f8 03          	sar    rax,0x3
    111c:	48 01 c6             	add    rsi,rax
    111f:	48 d1 fe             	sar    rsi,1
    1122:	74 14                	je     1138 <register_tm_clones+0x38>
    1124:	48 8b 05 c5 2e 00 00 	mov    rax,QWORD PTR [rip+0x2ec5]        # 3ff0 <_ITM_registerTMCloneTable>
    112b:	48 85 c0             	test   rax,rax
    112e:	74 08                	je     1138 <register_tm_clones+0x38>
    1130:	ff e0                	jmp    rax
    1132:	66 0f 1f 44 00 00    	nop    WORD PTR [rax+rax*1+0x0]
    1138:	c3                   	ret    
    1139:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

0000000000001140 <__do_global_dtors_aux>:
    1140:	f3 0f 1e fa          	endbr64 
    1144:	80 3d c5 2e 00 00 00 	cmp    BYTE PTR [rip+0x2ec5],0x0        # 4010 <__TMC_END__>
    114b:	75 2b                	jne    1178 <__do_global_dtors_aux+0x38>
    114d:	55                   	push   rbp
    114e:	48 83 3d a2 2e 00 00 	cmp    QWORD PTR [rip+0x2ea2],0x0        # 3ff8 <__cxa_finalize@GLIBC_2.2.5>
    1155:	00 
    1156:	48 89 e5             	mov    rbp,rsp
    1159:	74 0c                	je     1167 <__do_global_dtors_aux+0x27>
    115b:	48 8b 3d a6 2e 00 00 	mov    rdi,QWORD PTR [rip+0x2ea6]        # 4008 <__dso_handle>
    1162:	e8 f9 fe ff ff       	call   1060 <__cxa_finalize@plt>
    1167:	e8 64 ff ff ff       	call   10d0 <deregister_tm_clones>
    116c:	c6 05 9d 2e 00 00 01 	mov    BYTE PTR [rip+0x2e9d],0x1        # 4010 <__TMC_END__>
    1173:	5d                   	pop    rbp
    1174:	c3                   	ret    
    1175:	0f 1f 00             	nop    DWORD PTR [rax]
    1178:	c3                   	ret    
    1179:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]

0000000000001180 <frame_dummy>:
    1180:	f3 0f 1e fa          	endbr64 
    1184:	e9 77 ff ff ff       	jmp    1100 <register_tm_clones>

0000000000001189 <main>:
    1189:	f3 0f 1e fa          	endbr64 
    118d:	55                   	push   rbp
    118e:	48 89 e5             	mov    rbp,rsp
    1191:	48 83 ec 20          	sub    rsp,0x20
    1195:	64 48 8b 04 25 28 00 	mov    rax,QWORD PTR fs:0x28
    119c:	00 00 
    119e:	48 89 45 f8          	mov    QWORD PTR [rbp-0x8],rax
    11a2:	31 c0                	xor    eax,eax
    11a4:	c7 45 f0 01 00 00 00 	mov    DWORD PTR [rbp-0x10],0x1
    11ab:	48 8d 45 ec          	lea    rax,[rbp-0x14]
    11af:	48 89 c6             	mov    rsi,rax
    11b2:	48 8d 3d 4b 0e 00 00 	lea    rdi,[rip+0xe4b]        # 2004 <_IO_stdin_used+0x4>
    11b9:	b8 00 00 00 00       	mov    eax,0x0
    11be:	e8 cd fe ff ff       	call   1090 <__isoc99_scanf@plt>
    11c3:	c7 45 f4 01 00 00 00 	mov    DWORD PTR [rbp-0xc],0x1
    11ca:	eb 0e                	jmp    11da <main+0x51>
    11cc:	8b 45 f0             	mov    eax,DWORD PTR [rbp-0x10]
    11cf:	0f af 45 f4          	imul   eax,DWORD PTR [rbp-0xc]
    11d3:	89 45 f0             	mov    DWORD PTR [rbp-0x10],eax
    11d6:	83 45 f4 01          	add    DWORD PTR [rbp-0xc],0x1
    11da:	8b 45 ec             	mov    eax,DWORD PTR [rbp-0x14]
    11dd:	39 45 f4             	cmp    DWORD PTR [rbp-0xc],eax
    11e0:	7e ea                	jle    11cc <main+0x43>
    11e2:	8b 45 f0             	mov    eax,DWORD PTR [rbp-0x10]
    11e5:	89 c6                	mov    esi,eax
    11e7:	48 8d 3d 19 0e 00 00 	lea    rdi,[rip+0xe19]        # 2007 <_IO_stdin_used+0x7>
    11ee:	b8 00 00 00 00       	mov    eax,0x0
    11f3:	e8 88 fe ff ff       	call   1080 <printf@plt>
    11f8:	b8 00 00 00 00       	mov    eax,0x0
    11fd:	48 8b 55 f8          	mov    rdx,QWORD PTR [rbp-0x8]
    1201:	64 48 33 14 25 28 00 	xor    rdx,QWORD PTR fs:0x28
    1208:	00 00 
    120a:	74 05                	je     1211 <main+0x88>
    120c:	e8 5f fe ff ff       	call   1070 <__stack_chk_fail@plt>
    1211:	c9                   	leave  
    1212:	c3                   	ret    
    1213:	66 2e 0f 1f 84 00 00 	nop    WORD PTR cs:[rax+rax*1+0x0]
    121a:	00 00 00 
    121d:	0f 1f 00             	nop    DWORD PTR [rax]

0000000000001220 <__libc_csu_init>:
    1220:	f3 0f 1e fa          	endbr64 
    1224:	41 57                	push   r15
    1226:	4c 8d 3d 7b 2b 00 00 	lea    r15,[rip+0x2b7b]        # 3da8 <__frame_dummy_init_array_entry>
    122d:	41 56                	push   r14
    122f:	49 89 d6             	mov    r14,rdx
    1232:	41 55                	push   r13
    1234:	49 89 f5             	mov    r13,rsi
    1237:	41 54                	push   r12
    1239:	41 89 fc             	mov    r12d,edi
    123c:	55                   	push   rbp
    123d:	48 8d 2d 6c 2b 00 00 	lea    rbp,[rip+0x2b6c]        # 3db0 <__do_global_dtors_aux_fini_array_entry>
    1244:	53                   	push   rbx
    1245:	4c 29 fd             	sub    rbp,r15
    1248:	48 83 ec 08          	sub    rsp,0x8
    124c:	e8 af fd ff ff       	call   1000 <_init>
    1251:	48 c1 fd 03          	sar    rbp,0x3
    1255:	74 1f                	je     1276 <__libc_csu_init+0x56>
    1257:	31 db                	xor    ebx,ebx
    1259:	0f 1f 80 00 00 00 00 	nop    DWORD PTR [rax+0x0]
    1260:	4c 89 f2             	mov    rdx,r14
    1263:	4c 89 ee             	mov    rsi,r13
    1266:	44 89 e7             	mov    edi,r12d
    1269:	41 ff 14 df          	call   QWORD PTR [r15+rbx*8]
    126d:	48 83 c3 01          	add    rbx,0x1
    1271:	48 39 dd             	cmp    rbp,rbx
    1274:	75 ea                	jne    1260 <__libc_csu_init+0x40>
    1276:	48 83 c4 08          	add    rsp,0x8
    127a:	5b                   	pop    rbx
    127b:	5d                   	pop    rbp
    127c:	41 5c                	pop    r12
    127e:	41 5d                	pop    r13
    1280:	41 5e                	pop    r14
    1282:	41 5f                	pop    r15
    1284:	c3                   	ret    
    1285:	66 66 2e 0f 1f 84 00 	data16 nop WORD PTR cs:[rax+rax*1+0x0]
    128c:	00 00 00 00 

0000000000001290 <__libc_csu_fini>:
    1290:	f3 0f 1e fa          	endbr64 
    1294:	c3                   	ret    

.fini 區段的反組譯：

0000000000001298 <_fini>:
    1298:	f3 0f 1e fa          	endbr64 
    129c:	48 83 ec 08          	sub    rsp,0x8
    12a0:	48 83 c4 08          	add    rsp,0x8
    12a4:	c3                   	ret    

```
