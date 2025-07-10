# Agent Tesla – YARA Pattern Notes

## Static Strings

- `"This computer name is: "`
- `"Mozilla\\Firefox\\Profiles"`
- `"x-telegram-bot-token"`
- `"ftp://"`
- `"smtp."` or `"mail."`
- `"FormGrabber"` or `"Keylogger"`
- `"ScreenShot_"` or `"Screenshot saved to"`

## Mutex Patterns

- `TeslaMutex_<RANDOM>`
- Hardcoded or generated mutex in newer variants

## .NET / Assembly Markers

- `System.Windows.Forms.SendKeys`
- `System.Management` or `System.Reflection.Assembly`
- Uses embedded resources for config (encrypted strings)

## Registry Keys (Persistence)

- `HKCU\\Software\\Microsoft\\Windows\\CurrentVersion\\Run`
  - Often named: `"Windows Update"` or `"AgentLoader"`

## Execution Artifacts

- Command shell:
  - `cmd.exe /c start` with extracted payload
- PowerShell launchers:
  - `powershell -w hidden -noni -nop -enc <base64>`
- DLL injection in loader variants

## Related YARA Rules

- [agenttesla_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/agenttesla_basic.yar)
- [agenttesla_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/agenttesla_behavior.yar)
