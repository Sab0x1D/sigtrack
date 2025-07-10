# Lumma Stealer – YARA Pattern Notes

## Execution Behavior
- `.bat` file invokes `InstallUtil.exe` to execute payload
- Stealer may self-terminate quickly after contacting C2
- **Recommendation**: Suspend the process to capture indicators

## Static Strings
- `"{"r":[],"b":[],"g":0}"` JSON marker for socket protocol
- `"c2sock"` used in connection setup
- Strings related to browser and wallet harvesting:
  - `"mr.temp"`, `"user data"`, `"local state"`, `"TeslaBrowser"`
  - `"wallets"`, `"webcache"`, `".fun"` (domain or extension marker)

## Credential & Browser Targeting
- Chromium-based browser theft (via `"user data"` and `"local state"`)
- `"TeslaBrowser"` string often embedded in older versions
- May scrape stored credentials from `"webcache"`

## Related YARA Rules
- [lumma_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/lumma_basic.yar)
- [lumma_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/lumma_behavior.yar)
