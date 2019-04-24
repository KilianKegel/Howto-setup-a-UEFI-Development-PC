# HowTo-setup-an-UEFI-Development-PC

1. install a Windows 10 64 PC<br>
   i.  get MediaCreationTool https://go.microsoft.com/fwlink/?LinkId=691209 and download Win10 1809<br>
2. install GIT: https://github.com/git-for-windows/git/releases/download/v2.20.1.windows.1/Git-2.20.1-64-bit.exe
3. install tortoiseGIT: https://download.tortoisegit.org/tgit/2.7.0.0/TortoiseGit-2.7.0.0-64bit.msi
4. install/extract the ASL/ACPI compiler to C:\ASL -> https://acpica.org/sites/acpica/files/iasl-win-20160527.zip
5. install Python ver 2.7 to C:\Python27 -> https://www.python.org/ftp/python/2.7/python-2.7.amd64.msi
6. install Netwide Assembler ver. 2.13 to C:\NASM (NOTE: change default installation path) -> 

   https://www.nasm.us/pub/nasm/releasebuilds/2.13/win64/nasm-2.13-installer-x64.exe
7. install Visual Studio 2017

   choose version: https://visualstudio.microsoft.com/downloads/

   community version: https://visualstudio.microsoft.com/thank-you-downloading-visual-studio/?sku=Community&rel=15
## Nice to have / optional
8. install BeyondCompare -> http://www.scootersoftware.com/BCompare-4.2.9.23626.exe
9. install DoxyGen -> https://sourceforge.net/projects/doxygen/files/latest/download<br>
   install HTML Help Workshop -> https://www.microsoft.com/en-us/download/confirmation.aspx?id=21138&6B49FDFB-8E5B-4B07-BC31-15695C5A2143=1
10. install Latex -> https://miktex.org/download/ctan/systems/win32/miktex/setup/windows-x64/basic-miktex-2.9.7031-x64.exe
11. install Windows Subsystem for Linux WSL:<br>
  i. run PowerShell (as administrator): Enable-WindowsOptionalFeature -Online -FeatureName Microsoft-Windows-Subsystem-Linux<br>
  ii.install Ubuntu 18.4: https://aka.ms/wsl-ubuntu-1804<br>
  iii. run in the linux shell: sudo apt update<br>
  iv.  run in the linux shell: sudo apt install gcc<br>
12. disable Microsoft Defender: Regedit -> HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\DisableAntiSpyware = 1
