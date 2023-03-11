# HowTo-setup-an-UEFI-Development-PC
**NOTE:** To build all projects from https://github.com/KilianKegel the tools below are absolutely needed
* NASM
* ASL
* Windows 8.1 SDK (for  EDK2020-MinnowBoard)
* FLEX/BISON (for the Visual-ACPICA-for-UEFI-Shell project)

## Install a Windows 11/10 PC<br>
   *  get `MediaCreationTool` https://go.microsoft.com/fwlink/?linkid=2156295 and download Windows 11<br>
   	or
   *  get `MediaCreationTool` https://go.microsoft.com/fwlink/?LinkId=691209 and download Windows 10<br>
### Windows 11 configuration hint
   1. Restore Classic (Full) Context Menu in Windows<br>
      run in command prompt window:<br>
      `reg add HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32 /ve /d "" /f`<br>

## Install Visual Studio 2022<br>
   1. download: https://docs.microsoft.com/en-us/visualstudio/releases/2022/release-notes<br>
   2. configure setup:
   ![installselection2022](VS2022-components.png)
   
## Install GIT: https://github.com/git-for-windows/git/releases/download/v2.29.0.windows.1/Git-2.29.0-64-bit.exe<br>
## Install/extract the ASL/ACPI compiler to C:\ASL -> https://acpica.org/sites/acpica/files/iasl-win-20160527.zip
## Install Python https://www.python.org/ftp/python/3.7.4/python-3.7.4-amd64.exe<br>
   
   NOTE: If Python is installed from the Microsoft AppStore it can not be de-installed anymore!
## Install Netwide Assembler ver. 2.15.05 to C:\NASM 

**NOTE: change default installation path to C:\NASM**

   https://www.nasm.us/pub/nasm/releasebuilds/2.15.05/win64/nasm-2.15.05-installer-x64.exe
   
## Install the **Windows 8.1 SDK**, needed for the VS2015 based EDK2 buildprocess.<br>
**Windows 8.1 SDK** is provided in the Microsoft SDK archive at:<br> https://developer.microsoft.com/en-us/windows/downloads/sdk-archive, <br>or direct link: <br>
https://go.microsoft.com/fwlink/p/?LinkId=323507<br>
   NOTE: **Windows 8.1 SDK** is removed from VS2022, but still available with VS2017. VS2017 itself is not available
   anymore for free.

## Install FLEX/BISON to C:\GnuWin32\bin, needed for the ACPI/ACPICA project<br>
https://acpica.org/downloads/windows-source<br>
   i. add **C:\GnuWin32\bin** to [path](README.md#finally-adjust-path-variable)

   
# Nice to have / optional
## Install BeyondCompare -> https://www.scootersoftware.com/BCompare-4.4.2.26348.exe<br>
## Install tortoiseGIT: https://download.tortoisegit.org/tgit/2.11.0.0/TortoiseGit-2.11.0.0-64bit.msi
add to `%USERPROFILE%\.gitconfig`:<br>
```
[diff]
  tool = bc4
[difftool "bc4"]
  cmd = \"C:\\Program Files\\Beyond Compare 4\\BCompare.exe\" \"$LOCAL\" \"$REMOTE\"
[difftool]
  prompt = false
[merge]
  tool = bc4
[mergetool "bc4"]
  cmd = \"C:\\Program Files\\Beyond Compare 4\\BCompare.exe\" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\"
  trustExitCode = true
```
## Install Acrobat Reader DC  -> https://get.adobe.com/reader/otherversions/<br>
## Install compression tools<br>
   i. WinRar -> https://www.rarlab.com/rar/winrar-x64-571.exe<br>
   ii. 7Zip -> https://www.7-zip.org/a/7z1900-x64.exe<br>
## Install FTDI serial-USB driver -> https://www.ftdichip.com/Drivers/CDM/CDM21228_Setup.zip<br>
## Install TeraTerm -> https://ttssh2.osdn.jp/index.html.en<br>
## Install DoxyGen -> https://sourceforge.net/projects/doxygen/files/latest/download<br>
   install HTML Help Workshop -> https://www.microsoft.com/en-us/download/confirmation.aspx?id=21138&6B49FDFB-8E5B-4B07-BC31-15695C5A2143=1
## Install Latex -> https://miktex.org/download/ctan/systems/win32/miktex/setup/windows-x64
## Install Windows Subsystem for Linux WSL2 / Ubuntu 20.04

**NOTE: In order to run WSL2 on a HYPER-V virtual machine, enable Nested Virtualization on the Hyper-V Manager for this particular virtual machine, while the VM is in OFF state:**

* run PowerShell as administrator: `Set-VMProcessor <"VIRTUALMACHINENAME"> -ExposeVirtualizationExtensions $true`
* in case the *Virtual Machine Name* includes special characters, e.g. (), use quotation marks

![HyperVMgmt](HyperVMgmt.png)

https://docs.microsoft.com/en-us/windows/wsl/install-win10
	
**NOTE: In order to start WSL2 you have to run as an administrator:**
`bcdedit /set hypervisorlaunchtype auto`
	
* download install script:<br>
  `wget https://raw.githubusercontent.com/KilianKegel/HowTo-setup-a-YOCTO-Development-PC/master/install.sh`
* set x attribute: `chmod +x install.sh`
* run `./install.sh`
	
## Disable Microsoft Defender: 
### Windows 10: 
1. ```Regedit -> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware = 1```
### Windows 11: 
1. Windows security: Tamper Protection: DISABLE
2. ```GPEDIT.MSC -> Administrative Templates\Windows Components\Microsoft Defender Antivirus\Turn off Microsoft Defender Antivirus = Enabled```

## Install yED https://www.yworks.com/products/yed/download
## Install QT http://download.qt.io/official_releases/qt/5.14/5.14.2/qt-opensource-windows-x86-5.14.2.exe
## Install GIMP https://download.gimp.org/mirror/pub/gimp/v2.10/windows/gimp-2.10.22-setup.exe
## Install BGINFO https://download.sysinternals.com/files/BGInfo.zip
* copy BGINFO64.EXE to %USERPROFILE%\AppData\Local\Microsoft\WindowsApps
* create %USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\BGINFO.BAT that contains:
	```
	BGINFO64.EXE /timer:0
	```
## Install File Commander FCW https://www.heise.de/download/product/file-commander-7157/download/danke?id=7157-1

### finally: adjust PATH variable
![envedit.png](envedit.png)<br>
1: windows-R -> control.exe -> User Accounts -> Change my environment variables<br>
2. add to PATH:<br>
```
c:\progra~1\beyond~1                           --> bcompare.exe
c:\progra~1\winrar                             --> rar.exe
c:\progra~1\7-zip                              --> 7z.exe
c:\progra~2\teraterm                           --> ttermpro.exe
c:\progra~2\FILECO~1                           --> fcw.exe
c:\progra~1\MICROS~1\2022\COMMUN~1\Common7\ide --> devenv.exe
c:\GnuWin32\bin                                --> FLEX/BISON
```
### Vintage DDK
* Windows Server 2003 SP1 DDK: http://download.microsoft.com/download/9/0/f/90f019ac-8243-48d3-91cf-81fc4093ecfd/1830_usa_ddk.iso<br>
* WDK 7.1.0: http://download.microsoft.com/download/4/a/2/4a25c7d5-efbe-4182-b6a9-ae6850409a78/grmwdk_en_7600_1.iso <br>
* MICROSOFT ENTERPRISE WINDOWS DRIVER KIT: https://go.microsoft.com/fwlink/p/?LinkID=846038
### Microsoft DDK download page
* [Download the Windows Driver Kit (WDK)](https://learn.microsoft.com/en-us/windows-hardware/drivers/download-the-wdk)
* [Other WDK downloads](https://learn.microsoft.com/en-us/windows-hardware/drivers/other-wdk-downloads)
