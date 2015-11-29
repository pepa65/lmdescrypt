# lmdescrypt
### version 0.75

This script installs Linux Mint Debian Edition i686 or amd64, version 201403,
or Linux Mint Debian Edition version 2 (201504)
or regular Linux Mint 17.1 or 17.2 or 17.3 to be:<br>
*Fully luks encrypted, with lvm2 volumes of root, swap and (optionally) data*

Github page: https://github.com/pepa65/lmdescrypt

It is based on this Makefile: http://j.mp/makelmde<br>
See forum topics:
- http://forums.linuxmint.com/viewtopic.php?f=189&t=132520
- http://forums.linuxmint.com/viewtopic.php?f=241&t=194031

Shortlink to download the script: http://j.mp/lmdescrypt<br>
Questions?  solusos@passchier.net or post an Issue on the github page

## INSTRUCTIONS

**1. Boot the Live environment**

**2. Open a Terminal (Menu, Terminal) and enter:**

```
wget j.mp/lmdescrypt
```

**3. If needed, adapt the SETTINGS section:**

```
nano lmdescrypt
```

**4. Partition the drive, for instance (taking up all space):**

```
sudo fdisk /dev/sda
```

Within fdisk, enter the following:
```
 o [Enter]
 n [Enter]
 [Enter]
 [Enter]
 [Enter]
 +500M [Enter]
 n [Enter]
 [Enter]
 [Enter]
 [Enter]
 [Enter]
 w [Enter]
```
This is making a 500 MB boot partition, and giving the rest to the encrypted lvm2

**5. Start the script:**

```
sudo source lmdescrypt
```

**6. Answer the questions as they come up:**
* password for encryption (twice the same)
* password for decryption (same again)

Then after a wait for all the preparations to have happened:
* password for user, and some irrelevant info
* about the keyboard
* about the timezone

### Installing into a pre-existing environment

If there is already a boot-partition and/or a LVM partition that you want to use,
that is entirely supported. Make sure that in editing the script, you make sure you have nothing
listed as filesystem-type (then it doesn't get formatted). The root partition always gets formatted!!
In LVM, if you're using pre-existing names for the Volume Group and/or the Logical Volumes (partitions),
They won't get created.

## And that's it!
