**\*\*WARNING\*\*** Use at own risk **\*\*WARNING\*\*** May wreck your shit **\*\*WARNING\*\***

`lvm-rotate` is an [OpenRC](https://wiki.gentoo.org/wiki/OpenRC) init script. It rotates [LVM](https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29) snapshots during boot.

Specifically, it merges a LVM snapshot with its origin, and then creates a new
snapshot of the same size. This happens after LVM is set up, but before anything
is mounted.

# Installation

Install with portage from my [overlay](https://github.com/varingst/varingst-overlay), or copy
the files manually.

`init.d/lvm-rotate` and `conf.d/lvm-rotate` are the init script and its
configuration. `lvm-rotate` is for running manually or scheduled with i.e. cron.

# Usage

Provide snapshots and rotation interval in `/etc/init.d/lvm-rotate`

Add the script to runlevel boot:

```
# rc-update add lvm-rotate boot
```

The snapshot is only merged during boot. Backup of the origin can be done while
the snapshot is mounted. The `lvm-rotate` script (not the init script) will
copy the origin of a snapshot to a backup directory, if a backup has not already been made
since the latest snapshot was created:

```
# /usr/bin/lvm-rotate vg/snapshot1 vg/snapshot2 /path/to/backup
```

The script datestamps the images and does not overwrite existing non-emtpy files, so it
can be set to run daily with cron.

