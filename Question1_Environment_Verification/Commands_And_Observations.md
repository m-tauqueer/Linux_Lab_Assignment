# Question 1 - Commands, Outputs, and Observations

## Command 1

```bash
whoami
```

Output:

```text
tauqueer
```

Observation: This command prints the name of the currently logged-in user. The output confirms that the active account is tauqueer.

## Command 2

```bash
id
```

Output:

```text
uid=1000(tauqueer) gid=1000(tauqueer) groups=1000(tauqueer),955(i2c),983(video),992(input),998(wheel)
```

Observation: This command shows the user ID, group ID, and all group memberships. The output confirms that tauqueer belongs to groups including wheel, video, and input.

## Command 3

```bash
groups
```

Output:

```text
tauqueer i2c video input wheel
```

Observation: This command lists the group names for the current user. The output shows the same groups as the id command in a simpler format.

## Command 4

```bash
echo "$SHELL"
```

Output:

```text
/usr/bin/bash
```

Observation: This command prints the path to the default login shell. The output shows bash is configured as the default shell.

## Command 5

```bash
pwd
```

Output:

```text
/home/tauqueer/Desktop/Linux_Lab_Assignment/Question1_Environment_Verification
```

Observation: This command prints the present working directory. The output shows that commands were run from the Question 1 folder inside the assignment repository.

## Command 6

```bash
ls -la
```

Output:

```text
.rw-r--r--  1.6k tauqueer  3 Jul 11:43  command_output.txt
.rw-r--r--  2.6k tauqueer  3 Jul 11:43  Commands_And_Observations.md
.rw-r--r--  1.2k tauqueer  3 Jul 11:43  Environment_Report.txt
drwxr-xr-x     - tauqueer  3 Jul 11:41  screenshots
```

Observation: This command lists all files and directories with permissions, owner, size, and timestamps. The output shows the report files and screenshots folder, all owned by tauqueer.

## Command 7

```bash
ping -c 4 google.com
```

Output:

```text
PING google.com (2404:6800:4002:828::200e) 56 data bytes
64 bytes from tzdelb-ao-in-x0e.1e100.net (2404:6800:4002:828::200e): icmp_seq=1 ttl=114 time=44.1 ms
64 bytes from tzdelb-ao-in-x0e.1e100.net (2404:6800:4002:828::200e): icmp_seq=2 ttl=114 time=55.9 ms
64 bytes from tzdelb-ao-in-x0e.1e100.net (2404:6800:4002:828::200e): icmp_seq=3 ttl=114 time=53.1 ms
64 bytes from tzdelb-ao-in-x0e.1e100.net (2404:6800:4002:828::200e): icmp_seq=4 ttl=114 time=43.0 ms

--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 42.961/49.032/55.922/5.583 ms
```

Observation: This command sends four ICMP packets to google.com to test network connectivity. All packets were received with 0% loss, confirming the system has working internet access.
