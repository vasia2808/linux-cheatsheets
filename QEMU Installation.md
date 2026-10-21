# QEMU Installation

```bash
sudo pacman -S qemu-desktop virt-manager dnsmasq
sudo systemctl enable libvirtd
sudo usermod -aG libvirt vasya
```

Uncomment:
* unix_sock_group = "libvirt"
* unix_sock_rw_perms = "0770"

```bash
sudo nvim /etc/libvirt/libvirtd.conf
```

```bash
sudo virsh net-autostart default
```
