# Astaroth – YARA Pattern Notes

## Execution Patterns
- `"regsvr32.exe"` and `"wmic.exe"` abused for LOLBin execution
- `"regsvr32 /s /n /u /i"` used to invoke DLLs without GUI
- `"powershell -windowstyle hidden"` in multiple stages

## DLL & File Indicators
- `"efswrt.dll"` and `"ntdskutl.dll"` commonly dropped and registered
- Dropper or loader may be hidden in AppData or TEMP folders

## Credential Theft Indicators
- `"System.Security.Cryptography"` or `"DPAPI"` access
- `"MachineGuid"` from registry under `SOFTWARE\\Microsoft\\Cryptography`
- May perform `"FromBase64String"` decoding in PowerShell

## In-Memory Traits
- Often heavily obfuscated .NET loaders
- Unpacked modules loaded in runtime memory

## Related YARA Rules
- [astaroth_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/astaroth_basic.yar)
- [astaroth_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/astaroth_behavior.yar)
