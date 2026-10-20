# Arch Installation

### Connect to the internet

```bash
iwctl --passphrase ryangosling station wlan0 connect Bulo4ki
```

### Partition the disks

The first partition: 512MB, type - 1 EFI System;
The second partition: the rest of the space.

```bash
fdisk -l
fdisk /dev/sda
```

### Mount the file systems

```bash
mount /dev/sda2 /mnt
mount --mkdir /dev/sda1 /mnt/boot
```

### Install essential packages

```bash
pacstrap -K /mnt base linux linux-firmware grub efibootmgr sudo networkmanager intel-ucode neovim
```

### Generate fstab

```bash
genfstab -U /mnt >> /mnt/etc/fstab
```

### Change root into the new system

```bash
arch-chroot -S /mnt
```

### Time

```bash
ln -sf /usr/share/zoneinfo/Europe/Kyiv /etc/localtime
hwclock --systohc
```

### Localization

Uncomment:
