# AgentTesla – C2 Patterns & IOC Mapping

## Common C2 URLs:
- `http://<host>/api/addlog`
- `smtp.yandex.com`
- `smtp.office365.com`
- `mail.tutanota.com`

## Common Mutexes:
- `Mutex__Agt<Random>`
- `Global\ASYSTEM_XX`

## Notes:
AgentTesla variants use SMTP or HTTP POST to exfiltrate keylogs and screenshots. C2 URLs often contain `/api/`, `/panel/`, or `/addlog` endpoints.

## Related Rules:
- [ghostyara/families/agenttesla_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/agent_tesla_basic.yar)
