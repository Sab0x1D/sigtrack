# GULoader – YARA Pattern Notes

## Static Indicators
- API Usage:
  - `StringFromGUID2`
  - `CLSIDFromString`
  - `IsDebuggerPresent`
- Reference to decode site: `https://www.webutils.pl/index.php?idx=...`
- Hash/Artifact: `0293eec0b5432ad092f24065016203b2` (Imphashes)
- Often delivered as XXE-obfuscated payloads

## Behavioral Indicators
- Writes to `%TEMP%` or random folders under `Users\`
- Drops 2 DLLs into those folders
- Folder remains locked until process exits (anti-access technique)
- May show no process tree if payload runs inside a renamed AutoIt or mshta process

## Threat Chain
- XXE obfuscated payload (.xxe or .bin) → manually decoded to .exe
- Executes → drops unpacked payloads to temp/random locations
- Calls sensitive Windows API for environment detection

## Related YARA Rules
- [guloader_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/guloader_basic.yar)  
- [guloader_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/guloader_behavior.yar)
