# AgentTesla – YARA Pattern Notes

---

## Static Strings

- `"Mutex__Agt"`
- `"UseSmtpSSL"`, `"HostName"`
- `"smtp.yandex.com"`, `"smtp.office365.com"`
- `"TVqQAAMAAAAEAAAA"` (base64-encoded `MZ`)
- `"POST /api/addlog"`
- `"This computer name is: "`
- `"Mozilla\\Firefox\\Profiles"`
- `"x-telegram-bot-token"`
- `"ftp://"` or `"http://"`
- `"FormGrabber"` or `"Keylogger"`
- `"ScreenShot"` or `"Screenshot saved to"`

## Mutex Patterns

- `Mutex__Agt`
- `TeslaMutex_<RANDOM>` — hardcoded or generated in newer variants

## .NET / Assembly Markers

- `System.Net.Mail`, `SmtpClient`
- `System.Windows.Forms.SendKeys`
- `System.Management` or `System.Reflection.Assembly`
- `System.Net.NetworkCredential`
- Uses embedded resources for config (encrypted strings)

## Registry Keys (Persistence)

- `SOFTWARE\\Microsoft\\Windows\\CurrentVersion\\Run`
  - Often named: `"Windows Update"` or `"AgentLoader"`

## Execution Artifacts

- PowerShell (staged/encoded):
  - `powershell.exe -nop -w hidden -noni -nop -enc <base64>`
- Command shell:
  - `cmd.exe /c start` with extracted payload
- May run via Task Scheduler or DLL injection loaders

## Related YARA Rules

- [agenttesla_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/rules/agenttesla_basic.yar)
- [agenttesla_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/rules/agenttesla_behavior.yar)
