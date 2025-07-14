# Cobalt Strike – YARA Pattern Notes

## Static Configuration Markers
- Malleable C2 strings:
  - `http-get.uri`
  - `http-post.uri`
  - `publickey`
- Common embedded URIs:
  - `/submit.php`
  - `/jquery-3.3.1.min.js`
- XOR key pattern:
  - `{ 2e 63 6f 6e 66 69 67 00 }` (may vary slightly)

## Behavioral Traits
- Named pipe: `\\\\.\\pipe\\MSSE-*`
- Mutex or global object: `Global\\PostEx_Mutex`
- Injection APIs observed:
  - `VirtualAllocEx`
  - `WriteProcessMemory`
  - `CreateRemoteThread`

## Related YARA Rules
- [cobaltstrike_basic.yar](https://github.com/Sab0x1D/ghostyara/blob/main/families/cobaltstrike_basic.yar)  
- [cobaltstrike_behavior.yar](https://github.com/Sab0x1D/ghostyara/blob/main/ttps/cobaltstrike_behavior.yar)
