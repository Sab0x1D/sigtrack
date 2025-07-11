# LokiBot – YARA Pattern Notes

## Static Strings
- `fre.php`
- `profile.php` (used in newer variants as IP-based C2)
- `"aPLib v1.01"` string common in compressed payloads

## Browser Profile Artifacts
- `%s\Mozilla\Firefox\profiles.ini`
- `%s\Mozilla\SeaMonkey\profiles.ini`
- `%s\Thunderbird\profiles.ini`
- `%s\FossaMail\profiles.ini`
- `%s\Comodo\IceDragon\profiles.ini`
- `%s\Cyberfox\profiles.ini`
- `%s\NETGATE Technologies\BlackHawk\profiles.ini`

## Behavioral Indicators
- Targets `profiles.ini` across multiple browsers/mail clients
- Communicates to C2 using `.php` pages, often `fre.php` or `profile.php`
- Payloads often compressed using aPLib
- Commonly seen dropped in `%TEMP%` or `%APPDATA%` with .exe or packed binaries

## Related YARA Rules
- [lokibot_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/lokibot_basic.yar)  
- [lokibot_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/lokibot_behavior.yar)
