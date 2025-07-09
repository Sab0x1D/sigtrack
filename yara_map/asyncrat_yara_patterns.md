# AsyncRAT – YARA Pattern Notes

## Static Strings
- `"AsyncRAT Server"`
- `"InstallPath"`
- `"Paste_bin"` or `"Pastebin"`
- `"Settings::StartUp"`
- `"client_socket.Connect"`

## Mutex Patterns
- `AsyncMutex_<RANDOM>`
- `AsyncRatMutex_` in custom builds

## .NET / Assembly Markers
- `System.Management.Automation` (used in PowerShell runner modules)

## Registry Keys (Persistence)
- `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
  - Entry name often: `"Windows Security Update"` or `"System Config"`

## Execution Artifacts
- PowerShell (encoded or staged):
  - `powershell -nop -w hidden -e`
- Command shell:
  - `cmd /c start`
- May run via Task Scheduler or Services

## Related YARA Rules
- [`asyncrat_basic.yar`](https://github.com/Sab0x1D/ghostyara/blob/main/families/asyncrat_basic.yar)
- [`asyncrat_behavior.yar`](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/asyncrat_behavior.yar)
