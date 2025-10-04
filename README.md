# How to Set Up a UEFI Development PC

**NOTE:** To build all projects from https://github.com/KilianKegel the tools below are needed:
* NASM
* ASL
* *Obsolete:* Windows 8.1 SDK (for EDK2020-MinnowBoard)
* FLEX / BISON (for the `Visual-ACPICA-for-UEFI-Shell` project)

## Preparation for Upcoming Portable Projects
**NOTE:** To avoid build failures caused by incomplete or misconfigured build machines, upcoming and updated projects run their build tools locally within the project folder.

### Always start with `LAUNCH.BAT`!<br>The build environment is installed (once) locally and the environment (`PATH`) is initialized every time you start `LAUNCH.BAT`.

Currently the tools listed below are in use:
* [wget.exe](https://eternallybored.org/misc/wget/1.21.3/64/wget.exe) – downloads any missing tools during the initial `LAUNCH.BAT` run (or manually via a web search)
* [EnterpriseWDK_rs2_release_15063_20170317-1834.zip](https://go.microsoft.com/fwlink/p/?LinkID=846038) – Microsoft EWDK 1703
* [nasm-2.16.01-win64.zip](https://www.nasm.us/pub/nasm/releasebuilds/2.16.01/win64/nasm-2.16.01-win64.zip) – NASM assembler
* [python-3.10.11-embed-win64.zip](https://www.python.org/ftp/python/3.10.11/python-3.10.11-embed-amd64.zip) – Embedded Python
* [openssl-1.0.2r-x64_86-win64.zip](https://indy.fulgan.com/SSL/openssl-1.0.2r-x64_86-win64.zip) – OpenSSL
* [iasl-win-20230628.zip](https://downloadmirror.intel.com/783546/iasl-win-20230628.zip) – Intel ASL compiler
* [flex-2.5.4a-1-bin.zip](https://downloads.sourceforge.net/project/gnuwin32/flex/2.5.4a-1/flex-2.5.4a-1-bin.zip) – Lexical analyzer generator
* [bison-2.4.1-bin.zip](https://downloads.sourceforge.net/project/gnuwin32/bison/2.4.1/bison-2.4.1-bin.zip) – Parser generator
* [libintl-0.14.4-bin.zip](https://downloads.sourceforge.net/project/gnuwin32/libintl/0.14.4/libintl-0.14.4-bin.zip) – Support DLL for FLEX/BISON
* [libiconv-1.9.2-1-bin.zip](https://downloads.sourceforge.net/project/gnuwin32/libiconv/1.9.2-1/libiconv-1.9.2-1-bin.zip) – Support DLL for FLEX/BISON
* [regex-2.7-bin.zip](https://downloads.sourceforge.net/project/gnuwin32/regex/2.7/regex-2.7-bin.zip) – Support DLL for FLEX/BISON

To avoid multiple lengthy downloads, the original archives can optionally be downloaded once per build machine and stored in a folder referenced by the environment variable `MYDOWNLOADS`.

![MYDOWNLOADSfolder](https://github.com/KilianKegel/pictures/blob/master/MYDOWNLOADS.png)

To set this up:
1. Create a folder `MYDOWNLOADS`, e.g. run: `cmd /c MD %USERPROFILE%\MYDOWNLOADS`
2. Press Win+R → `control.exe` → User Accounts → Change my environment variables
3. Create environment variable `MYDOWNLOADS`, e.g. `MYDOWNLOADS=%USERPROFILE%\MYDOWNLOADS`
4. (Optional) Create environment variable `MYUSBSHARE`, e.g. `MYUSBSHARE=F:\` to automatically copy target files to an exchange drive via batch files or Visual Studio build events

![envedit.png](envedit.png)

## Install a Windows 11/10 PC
* Download the Media Creation Tool for Windows 11: https://go.microsoft.com/fwlink/?linkid=2156295
  or
* Download the Media Creation Tool for Windows 10: https://go.microsoft.com/fwlink/?LinkId=691209

### Windows 11 Configuration Hint
Restore the classic (full) context menu in Windows. Run in a Command Prompt:
```
reg add HKCU\Software\Classes\CLSID\{86ca1aa0-34aa-4e8b-a509-50c905bae2a2}\InprocServer32 /ve /d "" /f
```

### Private Activation Keys (References)
* [Windows Pro Activation key](https://github.com/KilianKegel/remember/blob/master/Win10ProActivation.md)
* [Windows Pro N and KN Activation key](https://github.com/KilianKegel/remember/blob/master/Win10ProNActivation.md)

## Install Visual Studio
![](https://github.com/KilianKegel/pictures/blob/master/VS2026.png)
1. Download: https://visualstudio.microsoft.com/insiders
2. Configure setup (optional for LLVM/Clang support):
   ![installselection2026](https://github.com/KilianKegel/pictures/blob/master/VS2026-components.png)

## Install Git
https://github.com/git-for-windows/git/releases/download/v2.50.1.windows.1/Git-2.50.1-64-bit.exe

## Install / Extract the ASL / ACPI Compiler
Extract to `C:\ASL` from: https://acpica.org/sites/acpica/files/iasl-win-20160527.zip

## Install Python
https://www.python.org/ftp/python/3.7.4/python-3.7.4-amd64.exe

NOTE: If Python is installed from the Microsoft Store it cannot be uninstalled normally.

## Install Netwide Assembler (NASM) 2.15.05
Install to `C:\NASM` (change default path):
https://www.nasm.us/pub/nasm/releasebuilds/2.15.05/win64/nasm-2.15.05-installer-x64.exe

## Obsolete: Windows 8.1 SDK
Needed only for the VS2015-based EDK2 build process. Provided in the Microsoft SDK archive:
https://developer.microsoft.com/en-us/windows/downloads/sdk-archive
Direct link: https://go.microsoft.com/fwlink/p/?LinkId=323507

NOTE:
* The Windows 8.1 SDK was removed from VS2022, though still available with VS2017 (no longer freely distributed).
* It is only required to supply the resource compiler `RC.EXE` to the EDK2 build.
* Environment variables `WINSDK81x86_PREFIX` and `WINSDK81_PREFIX` used by EDK2 can be adjusted to point to a newer SDK.

![installselectionWindows8.1SDK](Windows8.1SDK.png)

## Install FLEX / BISON (needed for ACPI / ACPICA project)
Install to: `C:\GnuWin32\bin`
https://acpica.org/downloads/windows-source

Add `C:\GnuWin32\bin` to the PATH (see section: Adjust PATH Variable).

## Nice to Have / Optional Tools
* Beyond Compare: https://www.scootersoftware.com/files/BCompare-4.4.7.28397.exe
* TortoiseGit: https://download.tortoisegit.org/tgit/2.17.0.0/TortoiseGit-2.17.0.2-64bit.msi
  Add to `%USERPROFILE%\.gitconfig`:
  ```
  [diff]
    tool = bc4
  [difftool "bc4"]
    cmd = "C:\\Program Files\\Beyond Compare 4\\BCompare.exe" "$LOCAL" "$REMOTE"
  [difftool]
    prompt = false
  [merge]
    tool = bc4
  [mergetool "bc4"]
    cmd = "C:\\Program Files\\Beyond Compare 4\\BCompare.exe" "$LOCAL" "$REMOTE" "$BASE" "$MERGED"
    trustExitCode = true
  ```
* Acrobat Reader DC: https://get.adobe.com/reader/otherversions/
* Compression tools:
  * WinRAR: https://www.rarlab.com/rar/winrar-x64-571.exe
  * 7-Zip: https://www.7-zip.org/a/7z1900-x64.exe
* FTDI USB-Serial Driver: https://www.ftdichip.com/Drivers/CDM/CDM21228_Setup.zip
* Tera Term: https://ttssh2.osdn.jp/index.html.en
* Doxygen: https://sourceforge.net/projects/doxygen/files/latest/download
* LaTeX (MiKTeX): https://miktex.org/download/ctan/systems/win32/miktex/setup/windows-x64
* WSL2 / Ubuntu 22.04.2

### WSL2 Notes
To run WSL2 inside a Hyper-V virtual machine, enable nested virtualization (with the VM powered off):
```
Set-VMProcessor "<VIRTUALMACHINENAME>" -ExposeVirtualizationExtensions $true
```
If the VM name includes special characters (e.g. parentheses), wrap it in quotes.

Docs: https://docs.microsoft.com/en-us/windows/wsl/install-win10

![ubuntuInstall1](https://github.com/KilianKegel/pictures/blob/master/ubuntuInstall.png)
![ubuntuInstall2](https://github.com/KilianKegel/pictures/blob/master/ubuntuInstall2.png)

To start WSL2 you must run as Administrator:
```
bcdedit /set hypervisorlaunchtype auto
```

Install helper script:
```
wget https://raw.githubusercontent.com/KilianKegel/HowTo-setup-a-YOCTO-Development-PC/master/install.sh
chmod +x install.sh
./install.sh
```

## Disable Microsoft Defender (Optional)
If the build machine is physically protected from malware, you can disable Defender to save resources. Create `DEFDIS.REG` with the content below and run it:
```
Windows Registry Editor Version 5.00

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender]
"DisableAntiSpyware"=dword:00000001
"DisableAntiVirus"=dword:00000001
"DisableRealtimeMonitoring"=dword:00000001
"DisableRoutinelyTakenAction"=dword:00000001
"DisableSpecialRunningModes"=dword:00000001
"ServiceKeepAlive"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Policy Manager]

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Real-Time Protection]
"DisableBehaviourMonitoring"=dword:00000001
"DisableRealtimeMonitoring"=dword:00000001
"DisableScanOnRealtimeEnable"=dword:00000001
"DisableOnAccessProtection"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Signature Updates]
"ForceUpdateFromMU"=dword:00000001

[HKEY_LOCAL_MACHINE\SOFTWARE\Policies\Microsoft\Windows Defender\Spynet]
"DisableBlockAtFirstSeen"=dword:00000001
```

## Install Intel C++ Compiler 2024 Toolchain
https://www.intel.com/content/www/us/en/developer/tools/oneapi/base-toolkit-download.html

NOTE: Recent versions no longer include 32-bit support.

## Additional Optional Software
* yEd: https://www.yworks.com/products/yed/download
* Qt 5.14.2: http://download.qt.io/official_releases/qt/5.14/5.14.2/qt-opensource-windows-x86-5.14.2.exe
* GIMP: https://download.gimp.org/mirror/pub/gimp/v2.10/windows/gimp-2.10.22-setup.exe
* BGInfo: https://download.sysinternals.com/files/BGInfo.zip
  * Copy `BGINFO64.EXE` to `%USERPROFILE%\AppData\Local\Microsoft\WindowsApps`
  * Create `%USERPROFILE%\AppData\Roaming\Microsoft\Windows\Start Menu\Programs\Startup\BGINFO.BAT` containing:
    ```
    BGINFO64.EXE /timer:0
    ```
* File Commander (FCW): https://www.heise.de/download/product/file-commander-7157/download/danke?id=7157-1

### Adjust PATH Variable
![envedit.png](envedit.png)
1. Win+R → `control.exe` → User Accounts → Change my environment variables
2. Append to PATH:
```
c:\progra~1\beyond~1                            # bcompare.exe
c:\progra~1\winrar                              # rar.exe
c:\progra~1\7-zip                               # 7z.exe
c:\progra~2\teraterm                            # ttermpro.exe
c:\progra~2\FILECO~1                            # fcw.exe
c:\progra~1\MICROS~1\2022\COMMUN~1\Common7\ide  # devenv.exe
c:\GnuWin32\bin                                 # FLEX/BISON
```

### Vintage DDK
* Windows Server 2003 SP1 DDK: http://download.microsoft.com/download/9/0/f/90f019ac-8243-48d3-91cf-81fc4093ecfd/1830_usa_ddk.iso
* WDK 7.1.0: http://download.microsoft.com/download/4/a/2/4a25c7d5-efbe-4182-b6a9-ae6850409a78/grmwdk_en_7600_1.iso
* EnterpriseWDK RS2 (15063): https://go.microsoft.com/fwlink/p/?LinkID=846038

### Microsoft DDK Download Pages
* Download the Windows Driver Kit (WDK): https://learn.microsoft.com/en-us/windows-hardware/drivers/download-the-wdk
* Other WDK downloads: https://learn.microsoft.com/en-us/windows-hardware/drivers/other-wdk-downloads
