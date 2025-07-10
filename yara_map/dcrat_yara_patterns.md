# DcRAT – YARA Pattern Notes

## Static Strings

- `"DC-Software"`
- `"DCRatClient"`
- `"ClientInstall"`
- `"Stub\\Config"`
- `"Software\\Microsoft\\Windows\\CurrentVersion\\Run"`

## Mutex Patterns

- `DCRAT_MUTEX` or custom-named mutex from builder

## .NET / Assembly Markers

- `System.Net.Sockets`
- `System.Reflection.Assembly`
- `System.Resources.ResourceManager`
- Binary often packed or obfuscated with stub loader

## Registry Keys (Persistence)

- `HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Run`
  - Registry key for persistence, often manually named

## Execution Artifacts

- `cmd.exe /c start`
- `powershell -nop -w hidden -enc <base64>`
- `InstallUtil` used in service-based or loader variants
- DLL side-loading from PE wrappers observed

## In-Memory Indicators

- `"dcrat"` (appears in memory even if obfuscated on disk)
- `"MUTEX"` (often a standalone memory string)
- `"Server 1"` (from hardcoded config labels)
- `"duckdns"` (common in C2 infrastructure)
- `"qwqdanchun"` (older builder/variant tag)

## Related YARA Rules

- [dcrat_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/dcrat_basic.yar)  
- [dcrat_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/dcrat_behavior.yar)
