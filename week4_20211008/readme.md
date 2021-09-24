# agenda
```
Symbolic Execution
Symbolic Execution: Tools introduction
Symbolic Execution with Z3 
Symbolic Execution with Angr
CTF解題
```



### Symbolic Execution

- symbolic execution (also symbolic evaluation or symbex) is a means of analyzing a program to determine what inputs cause each part of a program to execute. 
- An interpreter follows the program, assuming symbolic values for inputs rather than obtaining actual inputs as normal execution of the program would. 
- It thus arrives at expressions in terms of those symbols for expressions and variables in the program, and constraints in terms of those symbols for the possible outcomes of each conditional branch. 
- Finally, the possible inputs that trigger a branch can be determined by solving the constraints.

- [Symbolic execution and program testing|James C. King (Communications of the ACM 1976)](https://dl.acm.org/doi/10.1145/360248.360252)
  - Analysis	of	programs	with	unspecified	inputs	
  - “Execute”	a	program	on	symbolic	inputs	
  - Symbolic states represents sets of concrete states	
  - For	each	path,	build	a	path	condition	
  - Condition	on inputs –for the	execution to follow that path	
  - Check	path condition satisfiability	–	explore	only feasible paths	

## 挑戰課題
-  path explosion problem in DSE


### Static Symbolic Execution (SSE)
- [Avgerinoset al. 2016; Khurshid et al. 2003]. 
- the symbolic execution tree is encoded as a single logic formula whose treatment can be outsourced to an SMT solver [De Moura et al. 2002].
- The solver then deals with what is essentially a huge disjunctive formula. 
- limitations:(as compared with DSE, for example)  the loop bounds, including nestedloops, must be pre-specified. 
- advantage:( over (non-pruning) DSE): its SMTsolver can use the optimization method of conflict directed clause learning (CDCL) [Marques-Silva
and Sakallah 1999]. See e.g. Section 3.4 of [de Moura and Bjørner 2008] on how the SMT solver Z3
exploits CDCL. Essentially, CDCL enables “pruning” in the exploration process of the solver.

### Dynamic symbolic execution (DSE)
- Dynamic symbolic execution (DSE) is a powerful and trendy method. 
- It has been used for several tasks, such as:
  - Code coverage
  - Input and test-case generation
  - Exploit generation
  - Directed fuzzing
  - Out-of-bound access checking
  - Automatic crackme solving
  - Reconstruction of algorithm
  - Deobfuscation
- DART [Godefroid et al. 2005],
- CUTE [Sen et al. 2005] 
- [KLEE [Cadar et al. 2008a] w]
- [Miasm動態符號執行(DSE)](https://github.com/cea-sec/miasm)
- [](https://www.cis.upenn.edu/~mhnaik/edu/cis700/lessons/symbolic_execution.pdf)
- [Sydr: Cutting Edge Dynamic Symbolic Execution(202011)](https://arxiv.org/abs/2011.09269)
- [[PAPER]TracerX: Dynamic Symbolic Execution with Interpolation(202012)](https://arxiv.org/abs/2012.00556)


## Symbolic Execution

- [MIT 2014](https://www.youtube.com/watch?v=yRVZPvHYHzw)


## Angr
>* [SOK: (State of) The Art of War: Offensive Techniques in Binary Analysis](https://ieeexplore.ieee.org/document/7546500)
>* [1_論文2017](https://ieeexplore.ieee.org/document/8077799) [2_Youtube](https://www.youtube.com/watch?v=Wx2RhKI7TIU) [3_angr Documentation](https://docs.angr.io/) [4_GITHUB](https://github.com/angr/angr) [5_官方網址](https://angr.io/)
>* [範例](https://docs.angr.io/examples)

>* [Youtube 教學1](https://www.youtube.com/watch?v=a4tKDX4F5Ng)[Youtube 教學2](https://www.youtube.com/watch?v=XgHZ6QnZkgc)[Youtube 教學3](https://www.youtube.com/watch?v=XgHZ6QnZkgc)[Youtube 教學4](https://www.youtube.com/channel/UCLx14vWN9uw5ziL_dq0WDfA/videos)

>* [Teaching with angr: A Symbolic Execution Curriculum and CTF](https://www.usenix.org/sites/default/files/conference/protected-files/ase18_slides_feng.pdf)

>* [jakespringer/angr_ctf](https://github.com/jakespringer/angr_ctf)[解法1](https://cexplr.github.io/writeups/angr/3_angr_post_1.html)[解法2](https://github.com/ZERO-A-ONE/AngrCTF_FITM)[解法3](https://bbs.pediy.com/thread-267227.htm)

>* [Google CTF - BEGINNER Reverse Engineering w/ ANGR](https://www.youtube.com/watch?v=RCgEIBfnTEI)

## Z3

- [Z3求解器簡介及環境搭建](https://blog.csdn.net/guo_shaokun/article/details/99891545?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162904945016780262523657%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162904945016780262523657&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-5-99891545.pc_search_result_control_group&utm_term=z3&spm=1018.2226.3001.4187)
- pip install z3-solver
- [Z3求解器基本指南](https://blog.csdn.net/weixin_39408343/article/details/102680614?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162904945016780262523657%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162904945016780262523657&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-2-102680614.pc_search_result_control_group&utm_term=z3&spm=1018.2226.3001.4187)


>* []()



## Triton
- [Triton:a dynamic binary analysis (DBA) framework](https://triton.quarkslab.com/) [Presentations and Publications](https://triton.quarkslab.com/documentation/)[安裝](https://triton.quarkslab.com/documentation/doxygen/index.html#install_sec)
- [Triton/ctf-writeups/](https://github.com/JonathanSalwan/Triton/tree/master/src/examples/python/ctf-writeups)
- [CSCBE 2018 finals/serial_killer](https://github.com/jimbauwens/cscbe_ctf_serial_solver)
- [JonathanSalwan/binary-samples測試你的工具用的各種格式binary](https://github.com/JonathanSalwan/binary-samples)



## [Miasm動態符號執行(DSE)](https://github.com/cea-sec/miasm)
- Miasm is a free and open source (GPLv2) reverse engineering framework. Miasm aims to analyze / modify / generate binary programs. 
- features:
  - Opening / modifying / generating PE / ELF 32 / 64 LE / BE
  - Assembling / Disassembling X86 / ARM / MIPS / SH4 / MSP430
  - Representing assembly semantic using intermediate language
  - Emulating using JIT (dynamic code analysis, unpacking, ...)
  - Expression simplification for automatic de-obfuscation

- [France CyberSecurity Challenge(FCSC 2020 - Keykoolol)](https://github.com/icecr4ck/write-ups/tree/master/FCSC-2020/Keykoolol)[解法1](https://re-dojo.github.io/write-ups/2020-05-09-fcsc-2020-keykoolol/?fbclid=IwAR24oI6OcV-KgM_MWQpeBzGiuezQjtQw-bHuoprgu2R31nL-E4DUSaqyb3M) [解法2](https://blog.csdn.net/systemino/article/details/106538823)


## INTEL Pin Binary Instrumentation(BI)

>* [Pin 動態二進位插樁](https://firmianay.gitbooks.io/ctf-all-in-one/content/doc/5.2.1_pin.html)
>* [Pin Tutorial](https://www.ic.unicamp.br/~rodolfo/mo801/04-PinTutorial.pdf)

>* [ChrisTheCoolHut/PinCTF](https://github.com/ChrisTheCoolHut/PinCTF)
>* [pin-in-CTF/examples/](https://github.com/bash-c/pin-in-CTF/tree/master/examples)
