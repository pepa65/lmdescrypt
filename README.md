# zfse
**Run a modified Ubiquity installer to use natively encrypted ZFS**
* Usage:
  - Boot into a Ubuntu/Linuxmint Desktop installer.
  - In a terminal, download the script: `wget 4e4.win/zfse`.
  - Run the script: `bash zfse` which will tweak and start up Ubiquity.
  - In the 'Installation type' screen choose 'Erase whole disk' and then click
    on 'Advanced features...' and then 'EXPERIMENTAL: Erase disk and use ZFS'.
  - Reboot into the new install!

## Rationale
The `lmdescrypt` had a long run and helped installing Ubuntu / Linux Mint on
many incarnations of these distributions. It was always a fragile hack
that happened to work well. Now in 2020, the script needs more work to get it
to work properly. At the same time, ZFS rose in viability, and encrypted ZFS
does now exist, and it is getting support from the packagers. This page
https://openzfs.github.io/openzfs-docs/Getting%20Started/Ubuntu/Ubuntu%2020.04%20Root%20on%20ZFS.html convinced me that the time had come to switch my installs
to Encrypted ZFS. I used `zfse` to facilitate this type of install
(ideally Ubiquity should support randomly encrypted swap). There is a bug
preventing ZFS to support swap on zvols, so the swap partition gets separately
LUKS-encrypted.

To add to that, Ubiquity does now also support Encrypted LVM2, so there is less
need for `lmdescrypt`, even if the configuration options are still limited.

# encswap
**Transform a swap-partition into a randomly LUKS-encrypted swap partition**
* Usage:
  - In a terminal, download the script: `wget 4e4.win/encswap`
  - Run the script: `bash encswap`

# lmdescrypt
**version 0.991**

* **Funtion**: This script installs Linux Mint Debian Edition (201403), LMDE2
(201503 or 201701), LMDE3 (201808), LMDE4 (202004) or regular Linux Mint 17,
17.1/2/3, 18, 18.1/2/3, 19, 20beta, or Ubuntu 18.04, either i686 or amd64, with
MSDOS or GPT partitions, with UEFI or not.
* **Result**: a fully LUKS encrypted system, with LVM2 volumes of root and
swap (and optionally: data) with optional boot partition
(with optional boot-from-iso-file).
* Download shortlink for the script: https://4e4.win/lmdescrypt
* Tutorial on Linux Mint community: https://community.linuxmint.com/tutorial/view/2265
* Gitlab page: https://gitlab.com/pepa65/lmdescrypt
* Questions?  pepa65@passchier.net or post an Issue on the gitlab page

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
