# TestGit



Add-Type @"
using System;
using System.Runtime.InteropServices;

public class Power {
    [DllImport("kernel32.dll")]
    public static extern uint SetThreadExecutionState(uint esFlags);
}
"@

# ES_CONTINUOUS | ES_DISPLAY_REQUIRED | ES_SYSTEM_REQUIRED
$ES = 0x80000000 -bor 0x00000002 -bor 0x00000001

while ($true) {
    [Power]::SetThreadExecutionState($ES)
    Start-Sleep -Seconds 60
}
