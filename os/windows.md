# Windows



in your user folder put:

`aliases.bat`

```
@echo off

:: Navigation
doskey ls=dir /b /a
doskey ll=dir /a
doskey pwd=cd

:: File operations
doskey cp=copy $*
doskey mv=move $*
doskey rm=del $*
doskey mkdir=mkdir $*
doskey rmdir=rmdir $*
doskey touch=type nul ^> $*

:: Viewing files
doskey cat=type $*
doskey less=more $*
doskey head=powershell -NoProfile -Command "Get-Content $1 -TotalCount 20"
doskey tail=powershell -NoProfile -Command "Get-Content $1 -Tail 20"

:: Search
doskey grep=findstr $*
doskey which=where $*

:: System/process
doskey ps=tasklist
doskey kill=taskkill /PID $1 /F

:: Disk usage (df-like)
doskey df=powershell -NoProfile -Command "Get-PSDrive -PSProvider FileSystem | Select Name,@{N='Used(GB)';E={[math]::Round(($_.Used/1GB),2)}},@{N='Free(GB)';E={[math]::Round(($_.Free/1GB),2)}}"

:: Convenience
doskey clear=cls
doskey clr=cls
```



#### 2) Register it in the Windows Registry (AutoRun)

Create a `.reg` file like this:

```
Windows Registry Editor Version 5.00[HKEY_CURRENT_USER\Software\Microsoft\Command Processor]"AutoRun"="C:\\cmd\\aliases.bat"
```

Save as:

```
enable-cmd-autoload.reg
```

Double-click it to apply.

```
[HKEY_CURRENT_USER\Software\Microsoft\Command Processor]
"AutoRun"="C:\\currentuserpath\\aliases.bat"
```



```
reg add "HKCU\Software\Microsoft\Command Processor" ^
 /v AutoRun ^
 /t REG_SZ ^
 /d "C:\cmd\aliases.bat" ^
 /f
```
