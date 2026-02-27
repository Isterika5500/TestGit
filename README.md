
Add-Type @"
using System;
using System.Runtime.InteropServices;
public class Power {
    [DllImport("kernel32.dll")]
    public static extern uint SetThreadExecutionState(uint esFlags);
}
"@

$ES_CONTINUOUS       = [Convert]::ToUInt32(2147483648)
$ES_SYSTEM_REQUIRED  = [Convert]::ToUInt32(1)
$ES_DISPLAY_REQUIRED = [Convert]::ToUInt32(2)
$ES = [Convert]::ToUInt32($ES_CONTINUOUS -bor $ES_SYSTEM_REQUIRED -bor $ES_DISPLAY_REQUIRED)

try {
    while ($true) {
        [Power]::SetThreadExecutionState($ES) | Out-Null
        Start-Sleep -Seconds 55
    }
} finally {
    [Power]::SetThreadExecutionState([Convert]::ToUInt32(2147483648)) | Out-Null
}
