# njRAT (Bladabindi) – YARA Pattern Notes

## Static Indicators
- Common string artifacts:
  - "njRAT" (mutex or resource marker)
  - "Client successfully connected"
  - "cmd.exe /c start "
  - Registry path for autorun: `Software\Microsoft\Windows\CurrentVersion\Run`
  - Occasional .NET reflection: `System.Reflection.Assembly`

## Behavioral Indicators
- Installs persistence using `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
- Launches payload using command line execution
- Creates mutex/resource labeled “njRAT”
- Commonly uses `System.Reflection` for runtime loading

## Related YARA Rules
- [njrat_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/njrat_basic.yar)  
- [njrat_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/njrat_behavior.yar)
