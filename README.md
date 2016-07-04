
# lmdescrypt
### version 0.87

This script installs Linux Mint Debian Edition i686 or amd64, version 201403,
or Linux Mint Debian Edition version 2 (201504), or regular Linux Mint 17.1 or 17.2 or 17.3 to be:<br>
*Fully LUKS encrypted, with lvm2 volumes of root and swap (and optionally: data).*

Github page: https://github.com/pepa65/lmdescrypt

See forum topic: http://forums.linuxmint.com/viewtopic.php?f=189&t=132520

Shortlink to download the script: http://j.mp/lmdescrypt<br>
Questions?  solusos@passchier.net or post an Issue on the github page

## INSTRUCTIONS

**1. Boot the Live environment**

**2. Open a Terminal (Menu/Terminal of Ctrl-Alt-T) and enter:**

```
wget j.mp/lmdescrypt
chmod +x lmdescrypt
```

**3. If needed, adapt the SETTINGS section:**

```
nano lmdescrypt
```

**4. Make sure all the partitions mentioned in SETTINGS exist.**
For example, (re)partition the drive like this
(erasing all, taking up all space):

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
sudo ./lmdescrypt
```

**6. Answer the questions as they come up:**
* password for encryption (twice the same)
* password for decryption (same again)

Then after a wait for all the preparations to have happened, and supply:
* password for user, and some irrelevant info
* about the keyboard
* about the timezone

## And that's it!

### Installing into a pre-existing environment

Using a pre-existing boot-partition, LUKS partition and LVM Logical Volumes is entirely supported.
The options are to USE (or not), to CREATE (or not), and to FORMAT (or not) these devices.
