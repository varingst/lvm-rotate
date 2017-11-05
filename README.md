**\*\*WARNING\*\*** Use at own risk **\*\*WARNING\*\*** May wreck your shit **\*\*WARNING\*\***

`lvm-rotate` is an [OpenRC](https://wiki.gentoo.org/wiki/OpenRC) init script. It rotates [LVM](https://en.wikipedia.org/wiki/Logical_Volume_Manager_%28Linux%29) snapshots during boot.

Specifically, it merges a LVM snapshot with its origin, and then creates a new
snapshot of the same size. This happens after LVM is set up, but before anything
is mounted.
