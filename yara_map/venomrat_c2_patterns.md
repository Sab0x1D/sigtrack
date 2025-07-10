# VenomRAT – YARA Pattern Notes

## Static Strings
- "VenomMutex"
- "Venom RAT Client"
- "/gate.php"
- "Username"
- "Password"
- "Basic "
- "TVqQAAMAAAAEAAAA" (base64-encoded 'MZ')

## Mutex Patterns
- Typically hardcoded as "VenomMutex"
- May be customized in builder variants

## .NET / Assembly Markers
- Usually developed in .NET
- May use obfuscated or packed payloads

## Registry Keys (Persistence)
- `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
  - Common value: `"Venom"` or `"Client"`

## Execution Artifacts
- Powershell used to execute payload: `powershell -nop -w hidden`
- May side-load DLLs
- C2 commonly points to `/gate.php` over HTTP

## In-Memory Indicators
- Uses API calls like `VirtualAllocEx`, `WriteProcessMemory`
- Memory injection for remote process control

## Related YARA Rules
- [venomrat_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/venomrat_basic.yar)
- [venomrat_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/venomrat_behavior.yar)
