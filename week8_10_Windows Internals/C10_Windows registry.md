# Windows registry

- 經典導讀 Windows Internals, Part 2, 7th Edition/CHAPTER 10 Management, diagnostics, and tracing
- [Windows Registry Tutorial](https://www.netwrix.com/windows_registry_tutorial.html?itm_source=blog&itm_medium=context&itm_campaign=windows-server&itm_content=none&cID=70170000000kgEZ&_gl=1*1xpdiak*_ga*ODg1Nzg5ODYyLjE2MzA5Mzk0MjM.*_ga_Z8M2NDPEEV*MTYzMjEzOTI4OS40LjAuMTYzMjEzOTI4OS4w&_ga=2.40761255.407654581.1632139290-885789862.1630939423)
- [Practical Windows Registry Explanation](https://www.youtube.com/watch?v=tBwAHqqPoQY)
# Tools
- regdeit
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
