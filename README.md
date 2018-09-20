# lmdescrypt
### version 0.992

This script installs Linux Mint Debian Edition (201403), LMDE2 (201503 and
201701), LMDE3, or regular Linux Mint 17, 17.1/2/3, 18, 18.1/2/3, or 19,
or various flavours of Ubuntu,
either i686 or amd64, whether with MSDOS or GPT partitions, UEFI or not.
The result:

**a fully LUKS encrypted system, with LVM2 volumes of root and
swap (and optionally: data) with optional boot partition
(with optional boot-from-iso-file too).**

* Download shortlink for the script: http://4e4.win/lmdescrypt
* Tutorial on Linux Mint community: https://community.linuxmint.com/tutorial/view/2265
* Gitlab page: https://gitlab.com/pepa65/lmdescrypt
* Questions?  solusos@passchier.net or post an Issue on the gitlab page

## INSTRUCTIONS

**1. Boot the Live environment**

**2. Open a Terminal (Menu/Terminal of Ctrl-Alt-T) and enter:**

```
sudo -i
wget 4e4.win/lmdescrypt
```

**3. If needed, adapt the SETTINGS section:**

```
nano lmdescrypt
```

**4. Make sure all the partitions mentioned in SETTINGS exist.**
For example, (re)partition the drive like this
(erasing all, taking up all space):

```
# Unmount all automounted swap partitions
swapoff -a

# This ERASES the whole disk!
sgdisk -Zon1::+2M -t1:ef02 -c1:BIOS -n2::-0 -t2:8e00 -c2:X -g /dev/sda

# For a UEFI setup instead, this example works:
sgdisk -Zon1::+260M -t1:ef00 -c1:EFI -n2::-0 -t2:8e00 -c2:X -g /dev/sda
```
This is giving almost the whole drive to the encrypted lvm2

**5. Start the script:**

```
source lmdescrypt
```

**6. Answer the questions as they come up:**
* set password for encryption

Then after all the preparations have happened:
* set password for user
* set timezone
* configure keyboard

## And that's it!

### Installing into a pre-existing environment

* Using a pre-existing boot-partition, LUKS partition and LVM Logical Volumes is entirely supported.
* Not having a separate boot partition is also supported: total encryption!
* Multiple booting with other OSes also works out of the box.
* MBR, GPT partition tables and UEFI work according to configuration.
