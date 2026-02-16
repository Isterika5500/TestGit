Add-Type @"
using System;
using System.Runtime.InteropServices;

public class Power {
    [DllImport("kernel32.dll")]
    public static extern uint SetThreadExecutionState(uint esFlags);
}
"@

# ЯВНО UInt32
$ES_CONTINUOUS        = [uint32]0x80000000
$ES_SYSTEM_REQUIRED   = [uint32]0x00000001
$ES_DISPLAY_REQUIRED  = [uint32]0x00000002

$ES = $ES_CONTINUOUS -bor $ES_SYSTEM_REQUIRED -bor $ES_DISPLAY_REQUIRED

Write-Host "KeepAlive started successfully."

while ($true) {
    [Power]::SetThreadExecutionState($ES) | Out-Null
    Start-Sleep -Seconds 60
}
