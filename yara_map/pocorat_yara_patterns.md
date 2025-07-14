# Poco RAT – YARA Pattern Notes

## Static Indicators
- String matches:
  - "PocoClient"
  - "PocoRAT"
  - "startClientSocket"
  - "ClientCommandDispatcher"
  - "UpdateConfigFromServer"
  - Embedded Poco C++ framework references:
  - `poco-1.12.4-all\\foundation\\include\\poco`
  - `Poco`
- Embedded IP/C2 Indicators:
  - `94.131.119.126`
  - `193.233.203.63`
- File artifacts:
  - `cttune.exe`

## Behavioral Indicators
- Connects back via `startClientSocket`
- Dispatches commands using `ClientCommandDispatcher`
- Updates runtime config via `UpdateConfigFromServer`
- Static string “PocoRAT” seen across multiple unpacked samples
- Mutex name: “PocoClient”
- Threat chain: `url → .rev → exe → cttune.exe`
- Process tree:
  - CP09274.exe → dllhost.exe → cttune.exe
- Will beacon out to known C2 (94.131.119.126)
- May unzip `.rev` into PE artifacts

## Related YARA Rules
- [pocorat_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/pocorat_basic.yar)  
- [pocorat_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/pocorat_behavior.yar)
