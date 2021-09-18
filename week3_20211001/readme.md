# week 3: Basic Reverse Engineering
```
[assmebly Programming]
NASM Assembly programming
GAS Assembly programming
core Assembly language syntax
Calling Conventions

[Basic Reverse Engineering]
gdb
objdump
radare2
Ghidra

[Reverse-CTF]解題
```

# Tools

## [GDB: The GNU Project Debugger](https://www.gnu.org/software/gdb/)

- [Debugging with GDB](https://sourceware.org/gdb/current/onlinedocs/gdb/)
- [GDB Internals內部運作原理](https://sourceware.org/gdb/wiki/Internals)
- [Internals@WIKI](https://en.wikipedia.org/wiki/GNU_Debugger)
   - GDB uses a system call named ptrace (the name is an abbreviation of "process trace") to observe and control the execution of another process, and examine and change the process's memory and register. A list of common gdb commands and corresponding ptrace calls are listed below:
   - (gdb) start : PTRACE_TRACEME – makes parent a tracer (called by a tracee)
   - (gdb) attache PID: PTRACE_ATTACH – attach to a running process
   - (gdb) stop: kill(child_pid, SIGSTOP) (or PTRACE_INTERRUPT)
   - (gdb) continue: PTRACE_CONT
   - (gdb) info registers : PTRACE_GET(FP)REGS(ET) and PTRACE_SET(FP)REGS(ET)
   - (gdb) x : PTRACE_PEEKTEXT and PTRACE_POKETEXT

## [radare2](https://en.wikipedia.org/wiki/Radare2)
- [The Official Radare2 Book](https://book.rada.re/index.html)
- [radare2 Cheatsheet](https://scoding.de/uploads/r2_cs.pdf)
- [r2con](https://rada.re/con/)
- [r2con@youtube](https://www.youtube.com/c/r2con)

## Ghidra
- [Ghidra CheatSheet](https://ghidra-sre.org/CheatSheet.html)
- [The Ghidra Book(2020)](https://nostarch.com/GhidraBook)
