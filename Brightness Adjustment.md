# Brightness Adjustment

### Install essential packages

```bash
sudo pacman -S linux-headers ddcci-driver-linux-dkms-git ddcutil brightnessctl
```

### Replace the outdated function and install the module

Open **/usr/src/ddcci-0.4.5/ddcci/ddcci.c**:

```bash
sudo nvim /usr/src/ddcci-0.4.5/ddcci/ddcci.c
```

Replace **strncpy** with **strscpy**:

```vim
:%s/strncpy/strscpy/g
```

Install the module:

```bash
sudo dkms install ddcci/0.4.5
```

### Create udev rule

Run **i2c-dev** module:

```bash
modprobe i2c-dev
```

Find **I2C bus** (for example: /dev/i2c-4):

```bash
ddcutil detect
```

Find