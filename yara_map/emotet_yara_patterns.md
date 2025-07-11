# Emotet – YARA Pattern Notes

## Static Indicators
- `"Global\\EMOTET"` – typical mutex
- `"client_version="` or `"srv32"` present in loader config section
- Configs often contain references to `news.php?id=xxxxx`
- Sideloaded DLLs use `"rundll32.exe"` as launcher
- Junk padding like `"aaaaaaaa..."` observed

## Behavioral Traits
- Initial stage typically delivered via macro-enabled `.doc` files
- Powershell execution chain: `-nop -w hidden -enc ...`
- Connects via HTTP POST to C2 paths like `/news.php?id=xxxxx`
- Custom User-Agent string, usually mimicking common browsers
- Observed file types: `.doc`, `.zip`, embedded PE DLLs

## Execution Chain
- .doc → PowerShell → Emotet DLL (in memory) → C2 Beacon

## Related YARA Rules
- [emotet_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/emotet_basic.yar)  
- [emotet_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/emotet_behavior.yar)
