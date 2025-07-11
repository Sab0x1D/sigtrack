# LodaRAT – YARA Pattern Notes

## Static Strings
- `"Chrome.exe"`
- `"WinData"`
- `"172.111.138.100"`
- `"Mr. 3amo"`
- `"AutoIt"`
- `"wscript.exe"`
- `"New Resigned Contract"`

## Execution Chain
- Initial dropper from Google Drive
- Drops both `.exe` and `.vbs` to `%TEMP%`
- Spawns `wscript.exe` > spawns `"Chrome.exe"`

## .NET + AutoIt Markers
- Uses AutoIt scripting
- Executes with .NET wrappers in some variants

## Registry or File Persistence
- Drops secondary file to `%APPDATA%\Roaming\WinData`

## Related YARA Rules
- [lodarat_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/lodarat_basic.yar)
- [lodarat_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/lodarat_behavior.yar)
