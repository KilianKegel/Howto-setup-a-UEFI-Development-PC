# HowTo-setup-an-UEFI-Development-PC

1. install a Windows 10 64 PC<br>
   i.  get MediaCreationTool https://go.microsoft.com/fwlink/?LinkId=691209 and download Win10 1903<br>
2. install GIT: https://github.com/git-for-windows/git/releases/download/v2.23.0.windows.1/Git-2.23.0-64-bit.exe<br>
   NOTE: update to *GIT v2.23* because of [fixed submodule issue](https://github.com/git/git/blob/v2.23.0/Documentation/RelNotes/2.23.0.txt)
3. install/extract the ASL/ACPI compiler to C:\ASL -> https://acpica.org/sites/acpica/files/iasl-win-20160527.zip
4. install Python<br>
   i. for old build process: ver 2.7 to C:\Python27 -> https://www.python.org/ftp/python/2.7/python-2.7.amd64.msi<br>
   ii.for new build process: ver 3.7 https://www.python.org/ftp/python/3.7.4/python-3.7.4-amd64.exe<br>
   NOTE: If Python is installed from the Microsoft AppStore it can not be de-installed anymore!
5. install Netwide Assembler ver. 2.13 to C:\NASM (NOTE: change default installation path) -> 

   https://www.nasm.us/pub/nasm/releasebuilds/2.13/win64/nasm-2.13-installer-x64.exe
6. install Visual Studio 2019<br>
   https://docs.microsoft.com/en-us/visualstudio/releases/2019/release-notes<br>
   ![installselection2019](VS2019-components.png)
7. install the **Windows 8.1 SDK**, needed for the VS2015 based EDK2 buildprocess.<br>
**Windows 8.1 SDK** is provided in the Microsoft SDK archive at:<br> https://developer.microsoft.com/en-us/windows/downloads/sdk-archive, <br>or direct link: <br>
https://go.microsoft.com/fwlink/p/?LinkId=323507<br>
   NOTE: **Windows 8.1 SDK** is removed from VS2019, but still available with VS2017. VS2017 itself is not available
   anymore for free.
   
## Nice to have / optional
8. install tortoiseGIT: https://download.tortoisegit.org/tgit/2.8.0.0/TortoiseGit-2.8.0.0-64bit.msi
9. install BeyondCompare -> https://www.scootersoftware.com/BCompare-4.2.10.23938.exe<br>
   i. add to `%USERPROFILE%\.gitconfig`<br>
   `[diff]`<br>
	`  tool = bc4`<br>
   `[difftool "bc4"]`<br>
	   `  cmd = \"C:\\Program Files\\Beyond Compare 4\\BCompare.exe\" \"$LOCAL\" \"$REMOTE\"`<br>
   `[difftool]`<br>
	   `  prompt = false`<br>
   `[merge]`<br>
	   `  tool = bc4`<br>
   `[mergetool "bc4"]`<br>
	   `  cmd = \"C:\\Program Files\\Beyond Compare 4\\BCompare.exe\" \"$LOCAL\" \"$REMOTE\" \"$BASE\" \"$MERGED\"`<br>
	   `  trustExitCode = true`<br>
10. install Acrobat Reader DC  -> https://get.adobe.com/reader/otherversions/<br>
11. install compression tools<br>
   i. WinRar -> https://www.rarlab.com/rar/winrar-x64-571.exe<br>
   ii. 7Zip -> https://www.7-zip.org/a/7z1900-x64.exe<br>
12. install FTDI serial-USB driver -> https://www.ftdichip.com/Drivers/CDM/CDM21228_Setup.zip<br>
13. install TeraTerm -> https://ttssh2.osdn.jp/index.html.en<br>
14. install DoxyGen -> https://sourceforge.net/projects/doxygen/files/latest/download<br>
   install HTML Help Workshop -> https://www.microsoft.com/en-us/download/confirmation.aspx?id=21138&6B49FDFB-8E5B-4B07-BC31-15695C5A2143=1
15. install Latex -> https://miktex.org/download/ctan/systems/win32/miktex/setup/windows-x64/basic-miktex-2.9.7219-x64.exe 
16. install Windows Subsystem for Linux WSL:<br>
  1. run PowerShell (as administrator): Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux<br>
  2.install Ubuntu 18.4: https://aka.ms/wsl-ubuntu-1804<br>
  3. run in the linux shell: sudo apt update<br>
  4. run in the linux shell: sudo apt install gcc<br>
  5. run in the linux shell: sudo apt install gdb<br>
17. disable Microsoft Defender: Regedit -> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware = 1

### vintage DDK
* Windows Server 2003 SP1 DDK: http://download.microsoft.com/download/9/0/f/90f019ac-8243-48d3-91cf-81fc4093ecfd/1830_usa_ddk.iso<br>
* WDK 7.1.0: http://download.microsoft.com/download/4/a/2/4a25c7d5-efbe-4182-b6a9-ae6850409a78/grmwdk_en_7600_1.iso <br>

