# agenda
- [Symbolic Execution](#Symbolic Execution)

## Symbolic Execution

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

- [MIT 2014](https://www.youtube.com/watch?v=yRVZPvHYHzw)


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

### improving dynamic symbolic execution
- There are several interesting areas to research:
  - Modeling function semantics in symbolic execution could increase accuracy and possibly speed up DSE(tolower/toupper are interesting because they constrain a symbol case).
  - Symbolic memory model [9] could provide new symbolic states interesting for futher analysis.
  - Using Z3-solver tactics could possibly decrease time spent in solver.
  - Developing light-weight security predicates to find some types of dangerous vulnerabilities.

### review
- [(State of) The Art of War:Offensive Techniques in Binary Analysis(2016)](https://www.researchgate.net/publication/306304563_SOK_State_of_The_Art_of_War_Offensive_Techniques_in_Binary_Analysis)

## AUTOMATED BINARY ANALYSIS
