# The Ghidra Book_The Definitive Guide 導讀

- [官方網站(含有程式碼可下載)+ 可網路購買電子書](https://ghidrabook.com/l)

- Chapter 1: Introduction to Disassembly

- Chapter 2: Reversing and Disassembly Tools
  - Classification Tools == > file |  PE Tools | PEiD 
  - Summary Tools == >   nm | ldd | objdump | otool(macOS) | dumpbin(Windows) | c++filt
    - dumpbin /dependents C:\Windows\System32\notepad.exe 
  - Deep Inspection Tools == > strings | Disassemblers [ndisasm and diStorm]

- Chapter 3: Meet Ghidra
  - The Ghidra Directory Layout 目錄結構
    - Extensions ==>  Contains useful prebuilt extensions and important content and information for writing Ghidra extensions. 
    - Ghidra  ==>   Contains the code for Ghidra.  

- Chapter 4: Getting Started with Ghidra  基本操作
  - 先啟動專案  File => New Project  ==> 注意專案路徑
  - 載入檔案 File => Import File
  - Ghidra Import Results Summary window
  - Ghidra CodeBrowser window
  - The Analysis Options dialog(分析的各種選項)
  - Ghidra Help=>About
  - import summary information


- Chapter 5: Ghidra Data Displays
- Chapter 6: Making Sense of a Ghidra Disassembly
- Chapter 7: Disassembly Manipulation
- Chapter 8: Data Types and Data Structures
- Chapter 9: Cross-References
- Chapter 10: Graphs
- Chapter 11: Collaborative SRE with Ghidra
  - 多人協同分析 
  - 使用Ghidra Server 
- Chapter 12: Customizing Ghidra
- Chapter 13: Extending Ghidra’s Worldview
- Chapter 14: Basic Ghidra Scripting
- Chapter 15: Eclipse and GhidraDev
- Chapter 16: Ghidra in Headless Mode
- Chapter 17: Ghidra Loaders
- Chapter 18: Ghidra Processors
- Chapter 19: The Ghidra Decompiler
- Chapter 20: Compiler Variations
- Chapter 21: Obfuscated Code Analysis
- Chapter 22: Patching Binaries
- Chapter 23: Binary Differencing and Version Tracking
- Appendix: Ghidra for IDA Users
