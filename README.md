# Cpp_Repo_Template

## Header Size 2

### Header Size 3



---

#### Back Engineering



#### Kernel Driver Creation

[Microsoft Website On WDK Driver Creation](https://learn.microsoft.com/en-us/windows-hardware/drivers/download-the-wdk)
- [Visual Studio 2022](https://www.techspot.com/downloads/7493-visual-studio-2022.html)

- [WinSDK](https://developer.microsoft.com/en-us/windows/downloads/windows-sdk/)
- [WDK](https://go.microsoft.com/fwlink/?linkid=2335869)
- For Windows WDK - Windows 11 Driver Toolkit For Creating Kernel Level Cheats
- (For Red-Teaming And Testing For Personal Perposes Related To Game Design)

- All 3 in a single ISO 18GB
- [EWDK](https://learn.microsoft.com/en-us/legal/windows/hardware/enterprise-wdk-license-2022)




[![Watch the video](https://img.youtube.com/vi/HFobGp7VZeA/maxresdefault.jpg)](https://www.youtube.com/watch?v=HFobGp7VZeA)


a powershell script for checking the hash on the iso or other large download where a hash is provided
code
```cpp
# verify-iso.ps1
# Verifies SHA-256 hash of a downloaded ISO

param (
    [Parameter(Mandatory = $true)]
    [string]$IsoPath
)

# Expected SHA-256 for Win11 25H2 English International x64
$ExpectedHash = "BAAEB6C90DD51648154B64C40C9E0C14D93A427F611A1BB49C8077FA2FF73364"

if (-not (Test-Path $IsoPath)) {
    Write-Error "File not found: $IsoPath"
    exit 2
}

Write-Host "Computing SHA-256 hash..."
$Result = Get-FileHash -Algorithm SHA256 -Path $IsoPath

Write-Host ""
Write-Host "Expected : $ExpectedHash"
Write-Host "Computed : $($Result.Hash)"
Write-Host ""

if ($Result.Hash -ieq $ExpectedHash) {
    Write-Host "✔ Integrity check PASSED" -ForegroundColor Green
    exit 0
}
else {
    Write-Host "✘ Integrity check FAILED" -ForegroundColor Red
    Write-Host "File is corrupted or has been tampered with."
    exit 1
}
```

