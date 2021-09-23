# Ghidra
- [Ghidra簡介](#Ghidra簡介)
- [安裝](#安裝)
- [示範解題](#示範解題)
- [學習資源](#學習資源)

## [Ghidra簡介](https://en.wikipedia.org/wiki/Ghidra)

- Ghidra is a software reverse engineering (SRE) suite of tools developed by NSA’s Research Directorate in support of the Cybersecurity mission.
- Ghidra is open-source.
- Ghidra framework includes a suite of full-featured, high-end software analysis tools that enable users to analyze compiled code on a variety of platforms including Windows, Mac OS, and Linux. 
- Capabilities include disassembly, assembly, decompilation, graphing, and scripting, along with hundreds of other features. 
- Ghidra supports a wide variety of process instruction sets and executable formats and can be run in both user-interactive and automated modes. 
- Users may also develop their own Ghidra plug-in components and/or scripts using the exposed API.
- In support of NSA's Cybersecurity mission, Ghidra was built to solve scaling and teaming problems on complex SRE efforts, and to provide a customizable and extensible SRE research platform. 
- NSA has applied Ghidra SRE capabilities to a variety of problems that involve analyzing malicious code and generating deep insights for NSA analysts who seek a better understanding of potential vulnerabilities in networks and systems.

## 安裝
### 撰寫 run_ghidra.sh
```
mkdir Ghidra
cd Ghidra
wget https://ghidra-sre.org/ghidra_9.0.1_PUBLIC_20190325.zip
unzip ghidra_9.0.1_PUBLIC_20190325.zip
cd ghidra_9.0.1
sudo add-apt-repository ppa:openjdk-r/ppa 
sudo apt update 
sudo apt install openjdk-11-jdk 
sudo apt install openjdk-11-jre-headless
chmod +x ghidraRun
./ghidraRun
```

### 安裝
```
bash run_ghidra.sh
要一段時間  ==>  OK
```
### 執行Running Ghidra ==>GUI Mode
```
Navigate to <GhidraInstallDir>
Run ghidraRun.bat (Windows) or ghidraRun (Linux or macOS)
```
```
Ghidra Installation on Ubuntu |18.04, 16.04, 14.04
Posted on March 26, 2019 by Yılmaz Cemalettin
https://www.ylmzcmlttn.com/2019/03/26/ghidra-installation-on-ubuntu-18-04-16-04-14-04/
```
```
could not find decompiler executable decompile #1495
https://github.com/NationalSecurityAgency/ghidra/issues/1495

不支援32 位元
```
## 示範解題



## 學習資源
- [Ghidra - Journey from Classified NSA Tool to Open Source](https://www.youtube.com/watch?v=kx2xp7IQNSc&t=683s)
- [Ghidra and IDA - Solving a reverse engineering CTF crackme - AmIRootYet - Pranshu Bajpai](https://www.youtube.com/watch?v=S06pgk4DjFQ)

- [Reversing CrackMe with Ghidra (Part 1)](https://www.youtube.com/watch?v=6p5Qviusskk&t=33s)
- [Reversing CrackMe with Ghidra (Part 2)](https://www.youtube.com/watch?v=Eu9YC1Jq1Do)


