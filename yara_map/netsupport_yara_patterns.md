# NetSupport Manager – YARA Pattern Notes

## Static Strings
- `"client32.ini"` (main configuration file)
- `[Client]`, `Name=`, `GatewayAddress=`, `GatewayPort=`
- `"InstallPath="`, `"ConnectivityMode="`

## Behavioral Indicators
- Powershell with `-EncodedCommand` used to download stage 2
- Initial `.bat` file runs `.ps1` to download payload zip
- Zip contains:
  - `client32.exe`
  - `client32.dll`
  - `client32.ini`  
- C2 and campaign name stored in the `.ini` file  
- Default directory: `NetSupport\\client32\\`

## TTP Highlights
- Used in HTML/JS malspam delivery campaigns
- Highly abused for stealthy RAT access
- Powershell downloaders often obfuscated

## Related YARA Rules
- [netsupport_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/netsupport_basic.yar)  
- [netsupport_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/netsupport_behavior.yar)
