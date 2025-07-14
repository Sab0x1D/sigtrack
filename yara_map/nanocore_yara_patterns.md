# NanoCore – YARA Pattern Mapping

## Static Indicators
- Executable strings:
  - `"NanoCore Client"`, `"RegSvcs.exe"`, `duckdns.org`, `login.nanocore.io`
- Common mutex:
  - Found in embedded strings: `NanoCore`
- Pipe name indicators:
  - `\\\\.\\pipe\\NanoCore`

## Behavioral Indicators
- Payload often drops as a `.NET` executable
- Will **spawn `RegSvcs.exe`** after execution
- C2 comms visible in **Process Hacker's network tab**
- Uses **`duckdns.org`** in infrastructure (C2 or dynamic DNS resolution)
- May persist via registry or scheduled task

## Related YARA Rules
- [nanocore_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/nanocore_basic.yar)  
- [nanocore_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/nanocore_behavior.yar)
