# Zaborona VPN Installation

```bash
sudo pacman -S networkmanager-openvpn
nmcli c import type openvpn file Downloads/srv0.zaborona-help-TCP_maxroutes.ovpn
nmcli c show
nmcli c modify <VPN-UUID> ipv4.never-default yes
nmcli c modify <VPN-UUID> ipv6.never-default yes
nmcli c modify <ETHERNET-ID> connection.secondaries <VPN-ID>
sudo systemctl restart NetworkManager
```