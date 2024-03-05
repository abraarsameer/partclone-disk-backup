# Partclone Disk Backup Script

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
# ./disk-backup.sh backup /dev/sdX backup.tar.xz
```
Create an uncompressed backup archive:
```
# ./disk-backup.sh backup /dev/sdX backup.tar
```
Restore partitions from an archive:
```
# ./disk-backup.sh restore backup.tar /dev/sdX
```

## Prerequisites

- partclone
- parted
- sfdisk
- xz (for .tar.xz archives)
- gzip (for .tar.gz archives)

  ## Installation

1. Clone the repository:
```
git clone https://github.com/abraarsameer/partclone-disk-backup.git
```
2. Make the script executable:
```
chmod +x disk-backup.sh
```
3. (Optional) Copy/Symlink the script to `/usr/local/bin/` for system-wide access, or to `~/.local/bin/` for local user access.

## Warning

The restore operation will overwrite all existing data on the specified disk. Use with caution.

## Disclaimer

Use this script at your own risk. The author(s) are not liable for any data loss or damage caused by its use.

## License

This script is released under the [MIT License](LICENSE).

## Contributing

Contributions are welcome! Please open an issue or submit a pull request.
