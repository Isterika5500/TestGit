Add-Type @"
using System;
using System.Runtime.InteropServices;
public class Power {
    [DllImport("kernel32.dll")]
    public static extern uint SetThreadExecutionState(uint esFlags);
}
"@

$ES_CONTINUOUS       = [uint32]0x80000000
$ES_SYSTEM_REQUIRED  = [uint32]0x00000001
$ES_DISPLAY_REQUIRED = [uint32]0x00000002
$ES = $ES_CONTINUOUS -bor $ES_SYSTEM_REQUIRED -bor $ES_DISPLAY_REQUIRED

Write-Host "KeepAlive started. Press Ctrl+C to stop."

try {
    while ($true) {
        $result = [Power]::SetThreadExecutionState([uint32]$ES)
        if ($result -eq 0) { Write-Warning "SetThreadExecutionState failed!" }
        Start-Sleep -Seconds 60
    }
} finally {
    [Power]::SetThreadExecutionState([uint32]0x80000000) | Out-Null
    Write-Host "KeepAlive stopped."
}
