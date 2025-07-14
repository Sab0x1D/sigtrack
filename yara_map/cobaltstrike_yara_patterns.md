# Cobalt Strike – YARA Pattern Mapping

## Static Indicators
- Malleable C2 configs often contain:
  - `stage.cleanup`, `Malleable_C2`, or `cobaltstrike`
- Pipes and internal references:
  - `\\\\.\\pipe\\msagent_*`
- Common launch commands:
  - `"powershell -nop -w hidden"`
- May contain hardcoded URL paths like `/submit.php`, `/profile.php`

## Behavioral Indicators
- **Latest infection chain**:
  - `.html` from Google Drive  
  ⮕  `.zip` (pw protected)  
  ⮕  `.iso` with `.lnk`, `.pdf`, and log files  
  ⮕  `.lnk` launches PowerShell  
  ⮕  Downloads Beacon  
  ⮕  Executes only if `whoami` or region checks are passed
- Execution often results in an outbound C2 callback, followed by possible ransomware stage

## Related YARA Rules
- [cobaltstrike_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/cobaltstrike_basic.yar)  
- [cobaltstrike_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/cobaltstrike_behavior.yar)
