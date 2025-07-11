# Metamorfo – YARA Pattern Notes

## Static Strings
- `"InstallUtil.exe"`
- `"TeslaBrowser"`, `"mr.temp"`, `"webcache"`, `"wallets"`
- `*AutoHotKey version*`
- `"c2sock"`, `"local state"`, `".fun"`

## JSON Artifacts
- Partial config blob: `{"r":[],"b":[],"g":0}`  
- Often found within unpacked memory

## Behavioral Indicators
- MSI drops `.exe`, `.ahk`, `.dll`, and `.txt` under:
  - `C:\Users\REM\AppData\Local\XXXXXXXX`
- `.txt` file named in `MMYYYY.txt` format (used for staging exfil)
- `.uwg` file as indicator of Mekotio delivery
- AHK scripts spawn AutoHotKey and auxiliary binaries
- Uses `rundll32.exe` to invoke export from dropped DLL
- VM-aware payloads (regional and network aware)
  - VPN gating: Brazil, Mexico, Portugal only

## Crash/Telemetry Indicators
- Watson telemetry reachout triggered by payload
- Crashes fake processes intentionally to obfuscate flow

## Related YARA Rules
- [metamorfo_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/metamorfo_basic.yar)  
- [metamorfo_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/metamorfo_behavior.yar)
