# Question 3 - Commands, Outputs, and Observations

## Command 1

```bash
mkdir -p link_lab && cd link_lab
```

Output:

```text
No output
```

Observation: This command created a dedicated directory for the link experiment and moved into it.

## Command 2

```bash
echo "This is the original file for link analysis." > original.txt
```

Output:

```text
No output
```

Observation: This command created the original file with 45 bytes of sample text that will be used to test link behavior.

## Command 3

```bash
ln original.txt hardlink.txt
```

Output:

```text
No output
```

Observation: This command created a hard link named hardlink.txt. A hard link points to the same inode and data blocks as the original file.

## Command 4

```bash
ln -s original.txt symlink.txt
```

Output:

```text
No output
```

Observation: This command created a symbolic link named symlink.txt that stores the path "original.txt" rather than the file data.

## Command 5

```bash
ls -li
```

Output:

```text
4362660 .rw-r--r-- 45 tauqueer  3 Jul 11:53  hardlink.txt
4362660 .rw-r--r-- 45 tauqueer  3 Jul 11:53  original.txt
4362661 lrwxrwxrwx  - tauqueer  3 Jul 11:53  symlink.txt -> original.txt
```

Observation: This command lists files with their inode numbers. original.txt and hardlink.txt share inode 4362660, while symlink.txt has a different inode 4362661 and shows its target.

## Command 6

```bash
stat original.txt
```

Output:

```text
  File: original.txt
  Size: 45   Inode: 4362660   Links: 2
Access: (0644/-rw-r--r--)  Uid: (1000/tauqueer)  Gid: (1000/tauqueer)
```

Observation: This command shows detailed metadata for the original file. The link count of 2 confirms a hard link points to the same inode.

## Command 7

```bash
stat hardlink.txt
```

Output:

```text
  File: hardlink.txt
  Size: 45   Inode: 4362660   Links: 2
Access: (0644/-rw-r--r--)  Uid: (1000/tauqueer)  Gid: (1000/tauqueer)
```

Observation: This command shows hardlink.txt has the identical inode (4362660) and link count as original.txt, proving both names reference the same data.

## Command 8

```bash
stat symlink.txt
```

Output:

```text
  File: symlink.txt -> original.txt
  Size: 12   Inode: 4362661   Links: 1
Access: (0777/lrwxrwxrwx)  Uid: (1000/tauqueer)  Gid: (1000/tauqueer)
```

Observation: This command confirms symlink.txt is a symbolic link with its own inode (4362661) and a size of 12 bytes, which is the length of the stored path "original.txt".

## Command 9

```bash
cat original.txt hardlink.txt symlink.txt
```

Output:

```text
This is the original file for link analysis.
This is the original file for link analysis.
This is the original file for link analysis.
```

Observation: Before deletion, all three names return the same content because both links currently resolve to the original data.

## Command 10

```bash
rm original.txt
```

Output:

```text
No output
```

Observation: This command deleted the original filename to test whether the hard link and symbolic link can still access the data.

## Command 11

```bash
ls -li
```

Output:

```text
4362660 .rw-r--r-- 45 tauqueer  3 Jul 11:53  hardlink.txt
4362661 lrwxrwxrwx  - tauqueer  3 Jul 11:53  symlink.txt -> original.txt
```

Observation: After deletion, hardlink.txt remains with inode 4362660 (link count now 1), while the symlink still lists a target that no longer exists.

## Command 12

```bash
cat hardlink.txt
```

Output:

```text
This is the original file for link analysis.
```

Observation: The hard link still returns the full content because the underlying inode data persists after the original name was removed.

## Command 13

```bash
cat symlink.txt
```

Output:

```text
cat: symlink.txt: No such file or directory
```

Observation: The symbolic link is now broken because its target original.txt was deleted. This shows that symlinks depend on the target path existing.
