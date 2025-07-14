# Grandoreiro Banking Trojan – YARA Pattern Notes

## Static Indicators
- Strings:
  - "hacker2bank"
  - "Shell_TrayWnd" (overlay window reference)
  - "WinSta0\\Default" (mutex/session indicator)
  - Use of `SetWindowsHookExA`
  - Hardcoded path: `C:\ProgramData\%s\%s.exe`

## Behavioral Indicators
- Uses mutex or window station: `WinSta0\Default`
- Installs persistence under `Software\Microsoft\Windows\CurrentVersion\Run`
- Overlay behavior via `Shell_TrayWnd`
- C2 communication often to `/api/v1/` endpoints
- Deploys under `C:\ProgramData\` directory

## Related YARA Rules
- [grandoreiro_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/grandoreiro_basic.yar)  
- [grandoreiro_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/grandoreiro_behavior.yar)
