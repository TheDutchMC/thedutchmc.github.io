# Windows Hardware clock in UTC
By default, Windows stores time in the local timezone on the hardware clock. This causes some trouble when dualbooting with Linux, meaning your clock is off every time you switch from Linux to Windows.

### Solution
1. Open the Windows Registry (`WinKey + R`, `regedit`)
2. Go to the following path in the Registry: `Computer\HKEY_LOCAL_MACHINE\SYSTEM\ControlSet001\Control\TimeZoneInformation`
3. Create a DWORD (32-bit) named `RealTimeIsUniversal`
4. Double click it and give it a hexadecimal value of `1`, then press OK

Time is now stored in UTC on the hardware clock.