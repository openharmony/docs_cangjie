# toybox

<!--Del-->
> **Note:**
>
> Currently in the beta phase.
<!--DelEnd-->

toybox is a lightweight collection of Linux command-line utilities that combines commonly used Linux commands into a single executable.

## Prerequisites

### Usage Method 1

- Connect the device normally
- Use `hdc shell` to enter command-line execution mode

### Usage Method 2

- Run within the application sandbox

## Command Line Instructions

toybox can be executed in two ways:

- `toybox [command] [arguments...]`
- Direct execution: `[command] [arguments...]`

Where `[command]` can be replaced with any command supported by toybox (queryable by running toybox without parameters).  
`[arguments...]` represents the parameters required by `[command]`.

<!--RP1-->
<!--RP1End-->

### Help Command

Format: `toybox [--long | --help | --version | [command] [arguments...]]`

| Option | Parameters | Description |
| :- | :- | :- |
| --help | NA | Display command help. |
| --long | NA | Display paths of all supported commands. |
| --version | NA | Display version number. |
| NA | NA | Display all commands supported by `[command]`. |
| `[command]` | `[arguments]` | Execute specific command. Most commands also support `--help` and `--version` parameters. |

Format: `help [-ah] [command]`

| Parameter | Description |
| :- | :- |
| command | Display help for `command`. `[command]` can be replaced with any command supported by toybox. |

| Option | Description |
| :- | :- |
| -a | Display help for all commands. |

### Mathematical & Computer Fundamentals

| Command | Description |
| :- | :- |
| ascii     | Display ASCII encoding table.<br/>Usage: `ascii` |
| factor     | Factorize numbers.<br/>Usage: `factor NUMBER...` |
| mcookie | Generate 128-bit strong random number.<br/>Usage: `mcookie [-vV]` |
| mkpasswd | Encrypt passwords.<br/>Usage: `mkpasswd [-P FD] [-m TYPE] [-S SALT] [PASSWORD] [SALT]` |
| uuidgen    | Create and print new RFC4122 random UUID.<br/>Usage: `uuidgen` |

### Terminal Operations

| Command | Description |
| :- | :- |
| chvt   | Switch to virtual terminal N.<br/>Usage: `chvt N` |
| chroot | Run command with specified root directory.<br/>Usage: `chroot NEWROOT [COMMAND [ARG...]]` |
| clear  | Clear terminal.<br/>Usage: `clear` |
| nohup  | Run command immune to hangups.<br/>Usage: `nohup COMMAND [ARG...]` |
| tty    | Display terminal name connected to stdin.<br/>Usage: `tty [-s]` |
| reset  | Reset terminal.<br/>Usage: `reset` |
| microcom | Simple serial terminal.<br/>Usage: `microcom [-s SPEED] [-X] DEVICE` |

### Shell Logic Commands

| Command | Description |
| :- | :- |
| false | Return non-zero value.<br/>Usage: `false` |
| sh    | Shell command interpreter. |
| test  | Evaluate expression returning true/false. Returns false if no arguments.<br/>Usage: `test [-bcdefghLPrSsuwx PATH] [-nz STRING] [-t FD] [X ?? Y]` |
| true  | Return zero.<br/>Usage: `true` |
| yes   | Repeatedly output line until killed. Outputs "y" if no arguments.<br/>Usage: `yes [args...]` |

### System Operations

| Command | Description |
| :- | :- |
| acpi   | Query power/temperature status.<br/>Usage: `acpi [-abctV]` |
| arch | Print system architecture.<br/>Usage: `arch` |
| dmesg | Display/control kernel ring buffer.<br/>Usage: `dmesg [-Cc] [-r \| -t \| -T] [-n LEVEL] [-s SIZE] [-w]` |
| dnsdomainname | Display system name (same as `hostname -d`).<br/>Usage: `dnsdomainname` |
| getconf   | Get system configuration values (some require path parameter).<br/>Usage: `getconf -a [PATH] \| -l \| NAME [PATH]` |
| env       | Set environment for command invocation or list environment variables.<br/>Usage: `env [-i] [-u NAME] [NAME=VALUE...] [COMMAND [ARG...]]` |
| hostname  | Get/set hostname.<br/>Usage: `hostname [-bdsf] [-F FILENAME] [newname]` |
| insmod    | Load kernel module.<br/>Usage: `insmod MODULE [MODULE_OPTIONS]` |
| logger    | Log system messages.<br/>Usage: `logger [-s] [-t TAG] [-p [FACILITY.]PRIORITY] [message...]` |
| lsmod     | Show loaded modules with sizes/dependencies.<br/>Usage: `lsmod` |
| mix       | Display/set OSS mixer channels.<br/>Usage: `mix [-d DEV] [-c CHANNEL] [-l VOL] [-r RIGHT]` |
| modinfo   | Show kernel module information.<br/>Usage: `modinfo [-0] [-b basedir] [-k kernel] [-F field] [module \| file...]` |
| nproc     | Print processor count.<br/>Usage: `nproc [--all]` |
| oneit     | Simple init program.<br/>Usage: `oneit [-p] [-c /dev/tty0] command [...]` |
| partprobe | Inform kernel of partition table changes.<br/>Usage: `partprobe DEVICE...` |
| pivot_root | Change root directory.<br/>Usage: `pivot_root OLD NEW` |
| printenv  | Print environment variables.<br/>Usage: `printenv [-0] [env\_var...]` |
| reboot/halt/poweroff | Reboot/stop/power off.<br/>Usage: `reboot/halt/poweroff [-fn]` |
| rfkill    | Enable/disable wireless devices.<br/>Usage: `rfkill COMMAND [DEVICE]` |
| rmmod     | Unload kernel module.<br/>Usage: `rmmod [-wf] [MODULE]` |
| sendevent | Send Linux input event.<br/>Usage: `sendevent DEVICE TYPE CODE VALUE` |
| swapoff   | Disable swap space.<br/>Usage: `swapoff swapregion` |
| swapon    | Enable swapping on specified device/file.<br/>Usage: `swapon [-d] [-p priority] filename` |
| switch_root | Switch root directory and execute new INIT.<br/>Usage: `switch_root [-c /dev/console] NEW_ROOT NEW_INIT...` |
| uname     | Print system information.<br/>Usage: `uname [-asnrvm]` |
| vmstat    | Print virtual memory statistics.<br/>Usage: `vmstat [-n] [DELAY [COUNT]]` |

### Time & Date

| Command | Description |
| :- | :- |
| cal     | Print calendar.<br/>Usage: `cal [[month] year]` |
| date    | Set/get current date/time.<br/>Usage: `date [-u] [-r FILE] [-d DATE] [+DISPLAY\_FORMAT] [SET]` |
| hwclock | Get/set hardware clock.<br/>Usage: `hwclock [-rswtluf]` |
| sleep   | Wait for specified duration before exiting. Can be fractional. Optional suffixes: "m" (minutes), "h" (hours), "d" (days), or "s" (seconds, default).<br/>Usage: `sleep DURATION` |
| time    | Run command line and report real/user/system time in seconds.<br/>Usage: `time [-pv] COMMAND [ARGS...]` |
| uptime  | Display current time, system uptime, user count, and load averages.<br/>Usage: `uptime [-ps]` |
| usleep  | Wait for specified microseconds before exiting.<br/>Usage: `usleep MICROSECONDS` |

### User Operations

| Command | Description |
| :- | :- |
| groups  | Print user's groups.<br/>Usage: `groups [user]` |
| id      | Print user/group IDs.<br/>Usage: `id [-nGgru] [USER...]` |
| login   | User login.<br/>Usage: `login [-p] [-h host] [-f USERNAME] [USERNAME]` |
| logname/whoami | Print current username.<br/>Usage: `logname/whoami` |
| passwd  | Update user authentication token.<br/>Usage: `passwd [-a ALGO] [-dlu] [USER]` |
| who     | Print logged-in users.<br/>Usage: `who` |
| w       | Show logged-in users and login times.<br/>Usage: `w` |

### Process Operations

| Command | Description |
| :- | :- |
| chrt      | Get/set process scheduling policy/priority.<br/>Usage: `chrt [-Rmofrbi] {-p PID [PRIORITY] \| [PRIORITY COMMAND...]}` |
| iorenice  | Show/modify process I/O priority.<br/>Usage: `iorenice PID [CLASS] [PRIORITY]` |
| iotop     | Sort processes by I/O.<br/>Usage: `iotop [-AaKObq] [-n NUMBER] [-d SECONDS] [-p PID,] [-u USER,]` |
| ionice    | Show/modify process I/O scheduling priority.<br/>Usage: `ionice [-t] [-c CLASS] [-n LEVEL] [COMMAND...\|-p PID]` |
| kill      | Send signal to process.<br/>Usage: `kill [-l [SIGNAL] \| -s SIGNAL \| -SIGNAL] pid...` |
| killall   | Send signal to all processes with given name (default: SIGTERM).<br/>Usage: `killall [-l] [-iqv] [-SIGNAL \| -s SIGNAL]  PROCESS\_NAME...` |
| killall5  | Send signal to all processes outside current session.<br/>Usage: `killall5 [-l [SIGNAL]] [-SIGNAL \| -s SIGNAL] [-o PID]...` |
| pidof   | Print PIDs of processes with given name.<br/>Usage: `pidof [-s] [-o omitpid[,omitpid...]] [NAME...]` |
| pkill   | Kill processes by name.<br/>Usage: `pkill [-fnovx] [-SIGNAL \| -l SIGNAL] [PATTERN] [-G GID,] [-g PGRP,] [-P PPID,] [-s SID,] [-t TERM,] [-U UID,] [-u EUID,]` |
| pmap    | Show process memory map.<br/>Usage: `pmap [-xq] [pids...]` |
| ps      | Show process information.<br/>Usage: `ps [-AadefLlnwZ] [-gG GROUP,] [-k FIELD,] [-o FIELD,] [-p PID,] [-t TTY,] [-uU USER,]` |
| pwdx    | Print process working directory.<br/>Usage: `pwdx PID...` |
| renice  | Adjust process/group/user priority.<br/>Usage: `renice [-gpu] -n increment ID ...` |
| setsid  | Run command in new session.<br/>Usage: `setsid [-t] command [args...]` |
| taskset | Start task running only on specified processors.<br/>Usage: `taskset [-ap] [mask] [PID \| cmd [args...]]` |
| timeout | Execute command with timeout.<br/>Usage: `timeout [-k DURATION] [-s SIGNAL] DURATION COMMAND...` |
| top     | Show real-time process information.<br/>Usage: `top [-Hhbq] [-k FIELD,] [-o FIELD,] [-s SORT] [-n NUMBER] [-m LINES] [-d SECONDS] [-p PID,] [-u USER,]` |
| nice    | Run command with specified priority.<br/>Usage: `nice [-n PRIORITY] COMMAND [ARG...]` |
| nsenter | Run command in specified namespace.<br/>Usage: `nsenter [-t pid] [-F] [-i] [-m] [-n] [-p] [-u] [-U] COMMAND...` |
| ulimit/prlimit | Show/set process resource limits.<br/>Usage: `ulimit/prlimit [-P PID] [-SHRacdefilmnpqrstuv] [LIMIT]` |
| unshare | Create new namespace for process.<br/>Usage: `unshare [-imnpuUr] COMMAND...` |
| watch   | Run command repeatedly, showing output.<br/>Usage: `watch [-teb] [-n SEC] PROG ARGS` |
| xargs   | Run command line with arguments from stdin.<br/>Usage: `xargs [-0prt] [-s NUM] [-n NUM] [-E STR] COMMAND...` |

### Device Node Operations

| Command | Description |
| :- | :- |
| blkid       | Print filesystem type/label/UUID.<br/>Usage: `blkid [-s TAG] [-UL] DEV...` |
| blockdev    | Call ioctl on block devices.<br/>Usage: `blockdev --OPTION... BLOCKDEV...` |
| devmem      | Read/write physical address via /dev/mem.<br/>Usage: `devmem ADDR [WIDTH [DATA]]` |
| df          | Show disk space usage.<br/>Usage: `df [-HPkhi] [-t type] [FILESYSTEM ...]` |
| du          | Show disk usage by files/directories.<br/>Usage: `du [-d N] [-askxHLlmc] [file...]` |
| eject       | Eject device (default: /dev/cdrom).<br/>Usage: `eject [-stT] [DEVICE]` |
| free        | Show memory/swap usage.<br/>Usage: `free [-bkmgt]` |
| freeramdisk | Free all memory of specified ramdisk.<br/>Usage: `freeramdisk [RAM device]` |
| fsfreeze    | Freeze/unfreeze filesystem.<br/>Usage: `fsfreeze {-f \| -u} MOUNTPOINT` |
| fstype      | Print filesystem type.<br/>Usage: `fstype DEV...` |
| fsync       | Sync file state with storage.<br/>Usage: `fsync [-d] [FILE...]` |
| i2cdetect   | Detect i2c devices.<br/>Usage:<br/>&emsp;`i2cdetect [-ary] BUS [FIRST LAST]` <br/>&emsp;`i2cdetect -F BUS`<br/>&emsp;`i2cdetect -l`|
| i2cdump     | Print all i2c registers.<br/>Usage: `i2cdump [-fy] BUS CHIP` |
| i2cget      | Read i2c register.<br/>Usage: `i2cget [-fy] BUS CHIP ADDR` |
| i2cset      | Write i2c register.<br/>Usage: `i2cset [-fy] BUS CHIP ADDR VALUE... MODE` |
| losetup     | Setup loop devices.<br/>Usage: `losetup [-cdrs] [-o OFFSET] [-S SIZE] {-d DEVICE... \| -j FILE \| -af \| {DEVICE FILE}}` |
| lspci       | Show PCI device info.<br/>Usage: `lspci [-ekmn] [-i FILE ]` |
| lsusb       | Show USB device info.<br/>Usage: `lsusb` |
| makedevs    | Create special files (block/char devices etc).<br/>Usage: `makedevs [-d device_table] rootdir` |
| mount       | Mount filesystem or show mounts.<br/>Usage: `mount [-afFrsvw] [-t TYPE] [-o OPTION,] [[DEVICE] DIR]` |
| mountpoint  | Check if directory/device is mountpoint.<br/>Usage:<br/>&emsp;`mountpoint [-qd] DIR` <br/>&emsp;`mountpoint [-qx] DEVICE` |
| sync        | Write cached data to disk.<br/>Usage: `sync` |
| sysctl      | Read/write system control data.<br/>Usage: `sysctl [-aAeNnqw] [-p [FILE] \| KEY[=VALUE]...]` |
| tunctl      | Create/delete tun/tap virtual ethernet devices.<br/>Usage: `tunctl [-dtT] [-u USER] NAME` |
| vconfig     | Create/delete virtual ethernet devices.<br/>Usage: `vconfig COMMAND [OPTIONS]` |
| umount      | Unmount filesystem.<br/>Usage: `umount [-a [-t TYPE[,TYPE...]]] [-vrfD] [DIR...]` |

### Network Operations

| Command | Description |
| :- | :- |
| ftpget/ftpput | Interact with FTP server (read/write/list files). ftpget includes -g option. ftpput includes -s option.<br/>Usage: `ftpget/ftpput [-cvgslLmMdD] [-p PORT] [-P PASSWORD] [-u USER] HOST [LOCAL] REMOTE` |
| ifconfig      | Configure network interfaces.<br/>Usage: `ifconfig [-aS] [INTERFACE [ACTION...]]` |
| nbd-client    | Create NBD client.<br/>Usage: `nbd-client [-ns] HOST PORT DEVICE` |
| netstat   | Show network info.<br/>Usage: `netstat [-pWrxwutneal]` |
| ping/ping6    | Test network connectivity. ping6 includes -6 option.<br/>Usage: `ping/ping