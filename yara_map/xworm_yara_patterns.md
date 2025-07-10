# XWorm – YARA Pattern Notes

## Static Strings
- `"Mal_Xwormm"`
- `"aspnet_regbrowsers.exe"`
- `"X09ENE.exe"` (initial dropper)
- `"regsvcs.exe"` (stage loader)

## PowerShell Loader Markers
- `"FromBase64String"` and `"reverse"` used to decode payload
- `"powershell.exe -Command"` typical decode execution
- Base64 payload hosted (e.g., `/files/X09ENE.txt`) and reversed before decoding

## Process Indicators
- `"regsvcs.exe"` runs mid-stage
- `"aspnet_regbrowsers.exe"` final payload
- `"conhost.exe"` often runs alongside payload

## In-Memory Identifiers
- Mutex or string: `"Mal_Xwormm"` detected in memory scanners or strings

## Related YARA Rules
- [xworm_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/xworm_basic.yar)
- [xworm_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/xworm_behavior.yar)
