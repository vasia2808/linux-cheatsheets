# Brightness Adjustment

### Install essential packages

```bash
sudo pacman -S linux-headers ddcci-driver-linux-dkms-git ddcutil brightnessctl
```

### Replacethe outdated function

Open

```bash
sudo nvim /var/lib/dkms/ddcci/0.4.5/source/ddcci/ddcci.c
```

```bash
sudo dkms install ddcci/0.4.5 -k 7.2.2-arch1-1
```