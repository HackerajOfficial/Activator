# Disable-Test-Mode

Copy the following code and Save as .cmd or .bat extension and Run as administrator
```
:: Disable TestMode v2.0 - Info and updates at http://maxedtech.com/about-testmode/
@echo off

:: BatchGotAdmin by https://sites.google.com/site/eneerge/scripts/batchgotadmin
:-------------------------------------
REM  --> Check for permissions
>nul 2>&1 "%SYSTEMROOT%\system32\cacls.exe" "%SYSTEMROOT%\system32\config\system"

REM --> If error flag set, we do not have admin.
if '%errorlevel%' NEQ '0' (
    echo Requesting administrative privileges...
    goto UACPrompt
) else ( goto gotAdmin )

:UACPrompt
    echo Set UAC = CreateObject^("Shell.Application"^) > "%temp%\getadmin.vbs"
    echo UAC.ShellExecute "%~s0", "", "", "runas", 1 >> "%temp%\getadmin.vbs"

    "%temp%\getadmin.vbs"
    exit /B

:gotAdmin
    if exist "%temp%\getadmin.vbs" ( del "%temp%\getadmin.vbs" )
    pushd "%CD%"
    CD /D "%~dp0"
:--------------------------------------

:: test mode
@bcdedit /set testsigning off
@echo.
:: error found
IF %ERRORLEVEL% NEQ 0 goto Error
:: no error found
IF %ERRORLEVEL% EQU 0 goto Success

:Error
echo Error occured.
echo.
echo Info at http://maxedtech.com/about-testmode/
goto End

:Success
echo Restart the PC to deactivate the Test Mode. 
echo.
echo Coded By Hackeraj
goto End

:End
echo.
@echo Press any key to exit . . .
@PAUSE >nul
```
More Details article [Click Here](http://hackeraj.raaz.info.np/2021/09/test-mode.html)

[Facebook](https://www.facebook.com/ItsMeHackeraj/)
[Twitter](https://twitter.com/Hackeraj_np/)
[Instagram](https://www.instagram.com/hackeraj/)
[Youtube](https://www.youtube.com/c/HackerajOfficial/)
[Github](https://www.github.com/HackerajOfficial/)

