# ConnectWise RAT – YARA Pattern Notes

## Static Indicators
- Embedded service/client labels:
  - `ScreenConnect.WindowsClient.exe`
  - `ConnectWiseControl.Client`
  - `ScreenConnect.ClientService`
- Product namespace:
  - `ConnectWiseControl`
- Session-related components:
  - `SessionManager`

## Behavioral Indicators
- Service installed with name: `ScreenConnect Client`
- Common beaconing endpoints:
  - `/Host`
  - `/Join`
- Registry path:
  - `SOFTWARE\ScreenConnect`

## Related YARA Rules
- [connectwise_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/connectwise_basic.yar)  
- [connectwise_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/connectwise_behavior.yar)
