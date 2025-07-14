# BBTok – YARA Pattern Notes

## Static Strings
- "Insira seu CPF"  
- "Santander Empresas"  
- "Banco do Brasil"  
- "Bradesco Net Empresa"  
- "Itaú Empresas"  
- Mutex: `Global\\BBTOK_MUTEX`

## Registry / Install Paths
- Injected or launched via `RegAsm.exe`
- May use `HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Run` for persistence

## Overlay Artifacts
- Fake overlays rendered with full-screen form prompts
- Strings like "Captura de Tela" or "Senha do Cartão"

## Network Indicators
- Often reaches out to `/bbtok/vnc/index.php`
- May abuse dynamic DNS services for C2

## Related YARA Rules
- [bbtok_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/bbtok_basic.yar)  
- [bbtok_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/bbtok_behavior.yar)
