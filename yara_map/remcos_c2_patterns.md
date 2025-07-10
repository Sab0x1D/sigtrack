# Remcos – YARA Pattern Notes

## Static Strings
- `"Remcos.exe"`
- `"Remcos Agent"`
- `"Remcos Agent Initialized"`
- `"Remcos restarted by watchdog!"`
- `"Remcos v"`

## Mutex Patterns
- Hardcoded or watchdog-generated mutex may exist in older variants

## .NET / Assembly Markers
- Often built using unmanaged Delphi or C++ (not .NET)

## Registry Keys (Persistence)
- `HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Run`
  - Common value: `"Remcos"` or `"Remcos Agent"`

## Execution Artifacts
- `cmd.exe /c start` used to spawn payload
- `esentutl.exe` and `colorcpl.exe` as launcher/loader
- May sideload DLLs such as `NPSAPI.dll`
- C2s are often hosted on `duckdns.org` subdomains

## In-Memory Indicators
- `"Remcos Agent Initialized"` (appears in memory)
- `"Remcos restarted by watchdog!"` (behavioral restart loop)
- `"duckdns"` (C2 infrastructure)

## Related YARA Rules
- [remcos_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/remcos_basic.yar)  
- [remcos_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/remcos_behavior.yar)
