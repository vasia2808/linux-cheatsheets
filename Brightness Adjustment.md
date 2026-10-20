# Brightness Adjustment

### Install essential packages

```bash
sudo pacman -S linux-headers ddcci-driver-linux-dkms-git ddcutil brightnessctl
```

### Replace the outdated function

Open **/usr/src/ddcci-0.4.5/ddcci/ddcci.c**:

```bash
sudo nvim /usr/src/ddcci-0.4.5/ddcci/ddcci.c
```

```bash
sudo dkms install ddcci/0.4.5 -k 7.2.2-arch1-1
```