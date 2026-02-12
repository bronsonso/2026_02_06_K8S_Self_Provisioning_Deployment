### Install Harvester on HyperV
1. Setup HyperV
2. Create VM
3. Turn off VM

```
powershell
1. Update-VMVersion -Name 'Windows 11'
2. Set-VMProcessor -VMName 'Windows 11' -ExposeVirtualizationExtensions $True
```

