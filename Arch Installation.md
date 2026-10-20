# Arch Installation

### Connect to the internet

```bash
iwctl --passphrase ryangosling station wlan0 connect Bulo4ki
```

### Partition the disks

The first partition: 512MB;
The second partition: the rest of the space.

```bash
fdisk -l
fdisk /dev/sda
```

