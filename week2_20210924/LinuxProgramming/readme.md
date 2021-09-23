
# # W01_Binary analysis上課內容
```
測試分析環境說明
從原始程式碼到可執行檔
ELF 檔案格式與分析
靜態連結
動態連結
```

# 1.從原始程式碼到可執行檔
```
編譯原理
GCC 編譯過程
前置處理階段
編譯階段
組合語言階段
連結階段
```
## 實作練習_原始程式碼到可執行檔
## 實作練習_LD_PRELOAD技術

# 2.函式庫開發

# 2.1.靜態連結函式庫開發
```
位址空間分配
靜態連結過程
靜態程式庫
```
## 實作練習_靜態程式庫建立與分析
# 2.2.動態連結函式庫開發
```
動態連結
位置無關程式(Position-Independent Code, PIC)
延遲綁定(lazy binding)
```
## 實作練習_動態連結建立與分析

>* [[why use lazy binding for Position-Independent Code Function Calls]](https://stackoverflow.com/questions/63745016/why-use-lazy-binding-for-position-independent-code-function-calls)

## [Lazy binding](http://www.qnx.com/developers/docs/qnxcar2/index.jsp?topic=%2Fcom.qnx.doc.neutrino.prog%2Ftopic%2Fdevel_Lazy_binding.html) 
```
Lazy binding (also known as lazy linking or on-demand symbol resolution)

Procedure Linkage Table (PLT)
Global Offset Table (GOT)
```
### GOT hijacking



# 參考書籍與推薦章節

- [程式設計師的自我修養－連結、載入、程式庫](https://www.tenlong.com.tw/products/9789861818283?list_name=srh)
- [ Advanced C and C++ Compiling by Milan Stevanovic (Apress, 2014)](https://www.apress.com/gp/book/9781430266679) [[GITHUB]](https://github.com/Apress/adv-c-cpp-compiling)
