# AsyncRAT – YARA Pattern Notes

## Static Strings

- "AsyncRAT Server"
- "InstallPath"
- "Paste_bin" or "Pastebin"
- "Settings::StartUp"
- "client_socket.Connect"
- "duckdns.org"

## Mutex Patterns

- AsyncMutex_<RANDOM>
- AsyncRatMutex_ in custom builds

## .NET / Assembly Markers

- System.Management.Automation (used in PowerShell runner modules)
- System.Net.Sockets, System.Reflection, System.Threading
- "ExecuteCommand_Context" from encoded function

## Registry Keys (Persistence)

- HKCU\Software\Microsoft\Windows\CurrentVersion\Run
  - Entry name often: "Windows Security Update" or "System Config"

## Execution Artifacts

- PowerShell (encoded or staged):  
  - `powershell -nop -w hidden -e`
- Command shell:  
  - `cmd /c start`
- Binary may be dropped as InstallUtil.exe
- May use Task Scheduler or Services

## In-Memory Indicators

- "AsyncRAT Server0"
- "ExecuteCommand_Context"
- "duckdns.org"
- "InstallUtil.exe" (embedded in memory during runtime)

## Related YARA Rules

- [asyncrat_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/asyncrat_basic.yar)
- [asyncrat_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/asyncrat_behavior.yar)
