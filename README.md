encryptedMountHDD
=================

These are productivity scripts to mount and unmount encrypted external devices as a device.

Assumed is that the partition is encrypted with dm-crypt with LUKS with an ext4 filesystem. You may need to modify the 
script for 
other 
encryption or filesystem types (feel free to fork the project).

Please make sure the path "/mnt/backup" exists before using these scripts.

The procedure of the mounting script will be from /dev/sdX# (partition of a user-specified external drive) to 
/dev/mapper/backup and finally /mnt/backup. If your device is already decripted (/dev/mapper/backup exists), the 
script will mount /dev/mapper/backup to /mnt/backup.

The procedure of the unmounting script will be unmounting /mnt/backup and disabling the mapping (unencrypted form) 
from 
/dev/sdX# to 
/dev/mapper/backup. If /mnt/backup does not exists and /dev/mapper/backup exists, the script will only disable mapping 
(unencrypted form).

These scripts are licenced under the modified (3-clause) BSD license.

A use case could be for a stable point of access for backups (e.g. rsnapshot).
