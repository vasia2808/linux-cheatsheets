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

Replace **strncpy** with **strscpy**:

```vim
:%s/strncpy/strscpy/g
```

### Install the module

```bash
sudo dkms install ddcci/0.4.5
```

