# week 13:Vulnerability Finding:bug bounty| FUZZing

## FUZZ+ing

- Fuzz testing or Fuzzing is a Black Box software testing technique, which basically consists in finding implementation bugs using malformed/semi-malformed data injection in an automated fashion.[OWASP](https://owasp.org/www-community/Fuzzing)
- [Fuzzing - Wikipedia](https://en.wikipedia.org/wiki/Fuzzing)
  - Fuzzing or fuzz testing is an automated software testing technique that involves providing invalid, unexpected, or random data as inputs to a computer program. 
  - The program is then monitored for exceptions such as crashes, failing built-in code assertions, or potential memory leaks. 

## FUZZ+ing milestones
- [Fuzz testing was developed at the University of Wisconsin Madison in 1988 by Professor Barton Miller and students.](http://pages.cs.wisc.edu/~bart/fuzz/)
  - The term "fuzz" originates from a fall 1988 class project in the graduate Advanced Operating Systems class (CS736), taught by Prof. Barton Miller at the University of Wisconsin, whose results were subsequently published in 1990 
  - [Barton P. Miller; Lars Fredriksen; Bryan So (December 1990). "An Empirical Study of the Reliability of UNIX Utilities" (PDF). Communications of the ACM]
 
- 2012: Google announced ClusterFuzz, a cloud-based fuzzing infrastructure for security-critical components of the Chromium web browser.
  - Security researchers can upload their own fuzzers and collect bug bounties if ClusterFuzz finds a crash with the uploaded fuzzer.
- 2013: Google/AFL
- 2014: BASH Shellshock: most vulnerabilities of Shellshock were found using the fuzzer AFL.
- 2015, Hanno Böck showed how the fuzzer AFL could have found the 2014 Heartbleed vulnerability.
- 2016, Microsoft announced Project Springfield, a cloud-based fuzz testing service for finding security critical bugs in software
- [honggfuzz漏洞挖掘技術深究系列](https://bbs.pediy.com/thread-247954.htm)
- 2016, Google announced OSS-Fuzz which allows for continuous fuzzing of several security-critical open-source projects
- 2020, [Google/FuzzBench](): Fuzzer Benchmarking As a Service
  - [Google推出Fuzzer基準測試服務FuzzBench](https://www.ithome.com.tw/news/136258) 
- 2020, Microsoft released OneFuzz, a self-hosted fuzzing-as-a-service platform that automates the detection of software bugs.

## [Types of fuzzers](https://cybersecurity.springeropen.com/articles/10.1186/s42400-018-0002-y)
- Fuzzers can be classified in various ways.
  -  generation based and mutation based
  -  white box, gray box and black box fuzzers
  -  directed fuzzing and coverage-based fuzzing
  -  dumb fuzz and smart fuzz 

## [Fuzzing towards different applications](https://cybersecurity.springeropen.com/articles/10.1186/s42400-018-0002-y)
- File format fuzzing
  - Peach (PeachTech 2017) 
  - state-of-the-art AFL and its extensions (Rawat et al. 2017; Böhme et al. 2017, 2017)
- web browsers 
  - Grinder framework (Stephenfewer 2016), COMRaider (Zimmer 2013), BF3 (Aldeid 2013) 
- Kernel fuzzing
  - knowledge based fuzzers : knowledge on kernel API functions are leveraged in the fuzzing process
    - Trinity (Jones 2010) and IMF (Han and Cha 2017)
  - coverage guided fuzzers 
    -  syzkaller (Vyukov 2015), TriforceAFL (Hertz 2015) and kAFL (Schumilo et al. 2017) 
- Fuzzing of protocols
  - SPIKE
  - AutoFuzz (Gorbunov and Rosenbloom 2010)
  - SNOOZE (Banks et al. 2006)
  - [boofuzz: Network Protocol Fuzzing for Humans](https://github.com/jtpereyda/boofuzz) 

- [OpenRCE/sulley 不再維護,請用boofuzz](https://github.com/OpenRCE/sulley)

## CaseStudy: Google/AFL(2013)
- AFL(American Fuzzy Lop)是由安全研究員Michał Zalewski 開發的一款基於覆蓋引導（Coverage-guided）的模糊測試工具。
- 通過記錄輸入樣本的代碼覆蓋率，不斷對輸入進行變異，從而達到更高的代碼覆蓋率。
- AFL 採用新型的編譯時插樁和遺傳演算法自動發現新的測試用例，這些用例會觸發目標二進位檔案中的新內部狀態。這大大改善了模糊測試的代碼覆蓋範圍。
- 從源碼編譯器時進行插樁，以記錄代碼覆蓋率（Code Coverage）；
- 選擇一些輸入檔，作為初始測試集加入輸入佇列（queue）；
- 將佇列中的檔按一定的策略進行變異”；
- 如果經過變異檔更新了覆蓋範圍，則將其保留添加到佇列中；
- 上述過程會一直迴圈進行，期間觸發了crash的檔會被記錄下來。
- [经典 Fuzzer 工具 AFL 模糊测试指南(江下枫,2020)](https://blog.csdn.net/song_lee/article/details/104777149)

##　CaseStudy: Google/honggfuzz(20XX)
- honggfuzz 是由 google 開發的一款基於代碼覆蓋率的 fuzzer，與 afl、libfuzzer 並駕齊驅。也是一款效率很高的回饋驅動 fuzz 工具
- [使用反馈驱动 Fuzzer 工具 Honggfuzz 进行漏洞挖掘](https://blog.csdn.net/song_lee/article/details/105230099)
- [Honggfuzz实战](https://www.cnblogs.com/hac425/p/9416915.html)
```
git clone https://github.com/google/honggfuzz.git
cd honggfuzz
make
```
```
honggfuzz -f input_dir -z -s -- /usr/bin/djpeg

-f : 指定初始樣本集 目錄
-z : 使用編譯時的指令插樁資訊來 為 樣本變異做回饋， 預設選項
-s : 表示目的程式從 stdin 獲取輸入，即樣本資料通過 stdin 喂給程式
```
- [YOUTUBE　Fuzzing Labs - Patrick Ventuzelo](https://www.youtube.com/channel/UCGD1Qt2jgnFRjrfAITGdNfQ/videos)

## [CodeQL](https://codeql.github.com/)
- Write and run queries in Visual Studio Code
- [CodeQL Capture the Flag](https://securitylab.github.com/ctf/)


## FUZZing與 Fuzzer
- AFL ++
- 

## [FUZZing研究論文](https://github.com/fengjixuchui/FuzzingPaper)
- [REVIEW  The Art, Science, and Engineering of Fuzzing: A Survey(2018)](https://arxiv.org/abs/1812.00140)


## Automatic exploit generation
- [History of AEG](https://cacm.acm.org/magazines/2014/2/171687-automatic-exploit-generation/fulltext#sidebar-1)
- [AEG: Automatic Exploit Generation](https://security.ece.cmu.edu/aeg/aeg-current.pdf)
- [CRAX:Software Crash Analysis for Automatic Exploit Generation on Binary Programs(2014)](https://ir.nctu.edu.tw/bitstream/11536/24012/1/000332520700022.pdf)

## 全球大企業如何挖掘自家產品或服務的漏洞?
- [GOOGLE](github.com/google/fuzzing)
- [Microsoft|microsoft/onefuzz](https://github.com/microsoft/onefuzz)
- [Github|CodeQL](https://securitylab.github.com/tools/codeql/)
- AMAZON ?
- Apple ?
