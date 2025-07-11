# Amadey – YARA Pattern Notes

## Static Strings
- `"cred64.dll"` and `"clip64.dll"` – modules downloaded and sideloaded
- `"Global\\WindowsUpdate"` – known mutex
- `soft\\Microsoft\\Windows\\CurrentVersion\\Uninstall` – registry persistence key
- C2 control panel often responds at `/index.php`

## Behavioral Indicators
- Execution chain: `.exe → .dll → .exe`
- URLs follow pattern: `http://[IP]/[string]/index.php`
- C2 panel reused from older campaigns (common across variants)
- Login screen appears as generic HTML login form with label: `Unlock`

## Traffic Patterns
- Amadey implants use direct IP + string combo as C2 path
- Example: `http://[IP_address]/[string]/index.php`
- Known download artifacts: `cred64.dll`, `clip64.dll`

## Related YARA Rules
- [amadey_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/amadey_basic.yar)  
- [amadey_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/amadey_behavior.yar)
