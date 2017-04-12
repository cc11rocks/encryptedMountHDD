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

$destination_location is the final point where you want your encrypted partition to be mounted. This should be a full path such as /mnt/backup. This variable, if changed, needs to be 
updated on both scripts.

$destination_crypt is the name of the unencrypted mapping from /dev/sdX# to /dev/mapper/$destination_crypt. This should NOT be a full path, but only the desired name. There isn't 
really a reason to change this, but if a user does, they must update this variable on both scripts.

If $destination_location doesn't exist when running the mount script, then it will be attempted to be created. This is done with sudo permissions due to common mounting points such as 
/mnt/XXX, 
which requires sudo permissions.

The procedure of the mounting script will be from /dev/sdX# (partition of a user-specified external drive) to 
/dev/mapper/$destination_crypt and finally $destination_location. If your device is already decrypted (/dev/mapper/$destination_crypt exists), the 
script will mount /dev/mapper/$destination_crypt to $destination_location.

The procedure of the unmounting script will be unmounting /mnt/backup and disabling the mapping (unencrypted form) 
from 
/dev/sdX# to 
/dev/mapper/$destination_crypt. If $destination_location does not exist and /dev/mapper/$destination_crypt exists, the script will only disable mapping 
(unencrypted form).

These scripts are licenced under the modified (3-clause) BSD license.

A use case could be for an automated stable point of access to encrypted partitions for backups (e.g. rsnapshot 
using an external encrypted hard drive).

[License](https://github.com/lptech1024/encryptedMountHDD/blob/master/LICENSE.txt)
