= lmde2crypt

This script installs Linux Mint Debian Edition i686 or amd64, version 201403,\\
or Linux Mint Debian Edition version 2 (201504) to be:\\
//Fully luks encrypted, with lvm2 volumes of root, swap and (optionally) data//

Sourceforge page: https://sourceforge.net/projects/lmde2crypt

It is based on this Makefile: http://j.mp/makelmde\\
See forum topic: http://forums.linuxmint.com/viewtopic.php?f=189&t=132520

Shortlink to download the script: http://j.mp/lmde2crypt\\
Questions?  solusos@passchier.net or post an Issue on Sourceforge


== INSTRUCTIONS

**1. Boot the Live environment of LMDE 201403 or LMDE-2**

**2. Open a Terminal (Menu, Terminal) and enter:**

{{{ wget j.mp/lmde2crypt
 chmod +x lmde2crypt
}}}

**3. If needed, adapt the SETTINGS section:**

{{{ nano lmde2crypt
}}}

**4. Partition the drive, for instance (taking up all space):**

{{{ sudo fdisk /dev/sda
}}}

Within fdisk, enter the following:
{{{
 o [Enter]
 n [Enter]
 [Enter]
 [Enter]
 [Enter]
 +128M [Enter]
 n [Enter]
 [Enter]
 [Enter]
 [Enter]
 [Enter]
 w [Enter]
}}}
This is making a 128 MB boot partition, and giving the rest to the encrypted lvm2

**5. Start the script:**

{{{ sudo ./lmde2crypt
}}}

**6. Answer the questions as they come up:**
* password for encryption (twice the same)
* password for decryption (same again)

Then after a wait for all the preparations to have happened:
* password for user, and some irrelevant info
* about the keyboard
* about the timezone

== And that's it!
