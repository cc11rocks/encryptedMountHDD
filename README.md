encryptedMountHDD
=================

These are productivity scripts to mount and unmount encrypted external devices as a device.

Assumed is that the partition is an ext4 filesystem and is encrypted with dm-crypt with LUKS. 
You 
may need to 
modify 
the 
script for 
other 
encryption types or filesystems (feel free to fork the project).

If /mnt/backup doesn't exist when running the mount script, then it will be attempted to be created as long as /mnt/ 
exists.

The procedure of the mounting script will be from /dev/sdX# (partition of a user-specified external drive) to 
/dev/mapper/backup and finally /mnt/backup. If your device is already decrypted (/dev/mapper/backup exists), the 
script will mount /dev/mapper/backup to /mnt/backup.

The procedure of the unmounting script will be unmounting /mnt/backup and disabling the mapping (unencrypted form) 
from 
/dev/sdX# to 
/dev/mapper/backup. If /mnt/backup does not exist and /dev/mapper/backup exists, the script will only disable mapping 
(unencrypted form).

These scripts are licenced under the modified (3-clause) BSD license.

A use case could be for an automated stable point of access to encrypted partitions for backups (e.g. rsnapshot 
using an external encrypted hard drive).
