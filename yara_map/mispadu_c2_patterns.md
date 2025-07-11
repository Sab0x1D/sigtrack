# Mispadu – YARA Pattern Notes

## Static Strings
- `"AutoIt v3 Script has stopped working"`
- `"host.secureserver.net"`
- `"pastebin.com/raw"`, `"pastery.net"`, `"glitch.me"`

## Execution Chain
- Common threat chain: `PDF attachment → ZIP → HTA → VBS → AutoIT`
- Some variants use `URL → VBS → PS1 → EXE` (e.g., RegAsm.exe)
- HTA drops files into `C:\Users\Public\` and launches VBScript
- Displays fake password prompt to distract the user
- Malicious AutoIT executable is stored in `C:\` with random names

## C2 Infrastructure
- Direct IP-based panels seen:
  - `182.232.109.208`
  - `230.247.109.208`
  - `107.189.17.17`
  - `193.143.167.72`
  - `52.175.153.160`
- Known domains used:
  - `host.secureserver.net`
  - `pastebin.com`, `pastery.net`, `glitch.me`

## Related YARA Rules
- [mispadu_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/mispadu_basic.yar)
- [mispadu_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/mispadu_behavior.yar)
