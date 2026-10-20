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

### Format the partitions

```bash
mkfs.ext4 /dev/sda2
mkfs.fat -F 32 /dev/sda1
```

### Mount the file systems

```bash
mount /dev/sda2 /mnt
mount --mkdir /dev/sda1 /mnt/boot
```

### Install essential packages

**intel-ucode** for **Intel** CPU
**amd-ucode** for **AMD** CPU

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
* en_GB.UTF-8 UTF-8
* en_US.UTF-8 UTF-8
* ru_RU.UTF-8 UTF-8
* uk_UA.UTF-8 UTF-8

```bash
nvim /etc/locale.gen
locale-gen
echo LANG=en_US.UTF-8 >> /etc/locale.conf
echo LC_TIME=en_GB.UTF-8 >> /etc/locale.conf
echo LC_MEASUREMENT=en_GB.UTF-8 >> /etc/locale.conf
```

### Network configuration

```bash
echo arch > /etc/hostname
systemctl enable NetworkManager
```

### Root password

```bash
passwd
```

### Boot loader



```bash
grub-install --target=x86_64-efi --bootloader-id=GRUB --efi-directory=/boot --removable
nvim /etc/default/grub
grub-mkconfig -o /boot/grub/grub.cfg
```