# disk-backup.sh

Bash wrapper for creating and restoring backups of entire disks (partition table and filesystems) using the partclone utility. The script supports creating backups as compressed (.tar.gz or .tar.xz) or uncompressed (.tar) archives.

## Features

- Backup entire disks including partition table as tarballed partclone images
- Excludes blank filesystem space (partclone feature)
- Create a compressed or uncompressed archives
- Restore partition table and contents from a previously created archive
- Support for btrfs, ext2, ext3, ext4, reiserfs, xfs, fat and other common filesystems supported by partclone

## Usage
```
disk-backup.sh <operation> <disk> <archive_filename>
```

### Operations:

- `backup`: Create a backup archive from the specified disk.
- `restore`: Restore partitions from the specified archive to the disk.

### Examples:

Create a compressed backup archive:
```
./disk-backup.sh backup /dev/sdX backup.tar.xz
```
Create an uncompressed backup archive:
```
./disk-backup.sh backup /dev/sdX backup.tar
```
Restore partitions from an archive:
```
./disk-backup.sh restore backup.tar /dev/sdX
```

## Prerequisites

- partclone
- parted
- sfdisk
- xz (for .tar.xz archives)
- gzip (for .tar.gz archives)
