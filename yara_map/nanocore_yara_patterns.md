# Nanocore RAT – YARA Pattern Notes

## Static Indicators
- String matches:
  - "Nanocore Client"
  - "ClientPluginHost"
  - "StartModule"
  - "NanoHost" (mutex)
  - Registry strings: `runonce`, `Software\Microsoft\Windows\CurrentVersion\RunOnce`

## Behavioral Indicators
- Loads client modules/plugins via “ClientPluginHost”
- Spawns thread with `StartModule`
- Drops persistence keys in `RunOnce`
- Often uses `LoadLibraryW` to dynamically invoke DLLs
- Common mutex label: “NanoHost”

## Related YARA Rules
- [nanocore_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/nanocore_basic.yar)  
- [nanocore_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/nanocore_behavior.yar)
