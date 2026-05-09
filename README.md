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
# 1. AUTO-ADMIN: Automatically requests admin rights when launched
if (!([Security.Principal.WindowsPrincipal][Security.Principal.WindowsIdentity]::GetCurrent()).IsInRole([Security.Principal.WindowsBuiltInRole]::Administrator)) {
    Start-Process PowerShell -Verb RunAs -ArgumentList "-NoProfile -ExecutionPolicy Bypass -File `"$PSCommandPath`""
    Exit
}

# 2. UI SETUP: Custom Yellow & Black Theme
[Console]::BackgroundColor = "Black"
[Console]::ForegroundColor = "Yellow"
Clear-Host

# 3. CORE FUNCTIONS
function Show-Header {
    Clear-Host
    Write-Host "#################################################" -ForegroundColor Yellow
    Write-Host "#                                               #" -ForegroundColor Yellow
    Write-Host "#          KINGO TWEAKING UTILITY v1.0          #" -ForegroundColor Black -BackgroundColor Yellow
    Write-Host "#         0-Delay Performance Optimizer         #" -ForegroundColor Black -BackgroundColor Yellow
    Write-Host "#                                               #" -ForegroundColor Yellow
    Write-Host "#################################################" -ForegroundColor Yellow
    Write-Host " [STATUS] Gateway GW15-41P detected"
    Write-Host " [MODE]   Extreme Optimization Mode"
    Write-Host "-------------------------------------------------" -ForegroundColor Yellow
}

function Create-RestorePoint {
    Write-Host "[!] Creating System Restore Point for safety..." -ForegroundColor Yellow
    Checkpoint-Computer -Description "KingO_Before_Tweak" -RestorePointType "MODIFY_SETTINGS" -ErrorAction SilentlyContinue
}

# 4. MAIN PROGRAM LOOP
do {
    Show-Header
    Write-Host " 1. [MOUSE]     0.5ms Timer & 1000Hz Buffer Fix"
    Write-Host " 2. [CPU]       Boost Ryzen 7 Maximum Power"
    Write-Host " 3. [STRIP]     Extreme Bloat & Texture Removal"
    Write-Host " 4. [RESTORE]   Revert to Default Settings"
    Write-Host " 5. [EXIT]      Close Software"
    Write-Host "-------------------------------------------------" -ForegroundColor Yellow
    $choice = Read-Host " Select Option > "

    switch ($choice) {
        '1' {
            Write-Host "[!] Applying Mouse & Global Timer Resolution..." -ForegroundColor Cyan
            # Force 0.5ms Timer Resolution
            Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\kernel" -Name "GlobalTimerResolutionRequests" -Value 1
            Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Services\mouclass\Parameters" -Name "MouseDataQueueSize" -Value 25
            Start-Sleep -Seconds 2
        }
        '2' {
            Write-Host "[!] Unlocking Ryzen Performance..." -ForegroundColor Cyan
            # Ryzen Power Throttling Bypass
            Set-ItemProperty -Path "HKLM:\SYSTEM\CurrentControlSet\Control\Power" -Name "PowerThrottlingOff" -Value 1
            bcdedit /set disabledynamictick yes
            powercfg -duplicatescheme e9a42b02-d5df-448d-aa00-03f14749eb61 | Out-Null
            Start-Sleep -Seconds 2
        }
        '3' {
            Write-Host "[!] Stripping System Textures & Bloat..." -ForegroundColor Cyan
            # Visual Performance Tweak
            Set-ItemProperty -Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Explorer\VisualEffects" -Name "VisualFXSetting" -Value 2
            Get-AppxPackage -Name "*TikTok*" | Remove-AppxPackage -ErrorAction SilentlyContinue
            Start-Sleep -Seconds 2
        }
    }
} until ($choice -eq '5')

[Console]::ResetColor()
Clear-Host


