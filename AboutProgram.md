# KingO-Tweaking-utillity
Add a "Why KingO?" section that mentions:"Unlike other tools that bloat your PC, KingO is a lightweight PowerShell-based executable that makes permanent, safe changes to the Windows Registry for a cleaner, faster experience."
===========================================================
            KINGO TWEAKING UTILITY v1.0
===========================================================

[DESCRIPTION]
KingO Utility is a precision performance suite designed 
to reduce system latency and boost FPS on Windows.

[HOW TO START]
1. Choose your tweaks from the Yellow & Black menu.
2. Restart your PC to finalize changes.

[TWEAKS INCLUDED]
- 0.5ms Global Timer Resolution (1:1 Mouse Feel)
- Mouse Class Data Queue Optimization
- Ryzen CPU Power Throttling Bypass
- Extreme System Bloatware Removal

[DISCLAIMER]
This software modifies Registry and System settings. 
Use at your own risk. Always create a System Restore 
Point before applying tweaks.

[CREDITS]
Developed by KingO. 
Follow for more performance updates!
===========================================================
  
The powershell code
_______> # --- KINGO TWEAKING UTILITY v1.0 ---




# --- KINGO TWEAKING UTILITY v1.0 --




# 1. AUTO-ADMIN ELEVATION: Ensures registry tweaks are applied correctly
if (!([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)) {
    Start-Process PowerShell -Verb RunAs -ArgumentList "-NoProfile -ExecutionPolicy Bypass -File `"$PSCommandPath`""
    Exit
}

# 2. THEME & UI COLORS
[Console]::BackgroundColor = "Black"
[Console]::ForegroundColor = "Yellow"
Clear-Host

# 3. HEADER FUNCTION: The "Professional Tweaker" Look
function Show-Header {
    Clear-Host
    Write-Host "#################################################" -ForegroundColor Yellow
    Write-Host "#                                               #" -ForegroundColor Yellow
    Write-Host "#          KINGO TWEAKING UTILITY v1.0          #" -ForegroundColor Black -BackgroundColor Yellow
    Write-Host "#         0-Delay Performance Optimizer         #" -ForegroundColor Black -BackgroundColor Yellow
    Write-Host "#                                               #" -ForegroundColor Yellow
    Write-Host "#################################################" -ForegroundColor Yellow
    Write-Host " [DEVICE]  Gateway GW15-41P detected"
    Write-Host " [USER]    $env:USERNAME"
    Write-Host " [STATUS]  Ready to optimize..."
    Write-Host "-------------------------------------------------" -ForegroundColor Yellow
}

# 4. OPTIMIZATION LOGIC (The Tweaks)
do {
    Show-Header
    Write-Host " 1. [MOUSE]     Apply 1000Hz Polling & 0.5ms Timer"
    Write-Host " 2. [CPU]       Unlock Ryzen 7 Maximum Power"
    Write-Host " 3. [STRIP]     Permanent Bloatware & Texture Removal"
    Write-Host " 4. [RESTORE]   Reset All to Windows Defaults"
    Write-Host " 5. [EXIT]      Close Utility"
    Write-Host "-------------------------------------------------" -ForegroundColor Yellow
    Write-Host " Select Option > " -NoNewline -ForegroundColor Yellow
    $choice = Read-Host

    switch ($choice) {
        '1' {
            Write-Host "[!] Optimizing Mouse & Timer..." -ForegroundColor Black -BackgroundColor Yellow
            # 0.5ms Timer & 1000Hz Tweak Logic
            Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\kernel" -Name "GlobalTimerResolutionRequests" -Value 1
            Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\mouclass\Parameters" -Name "MouseDataQueueSize" -Value 25
            Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseSpeed" -Value 0
            Start-Sleep -Seconds 2
        }
        '2' {
            Write-Host "[!] Boosting Ryzen CPU..." -ForegroundColor Black -BackgroundColor Yellow
            # CPU Throttling & Power Plan
            Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Power" -Name "PowerThrottlingOff" -Value 1
            bcdedit /set disabledynamictick yes
            powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61 | Out-Null # Ultimate Perf
            Start-Sleep -Seconds 2
        }
        '3' {
            Write-Host "[!] Stripping Bloat..." -ForegroundColor Black -BackgroundColor Yellow
            # Permanent Deletion Logic
            Get-AppxPackage -Name "*TikTok*" | Remove-AppxPackage -ErrorAction SilentlyContinue
            Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects" -Name "VisualFXSetting" -Value 2
            Start-Sleep -Seconds 2
        }
        '4' {
            Write-Host "[!] Restoring Defaults..." -ForegroundColor Black -BackgroundColor Yellow
            # Revert Tweak
            Set-ItemProperty -Path "HKCU:\Control Panel\Mouse" -Name "MouseSpeed" -Value 1
            bcdedit /set disabledynamictick no
            Start-Sleep -Seconds 2
        }
    }
} until ($choice -eq '5')

[Console]::ResetColor()
Clear-Host
