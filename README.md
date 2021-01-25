# HowTo-setup-an-UEFI-Development-PC

#### 1. install a Windows 10 64 PC<br>
   i.  get `MediaCreationTool` https://go.microsoft.com/fwlink/?LinkId=691209 and download Win10<br>
#### 2. install Visual Studio 2019<br>
   https://docs.microsoft.com/en-us/visualstudio/releases/2019/release-notes<br>
   ![installselection2019](VS2019-components.png)
   
   **NOTE: For [Visual-Studio-for-UEFI-Shell](https://github.com/KilianKegel/Visual-Studio-for-UEFI-Shell)-only development you can stop the installation here**
   
#### 3. install GIT: https://github.com/git-for-windows/git/releases/download/v2.29.0.windows.1/Git-2.29.0-64-bit.exe<br>
#### 4. install/extract the ASL/ACPI compiler to C:\ASL -> https://acpica.org/sites/acpica/files/iasl-win-20160527.zip
#### 5. install Python<br>
   i. for old build process: ver 2.7 to C:\Python27 -> https://www.python.org/ftp/python/2.7/python-2.7.amd64.msi<br>
   ii.for new build process: ver 3.7 https://www.python.org/ftp/python/3.7.4/python-3.7.4-amd64.exe<br>
   NOTE: If Python is installed from the Microsoft AppStore it can not be de-installed anymore!
#### 6. install Netwide Assembler ver. 2.13 to C:\NASM 

**NOTE: change default installation path to C:\NASM**

   https://www.nasm.us/pub/nasm/releasebuilds/2.13/win64/nasm-2.13-installer-x64.exe
   
#### 7. install the **Windows 8.1 SDK**, needed for the VS2015 based EDK2 buildprocess.<br>
**Windows 8.1 SDK** is provided in the Microsoft SDK archive at:<br> https://developer.microsoft.com/en-us/windows/downloads/sdk-archive, <br>or direct link: <br>
https://go.microsoft.com/fwlink/p/?LinkId=323507<br>
   NOTE: **Windows 8.1 SDK** is removed from VS2019, but still available with VS2017. VS2017 itself is not available
   anymore for free.
   
## Nice to have / optional
#### 8. install BeyondCompare -> http://www.scootersoftware.com/BCompare-4.3.7.25118.exe<br>
#### 9. install tortoiseGIT: https://download.tortoisegit.org/tgit/2.11.0.0/TortoiseGit-2.11.0.0-64bit.msi
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
#### 10. install Acrobat Reader DC  -> https://get.adobe.com/reader/otherversions/<br>
#### 11. install compression tools<br>
   i. WinRar -> https://www.rarlab.com/rar/winrar-x64-571.exe<br>
   ii. 7Zip -> https://www.7-zip.org/a/7z1900-x64.exe<br>
#### 12. install FTDI serial-USB driver -> https://www.ftdichip.com/Drivers/CDM/CDM21228_Setup.zip<br>
#### 13. install TeraTerm -> https://ttssh2.osdn.jp/index.html.en<br>
#### 14. install DoxyGen -> https://sourceforge.net/projects/doxygen/files/latest/download<br>
   install HTML Help Workshop -> https://www.microsoft.com/en-us/download/confirmation.aspx?id=21138&6B49FDFB-8E5B-4B07-BC31-15695C5A2143=1
#### 15. install Latex -> https://miktex.org/download/ctan/systems/win32/miktex/setup/windows-x64
#### 16. install Windows Subsystem for Linux WSL2 / Ubuntu 20.04

**NOTE: In order to run WSL2 on a HYPER-V virtual machine, enable Nested Virtualization on the Hyper-V Manager for this particular virtual machine, while the VM is in OFF state:**

* run PowerShell as administrator: `Set-VMProcessor <"VIRTUALMACHINENAME"> -ExposeVirtualizationExtensions $true`
* in case the *Virtual Machine Name* includes special characters, e.g. (), use quotation marks

![HyperVMgmt](HyperVMgmt.png)

https://docs.microsoft.com/en-us/windows/wsl/install-win10
	
**NOTE: In order to start WSL2 you have to run as an admnistrator:**
`bcdedit /set hypervisorlaunchtype auto`
	
* download install script:<br>
  `wget https://raw.githubusercontent.com/KilianKegel/HowTo-setup-a-YOCTO-Development-PC/master/install.sh`
* set x attribute: `chmod +x install.sh`
* run `./install.sh`
	
#### 18. disable Microsoft Defender: Regedit -> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware = 1
#### 19. install yED https://www.yworks.com/products/yed/download
#### 20. install QT http://download.qt.io/official_releases/qt/5.14/5.14.2/qt-opensource-windows-x86-5.14.2.exe
#### 21. install GIMP https://download.gimp.org/mirror/pub/gimp/v2.10/windows/gimp-2.10.22-setup.exe
#### 22. install BGINFO https://download.sysinternals.com/files/BGInfo.zip
* copy BGINFO64.EXE to %USERPROFILE%\AppData\Local\Microsoft\WindowsApps
* create %USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\BGINFO.BAT that contains:
	```
	BGINFO64.EXE /timer:0
	```
#### lastly: adjust PATH variable
1: windows-R -> control.exe -> User Accounts -> Change my environment variables<br>
2. add to PATH:<br>
```
c:\progra~1\beyond~1
c:\progra~1\winrar
c:\progra~1\7-zip
c:\progra~2\teraterm
```

### vintage DDK
* Windows Server 2003 SP1 DDK: http://download.microsoft.com/download/9/0/f/90f019ac-8243-48d3-91cf-81fc4093ecfd/1830_usa_ddk.iso<br>
* WDK 7.1.0: http://download.microsoft.com/download/4/a/2/4a25c7d5-efbe-4182-b6a9-ae6850409a78/grmwdk_en_7600_1.iso <br>
* MICROSOFT ENTERPRISE WINDOWS DRIVER KIT: https://go.microsoft.com/fwlink/p/?LinkID=846038

