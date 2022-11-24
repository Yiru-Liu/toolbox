# Windows Toolbox

## Tell Windows that hardware clock is in UTC, not local time
1. Open an Administrator cmd
2. `reg add "HKEY_LOCAL_MACHINE\System\CurrentControlSet\Control\TimeZoneInformation" /v RealTimeIsUniversal /d 1 /t REG_DWORD /f`

## Display seconds in taskbar
1. Open a cmd
2. `reg add "HKEY_CURRENT_USER\Software\Microsoft\Windows\CurrentVersion\Explorer\Advanced" /v ShowSecondsInSystemClock /t REG_DWORD /d 1 /f`
