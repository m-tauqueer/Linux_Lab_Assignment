# Question 2 - Commands, Outputs, and Observations

## Command 1

```bash
mkdir -p project_workspace
```

Output:

```text
No output
```

Observation: This command created the project_workspace directory. The -p flag avoids an error if the directory already exists. No output means it succeeded.

## Command 2

```bash
touch project_workspace/plan.txt project_workspace/notes.txt
```

Output:

```text
No output
```

Observation: This command created two empty documentation files inside the workspace to represent project files.

## Command 3

```bash
ls -ld project_workspace
```

Output (before chmod):

```text
drwxr-xr-x - tauqueer  3 Jul 11:47  project_workspace
```

Observation: This command shows the directory's own permissions. The workspace was created with the default 755 permissions, allowing all users to enter and list it.

## Command 4

```bash
ls -l project_workspace
```

Output (before chmod):

```text
.rw-r--r-- 0 tauqueer  3 Jul 11:47  notes.txt
.rw-r--r-- 0 tauqueer  3 Jul 11:47  plan.txt
```

Observation: This command lists the files inside the workspace with their permissions. Both files have the default 644 permissions and are owned by tauqueer.

## Command 5

```bash
umask
```

Output:

```text
0022
```

Observation: This command displays the current umask value. A umask of 0022 means new files default to 644 and new directories default to 755.

## Command 6

```bash
id
```

Output:

```text
uid=1000(tauqueer) gid=1000(tauqueer) groups=1000(tauqueer),955(i2c),983(video),992(input),998(wheel)
```

Observation: This command confirms the identity that owns the workspace. All files and the directory are owned by tauqueer (uid 1000, gid 1000).

## Command 7

```bash
chmod 750 project_workspace
```

Output:

```text
No output
```

Observation: This command changes the directory permission to 750, giving the owner full access, the group read/execute, and removing all access for other users.

## Command 8

```bash
ls -ld project_workspace
```

Output (after chmod):

```text
drwxr-x--- - tauqueer  3 Jul 11:47  project_workspace
```

Observation: This command verifies the new permissions. The directory changed from drwxr-xr-x (755) to drwxr-x--- (750), confirming that "other" users can no longer access the workspace.

## Command 9

```bash
ls -ln project_workspace
```

Output:

```text
.rw-r--r-- 0 1000  3 Jul 11:47  notes.txt
.rw-r--r-- 0 1000  3 Jul 11:47  plan.txt
```

Observation: This command shows numeric owner and group IDs. The uid 1000 confirms the files belong to tauqueer, matching the id command output.
