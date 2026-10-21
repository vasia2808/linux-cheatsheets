# Brightness Adjustment

### Install packages

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

Find **I<sup>2</sup>C bus** (for example /dev/**i2c-4**):

```bash
ddcutil detect
```

Find I<sup>2</sup>C bus adapter name (for example **AMDGPU DM i2c hw bus 2**):

```bash
cat /sys/bus/i2c/devices/i2c-4/name
```

Create **90-ddcci.rules** file:

```bash
sudo nvim /etc/udev/rules.d/90-ddcci.rules
```

Write udev rule:

```udev
ACTION=="add", SUBSYSTEM=="i2c", ATTR{name}=="AMDGPU DM i2c hw bus 2", RUN+="/bin/sh -c 'echo ddcci 0x37 > /sys%p/new_device'"
```
