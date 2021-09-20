# Windows Management Instrumentation(WMI)

- WMI is an implementation of Web-Based Enterprise Management (WBEM), a standard that the Distributed Management Task Force (DMTF—an industry industry
consortium) defines. 
- The WBEM standard encompasses the design of an extensible enterprise data-collection and data-management facility that has the flexibility and extensibility required to manage local and remote systems that comprise arbitrary components.

- WMI是一項核心的Windows管理技術，WMI作為一種規範和基礎結構，通過它可以訪問、配置、管理和監視幾乎所有的Windows資源
- 使用者可在遠程計算機器上啟動一個進程；設定一個在特定日期和時間運行的進程；遠程啟動計算機；獲得本地或遠程計算機的已安裝程序列表；查詢本地或遠程計算機的Windows事件日誌等等。

# WMI architecture see Figure 10-27

- WMI consists of four main components : management applications, WMI infrastructure, providers, and managed objects. 
  - [1]Management applications are Windows applications that access and display or process data about managed objects. 
    - example 1: performance tool replacement that relies on WMI rather than the Performance API to obtain performance information. 
    - example 2 :is an enterprise-management tool that lets administrators perform automated inventories of the software and hardware configuration of every computer in their enterprise.
  - [2]An object might represent one component, such as a network adapter device, or a collection of components, such as a computer. 
  - (The computer object might contain the network adapter object.) 
  - [3]Providers need to define and export the representation of the objects that management applications are interested in. 
    - the vendor of a network adapter might want to add adapterspecific properties to the network adapter WMI support that Windows includes, querying and setting the adapter’s state and behavior as the management applications direct
    - - provider that has its own API to help developers leverage the provider’s implementation for their own managed objects with minimal coding effort.
  - [4]The WMI infrastructure, the heart of which is the Common Information Model (CIM) Object Manager (CIMOM), is the glue that binds management applications and providers. 
    - The infrastructure also serves as the object-class store and, in many cases, as the storage manager for persistent object properties. 
    - WMI implements the store, or repository, as an on-disk database named the CIMOM Object Repository. 
    - WMI supports several APIs through which management applications access object data and providers supply data and class definitions.

- WMI providers
  - At the core of WBEM is the DMTF-designed CIM specification. 
  - The CIM specifies how management systems represent, from a systems management perspective, anything from a computer to an application or device on a computer. 
  - Provider developers use the CIM to represent the components that make up the parts of an application for which the developers want to enable management. 
  - Developers use the Managed Object Format (MOF) language to implement a CIM representation.
 
# 存取WMI 和 CIM方法[練習與實測]
## [1]使用powershell 存取WMI 和 CIM
  - [Working with WMI](https://docs.microsoft.com/en-us/powershell/scripting/learn/ps101/07-working-with-wmi?view=powershell-7.1) 
  - Get-Command -Noun WMI*  ==> used to determine what WMI cmdlets exist in PowerShell 
    - The CIM cmdlets are designed so they can be used on both Windows and non-Windows machines. 
    - The WMI cmdlets are deprecated so my recommendation is to use the CIM cmdlets instead of the older WMI ones.
  - Get-Command -Module CimCmdlets  ==> obtain a list of the CIM cmdlets
  - [CimCmdlets參考資料](https://docs.microsoft.com/en-us/powershell/module/cimcmdlets/?view=powershell-7.1)
  - [Get-CimInstance](https://docs.microsoft.com/en-us/powershell/module/cimcmdlets/get-ciminstance?view=powershell-7.1)
    - Get-CimInstance -Query 'Select * from Win32_BIOS' ==> can take the WQL query from that VBScript and use it with the Get-CimInstance cmdlet
    - Get-CimInstance -ClassName Win32_BIOS
  - [Invoke-CimMethod: Invokes a method of a CIM class.](https://docs.microsoft.com/en-us/powershell/module/cimcmdlets/invoke-cimmethod?view=powershell-7.1)
    - Invoke a static method using arguments
```powsershell
Invoke-CimMethod -ClassName Win32_Process -MethodName "Create" -Arguments @{
  CommandLine = 'notepad.exe'; CurrentDirectory = "C:\windows\system32"
}
```
## [2]使用python存取WMI 和 CIM ==> [wmi模組](https://pypi.org/project/WMI/)
  - The Python WMI module is a lightweight wrapper on top of the pywin32 extensions, and hides some of the messy plumbing needed to get Python to talk to the WMI API.
  - [python wmi模塊 獲取windows內部信息](https://www.itread01.com/content/1553437344.html) 
  - [Python wmi.WMI屬性代碼示例](https://vimsky.com/zh-tw/examples/detail/python-attribute-wmi.WMI.html)
  - [Managing Windows System Administration With WMI And Python](https://blog.ipswitch.com/managing-windows-system-administration-with-wmi-and-python)
  - [wmi Cookbook](http://timgolden.me.uk/python/wmi/cookbook.html)
