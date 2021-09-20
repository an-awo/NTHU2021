# Windows registry

- 經典導讀 Windows Internals, Part 2, 7th Edition/CHAPTER 10 Management, diagnostics, and tracing
- [Windows Registry Tutorial](https://www.netwrix.com/windows_registry_tutorial.html?itm_source=blog&itm_medium=context&itm_campaign=windows-server&itm_content=none&cID=70170000000kgEZ&_gl=1*1xpdiak*_ga*ODg1Nzg5ODYyLjE2MzA5Mzk0MjM.*_ga_Z8M2NDPEEV*MTYzMjEzOTI4OS40LjAuMTYzMjEzOTI4OS4w&_ga=2.40761255.407654581.1632139290-885789862.1630939423)
- [Practical Windows Registry Explanation](https://www.youtube.com/watch?v=tBwAHqqPoQY)
- [Windows Registry@維基百科]()

## Registry logical structure and 9 Registry root keys
|名稱| 縮寫| 敘述 |
|----| -----| ------|
|HKEY_CLASSES_ROOT|HKCR	|儲存Windows可辨識的檔案類型的詳細列表，以及相關聯的程式。|
|HKEY_CURRENT_USER|HKCU|	儲存當前使用者設定的資訊。|
|HKEY_LOCAL_MACHINE|HKLM	|包括安裝在電腦上的硬體和軟體的資訊。|
|HKEY_USERS|	HKU|包含使用電腦的使用者的資訊。|
|HKEY_CURRENT_CONFIG|HKCC|	這個分支包含電腦當前的硬體組態資訊。|
|HKEY_CURRENT_USER_LOCAL_SETTINGS|HKCULS||
|HKEY_PERFORMANCE_DATA|HKPD||
|HKEY_PERFORMANCE_NLSTEXT|HKPNL||
|HKEY_PERFORMANCE_TEXT|HKPT||

- Viewing key control blocks
  - !reg querykey command. ==> list all the key control blocks allocated on a system
  - !reg openkeys command. ==> view the key control block for a particular open key
  - 0: kd> !reg querykey \Registry\machine\software\microsoft

# 資料結構
- 登錄檔由鍵（key，或稱「項」）、子鍵（subkey，子項）和值項（value）構成。
- 一個鍵就是樹狀資料結構中的一個節點，而子鍵就是這個節點的子節點，子鍵也是鍵。
- 一個值項則是一個鍵的一條內容，由名稱（name）、資料類型（datatype）以及資料（data）組成。
- 一個鍵可以有一個或多個值，每個值的名稱各不相同，如果一個值的名稱為空，則該值為該鍵的預設值。


# Tools
- regedit登錄編輯程式
  - [Regedit: The built-in editor for the Windows registry](https://www.ionos.com/digitalguide/websites/web-development/regedit/) 
- kernel debugger
- Powershell
  - [Working with Registry Keys](https://docs.microsoft.com/en-us/powershell/scripting/samples/working-with-registry-keys?view=powershell-7.1)
  - [Working with Registry Entries](https://docs.microsoft.com/en-us/powershell/scripting/samples/working-with-registry-entries?view=powershell-7.1)
  - [How to Get, Edit, Create and Delete Registry Keys with PowerShell(2018)](https://blog.netwrix.com/2018/09/11/how-to-get-edit-create-and-delete-registry-keys-with-powershell/)
- Python
  - [winreg:  Windows registry access](https://docs.python.org/3/library/winreg.html)
    - [Updating the windows registry with python (Modify path variable in windows with python)](https://www.youtube.com/watch?v=MdshNIw_ZRM)  
    - [example](https://www.tutorialspoint.com/windows-registry-access-using-python-winreg)
```Python
import winreg
#connecting to key in registry
access_registry = winreg.ConnectRegistry(None,winreg.HKEY_LOCAL_MACHINE)

access_key = winreg.OpenKey(access_registry,r"SOFTWARE\Microsoft\Windows\CurrentVersion")
#accessing the key to open the registry directories under
for n in range(20):
   try:
      x =winreg.EnumKey(access_key,n)
      print(x)
   except:
      break
```
  - [python-registry](https://github.com/williballenthin/python-registry)
