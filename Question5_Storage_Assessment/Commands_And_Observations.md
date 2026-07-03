# Question 5 - Commands, Outputs, and Observations

## Command 1

```bash
lsblk
```

Output:

```text
NAME        MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
zram0       253:0    0   7.7G  0 disk [SWAP]
nvme0n1     259:0    0 476.9G  0 disk
├─nvme0n1p1 259:1    0   200M  0 part /boot/efi
├─nvme0n1p2 259:2    0    16M  0 part
├─nvme0n1p3 259:3    0 249.2G  0 part
├─nvme0n1p4 259:4    0   780M  0 part
└─nvme0n1p5 259:5    0 226.7G  0 part /
```

Observation: This command lists all block devices in a tree format. The system has one 476.9G NVMe drive with five partitions and a 7.7G zram swap device.

## Command 2

```bash
df -h
```

Output:

```text
Filesystem      Size  Used Avail Use% Mounted on
/dev/nvme0n1p5  223G   91G  120G  44% /
/dev/nvme0n1p1  196M   47M  150M  24% /boot/efi
tmpfs           7.7G   50M  7.7G   1% /tmp
```

Observation: This command shows disk space usage in human-readable format. The root filesystem uses 44% of capacity with 120G still available.

## Command 3

```bash
mount | head -15
```

Output:

```text
/dev/nvme0n1p5 on / type ext4 (rw,relatime)
/dev/nvme0n1p1 on /boot/efi type vfat (rw,relatime,...)
tmpfs on /dev/shm type tmpfs (rw,nosuid,nodev,inode64,...)
```

Observation: This command displays currently mounted filesystems with their mount options. The root partition uses ext4 and the EFI partition uses vfat.

## Command 4

```bash
df -i
```

Output:

```text
Filesystem       Inodes   IUsed    IFree IUse% Mounted on
/dev/nvme0n1p5 14860288 1184860 13675428    8% /
```

Observation: This command shows inode usage per filesystem. Root has 8% inode utilization, which is healthy and far from exhaustion.

## Command 5

```bash
vim Storage_Assessment_Report.txt
```

Output:

```text
No terminal output
```

Observation: I opened Storage_Assessment_Report.txt in vim to create and edit the storage assessment report as required by the assignment. The report documents devices, mount points, disk usage, inode utilization, health observations, and recommendations.
