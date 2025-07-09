## Behavioral Indicators

- Registry Run Keys:
  - `HKCU\Software\Microsoft\Windows\CurrentVersion\Run`
  - Often uses values like `"Windows Update Service"` or `"System Manager"`

- SMTP-based exfil:
  - `"smtp.office365.com"`
  - `"smtp.yandex.com"`

- Credential capture indicators:
  - `.NET usage of System.Net.NetworkCredential`
  - PowerShell launchers with `-nop -w hidden`

## Related Rules
- [`agenttesla_basic.yar`](https://github.com/Sab0x1D/ghostyara/blob/main/families/agent_tesla_basic.yar)
- [`agenttesla_behavior.yar`](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/agenttesla_behavior.yar)
