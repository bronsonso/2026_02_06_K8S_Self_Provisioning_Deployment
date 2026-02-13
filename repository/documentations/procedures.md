# Procedures of installing Rancher + RKE2 on HyperV,  rke2-01, rke2-02, rke2-03

2. Create VM

### Allow nested virtualization
3. Turn off VM

```
powershell
1. Update-VMVersion -Name 'Windows 11'
2. Set-VMProcessor -VMName 'Windows 11' -ExposeVirtualizationExtensions $True
```

### Enable NAT switch
```
powershell
#Create a new virtual switch named "NAT Virtual Switch"
New-VMSwitch -SwitchName "NAT Virtual Switch" -SwitchType Internal

Get-Netadapter
[get ifIndex for the NAT Virtual Switch Adapter]
New-NetIPAddress -IPAddress 192.168.0.254 -PrefixLength 24 -InterfaceIndex [ifIndex]

New-NetNat -Name NATnetwork01 -InternalIPInterfaceAddressPrefix 192.168.0.0/24

### Gateway: 192.168.0.254
### IP: 192.168.0.1 - 192.168.0.253
### DNS: Get from Hyperv Host
    ipconfig /all | findstr "DNS"
```

### Apply CIS on Ubuntu 24.04

## Verify if internet setting in VM
```
curl -I www.google.com              # error! DNS issue
curl -I 143.250.198.36              # internet connection issue
sudo cat /etc/netplan/50-cloud-init.yaml
```

## Install basic utility for Ubuntu
```
sudo apt update
sudo apt upgrade -y
# install ping
sudo apt install -y iputils-ping
# install ifconfig
sudo apt install -y net-tools
# install vim
sudo apt install -y vim
