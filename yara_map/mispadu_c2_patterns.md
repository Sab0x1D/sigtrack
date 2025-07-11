# Mispadu – YARA Pattern Notes

## Static Indicators
- `"AutoIt v3 Script has stopped working"`
- `"Introduzca la contrasena"`
- `.hta`, `.vbs`, `"C:\Users\Public"`
- `host.secureserver.net`, C2 IPs (e.g., `182.232.109.208`, `107.189.17.17`)

## Behavior Chain
- Email attachment or URL → password-protected ZIP
- ZIP → HTA → VBS → AutoIt EXE (random filename)
- Files dropped to `C:\Users\Public` with distraction prompts
- AutoIt EXE errors shown as decoy

## Execution Traits
- AutoIt interpreter used for final payload
- Often requires Argentina VPN for VBS second-stage to drop
- Mimics document downloads, often themed as invoices

## Related YARA Rules
- [mispadu_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/mispadu_basic.yar)  
- [mispadu_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/mispadu_behavior.yar)
