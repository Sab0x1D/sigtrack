# FormBook – YARA Pattern Notes

## Static Strings
- `ulur` (seen in FormBook POST traffic)
- `http` (embedded cleartext in payload)
- `Form` (embedded form object or class marker)

## Behavioral Indicators
- Uses HTTP POST with parameter `/ulur`
- Targeted form grabber functionality (`Form1`, form fields)
- May include hardcoded `Content-Type: application/x-www-form-urlencoded`
- Known for injecting into browser processes (e.g. explorer.exe, svchost.exe)

## Related YARA Rules
- [formbook_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/formbook_basic.yar)  
- [formbook_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/formbook_behavior.yar)
