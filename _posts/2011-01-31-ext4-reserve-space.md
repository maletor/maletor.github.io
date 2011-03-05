# Ext4 Reserve Space

_January 31, 2011_

The Ext4 file system, like Ext3, reserves 5% of the blocks on the file system for the root user. The reserved blocks are there for root's use as a safe guard if the filesystem gets full. It provides some wiggle room to enable the really important programs to still function, like rm. But in some cases there’s not much point in having space reserved for root.

I’ve recently upgraded my workstation with a 4TB internal RAID 5 array for data storage (music, videos, photos, etc.) My OS boots from a 64GB OCZ Vertex. For my 4TB array I want the maximum available storage and was interested to see what effect removing the reserved space would have.

First I made the Ext4 file system, mounted it and queried how much space was available.

    $ sudo mkfs.ext4 /dev/md0
    $ sudo mount /dev/md0 /home
    $ df -h
    Filesystem            Size  Used Avail Use% Mounted on
    /dev/md0             3.69T  186M 3.69T   1% /home
    ...

Looks like I have 3.69T of available space. Then I unmounted the file system, removed the reserved blocks, checked the consistency of the file system, mounted it and queried how much space was available.

    $ sudo umount /mnt
    $ sudo tune2fs -m 0 /dev/md0
    $ sudo e2fsck /dev/md0
    $ df -h
    Filesystem            Size  Used Avail Use% Mounted on
    /dev/md0             3.92T  186M 3.92T   1% /home
    ...

Looks like I have 3.92TB available now for a saving of 235GB.

Now, I could have simply created the files system without the reserved blocks in the first place, but I was interested to see the comparison.
