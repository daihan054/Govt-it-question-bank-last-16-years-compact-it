<!-- TOC START -->
**Table of Contents** — 12 subtopics · 196 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Linux / Unix Commands & Administration](#linux--unix-commands--administration-47) | 47 |
| 2 | [CPU Scheduling Algorithms](#cpu-scheduling-algorithms-25) | 25 |
| 3 | [OS Concepts & System Software](#os-concepts--system-software-24) | 24 |
| 4 | [Deadlock & Resource Allocation](#deadlock--resource-allocation-23) | 23 |
| 5 | [Virtual Memory & Page Replacement (Thrashing)](#virtual-memory--page-replacement-thrashing-16) | 16 |
| 6 | [Memory Management & Paging](#memory-management--paging-16) | 16 |
| 7 | [Process Management & Process States](#process-management--process-states-12) | 12 |
| 8 | [Concurrency, Threads & Synchronization](#concurrency-threads--synchronization-11) | 11 |
| 9 | [File Systems & Disk Management](#file-systems--disk-management-7) | 7 |
| 10 | [CPU Scheduling](#cpu-scheduling-6) | 6 |
| 11 | [Windows & System Administration](#windows--system-administration-5) | 5 |
| 12 | [Process Synchronization & Concurrency](#process-synchronization--concurrency-4) | 4 |

<!-- TOC END -->

---

## Linux / Unix Commands & Administration (47)

1. **Write Linux command:** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*
   (a) Give a file Read Write and Execute permission.
   (b) IP address show.
   (c) Delete all files in a folder.
   (d) Show partition.

   Answer: (a) Give a file read, write and execute permission
   ```bash
      chmod 777 filename          # everyone : read + write + execute
      chmod u+rwx filename        # only the OWNER gets rwx
      chmod a+rwx filename        # symbolic form of 777
   ```
   ```
      Permission values :  r = 4 , w = 2 , x = 1
      rwx = 4 + 2 + 1 = 7

      777  ->  owner 7 , group 7 , others 7
   ```

   (b) Show the IP address
   ```bash
      ip addr show                # the modern command
      ip a                        # short form
      ifconfig                    # older, from net-tools
      hostname -I                 # just the IP addresses
      ip route get 1.1.1.1        # shows which interface is used
   ```

   (c) Delete all files in a folder
   ```bash
      rm /path/to/folder/*             # files only, not subdirectories
      rm -r /path/to/folder/*          # files AND subdirectories
      rm -rf /path/to/folder/*         # force, no confirmation

      find /path/to/folder -type f -delete    # safer for very many files
   ```
   - `rm -rf` is unforgiving. There is no recycle bin, and a mistyped path such as `rm -rf / home` instead of `rm -rf /home` destroys the system.

   (d) Show partitions
   ```bash
      lsblk                       # block devices and partitions, as a tree
      fdisk -l                    # detailed partition table (needs root)
      df -h                       # MOUNTED filesystems, human readable
      parted -l                   # partition details
      cat /proc/partitions        # the kernel's own list
      blkid                       # UUID and filesystem type of each partition
   ```

   Sample outputs
   ```
      $ lsblk
      NAME   MAJ:MIN RM  SIZE RO TYPE MOUNTPOINT
      sda      8:0    0  500G  0 disk
      |-sda1   8:1    0    1G  0 part /boot
      |-sda2   8:2    0  100G  0 part /
      `-sda3   8:3    0  399G  0 part /home

      $ df -h
      Filesystem      Size  Used Avail Use% Mounted on
      /dev/sda2       100G   45G   50G  48% /
      /dev/sda3       399G  120G  259G  32% /home
   ```

   Summary

   | Task | Command |
   |---|---|
   | Full permission | `chmod 777 filename` |
   | Show IP address | `ip addr show` or `ifconfig` |
   | Delete all files in a folder | `rm -rf /path/*` |
   | Show partitions | `lsblk` or `fdisk -l` |

2. **Write a Linux command to count the total number of characters and words from the first 10 lines of a file named "wasacustomers.txt".** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*

   Answer: The task is to take the `first 10 lines` of the file and count the characters and words in them.
   ```bash
      head -10 wasacustomers.txt | wc -cw
   ```

   How it works
   ```
      head -10 wasacustomers.txt   takes the first 10 lines
           |                       the pipe passes them to the next command
      wc -cw                       counts characters (-c) and words (-w)
   ```

   The `wc` options
   ```
      wc -l    count LINES
      wc -w    count WORDS
      wc -c    count BYTES (characters)
      wc -m    count CHARACTERS (correct for multibyte UTF-8 text)
      wc       with no option : lines, words and bytes together
   ```

   Variants
   ```bash
      head -10 wasacustomers.txt | wc -w        # words only
      head -10 wasacustomers.txt | wc -c        # characters only
      head -10 wasacustomers.txt | wc -m        # characters, UTF-8 aware
      head -10 wasacustomers.txt | wc           # lines, words and characters

      head -n 10 wasacustomers.txt | wc -cw     # -n 10 is the explicit form
   ```

   Sample output
   ```
      $ head -10 wasacustomers.txt | wc -cw
         452     78
         ^       ^
         chars   words
   ```

   Related commands worth knowing
   ```bash
      tail -10 file            # the LAST 10 lines
      tail -f  file            # follow a log file as it grows
      head -5 file | tail -1   # only the 5th line
      sed -n '11,15p' file     # lines 11 to 15
      wc -l file               # how many lines the whole file has
      cat file | wc -w         # words in the WHOLE file
   ```

   - Point worth noting: for text containing Bengali or any other multibyte script, use `wc -m` rather than `wc -c`. `-c` counts bytes, and a Bengali character occupies three bytes in UTF-8, so `-c` would give roughly three times the true character count.

3. **Linux command:** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1361 (ET: BUET)], [GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)], [PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*

   Answer: The question is `incomplete` — the paper printed only the heading "Linux command:" and the list of specific commands asked for was not captured. The commands that appear most often in this paper are given below, so the answer is usable whichever sub-questions were intended.

   File and directory commands
   ```bash
      ls -la                  # list all files with details, including hidden
      pwd                     # print the current working directory
      cd /path                # change directory ; cd .. up , cd ~ home
      mkdir -p a/b/c          # create a directory, with parents
      rmdir folder            # remove an EMPTY directory
      rm file                 # remove a file
      rm -r folder            # remove a directory and its contents
      cp file dest            # copy ; cp -r for a directory
      mv old new              # move, or RENAME
      touch file              # create an empty file
      find / -name "*.txt"    # search for files by name
   ```

   Viewing and searching file contents
   ```bash
      cat file                # display the whole file
      head -10 file           # first 10 lines
      tail -10 file           # last 10 lines
      tail -f logfile         # follow a log as it grows
      less file               # page through a file
      grep -n "text" file     # search for a string, with line numbers
      grep -r "text" /path    # search recursively
      wc -l file              # count lines ; -w words , -c bytes
      sed -n '10,20p' file    # print lines 10 to 20
   ```

   Permission and ownership
   ```bash
      chmod 755 file          # set permissions (r=4 , w=2 , x=1)
      chmod u+x file          # symbolic form
      chown user:group file   # change owner and group
      ls -l file              # view the current permissions
   ```

   Process and system information
   ```bash
      ps aux                  # every running process
      top                     # live CPU, memory and process view
      kill -9 PID             # terminate a process
      df -h                   # disk space of all filesystems
      du -sh folder           # size of a folder
      free -h                 # RAM and swap
      uname -a                # kernel and system information
      uptime                  # how long the system has been up
   ```

   Network commands
   ```bash
      ip addr show            # IP addresses  (older: ifconfig)
      ping -c 4 host          # test connectivity
      traceroute host         # the path packets take
      netstat -tuln           # listening ports  (modern: ss -tuln)
      ssh user@host           # secure remote login
      scp file user@host:/dir # copy a file over SSH
      wget URL                # download a file
   ```

   User management
   ```bash
      sudo useradd -m user    # create a user with a home directory
      sudo passwd user        # set the password
      sudo usermod -aG grp u  # add the user to a group
      whoami , id , groups    # who am I, and what groups am I in
   ```

   Archiving and packages
   ```bash
      tar -czvf a.tar.gz dir  # create a compressed archive
      tar -xzvf a.tar.gz      # extract it
      sudo apt install pkg    # Debian and Ubuntu
      sudo yum install pkg    # RHEL and CentOS
   ```

   - The permission arithmetic, which almost every version of this question needs: `r = 4, w = 2, x = 1`, so `rwx = 7`, `r-x = 5` and `r-- = 4`, giving the familiar `755` and `644`.

4. **Write Linux command:** *[BCIC Assistant Programmer 14.02.2025 compact it 1324 (ET: BUET)]*
   * **(a) Displays real-time system statistics, including CPU usage, memory usage, running processes, and system load.**
   * **(b) Searches for a specified pattern in a file or output.**
   * **(c) Shows disk usage for all mounted file systems.**
   * **(d) Displays information about system memory (RAM and swap).** *[BCIC Assistant Programmer 14.02.2025 compact it 1325 (ET: BUET)]*

   Answer: (a) Real-time system statistics — CPU, memory, processes, load
   ```bash
      top                    # the classic real-time process viewer
      htop                   # a friendlier colour version, if installed
   ```
   ```
      top - 14:32:01 up 5 days,  3:12,  2 users,  load average: 0.52, 0.58, 0.59
      Tasks: 245 total,   1 running, 244 sleeping
      %Cpu(s):  4.2 us,  1.1 sy,  0.0 ni, 94.5 id
      MiB Mem :  15852.0 total,   4210.5 free,   6120.3 used
   ```
   - Press `q` to quit, `k` to kill a process, `M` to sort by memory and `P` to sort by CPU.

   (b) Search for a pattern in a file or in output
   ```bash
      grep "pattern" filename
      grep -i "pattern" filename       # ignore case
      grep -r "pattern" /path          # search recursively
      grep -n "pattern" filename       # show line numbers
      grep -v "pattern" filename       # INVERT - lines NOT matching
      grep -c "pattern" filename       # count matching lines

      ps aux | grep httpd              # searching the output of another command
   ```

   (c) Disk usage for all mounted file systems
   ```bash
      df -h                   # human readable : G, M, K
      df -Th                  # also shows the filesystem TYPE
      df -i                   # inode usage instead of blocks
   ```
   ```
      Filesystem      Size  Used Avail Use% Mounted on
      /dev/sda2       100G   45G   50G  48% /
      /dev/sda3       399G  120G  259G  32% /home
      tmpfs           7.8G  1.2M  7.8G   1% /run
   ```
   - Do not confuse `df` with `du`: `df` reports `filesystem` usage, while `du` reports the size of `directories`.

   (d) System memory — RAM and swap
   ```bash
      free -h                 # human readable
      free -m                 # in megabytes
      free -g                 # in gigabytes
      cat /proc/meminfo       # the kernel's detailed view
      vmstat                  # memory plus CPU and I/O statistics
   ```
   ```
                     total        used        free      shared  buff/cache   available
      Mem:            15Gi       6.0Gi       4.1Gi       1.2Gi       5.4Gi       8.0Gi
      Swap:          2.0Gi          0B       2.0Gi
   ```

   Summary

   | Requirement | Command |
   |---|---|
   | (a) Real-time CPU, memory, processes, load | `top` (or `htop`) |
   | (b) Search a pattern | `grep "pattern" file` |
   | (c) Disk usage of all filesystems | `df -h` |
   | (d) RAM and swap information | `free -h` |

   - Related monitoring commands worth naming: `uptime` for the load average alone, `iostat` for disk I/O, `netstat` or `ss` for network sockets, and `ps aux` for a one-off snapshot of every process.

5. **ফাইল Rename করার Linux কমান্ড কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Linux has no separate rename command in the classic Unix set. Renaming is done with `mv`.
   ```bash
      mv oldname.txt newname.txt
   ```
   - `mv` means "move". Moving a file to a new name in the same directory `is` a rename, because the file's data never moves — only its directory entry changes.

   Examples
   ```bash
      mv report.txt final_report.txt          # rename a file
      mv olddir newdir                        # rename a directory
      mv /home/user/a.txt /home/user/b.txt    # rename with a full path
      mv -i old.txt new.txt                   # ask before overwriting
      mv -v old.txt new.txt                   # verbose - show what was done
   ```

   Renaming many files at once — the `rename` command
   ```bash
      rename 's/.txt/.doc/' *.txt        # change every .txt to .doc (Perl version)
      rename .txt .doc *.txt             # the util-linux version
   ```

   Renaming many files with a loop, which works everywhere
   ```bash
      for f in *.txt; do
          mv "$f" "${f%.txt}.doc"
      done
   ```

   Points to note
   ```
      mv OVERWRITES the destination silently if it already exists.
           Use  mv -i  to be asked first, or  mv -n  never to overwrite.

      mv also MOVES a file to another directory :
           mv file.txt /home/user/documents/

      Quote names containing spaces :
           mv "my file.txt" "my_file.txt"

      Renaming needs WRITE permission on the DIRECTORY, not on the file.
   ```

   Related commands
   ```
      cp   copy a file
      rm   delete a file
      mv   move or rename
      ln   create a link
   ```
   - Short answer: `mv oldname newname`.

6. **Which file is need by init to get the default run level?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*

   Answer: The file is `/etc/inittab`.

   - On a traditional `SysV init` system, `init` reads `/etc/inittab` at boot and finds the default run level in the `initdefault` line.
   ```
      id:3:initdefault:
         ^
         the default run level
   ```

   The run levels
   ```
      0  : Halt - shut the system down
      1  : Single-user mode, for maintenance
      2  : Multi-user without networking (Debian: full multi-user)
      3  : Full multi-user with networking, TEXT console      <- servers
      4  : Unused / user definable
      5  : Full multi-user with a GRAPHICAL interface (X11)   <- desktops
      6  : Reboot
   ```

   Related commands
   ```bash
      runlevel               # show the previous and current run level
      who -r                 # the same information
      init 3                 # switch to run level 3 now
      telinit 5              # the same as init
   ```

   On a modern `systemd` system
   - `/etc/inittab` is no longer used. The equivalent is a symbolic link:
   ```bash
      /etc/systemd/system/default.target
   ```
   ```bash
      systemctl get-default               # show the default target
      systemctl set-default multi-user.target      # equivalent to run level 3
      systemctl set-default graphical.target       # equivalent to run level 5
      systemctl isolate multi-user.target          # switch now
   ```

   Mapping between the two
   ```
      Run level 0  ->  poweroff.target
      Run level 1  ->  rescue.target
      Run level 3  ->  multi-user.target
      Run level 5  ->  graphical.target
      Run level 6  ->  reboot.target
   ```

   - Short answer: `/etc/inittab` on a SysV init system, and `/etc/systemd/system/default.target` on a systemd system. Since almost every current distribution uses systemd, both should be mentioned.

7. **Show last 10 lines of log file which is continuously updating in Linux command?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*

   Answer: The command is `tail -f`.
   ```bash
      tail -f /var/log/syslog
   ```

   - `tail` shows the `last` part of a file. By default it prints the last `10` lines, which is exactly what the question asks for, and `-f` means `follow`: the command does not exit but keeps printing new lines as they are appended. This is how a live log is watched.

   Variants
   ```bash
      tail -f logfile             # last 10 lines, then follow
      tail -n 10 -f logfile       # the same, written explicitly
      tail -20f logfile           # last 20 lines, then follow
      tail -F logfile             # follow even if the file is ROTATED or
                                  # recreated - safer for real logs
      tailf logfile               # older equivalent of tail -F
   ```
   - Press `Ctrl + C` to stop following.

   Why `-F` is usually better than `-f`
   ```
      Log files are ROTATED : syslog becomes syslog.1 and a new empty
      syslog is created. With -f, tail keeps reading the OLD file and
      shows nothing further. With -F it notices and follows the new file.
   ```

   Following several files at once
   ```bash
      tail -f /var/log/syslog /var/log/auth.log
      # each file's output is preceded by a ==> filename <== header
   ```

   Combining with grep, which is the usual practical form
   ```bash
      tail -f /var/log/apache2/error.log | grep "500"
      tail -f /var/log/syslog | grep -i "error"
      tail -f app.log | grep --line-buffered "ERROR"   # avoids buffering delay
   ```

   On a systemd system, for service logs
   ```bash
      journalctl -f                        # follow the whole journal
      journalctl -u nginx -f               # follow one service
      journalctl -n 10 -f                  # last 10 entries, then follow
   ```

   Related commands
   ```
      head -10 file      the FIRST 10 lines
      tail -10 file      the LAST 10 lines
      less +F file       like tail -f, but Ctrl+C returns to normal paging
      watch -n 2 cmd     re-run a command every 2 seconds
   ```

   - Short answer: `tail -f filename` — and `tail -F` in production, so that log rotation does not silently stop the output.

8. **Linux Command in ownership and group permission.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 567 (ET: N/A)]*

   Answer: Ownership is changed with `chown` and `chgrp`; permissions are changed with `chmod`.

   Changing the owner — `chown`
   ```bash
      chown newowner filename                # change the OWNER only
      chown newowner:newgroup filename       # change owner AND group
      chown :newgroup filename               # change the GROUP only
      chown -R newowner:newgroup /path       # recursive, for a whole tree
      chown --reference=file1 file2          # copy file1's ownership to file2
   ```
   ```bash
      chown rahim report.txt                 # rahim now owns it
      chown rahim:accounts report.txt        # owner rahim, group accounts
      chown -R www-data:www-data /var/www    # typical for a web server
   ```

   Changing the group — `chgrp`
   ```bash
      chgrp newgroup filename
      chgrp -R accounts /home/finance
   ```
   - `chgrp accounts file` and `chown :accounts file` do exactly the same thing.

   Changing permissions — `chmod`
   ```
      Three classes :  u = user (owner) , g = group , o = others , a = all
      Three rights  :  r = read (4) , w = write (2) , x = execute (1)
   ```

   Numeric (octal) form
   ```bash
      chmod 755 filename      # owner rwx , group r-x , others r-x
      chmod 644 filename      # owner rw- , group r-- , others r--
      chmod 700 filename      # owner rwx , nobody else anything
      chmod 777 filename      # everyone everything - rarely wise
      chmod -R 755 /var/www   # recursive
   ```
   ```
      7 = 4+2+1 = rwx        4 = r--
      6 = 4+2   = rw-        2 = -w-
      5 = 4+1   = r-x        1 = --x
      3 = 2+1   = -wx        0 = ---
   ```

   Symbolic form
   ```bash
      chmod u+x script.sh          # add execute for the owner
      chmod g-w file.txt           # remove write from the group
      chmod o=r file.txt           # set others to read only
      chmod a+r file.txt           # add read for everyone
      chmod u=rwx,g=rx,o= file     # set all three at once
   ```

   Viewing the current ownership and permissions
   ```bash
      ls -l report.txt
   ```
   ```
      -rwxr-xr--  1  rahim  accounts  2048  Sep 4 10:30  report.txt
      ^^^^^^^^^^     ^^^^^  ^^^^^^^^
      |||  |||  |||  owner  group
      |||  |||  +--- others : r--
      |||  +-------- group  : r-x
      +------------- owner  : rwx
      ^
      file type : - file , d directory , l link
   ```

   Special permission bits
   ```bash
      chmod u+s file          # SETUID  - run as the file's owner
      chmod g+s directory     # SETGID  - new files inherit the directory's group
      chmod +t /tmp           # STICKY  - only the owner may delete their files
      chmod 1777 /tmp         # the same, in numeric form
   ```

   Summary

   | Task | Command |
   |---|---|
   | Change owner | `chown user file` |
   | Change owner and group | `chown user:group file` |
   | Change group only | `chgrp group file` or `chown :group file` |
   | Change permission (numeric) | `chmod 755 file` |
   | Change permission (symbolic) | `chmod u+x file` |
   | View ownership and permission | `ls -l file` |
   | Apply to a whole tree | add `-R` |

   - Only `root` may give a file away to another user; an ordinary owner may change the group only to one they belong to.

9. **UNIX command with example: File move, Change Directory and search from a specific line.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 500 (ET: IBA)]*

   Answer: File move — `mv`
   ```bash
      mv source destination
   ```
   ```bash
      mv report.txt /home/user/documents/          # move to another directory
      mv report.txt final.txt                      # RENAME in place
      mv file1.txt file2.txt /backup/              # move several at once
      mv *.txt /home/user/docs/                    # move by wildcard
      mv -i old.txt new.txt                        # ask before overwriting
      mv -v report.txt /backup/                    # verbose
   ```
   - `mv` serves as both `move` and `rename`, because renaming is simply moving a file to a new name in the same directory.
   - It overwrites the destination `silently` if it exists — use `-i` to be prompted or `-n` never to overwrite.

   Change directory — `cd`
   ```bash
      cd /home/user/documents      # absolute path, from the root
      cd documents                 # relative path, from where you are
      cd ..                        # up one level
      cd ../..                     # up two levels
      cd ~                         # the HOME directory
      cd                           # also home, with no argument
      cd -                         # back to the PREVIOUS directory
      cd /                         # the root directory
   ```
   ```bash
      $ pwd
      /home/rahim
      $ cd documents/reports
      $ pwd
      /home/rahim/documents/reports
      $ cd ../..
      $ pwd
      /home/rahim
   ```
   - `cd` is a `shell built-in`, not a program, because it must change the shell's own working directory.

   Search from a specific line — `grep`, `sed` and `awk`
   ```bash
      # search for a pattern anywhere in the file
      grep "pattern" filename
      grep -n "pattern" filename          # WITH line numbers
      grep -i "pattern" filename          # ignore case
      grep -r "pattern" /path             # recursive
      grep -c "pattern" filename          # count matching lines
      grep -v "pattern" filename          # lines that do NOT match
   ```
   ```bash
      # print a specific RANGE of lines
      sed -n '10,20p' filename            # lines 10 to 20
      sed -n '15p' filename               # only line 15
      awk 'NR >= 10 && NR <= 20' filename # the same, with awk
      head -20 filename | tail -11        # lines 10 to 20, another way
   ```
   ```bash
      # search only FROM a given line onward
      tail -n +10 filename | grep "pattern"       # from line 10 to the end
      sed -n '10,$p' filename | grep "pattern"    # the same
      awk 'NR >= 10 && /pattern/' filename        # awk does both at once
   ```

   Worked example
   ```bash
      $ cat customers.txt
      1  Rahim  Dhaka
      2  Karim  Chattogram
      ...

      $ grep -n "Dhaka" customers.txt
      1:1  Rahim  Dhaka
      14:14 Jamal  Dhaka

      $ sed -n '10,15p' customers.txt        # lines 10 to 15 only

      $ awk 'NR >= 10 && /Dhaka/' customers.txt   # Dhaka, from line 10 onward
   ```

   Summary

   | Task | Command | Example |
   |---|---|---|
   | Move a file | `mv` | `mv a.txt /backup/` |
   | Rename a file | `mv` | `mv a.txt b.txt` |
   | Change directory | `cd` | `cd /home/user` |
   | Go up one level | `cd ..` | |
   | Go home | `cd ~` or `cd` | |
   | Search for a string | `grep` | `grep -n "text" file` |
   | Print a line range | `sed -n` | `sed -n '10,20p' file` |
   | Search from a line onward | `tail -n +N \| grep` | `tail -n +10 f \| grep x` |

10. **Write appropriate linux command:**
| Questions |
|---|
| Show hidden files and directories |
| Delete a directory and its file |
| Prints last five lines of a text file |
| Download a file from an URL |
*[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 474 (ET: N/A)]*

    Answer: The four commands.

    | Requirement | Command |
    |---|---|
    | Show hidden files and directories | `ls -a` |
    | Delete a directory and its files | `rm -r directoryname` |
    | Print the last five lines of a text file | `tail -5 filename` |
    | Download a file from a URL | `wget URL` |

    1. Show hidden files and directories
    ```bash
       ls -a                # all files, including those beginning with .
       ls -la               # long listing with details
       ls -A                # all except . and ..
       ls -alh              # long, all, human-readable sizes
    ```
    - In Linux a `hidden file` is simply one whose name begins with a `dot`: `.bashrc`, `.ssh`, `.config`. There is no hidden attribute as in Windows.

    2. Delete a directory and its contents
    ```bash
       rm -r directoryname          # recursive delete, prompts for some files
       rm -rf directoryname         # force, no prompts at all
       rm -ri directoryname         # ask before each deletion - safest
       rmdir directoryname          # only works if the directory is EMPTY
    ```
    - `rm -rf` is unforgiving: there is no recycle bin, and a mistyped path such as `rm -rf / home` instead of `rm -rf /home` destroys the system.

    3. Print the last five lines
    ```bash
       tail -5 filename
       tail -n 5 filename           # the explicit form
       tail -f filename             # follow a growing log file
       head -5 filename             # the FIRST five lines, for contrast
    ```

    4. Download a file from a URL
    ```bash
       wget https://example.com/file.zip
       wget -O newname.zip URL              # save under a different name
       wget -c URL                          # CONTINUE an interrupted download
       wget -q URL                          # quiet

       curl -O https://example.com/file.zip # curl, keeping the remote name
       curl -o newname.zip URL              # curl, choosing the name
    ```
    ```
       wget : built for downloading; can recurse through a whole site
       curl : built for transferring data with many protocols; better for
              APIs, POST requests and headers
    ```

    Related commands worth knowing
    ```bash
       ls -lt              # sort by modification time
       ls -lS              # sort by size
       cp -r src dest      # copy a directory recursively
       mv a b              # move or rename
       du -sh folder       # total size of a folder
       head -20 file       # first 20 lines
       wc -l file          # count the lines
    ```

11. **Write Linux command to find out the following question:** *[BTCL Assistant Manager (Technical) 2023 compact it 592 (ET: BUET)]*
   (a) To show current file directory.
   (b) To show 11^{\text{th}} to 15^{\text{th}} line from file name myfile.
   (c) To show permission for read, write and execution file name myfile.

    Answer: (a) Show the current working directory
    ```bash
       pwd                     # "print working directory"
    ```
    ```
       $ pwd
       /home/rahim/documents
    ```
    - To list what is `in` the current directory instead:
    ```bash
       ls                      # names only
       ls -l                   # long listing with permissions and sizes
       ls -la                  # including hidden files
    ```

    (b) Show the 11th to 15th line of a file named `myfile`
    ```bash
       sed -n '11,15p' myfile
    ```
    ```
       sed     the stream editor
       -n      do not print every line automatically
       11,15   the range of lines
       p       print the selected lines
    ```
    Other ways to do the same thing
    ```bash
       head -15 myfile | tail -5           # first 15 lines, then the last 5 of those
       awk 'NR >= 11 && NR <= 15' myfile   # NR is the current line number
       awk 'NR==11, NR==15' myfile
       tail -n +11 myfile | head -5        # from line 11, take 5
    ```

    (c) Show the read, write and execute permission of `myfile`
    ```bash
       ls -l myfile
    ```
    ```
       -rwxr-xr--  1  rahim  accounts  2048  Sep 4 10:30  myfile
       ^^^^^^^^^^     ^^^^^  ^^^^^^^^
       |||  |||  |||  owner  group
       |||  |||  +--- others : r--     (read only)
       |||  +-------- group  : r-x     (read, execute)
       +------------- owner  : rwx     (read, write, execute)
       ^
       file type : - regular file , d directory , l symbolic link
    ```
    Other ways
    ```bash
       stat myfile                     # detailed metadata
       stat -c "%A %a %n" myfile       # e.g. "-rwxr-xr-- 754 myfile"
       namei -l myfile                 # permissions of every element of the path
       getfacl myfile                  # access control lists, if used
    ```
    ```
       $ stat -c "%A %a %n" myfile
       -rwxr-xr-- 754 myfile
    ```

    Reading the permission numbers
    ```
       r = 4 , w = 2 , x = 1

       rwx = 4+2+1 = 7
       r-x = 4+0+1 = 5
       r-- = 4+0+0 = 4
       ->  754
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | (a) Current directory | `pwd` |
    | (b) Lines 11 to 15 of `myfile` | `sed -n '11,15p' myfile` |
    | (c) Permissions of `myfile` | `ls -l myfile` |

12. **Write down the names of the three users who can access a file on directory on Linux.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 447 (ET: BUET)]*

    Answer: Linux defines `three` classes of user for every file and directory.
    ```
       1. USER   (owner)  - u   : the user who owns the file
       2. GROUP           - g   : the members of the file's group
       3. OTHERS          - o   : everyone else on the system
    ```
    - A fourth shorthand, `a` (all), refers to all three at once.

    How they appear in a listing
    ```bash
       $ ls -l report.txt
       -rwxr-xr--  1  rahim  accounts  2048  Sep 4 10:30  report.txt
        |  |  |       ^^^^^  ^^^^^^^^
        |  |  |       owner  group
        |  |  +--- OTHERS : r--   read only
        |  +------ GROUP  : r-x   read and execute
        +--------- USER   : rwx   read, write and execute
    ```

    What each class means
    ```
       USER (owner)
            The user who created the file, or to whom it was given with
            chown. Has the most control, and is the only one who may change
            the file's permissions.

       GROUP
            Every file belongs to one group. All members of that group get
            the group permissions. This is how a team shares files without
            opening them to everyone.

       OTHERS
            Every other account on the system - anyone who is neither the
            owner nor a member of the group.
    ```

    Permissions each class may hold
    ```
       r = read    (4)   view the contents; for a directory, list it
       w = write   (2)   modify; for a directory, create or delete files in it
       x = execute (1)   run it; for a directory, ENTER it (cd into it)
    ```

    Setting permissions per class
    ```bash
       chmod u+x file          # give the OWNER execute
       chmod g-w file          # remove write from the GROUP
       chmod o=r file          # set OTHERS to read only
       chmod a+r file          # give everyone read

       chmod 754 file          # owner rwx (7) , group r-x (5) , others r-- (4)
    ```

    Changing the owner and the group
    ```bash
       chown rahim file.txt              # change the USER
       chgrp accounts file.txt           # change the GROUP
       chown rahim:accounts file.txt     # change both at once
    ```

    Seeing who you are and which groups you belong to
    ```bash
       whoami            # the current username
       id                # uid, gid and all group memberships
       groups            # just the group names
       id rahim          # the same for another user
    ```

    - One user stands outside the scheme: `root`, the superuser, whose UID is 0. Root bypasses every permission check, which is why administrative work is done with `sudo` rather than by logging in as root.
    - A fourth, finer mechanism exists for unusual cases: `ACLs` (`setfacl` and `getfacl`), which grant permission to a named individual outside the three classes.

13. **You need to find the total number of linux of the .c and .h file in the current directory formulas the linux commands to display this......... (Approximate)** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 448 (ET: BUET)]*

    Answer: The task is to count the total number of `lines` in all `.c` and `.h` files in the current directory.
    ```bash
       wc -l *.c *.h
    ```
    - This lists each file with its line count and prints a `total` at the end.
    ```
       $ wc -l *.c *.h
          120 main.c
           85 utils.c
           40 main.h
           25 utils.h
          270 total
    ```

    Just the total
    ```bash
       cat *.c *.h | wc -l
       wc -l *.c *.h | tail -1
    ```

    Including subdirectories, which is the usual real requirement
    ```bash
       find . -name "*.c" -o -name "*.h" | xargs wc -l

       find . \( -name "*.c" -o -name "*.h" \) -exec wc -l {} +

       find . -name "*.[ch]" | xargs wc -l          # compact form
    ```
    - The brackets group the `-o` (or) condition, and they must be escaped as `\(` and `\)` in the shell.

    Total only, from a recursive search
    ```bash
       find . -name "*.[ch]" -exec cat {} + | wc -l

       find . -name "*.[ch]" | xargs cat | wc -l
    ```

    Handling filenames containing spaces
    ```bash
       find . -name "*.[ch]" -print0 | xargs -0 wc -l
    ```
    - `-print0` and `-xargs -0` separate names with a null byte instead of whitespace, so a name such as `my file.c` is not split in two.

    Counting the number of `files` rather than lines
    ```bash
       ls *.c *.h | wc -l                    # in this directory
       find . -name "*.[ch]" | wc -l         # recursively
    ```

    Counting lines of actual code, ignoring blanks and comments
    ```bash
       grep -v "^\s*$" *.c *.h | wc -l               # non-blank lines
       grep -vE "^\s*(//|/\*|\*|$)" *.c | wc -l      # rough "code only" count
       cloc .                                        # the proper tool, if installed
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | Line count of each `.c` and `.h`, with a total | `wc -l *.c *.h` |
    | Total only | `cat *.c *.h \| wc -l` |
    | Including subdirectories | `find . -name "*.[ch]" \| xargs wc -l` |
    | Number of such files | `find . -name "*.[ch]" \| wc -l` |

    - The `wc` options for reference: `-l` lines, `-w` words, `-c` bytes, `-m` characters.

14. **Find the possible path to know how data on the internet treavels from your mechine to the site www.bicic.gov.bd. Write down the necessary command to accomplish this.** *[BICIC Assistant Programmer 2022 compact it 633 (ET: BUET)]*

    Answer: The command is `traceroute`.
    ```bash
       traceroute www.bicic.gov.bd
    ```
    - It shows every `router (hop)` a packet passes through on its way to the destination, together with the round-trip time to each.

    Sample output
    ```
       traceroute to www.bicic.gov.bd (203.112.x.x), 30 hops max, 60 byte packets
        1  192.168.1.1 (192.168.1.1)        1.234 ms  1.180 ms  1.150 ms
        2  10.10.0.1 (10.10.0.1)            5.421 ms  5.390 ms  5.360 ms
        3  isp-gateway.net (203.82.x.x)    12.567 ms 12.540 ms 12.510 ms
        4  bdix.net.bd (103.15.x.x)        18.234 ms 18.200 ms 18.180 ms
        5  203.112.x.x (203.112.x.x)       22.891 ms 22.850 ms 22.820 ms
    ```
    ```
       Each line = one hop
       Three times = three probe packets, to show consistency
       * * *  = that hop did not reply (often a firewall blocking ICMP)
    ```

    How it works
    - It sends packets with a deliberately small `TTL` (Time To Live). The first packet has TTL = 1, so the first router decrements it to 0, discards it and returns an `ICMP Time Exceeded` message — revealing its address. The next packet has TTL = 2, revealing the second router, and so on until the destination is reached.

    Variants and options
    ```bash
       traceroute -n www.bicic.gov.bd      # numeric only, skip DNS lookups (faster)
       traceroute -m 15 host               # limit to 15 hops
       traceroute -I host                  # use ICMP instead of UDP
       traceroute -T -p 80 host            # TCP to port 80, passes many firewalls
       traceroute6 host                    # IPv6
    ```

    Equivalents on other systems
    ```bash
       tracert www.bicic.gov.bd            # WINDOWS
       tracepath www.bicic.gov.bd          # Linux, no root needed
       mtr www.bicic.gov.bd                # traceroute + ping, live and continuous
    ```
    - `mtr` is the most useful of these in practice: it keeps probing and shows packet loss per hop, which identifies exactly where a connection degrades.

    Related diagnostic commands
    ```bash
       ping www.bicic.gov.bd        # is the host reachable, and how fast
       nslookup www.bicic.gov.bd    # resolve the name to an IP address
       dig www.bicic.gov.bd         # detailed DNS query
       host www.bicic.gov.bd        # simple DNS lookup
       whois bicic.gov.bd           # registration details
       curl -I https://www.bicic.gov.bd   # HTTP headers only
    ```

    A practical diagnostic order
    ```
       1. ping        - is the host up at all?
       2. nslookup    - does the name resolve correctly?
       3. traceroute  - where along the path does it fail or slow down?
       4. mtr         - which hop is losing packets, over time?
    ```

    - Short answer: `traceroute www.bicic.gov.bd` on Linux, or `tracert` on Windows.

15. **You want to run some specific commands at some price schedules time. Which command will have to be used for this.** *[BICIC Assistant Programmer 2022 compact it 633 (ET: BUET)]*

    Answer: The command is `cron`, configured through `crontab`. For a task that should run `once` at a particular time, the command is `at`.

    `cron` — for repeating scheduled commands
    ```bash
       crontab -e          # edit the current user's crontab
       crontab -l          # list the scheduled jobs
       crontab -r          # remove all of them
       crontab -u rahim -e # edit another user's (needs root)
    ```

    The crontab format
    ```
       *  *  *  *  *  command_to_run
       |  |  |  |  |
       |  |  |  |  +--- day of week   (0-7, both 0 and 7 mean Sunday)
       |  |  |  +------ month         (1-12)
       |  |  +--------- day of month  (1-31)
       |  +------------ hour          (0-23)
       +--------------- minute        (0-59)
    ```

    Examples
    ```bash
       0 2 * * *      /home/user/backup.sh
            # every day at 02:00

       */15 * * * *   /home/user/check.sh
            # every 15 minutes

       0 0 1 * *      /home/user/monthly_report.sh
            # at midnight on the 1st of every month

       30 8 * * 1-5   /home/user/office_task.sh
            # 08:30, Monday to Friday

       0 */6 * * *    /home/user/sync.sh
            # every 6 hours

       @reboot        /home/user/startup.sh
            # once, at every system boot
    ```

    Special shorthand strings
    ```
       @reboot , @yearly , @monthly , @weekly , @daily , @hourly
    ```

    `at` — for a command to run once, at a stated time
    ```bash
       at 14:30
       > /home/user/script.sh
       > <Ctrl+D>

       at now + 2 hours
       at 10:00 tomorrow
       at 3:00 PM next Friday

       atq                  # list pending 'at' jobs
       atrm 5               # remove job number 5
    ```

    On a systemd system — `systemd timers`
    ```bash
       systemctl list-timers                 # show all timers
       systemctl enable --now mytask.timer
    ```
    - Timers are more powerful than cron: they log to the journal, can depend on other units, and can catch up on a job missed while the machine was off (`Persistent=true`).

    Which to use
    ```
       cron / crontab  : a command that must run REPEATEDLY on a schedule
       at              : a command that must run ONCE, at a future time
       systemd timer   : modern replacement for cron, with logging and
                         dependency handling
       watch           : re-run a command every few seconds interactively -
                         not a scheduler
    ```

    Practical points
    ```
       Always use ABSOLUTE paths in a cron job. Cron runs with a very
            limited PATH, so 'python script.py' often fails where
            '/usr/bin/python3 /home/user/script.py' works.

       Redirect the output, or cron will try to e-mail it :
            0 2 * * * /home/user/backup.sh >> /var/log/backup.log 2>&1

       The cron daemon must be running :  systemctl status cron
       System-wide jobs live in /etc/crontab and /etc/cron.d/
    ```

    - Short answer: `cron` (edited with `crontab -e`) for repeating jobs, and `at` for a one-off job at a scheduled time.

16. **Linux Command লিখ:** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*
   a) একটি ফোল্ডারের সকল ফাইল দেখানোর কমান্ড।
   b) নতুন ডিরেক্টরি তৈরির কমান্ড।
   c) ফাইল এ্যাকসেস পারমিশন দেখানোর কমান্ড।

    Answer: (Answered in English, as required for IT topics.) (a) Show all the files in a folder
    ```bash
       ls                      # names only
       ls -l                   # long listing : permissions, owner, size, date
       ls -a                   # ALL files, including hidden ones (starting with .)
       ls -la                  # long listing including hidden files
       ls -lh                  # human-readable sizes : K, M, G
       ls /home/user           # list a specific folder
    ```
    ```
       $ ls -la
       total 24
       drwxr-xr-x  3 rahim rahim 4096 Sep  4 10:30 .
       drwxr-xr-x 20 rahim rahim 4096 Sep  4 09:15 ..
       -rw-r--r--  1 rahim rahim  220 Sep  4 10:00 .bashrc
       -rwxr-xr-x  1 rahim rahim 1024 Sep  4 10:30 script.sh
    ```

    (b) Create a new directory
    ```bash
       mkdir foldername                    # create one directory
       mkdir dir1 dir2 dir3                # create several at once
       mkdir -p /home/user/a/b/c           # create the whole path, parents too
       mkdir -m 755 foldername             # create with given permissions
       mkdir -v foldername                 # verbose - confirm what was created
    ```
    - `-p` is the important option: without it, `mkdir a/b/c` fails unless `a/b` already exists.

    (c) Show the access permission of a file
    ```bash
       ls -l filename
    ```
    ```
       -rwxr-xr--  1  rahim  accounts  2048  Sep 4 10:30  filename
       ^^^^^^^^^^
       |||  |||  +--- others : r--   read only
       |||  +-------- group  : r-x   read and execute
       +------------- owner  : rwx   read, write, execute
       ^
       type : - file , d directory , l link
    ```
    ```bash
       stat filename                    # full metadata
       stat -c "%A %a %n" filename      # e.g. "-rwxr-xr-- 754 filename"
       namei -l /path/to/file           # permissions of every path component
    ```

    Reading the numbers
    ```
       r = 4 , w = 2 , x = 1

       rwx = 7 , r-x = 5 , r-- = 4     ->  754
    ```

    Changing permissions, for completeness
    ```bash
       chmod 755 filename          # numeric
       chmod u+x filename          # symbolic : add execute for the owner
       chmod -R 755 foldername     # recursive
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | (a) Show all files in a folder | `ls -la` |
    | (b) Create a new directory | `mkdir foldername` |
    | (c) Show a file's permissions | `ls -l filename` |

17. **UNIX command (directory listing with hidden files).** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*

    Answer: The command is `ls -a`.
    ```bash
       ls -a                   # list ALL entries, including hidden ones
       ls -A                   # all except . and ..
       ls -la                  # long listing with details, including hidden
       ls -alh                 # long, all, human-readable sizes
    ```

    What a hidden file is in Unix
    - Any file or directory whose name `begins with a dot`. There is no hidden attribute as in Windows — the dot is the whole mechanism.
    ```
       .bashrc      .profile      .ssh/      .config/      .git/
    ```

    Example
    ```
       $ ls
       documents  script.sh  report.txt

       $ ls -a
       .  ..  .bashrc  .profile  .ssh  documents  script.sh  report.txt

       $ ls -la
       total 32
       drwxr-xr-x  4 rahim rahim 4096 Sep  4 10:30 .
       drwxr-xr-x 20 root  root  4096 Sep  4 09:15 ..
       -rw-r--r--  1 rahim rahim  220 Sep  4 10:00 .bashrc
       -rw-r--r--  1 rahim rahim  807 Sep  4 10:00 .profile
       drwx------  2 rahim rahim 4096 Sep  4 10:20 .ssh
       drwxr-xr-x  2 rahim rahim 4096 Sep  4 10:30 documents
       -rwxr-xr-x  1 rahim rahim 1024 Sep  4 10:30 script.sh
    ```
    ```
       .   the CURRENT directory
       ..  the PARENT directory

       -A suppresses these two, which is often what is actually wanted.
    ```

    Useful `ls` options
    ```
       -l   long format : permissions, links, owner, group, size, date
       -a   all, including hidden
       -A   almost all - hidden, but not . and ..
       -h   human-readable sizes (with -l)
       -t   sort by modification time, newest first
       -S   sort by size, largest first
       -r   reverse the sort order
       -R   recurse into subdirectories
       -d   the directory itself, not its contents
       -i   show inode numbers
       -F   append a symbol : / directory , * executable , @ link
    ```

    Common combinations
    ```bash
       ls -lah                 # everything, readable    (the most used)
       ls -lt                  # newest first
       ls -lS                  # largest first
       ls -ltr                 # oldest last - handy for log directories
       ls -ld foldername       # the folder's own entry, not its contents
       ls -R                   # the whole tree
    ```

    Listing only hidden files
    ```bash
       ls -d .*                # only entries beginning with a dot
       ls -A | grep "^\."      # the same, filtered
    ```

    - Short answer: `ls -a` (or `ls -la` for details).

18. **Difference between below 3 linux command: cd, cd usr/desk/home, cd/user/desk/home** *[EGCB Assistant Engineer (CSE) 2022 compact it 717 (ET: BUET)]*

    Answer: The three differ in `where they start from` — and one of them contains a mistake.

    1. `cd`
    ```bash
       cd
    ```
    - With `no argument`, `cd` goes to the user's `home directory`. It is exactly equivalent to `cd ~` or `cd $HOME`.
    ```
       $ pwd
       /var/log
       $ cd
       $ pwd
       /home/rahim
    ```

    2. `cd usr/desk/home` — a RELATIVE path
    ```bash
       cd usr/desk/home
    ```
    - There is `no leading slash`, so the path is `relative to the current directory`. The shell looks for a folder named `usr` `inside where you are now`.
    ```
       If pwd is /home/rahim  ->  it tries  /home/rahim/usr/desk/home
       If pwd is /tmp         ->  it tries  /tmp/usr/desk/home
    ```
    - The result therefore `depends on where you are standing`. If no such folder exists there, the shell reports:
    ```
       bash: cd: usr/desk/home: No such file or directory
    ```

    3. `cd/user/desk/home` — a SYNTAX ERROR as written
    ```bash
       cd/user/desk/home
    ```
    - There is `no space` between `cd` and the path, so the shell treats the whole string as one command name and looks for a program called `cd/user/desk/home`.
    ```
       bash: cd/user/desk/home: No such file or directory
    ```
    - What was almost certainly intended is:
    ```bash
       cd /user/desk/home
    ```
    - With the space, this is an `absolute path`: the leading `/` means start from the `root` of the filesystem, so it always refers to the same place whatever the current directory is.

    Comparison

    | Command | Type | Starts from | Result |
    |---|---|---|---|
    | `cd` | No argument | — | Goes to the home directory |
    | `cd usr/desk/home` | `Relative` path | The current directory | Depends on where you are |
    | `cd/user/desk/home` | `Syntax error` | — | Command not found — a space is missing |
    | `cd /user/desk/home` | `Absolute` path | The root `/` | Always the same directory |

    Absolute versus relative, the essential distinction
    ```
       ABSOLUTE : begins with /   ->  always from the root
                  /home/rahim/documents

       RELATIVE : does not begin with /  ->  from the current directory
                  documents
                  ../documents
                  ./script.sh
    ```

    Other forms of `cd`
    ```bash
       cd ..            # up one level
       cd ../..         # up two levels
       cd ~             # home directory
       cd ~rahim        # another user's home directory
       cd -             # back to the PREVIOUS directory
       cd /             # the root directory
    ```

    - One further point worth noting: `cd` is a `shell built-in`, not an external program. It has to be, because a child process cannot change its parent's working directory — only the shell itself can.

19. **Linux Command: Write down the linux command: All hidden flies, remove a file, permission of a file, search for a string.** *[Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)], [MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*

    Answer: The four commands.

    1. Show all hidden files
    ```bash
       ls -a                   # all entries, including hidden
       ls -la                  # long listing with details
       ls -A                   # all except . and ..
       ls -d .*                # ONLY the hidden entries
    ```
    - A hidden file in Unix is simply one whose name `begins with a dot`: `.bashrc`, `.ssh`, `.config`.

    2. Remove a file
    ```bash
       rm filename                  # delete one file
       rm file1 file2 file3         # several at once
       rm *.txt                     # by wildcard
       rm -i filename               # ask before deleting - safest
       rm -f filename               # force, no prompt, no error if missing

       rm -r foldername             # a DIRECTORY and its contents
       rm -rf foldername            # force recursive - dangerous
       rmdir foldername             # only if the directory is EMPTY
    ```
    - There is no recycle bin. `rm -rf` on the wrong path is unrecoverable.

    3. Show or set the permission of a file
    ```bash
       ls -l filename              # SHOW the permissions
       stat -c "%A %a %n" file     # e.g. "-rwxr-xr-- 754 file"

       chmod 755 filename          # SET, numeric form
       chmod u+x filename          # SET, symbolic form
       chmod -R 755 folder         # recursive
    ```
    ```
       -rwxr-xr--
       |||  |||  +--- others : r--
       |||  +-------- group  : r-x
       +------------- owner  : rwx

       r = 4 , w = 2 , x = 1     ->   rwx = 7 , r-x = 5 , r-- = 4  ->  754
    ```

    4. Search for a string
    ```bash
       grep "string" filename           # basic search
       grep -i "string" filename        # ignore case
       grep -n "string" filename        # with line numbers
       grep -r "string" /path           # recursive, through a directory tree
       grep -v "string" filename        # lines that do NOT match
       grep -c "string" filename        # count the matching lines
       grep -w "string" filename        # whole word only
       grep -l "string" *.txt           # just the names of matching files

       grep -rn "string" .              # the everyday combination
    ```
    ```bash
       # searching the output of another command
       ps aux | grep httpd
       dmesg | grep -i error
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | All hidden files | `ls -a` |
    | Remove a file | `rm filename` |
    | Remove a directory | `rm -r foldername` |
    | Show permissions | `ls -l filename` |
    | Set permissions | `chmod 755 filename` |
    | Search for a string | `grep "string" filename` |

20. **(b) Write Linux commands to: (i) Make a directory named PSC (ii) Copy a directory with all its Contents into a directory name/home/admin.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*

    Answer: (i) Make a directory named `PSC`
    ```bash
       mkdir PSC
    ```
    ```bash
       mkdir -p /home/admin/PSC        # create the whole path if parents are missing
       mkdir -m 755 PSC                # create with specific permissions
       mkdir -v PSC                    # verbose - confirm what was created
    ```

    (ii) Copy a directory with all its contents into `/home/admin`
    ```bash
       cp -r PSC /home/admin/
    ```
    ```
       cp   copy
       -r   RECURSIVE - copy the directory and everything inside it
    ```
    - Without `-r`, `cp` refuses:
    ```
       cp: -r not specified; omitting directory 'PSC'
    ```

    Better variants
    ```bash
       cp -a PSC /home/admin/          # ARCHIVE mode - preserves permissions,
                                       # ownership, timestamps and links.
                                       # This is usually what is wanted.

       cp -rv PSC /home/admin/         # verbose - list each file copied
       cp -ri PSC /home/admin/         # ask before overwriting anything
       cp -ru PSC /home/admin/         # UPDATE - copy only newer files
    ```

    A subtlety about the trailing slash
    ```bash
       cp -r PSC  /home/admin/         # creates  /home/admin/PSC
       cp -r PSC/ /home/admin/         # same result on most systems
       cp -r PSC/. /home/admin/        # copies the CONTENTS of PSC directly
                                       # into /home/admin, without the PSC folder
    ```

    For large directories, `rsync` is better
    ```bash
       rsync -av PSC /home/admin/           # archive mode, verbose
       rsync -av --progress PSC /home/admin/
       rsync -av --delete PSC/ /home/admin/PSC/   # make the target an exact mirror
    ```
    - `rsync` can resume an interrupted copy and transfers only what has changed, so it is the standard tool for backups and for copying over a network.

    Related commands
    ```bash
       mv PSC /home/admin/          # MOVE instead of copy
       rm -r PSC                    # remove the directory and its contents
       ls -la /home/admin/PSC       # verify the result
       du -sh /home/admin/PSC       # check the copied size
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | (i) Make a directory `PSC` | `mkdir PSC` |
    | (ii) Copy it with all contents to `/home/admin` | `cp -r PSC /home/admin/` |
    | Preferred form, preserving attributes | `cp -a PSC /home/admin/` |

21. **In Linux, History is a very useful command to show you all of the last commands that have been recently used. Grep is a Linux command-line tool used to search for a string of characters in a specified file. Write grep and history command to find previous commands in Linux.** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*

    Answer: The two commands are used together with a `pipe`, so that `history` produces the list and `grep` filters it.
    ```bash
       history | grep "command"
    ```

    Examples
    ```bash
       history | grep "ssh"          # every past command containing ssh
       history | grep "chmod"        # every chmod ever run
       history | grep -i "mysql"     # ignore case
       history | grep "apt" | tail -5    # the last 5 matching commands
    ```
    ```
       $ history | grep "ssh"
         245  ssh admin@192.168.1.10
         318  ssh-keygen -t rsa
         402  ssh -p 2222 user@server.com
    ```
    - The number on the left is the command's position in the history list, and it can be used to re-run the command.

    Using `history` on its own
    ```bash
       history                   # the whole history list
       history 20                # the last 20 commands
       history -c                # CLEAR the history
       history -d 245            # delete entry number 245
       !245                      # re-run command number 245
       !!                        # re-run the previous command
       !ssh                      # re-run the last command starting with "ssh"
    ```

    The interactive alternative — reverse search
    ```
       Press  Ctrl + R  , then start typing.
       Bash searches backwards through the history as you type.
       Press Ctrl+R again to step to an earlier match, Enter to run it.
    ```

    Useful `grep` options in this context
    ```bash
       history | grep -n "git"           # with line numbers
       history | grep -c "sudo"          # COUNT how many times sudo was used
       history | grep -v "ls"            # everything EXCEPT ls
       history | grep -E "ssh|scp|sftp"  # any of several patterns
       history | grep "docker" | wc -l   # count docker commands
    ```

    Finding the most frequently used commands
    ```bash
       history | awk '{print $2}' | sort | uniq -c | sort -rn | head -10
    ```
    ```
       $ history | awk '{print $2}' | sort | uniq -c | sort -rn | head -5
          152 ls
           98 cd
           76 git
           54 vim
           41 grep
    ```

    Where the history is kept
    ```
       ~/.bash_history        the file, written when the shell exits
       HISTSIZE               how many commands are kept in memory
       HISTFILESIZE           how many are kept in the file
       HISTCONTROL=ignoredups suppress consecutive duplicates
       HISTTIMEFORMAT="%F %T "  prepend a timestamp to each entry
    ```
    ```bash
       export HISTTIMEFORMAT="%F %T "
       history | grep "ssh"
       # 245  2026-09-01 14:32:10 ssh admin@192.168.1.10
    ```

    - Security point worth stating: a password typed on the command line ends up in `~/.bash_history` in plain text. Prefixing a command with a `space` keeps it out of the history when `HISTCONTROL=ignorespace` is set, and a password should never be passed as a command-line argument in the first place.

22. **Write down a shell script program that would add the line “This is my file” at the top of each file having the extention ‘txt’ in the current directory. Note that all the other contents of the .txt file(s) would remain unchanged and start from the second line.** *[BPDB Assistant Engineer (CSE) 2021 compact it 818 (ET: BUET)]*

    Answer: The script must insert a line at the `top` of every `.txt` file while keeping the rest of the contents unchanged, starting from the second line.

    Method 1 — using `sed` (the shortest)
    ```bash
    #!/bin/bash

    for file in *.txt
    do
        if [ -f "$file" ]; then
            sed -i '1i This is my file' "$file"
            echo "Updated: $file"
        fi
    done
    ```
    ```
       sed -i        edit the file IN PLACE
       1i text       INSERT 'text' BEFORE line 1
    ```

    Method 2 — using a temporary file (works on every Unix)
    ```bash
    #!/bin/bash

    for file in *.txt
    do
        if [ -f "$file" ]; then
            echo "This is my file" > temp_file
            cat "$file" >> temp_file
            mv temp_file "$file"
            echo "Updated: $file"
        fi
    done
    ```
    - `>` creates the temporary file with the new first line, `>>` appends the original contents, and `mv` puts it back. This is the classic portable approach.

    Method 3 — using `cat` with process substitution
    ```bash
    #!/bin/bash

    for file in *.txt
    do
        [ -f "$file" ] || continue
        printf 'This is my file\n%s' "$(cat "$file")" > "$file.tmp"
        mv "$file.tmp" "$file"
    done
    ```

    Running the script
    ```bash
       chmod +x addline.sh          # make it executable
       ./addline.sh                 # run it
    ```

    Before and after
    ```
       BEFORE  (report.txt)          AFTER (report.txt)
       -------------------          --------------------
       Line one of the report        This is my file
       Line two                      Line one of the report
       Line three                    Line two
                                     Line three
    ```

    A safer version, taking a backup first
    ```bash
    #!/bin/bash

    LINE="This is my file"

    for file in *.txt
    do
        if [ -f "$file" ]; then
            cp "$file" "$file.bak"                 # keep a backup
            sed -i "1i $LINE" "$file"
            echo "Updated $file (backup: $file.bak)"
        fi
    done

    echo "Done. $(ls *.txt | wc -l) files processed."
    ```
    - `sed -i.bak '1i ...' file` does the same in one step, creating `file.bak` automatically.

    Including subdirectories
    ```bash
    #!/bin/bash

    find . -type f -name "*.txt" | while read -r file
    do
        sed -i '1i This is my file' "$file"
        echo "Updated: $file"
    done
    ```

    Points worth stating
    ```
       ALWAYS quote "$file" - without the quotes, a filename containing a
            space is split into two arguments and the script fails.

       [ -f "$file" ] checks that it really is a regular file, which also
            guards against the case where NO .txt file exists and the shell
            leaves the literal string "*.txt" in the variable.

       sed -i is a GNU extension. On macOS or BSD it must be written
            sed -i '' '1i\' ... , so the temporary-file method is more portable.

       Test on a copy first. sed -i overwrites the original with no undo.
    ```

23. **Write the following UNIX command with example: (a) ls (b) grep (c) ssh** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820 (ET: BUET)]*

    Answer: (a) `ls` — list directory contents
    ```bash
       ls                      # names only
       ls -l                   # long listing : permissions, owner, size, date
       ls -a                   # ALL entries, including hidden (dot) files
       ls -la                  # long listing including hidden files
       ls -lh                  # human-readable sizes : K, M, G
       ls -lt                  # sort by modification time, newest first
       ls -lS                  # sort by size, largest first
       ls -R                   # recurse into subdirectories
       ls /home/user           # list a specific directory
    ```
    ```
       $ ls -lh
       total 24K
       drwxr-xr-x 2 rahim rahim 4.0K Sep  4 10:30 documents
       -rwxr-xr-x 1 rahim rahim 1.0K Sep  4 10:30 script.sh
       -rw-r--r-- 1 rahim rahim  15K Sep  4 09:15 report.txt
       ^          ^ ^     ^      ^    ^                ^
       perms      | owner group  size date             name
                  links
    ```

    (b) `grep` — search for a pattern
    ```bash
       grep "pattern" filename          # basic search
       grep -i "pattern" file           # ignore case
       grep -n "pattern" file           # show line numbers
       grep -r "pattern" /path          # recursive through a directory tree
       grep -v "pattern" file           # INVERT : lines that do NOT match
       grep -c "pattern" file           # COUNT the matching lines
       grep -w "word" file              # whole word only
       grep -l "pattern" *.txt          # just the names of matching files
       grep -E "cat|dog" file           # extended regex : either pattern
    ```
    ```
       $ grep -n "error" /var/log/syslog
       142:Sep  4 10:15:22 server kernel: error reading device
       289:Sep  4 11:02:10 server httpd: error 500 on /index.php

       $ ps aux | grep httpd            # filtering another command's output
    ```
    - The name comes from the `ed` editor command `g/re/p` — globally search for a regular expression and print.

    (c) `ssh` — secure shell, log in to a remote machine
    ```bash
       ssh username@hostname                    # basic login
       ssh rahim@192.168.1.10
       ssh -p 2222 rahim@server.com             # a non-standard port
       ssh -i ~/.ssh/id_rsa rahim@server.com    # use a specific private key
       ssh rahim@server.com "df -h"             # run ONE command and return
       ssh -X rahim@server.com                  # forward X11, for GUI programs
       ssh -v rahim@server.com                  # verbose, for debugging
    ```
    ```
       $ ssh admin@192.168.1.10
       admin@192.168.1.10's password:
       Welcome to Ubuntu 22.04 LTS
       admin@server:~$
    ```
    - `ssh` encrypts everything, which is why it replaced `telnet` and `rlogin`. It listens on TCP port `22` by default.

    Key-based login, which is the normal practice
    ```bash
       ssh-keygen -t rsa -b 4096                # generate a key pair
       ssh-copy-id rahim@server.com             # install the public key remotely
       ssh rahim@server.com                     # now logs in with no password
    ```

    Related tools in the same family
    ```bash
       scp file.txt rahim@server:/home/rahim/   # copy a file over SSH
       scp -r folder rahim@server:/home/        # copy a directory
       sftp rahim@server                        # interactive file transfer
       rsync -avz -e ssh folder rahim@server:/  # efficient sync over SSH
    ```

    Summary

    | Command | Purpose | Common form |
    |---|---|---|
    | `ls` | List directory contents | `ls -la` |
    | `grep` | Search for a pattern | `grep -rn "text" .` |
    | `ssh` | Secure remote login | `ssh user@host` |

24. **(a) Check if the website of ‘TGTDCL’. (b) How to create folder in sub-directory?** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*

    Answer: (a) Check whether the TGTDCL website is reachable

    Several commands answer different parts of "is the site up".
    ```bash
       ping www.tgtdcl.gov.bd               # is the host reachable at all?
       ping -c 4 www.tgtdcl.gov.bd          # send only 4 packets and stop
    ```
    ```
       PING www.tgtdcl.gov.bd (203.112.x.x) 56(84) bytes of data.
       64 bytes from 203.112.x.x: icmp_seq=1 ttl=54 time=12.3 ms
       64 bytes from 203.112.x.x: icmp_seq=2 ttl=54 time=11.8 ms
       --- 2 packets transmitted, 2 received, 0% packet loss
    ```
    ```bash
       curl -I https://www.tgtdcl.gov.bd    # HTTP headers only - is the SITE up?
    ```
    ```
       HTTP/1.1 200 OK
       Server: nginx
       Content-Type: text/html
    ```
    - `ping` tests the `host`; `curl -I` tests the `web service`. A server can answer ping while its web server is down, so both are worth showing.
    ```bash
       wget --spider https://www.tgtdcl.gov.bd     # check without downloading
       nslookup www.tgtdcl.gov.bd                  # does the name resolve?
       dig www.tgtdcl.gov.bd                       # detailed DNS answer
       host www.tgtdcl.gov.bd                      # simple DNS lookup
       traceroute www.tgtdcl.gov.bd                # where the path fails
       telnet www.tgtdcl.gov.bd 80                 # is port 80 open?
       nc -zv www.tgtdcl.gov.bd 443                # is port 443 open?
       whois tgtdcl.gov.bd                         # registration details
    ```

    A practical diagnostic order
    ```
       1. nslookup   - does the name resolve to an IP address?
       2. ping       - is the host reachable?
       3. curl -I    - is the web server answering?
       4. traceroute - if not, where along the path does it stop?
    ```

    (b) Create a folder inside a subdirectory
    ```bash
       mkdir parent/child                       # parent must already exist
       mkdir -p parent/child/grandchild         # -p creates the WHOLE path
    ```
    - `-p` is the key option. Without it:
    ```
       $ mkdir a/b/c
       mkdir: cannot create directory 'a/b/c': No such file or directory
    ```
    - With it, every missing parent is created silently, and it does not complain if the directory already exists.
    ```bash
       mkdir -p /home/user/projects/2026/reports
       mkdir -p documents/{2024,2025,2026}          # brace expansion - three folders
       mkdir -p project/{src,bin,doc,test}          # a whole project skeleton
       mkdir -m 755 -p parent/child                 # with permissions
       mkdir -pv a/b/c                              # verbose
    ```
    ```
       $ mkdir -pv a/b/c
       mkdir: created directory 'a'
       mkdir: created directory 'a/b'
       mkdir: created directory 'a/b/c'
    ```

    Verifying
    ```bash
       ls -R parent            # show the whole tree
       tree parent             # a nicer tree view, if installed
       pwd                     # confirm where you are
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | (a) Is the host reachable | `ping www.tgtdcl.gov.bd` |
    | (a) Is the website responding | `curl -I https://www.tgtdcl.gov.bd` |
    | (b) Folder inside a subdirectory | `mkdir -p parent/child` |

25. **Write a Linux command to revoke permission from no user but owner from a file “jdcl.txt”.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*

    Answer: The requirement is that `nobody except the owner` has any permission on `jdcl.txt`.
    ```bash
       chmod 700 jdcl.txt
    ```
    ```
       7 = rwx  for the OWNER
       0 = ---  for the GROUP
       0 = ---  for OTHERS
    ```

    Symbolic equivalents
    ```bash
       chmod go-rwx jdcl.txt        # REMOVE all rights from group and others
       chmod go= jdcl.txt           # set group and others to nothing
       chmod u=rwx,go= jdcl.txt     # state all three explicitly
       chmod a-rwx,u+rwx jdcl.txt   # strip everything, then restore the owner
    ```

    Verification
    ```bash
       $ ls -l jdcl.txt
       -rwx------  1 rahim rahim  2048  Sep 4 10:30  jdcl.txt
        ^^^ ^^^^^^
        |   +------ group and others : NOTHING
        +---------- owner : rwx
    ```

    If the owner needs only read and write, not execute
    ```bash
       chmod 600 jdcl.txt
    ```
    ```
       -rw-------
    ```
    - `600` is the usual setting for a private data file; `700` is for a private script or directory that must also be executable or enterable.

    The permission arithmetic
    ```
       r = 4 , w = 2 , x = 1

       rwx = 4+2+1 = 7        r-- = 4
       rw- = 4+2   = 6        --- = 0
       r-x = 4+1   = 5
    ```

    Common permission settings, for context
    ```
       700   private script or directory - owner only
       600   private file - owner read/write     (e.g. ~/.ssh/id_rsa)
       644   public read, owner write            (normal documents)
       755   public read and execute, owner all  (programs, web directories)
       777   everyone everything                 (almost never appropriate)
    ```

    Related commands
    ```bash
       chmod -R 700 foldername       # apply to a whole directory tree
       chown rahim jdcl.txt          # change the owner
       chgrp accounts jdcl.txt       # change the group
       umask 077                     # make NEW files private by default
    ```

    - One caution: `root` bypasses every permission check, so `chmod 700` protects a file from other ordinary users but not from the system administrator. For genuine secrecy the file must be `encrypted`, for example with `gpg`.

26. **Linux এর ক্ষেত্রে User Creation এর কমান্ড লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) The command is `useradd` (or `adduser` on Debian and Ubuntu).
    ```bash
       sudo useradd username
       sudo passwd username              # then set the password
    ```

    `useradd` — the low-level command, available on every distribution
    ```bash
       sudo useradd -m rahim                  # -m CREATES the home directory
       sudo useradd -m -s /bin/bash rahim     # also set the login shell
       sudo useradd -m -c "Rahim Uddin" rahim # add a full-name comment
       sudo useradd -m -G sudo,developers rahim   # add to extra groups
       sudo useradd -m -d /data/rahim rahim   # a custom home directory
       sudo useradd -e 2026-12-31 rahim       # an expiry date
       sudo useradd -r serviceacct            # a SYSTEM account, no home
    ```
    - `-m` matters: without it the home directory is not created, and the user logs in to a directory that does not exist.

    `adduser` — the friendly wrapper on Debian and Ubuntu
    ```bash
       sudo adduser rahim
    ```
    ```
       Adding user 'rahim' ...
       Creating home directory '/home/rahim' ...
       Enter new UNIX password:
       Retype new UNIX password:
       Full Name []: Rahim Uddin
       Room Number []:
       ...
       Is the information correct? [Y/n] Y
    ```
    - It creates the home directory, copies `/etc/skel`, sets the shell and prompts for the password — all in one interactive step.

    Setting the password
    ```bash
       sudo passwd rahim                 # set or change it
       passwd                            # change your own
       sudo passwd -l rahim              # LOCK the account
       sudo passwd -u rahim              # unlock it
       sudo passwd -e rahim              # force a change at next login
    ```

    Managing the account afterwards
    ```bash
       sudo usermod -aG sudo rahim       # ADD to a group (note the -a!)
       sudo usermod -s /bin/bash rahim   # change the login shell
       sudo usermod -l newname oldname   # rename the account
       sudo usermod -L rahim             # lock
       sudo userdel rahim                # delete, keeping the home directory
       sudo userdel -r rahim             # delete WITH the home directory
    ```
    - `usermod -G` without `-a` `replaces` the group list and silently removes the user from every other group. Always use `-aG`.

    Checking
    ```bash
       id rahim                     # uid, gid and group memberships
       groups rahim                 # group names only
       getent passwd rahim          # the account's entry
       cat /etc/passwd | grep rahim
       ls -la /home/rahim           # confirm the home directory
    ```

    The files involved
    ```
       /etc/passwd    account records : name, uid, gid, home, shell
       /etc/shadow    encrypted passwords and ageing rules (root only)
       /etc/group     group definitions
       /etc/skel      template files copied into every new home directory
    ```
    ```
       $ cat /etc/passwd | grep rahim
       rahim:x:1001:1001:Rahim Uddin:/home/rahim:/bin/bash
         |    |   |    |       |          |          |
       name  |  uid  gid    comment     home       shell
          password is in /etc/shadow
    ```

    Group commands
    ```bash
       sudo groupadd developers
       sudo usermod -aG developers rahim
       sudo gpasswd -d rahim developers      # remove from a group
       sudo groupdel developers
    ```

    - Short answer: `sudo useradd -m -s /bin/bash username` followed by `sudo passwd username`, or simply `sudo adduser username` on Debian and Ubuntu.

27. **Write Linux command for following question: a) Create a file apscl.txt in current location. b) Given permission to all read write and execute to the file apscl.txt c) Read first 7 lines from apscl.txt file d) Delete the file apscl.txt** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867-868 (ET: BUET)]*

    Answer: (a) Create a file `apscl.txt` in the current location
    ```bash
       touch apscl.txt                    # create an empty file
    ```
    ```bash
       cat > apscl.txt                    # create and type contents, Ctrl+D to end
       echo "some text" > apscl.txt       # create with one line of text
       vi apscl.txt                       # create and edit
       > apscl.txt                        # create empty, or TRUNCATE if it exists
    ```
    - `touch` is the standard answer. It creates the file if it does not exist, and merely updates the timestamp if it does.

    (b) Give read, write and execute permission to all
    ```bash
       chmod 777 apscl.txt
    ```
    ```bash
       chmod a+rwx apscl.txt              # symbolic equivalent
       chmod ugo+rwx apscl.txt            # the same, spelled out
    ```
    ```
       7 = 4+2+1 = rwx    ->   owner 7 , group 7 , others 7

       $ ls -l apscl.txt
       -rwxrwxrwx  1 rahim rahim  0  Sep 4 10:30  apscl.txt
    ```
    - Worth stating: `777` is almost never appropriate in practice. It lets any user on the system modify or replace the file, which is a serious security hole. `755` or `644` is normally correct.

    (c) Read the first 7 lines
    ```bash
       head -7 apscl.txt
    ```
    ```bash
       head -n 7 apscl.txt                # the explicit form
       sed -n '1,7p' apscl.txt            # using sed
       awk 'NR <= 7' apscl.txt            # using awk
       tail -7 apscl.txt                  # the LAST 7 lines, for contrast
    ```

    (d) Delete the file
    ```bash
       rm apscl.txt
    ```
    ```bash
       rm -i apscl.txt                    # ask before deleting - safest
       rm -f apscl.txt                    # force, no prompt, no error if absent
       unlink apscl.txt                   # removes exactly one file
    ```
    - There is no recycle bin. A deleted file is gone.

    All four together
    ```bash
       $ touch apscl.txt
       $ chmod 777 apscl.txt
       $ ls -l apscl.txt
       -rwxrwxrwx 1 rahim rahim 0 Sep  4 10:30 apscl.txt
       $ head -7 apscl.txt
       $ rm apscl.txt
       $ ls apscl.txt
       ls: cannot access 'apscl.txt': No such file or directory
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | (a) Create the file | `touch apscl.txt` |
    | (b) Full permission to everyone | `chmod 777 apscl.txt` |
    | (c) First 7 lines | `head -7 apscl.txt` |
    | (d) Delete the file | `rm apscl.txt` |

28. **How do you define bash?** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 875 (ET: BUET)]*

    Answer: `Bash` stands for `Bourne Again SHell`. It is a `command-line interpreter` — a program that reads the commands a user types, interprets them, and asks the kernel to carry them out.

    - It is the `default shell` on most Linux distributions, written by Brian Fox in 1989 as a free replacement for the original `Bourne shell (sh)`. The name is a pun on that ancestry.

    What a shell is
    ```
       USER
         |  types a command
         v
       SHELL (bash)  - interprets it, expands wildcards and variables,
         |             sets up pipes and redirection
         v
       KERNEL        - actually creates processes and touches the hardware
         |
         v
       HARDWARE
    ```
    - The shell is the `interface` between the user and the kernel. It is an ordinary program, not part of the operating system itself.

    Two ways bash is used
    ```
       INTERACTIVE : the user types commands at a prompt

       SCRIPTING   : commands are written in a file and run as a program

            #!/bin/bash
            for f in *.txt; do
                echo "Processing $f"
            done
    ```
    - The first line, `#!/bin/bash`, is the `shebang`; it tells the kernel which interpreter to use.

    Main features
    ```
       Command execution and PATH searching
       Variables and environment variables   :  NAME="Rahim" ; echo $NAME
       Wildcards (globbing)                  :  *.txt , file? , [a-z]*
       Pipes                                 :  ls -l | grep ".txt"
       Redirection                           :  > , >> , < , 2>
       Command substitution                  :  today=$(date)
       Control structures                    :  if , for , while , case
       Functions
       Job control                           :  &  , fg , bg , jobs
       Command history                       :  history , !! , Ctrl+R
       Tab completion
       Aliases                               :  alias ll='ls -la'
       Startup files                         :  ~/.bashrc , ~/.bash_profile
    ```

    A short script showing several of them
    ```bash
    #!/bin/bash

    NAME="Rahim"                          # variable
    echo "Hello, $NAME"                   # variable expansion

    for file in *.txt                     # loop with a wildcard
    do
        lines=$(wc -l < "$file")          # command substitution
        if [ "$lines" -gt 100 ]; then     # condition
            echo "$file is large: $lines lines"
        fi
    done
    ```

    Other shells, for comparison
    ```
       sh    Bourne shell        - the original, 1977
       bash  Bourne Again Shell  - the Linux default
       csh   C shell             - C-like syntax
       ksh   Korn shell          - a superset of sh
       zsh   Z shell             - very configurable; the macOS default since 2019
       fish  Friendly shell      - modern, not POSIX compatible
    ```
    ```bash
       echo $SHELL          # which shell you are using
       cat /etc/shells      # which shells are installed
       chsh -s /bin/bash    # change your login shell
    ```

    - The essential definition to state: bash is a `Unix shell and command language` that acts as the interface between the user and the kernel, usable both `interactively` at a prompt and as a `scripting language` for automating tasks.

29. **Linux Command: Write a code for listing home directory files with all details and human readable size got to Home directory, list directory files with 10-15 are display only 10^{\text{th}} to 15^{\text{th}} lines of words of them. Write the instructions in a way that they execute together and shows the result.** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 878 (ET: BUET)]*

    Answer: The requirement is a `single command line` that goes to the home directory, lists its files with full details and human-readable sizes, and then shows only the 10th to 15th lines of that listing.
    ```bash
       cd ~ && ls -lh | sed -n '10,15p'
    ```

    Breaking it down
    ```
       cd ~            go to the HOME directory
       &&              run the next command only if this one succeeded
       ls -lh          long listing (-l) with human-readable sizes (-h)
       |               pipe the listing into the next command
       sed -n '10,15p' print only lines 10 to 15
    ```

    Sample output
    ```
       $ cd ~ && ls -lh | sed -n '10,15p'
       -rw-r--r--  1 rahim rahim  15K Sep  4 09:15 report.txt
       drwxr-xr-x  2 rahim rahim 4.0K Sep  4 10:30 scripts
       -rwxr-xr-x  1 rahim rahim 1.0K Sep  4 10:30 setup.sh
       -rw-r--r--  1 rahim rahim 2.3M Sep  3 18:22 backup.tar.gz
       drwxr-xr-x 5 rahim rahim 4.0K Sep  2 11:40 projects
       -rw-r--r--  1 rahim rahim  856 Sep  1 08:05 notes.md
    ```

    Equivalent ways to select the line range
    ```bash
       cd ~ && ls -lh | head -15 | tail -6      # first 15 lines, last 6 of those
       cd ~ && ls -lh | awk 'NR >= 10 && NR <= 15'
       cd ~ && ls -alh | sed -n '10,15p'         # including hidden files
    ```

    Note about `head -15 | tail -6`
    ```
       Lines 10 to 15 inclusive is SIX lines (10,11,12,13,14,15),
       so tail must take 6, not 5. Getting this off by one is the
       commonest mistake in such questions.
    ```

    Joining commands on one line — the three separators
    ```bash
       cmd1 ; cmd2         run cmd2 REGARDLESS of whether cmd1 succeeded
       cmd1 && cmd2        run cmd2 ONLY IF cmd1 succeeded  (exit status 0)
       cmd1 || cmd2        run cmd2 ONLY IF cmd1 FAILED
    ```
    - `&&` is the right choice here: if `cd ~` fails there is no point listing anything.

    Useful `ls` options in this context
    ```
       -l   long format : permissions, links, owner, group, size, date
       -h   human-readable sizes : 1.0K , 2.3M , 4.7G
       -a   include hidden files
       -t   sort by modification time, newest first
       -S   sort by size, largest first
       -r   reverse the order
    ```

    - Point worth stating: `ls -lh` prints a `total` line first, so the numbering used by `sed` includes it. If the intention is the 10th to 15th `files`, the total line must be skipped — for example `ls -lh | tail -n +2 | sed -n '10,15p'`.

30. **(i) Linux command for showing all files including the hidden files inside the home directory.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*

    Answer: The command is `ls -a` run in the home directory.
    ```bash
       ls -a ~
    ```
    ```bash
       cd ~ && ls -a               # go home first, then list
       ls -a /home/username        # by explicit path
       ls -la ~                    # with full details
       ls -alh ~                   # with human-readable sizes
       ls -A ~                     # all except . and ..
    ```

    What counts as hidden
    - A file or directory whose name `begins with a dot`. There is no hidden attribute as in Windows — the leading dot is the entire mechanism.
    ```
       .bashrc   .profile   .ssh/   .config/   .gitconfig   .cache/
    ```

    Example
    ```
       $ ls ~
       Desktop  Documents  Downloads  Pictures  script.sh

       $ ls -a ~
       .   .bash_history  .config   .profile  Documents  Pictures
       ..  .bashrc        .gitconfig  .ssh    Downloads  script.sh
                                              Desktop

       $ ls -la ~
       total 56
       drwxr-xr-x 12 rahim rahim 4096 Sep  4 10:30 .
       drwxr-xr-x  3 root  root  4096 Aug  1 09:00 ..
       -rw-------  1 rahim rahim 3200 Sep  4 10:25 .bash_history
       -rw-r--r--  1 rahim rahim  220 Aug  1 09:00 .bashrc
       drwx------  2 rahim rahim 4096 Sep  2 14:10 .ssh
       drwxr-xr-x  2 rahim rahim 4096 Sep  1 11:00 Documents
    ```
    ```
       .    the CURRENT directory
       ..   the PARENT directory

       Use  ls -A  to suppress these two, which is usually what is wanted.
    ```

    Ways of naming the home directory
    ```bash
       ls -a ~                     # the tilde shorthand
       ls -a $HOME                 # the environment variable
       ls -a /home/rahim           # the explicit path
       cd && ls -a                 # 'cd' with no argument goes home
    ```

    Listing only the hidden entries
    ```bash
       ls -d ~/.*                  # only entries beginning with a dot
       ls -A ~ | grep "^\."        # the same, filtered
    ```

    Counting them
    ```bash
       ls -A ~ | wc -l             # how many entries in total
       ls -d ~/.* | wc -l          # how many hidden entries
    ```

    - Short answer: `ls -a ~` — or `ls -la ~` when the details are wanted as well.

31. **(ii) Linux command for showing page size, disk space in a human-readable format.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*

    Answer: Two separate things are asked for: the memory `page size`, and the `disk space` in human-readable form.

    Page size
    ```bash
       getconf PAGESIZE            # the standard command
       getconf PAGE_SIZE           # the same
    ```
    ```
       $ getconf PAGESIZE
       4096
    ```
    - The answer is in bytes, so `4096` means a `4 KB` page — the usual value on x86 and x86-64 Linux.
    ```bash
       pagesize                    # a shorter equivalent, where available
       grep -i pagesize /proc/meminfo
    ```

    Disk space in a human-readable format
    ```bash
       df -h
    ```
    ```
       Filesystem      Size  Used Avail Use% Mounted on
       /dev/sda2       100G   45G   50G  48% /
       /dev/sda3       399G  120G  259G  32% /home
       tmpfs           7.8G  1.2M  7.8G   1% /run
    ```
    ```
       df    "disk free" - reports FILESYSTEM usage
       -h    human readable : K , M , G , T instead of raw blocks
    ```
    ```bash
       df -h                       # all mounted filesystems
       df -h /home                 # one filesystem
       df -Th                      # also show the filesystem TYPE
       df -i                       # inode usage instead of blocks
       df -h --total               # add a grand total line
    ```

    The related command for directory sizes
    ```bash
       du -h foldername            # size of each item inside it
       du -sh foldername           # SUMMARY - just the total
       du -sh *                    # size of everything in the current directory
       du -sh * | sort -rh | head  # the ten largest, biggest first
    ```
    ```
       df  =  how much of the FILESYSTEM is used
       du  =  how much space a DIRECTORY occupies

       They disagree quite often, usually because a deleted file is still
       held open by a running process.
    ```

    Memory, if that was the intention instead
    ```bash
       free -h                     # RAM and swap, human readable
       cat /proc/meminfo           # the kernel's detailed view
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | Page size | `getconf PAGESIZE` |
    | Disk space, human readable | `df -h` |
    | Size of a directory | `du -sh foldername` |
    | Memory, human readable | `free -h` |

    - Why the page size matters: it is the unit in which the operating system allocates memory and moves data between RAM and the swap area. A larger page reduces the number of page-table entries and TLB misses, but wastes more memory to internal fragmentation. Linux also supports `huge pages` of 2 MB or 1 GB for databases and virtual machines.

32. **A home directory called SGFL exists on your computer. Write a Linux command to create a link called “SGFL-Link” in the home directory.** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*

    Answer: The command is `ln -s`.
    ```bash
       ln -s ~/SGFL ~/SGFL-Link
    ```
    - `ln` creates a link; `-s` makes it `symbolic` (a soft link), which is what is needed for a directory.

    The general form
    ```
       ln -s  <target>  <link name>
              ^          ^
              what it    the new name
              points to  being created
    ```

    Variants
    ```bash
       ln -s /home/user/SGFL /home/user/SGFL-Link      # explicit full paths
       cd ~ && ln -s SGFL SGFL-Link                    # from inside the home dir
       ln -sf ~/SGFL ~/SGFL-Link                       # force - replace an
                                                       # existing link
       ln -sv ~/SGFL ~/SGFL-Link                       # verbose
    ```

    Verification
    ```bash
       $ ls -l ~/SGFL-Link
       lrwxrwxrwx 1 rahim rahim 15 Sep  4 10:30 SGFL-Link -> /home/rahim/SGFL
       ^                                                  ^^
       'l' = symbolic link                                points to
    ```
    ```bash
       readlink SGFL-Link          # show what it points to
       readlink -f SGFL-Link       # resolve to the final absolute path
       cd SGFL-Link                # entering the link enters the real directory
    ```

    Symbolic link versus hard link
    ```bash
       ln -s target linkname       # SYMBOLIC (soft) link
       ln target linkname          # HARD link
    ```

    | Point | Symbolic link | Hard link |
    |---|---|---|
    | What it stores | A `path` to the target | Another `name` for the same inode |
    | Works on directories | `Yes` | `No` (not permitted) |
    | Works across filesystems | `Yes` | `No` |
    | If the target is deleted | Becomes a broken link | The data survives until the last link goes |
    | Inode number | Its own | The same as the target |
    | Size | The length of the path string | The size of the file |
    | Shown by `ls -l` | `l` and an arrow `->` | Looks like an ordinary file |

    - A directory can only be linked `symbolically`. Hard links to directories are forbidden, because they would allow loops in the filesystem tree that `fsck` could not resolve.

    Removing a link
    ```bash
       rm SGFL-Link                # removes the LINK only, never the target
       unlink SGFL-Link            # the same
    ```
    - Note the trap: `rm SGFL-Link/` with a trailing slash may act on the target's contents on some systems. Always remove a link without the slash.

    Everyday uses
    ```bash
       ln -s /var/www/html ~/www                    # a shortcut to a long path
       ln -s /usr/bin/python3.11 /usr/bin/python    # a version-independent name
       ln -s /mnt/backup/2026 ~/current-backup      # a pointer that can be moved
    ```
    - This is how Linux keeps `/usr/bin/python` pointing at whichever version is current: only the link is changed, and every script that calls `python` follows it.

33. **Write Shell command which make a folder name ‘A’ with read permission access only.** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*

    Answer: The folder must be created and then given `read permission only`.
    ```bash
       mkdir A && chmod 444 A
    ```
    - Or as two separate commands:
    ```bash
       mkdir A
       chmod 444 A
    ```
    ```
       4 = r--   read only, for owner, group and others
    ```

    Verification
    ```bash
       $ ls -ld A
       dr--r--r--  2 rahim rahim 4096 Sep  4 10:30 A
       ^^^^^^^^^^
       d = directory , then r-- r-- r--
    ```
    - `ls -ld` shows the directory's `own` entry rather than its contents, which is what is wanted here.

    An important caution about directories
    ```
       For a DIRECTORY the permission bits mean something different:

            r  = list the names inside it
            w  = create or delete files inside it
            x  = ENTER it (cd into it) and access files by name

       With 444 the directory can be LISTED but not ENTERED :

            $ ls A          works
            $ cd A          Permission denied
            $ ls -l A       cannot stat the files - shows ? for every field
    ```
    - So a "read-only directory" that is actually usable normally needs the execute bit as well:
    ```bash
       chmod 555 A          # r-x for everyone : can list AND enter, cannot write
       chmod 500 A          # owner can list and enter, nobody else anything
    ```
    - `555` is almost always what is intended by "read permission access only" for a folder.

    Creating it with the permission in one step
    ```bash
       mkdir -m 444 A       # create directly with mode 444
       mkdir -m 555 A       # create read and enter, no write
    ```

    Symbolic forms
    ```bash
       chmod a=r A          # everyone gets read only
       chmod a-wx,a+r A     # strip write and execute, add read
       chmod ugo=r A        # spelled out
    ```

    The permission arithmetic
    ```
       r = 4 , w = 2 , x = 1

       r-- = 4        r-x = 5        rwx = 7
       rw- = 6        r-x = 5        --- = 0
    ```

    Related commands
    ```bash
       ls -ld A                 # show the directory's own permissions
       chmod -R 444 A           # apply to everything INSIDE it as well
       chown rahim:rahim A      # change ownership
       stat -c "%A %a %n" A     # e.g. "dr--r--r-- 444 A"
    ```

    - Answer to state: `mkdir A && chmod 444 A` for literal read-only, adding that `chmod 555 A` is the practically useful form, because without the execute bit the folder cannot be entered at all.

34. **Write Shell command which copy folder ‘A’ all information into folder ‘P’. Folder ‘A’ and folder ‘P’s parent folder is same.** *[Janata Bank Assistant System Administrator 2021 compact it 938-939 (ET: N/A)]*

    Answer: Both folders share the same parent, so the copy is a simple recursive `cp`.
    ```bash
       cp -r A/* P/
    ```
    - This copies everything `inside` A into P, without creating an `A` folder inside P.

    The distinction that matters
    ```bash
       cp -r A P            # creates  P/A/...      - A itself goes INSIDE P
       cp -r A/* P/         # copies the CONTENTS of A directly into P
       cp -r A/. P/         # the same, and it also catches HIDDEN files
    ```
    - `A/*` misses files whose names begin with a dot, because the shell's `*` does not match them. `A/.` copies everything including hidden files, so it is the safer form:
    ```bash
       cp -r A/. P/
    ```

    Preserving attributes
    ```bash
       cp -a A/. P/         # ARCHIVE mode : preserves permissions, ownership,
                            # timestamps and symbolic links. Usually the right
                            # choice for "copy all information".
    ```
    - Since the question says "all information", `cp -a` is the better answer than plain `cp -r`.

    Useful options
    ```bash
       cp -rv A/. P/        # verbose - list each file as it is copied
       cp -ri A/. P/        # interactive - ask before overwriting
       cp -ru A/. P/        # update - copy only files that are newer
       cp -rp A/. P/        # preserve mode, ownership and timestamps
    ```

    Using `rsync` instead, which is better for large trees
    ```bash
       rsync -av A/ P/                    # note the trailing slash on A/
       rsync -av --progress A/ P/         # show progress
       rsync -av --delete A/ P/           # make P an exact MIRROR of A
    ```
    - `rsync` transfers only what has changed and can resume after an interruption, so it is the standard tool for backups.

    The trailing-slash rule, which catches everyone
    ```
       rsync -av A  P/      ->  creates  P/A/...
       rsync -av A/ P/      ->  copies the CONTENTS of A into P
    ```

    Verification
    ```bash
       ls -la P                     # check the result
       diff -r A P                  # confirm the two trees are identical
       du -sh A P                   # compare the sizes
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | Copy A's contents into P | `cp -r A/* P/` |
    | Including hidden files | `cp -r A/. P/` |
    | Preserving all attributes | `cp -a A/. P/` |
    | Copy the folder A itself into P | `cp -r A P/` |
    | Large trees, resumable | `rsync -av A/ P/` |

35. **৩. লিনাক্স এর প্রিন্ট কমান্ডটি লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The Linux print command is `lpr` (or `lp`).
    ```bash
       lpr filename.txt              # send a file to the default printer
       lp filename.txt               # the System V equivalent
    ```

    `lpr` — the BSD-style command
    ```bash
       lpr document.pdf                    # print to the default printer
       lpr -P HP_LaserJet document.pdf     # choose a printer
       lpr -# 3 document.pdf               # print 3 copies
       lpr -o sides=two-sided-long-edge f  # double sided
    ```

    `lp` — the System V style command
    ```bash
       lp document.pdf
       lp -d HP_LaserJet document.pdf      # choose a printer
       lp -n 3 document.pdf                # 3 copies
       lp -o media=A4 document.pdf         # paper size
    ```

    Managing the print queue
    ```bash
       lpq                    # show the queue for the default printer
       lpq -P HP_LaserJet     # for a named printer
       lpstat -p              # printer status
       lpstat -a              # which printers are accepting jobs
       lprm 42                # remove job number 42
       lprm -                 # remove all of your own jobs
       cancel 42              # the System V equivalent of lprm
    ```
    ```
       $ lpq
       HP_LaserJet is ready
       Rank    Owner   Job     File(s)              Total Size
       1st     rahim   42      report.pdf           245760 bytes
    ```

    Printing formatted text
    ```bash
       pr -h "Monthly Report" data.txt | lpr    # add a header and paginate
       a2ps document.txt                        # pretty-print text to PostScript
       enscript -2r file.txt                    # two columns, landscape
    ```

    The printing system underneath
    ```
       CUPS  - the Common Unix Printing System - is what actually handles
               printing on Linux. lpr and lp are its front ends.

       systemctl status cups        # is the print service running?
       lpadmin -p name -E -v uri    # add a printer
       http://localhost:631         # the CUPS web interface
    ```

    Related meaning of "print"
    - If the question means printing `to the screen` rather than to a printer, the commands are:
    ```bash
       echo "text"           # print a line
       printf "%s\n" "text"  # formatted print
       cat filename          # print a whole file
       pwd                   # print the working directory
    ```

    - Short answer: `lpr filename` or `lp filename` for a printer, and `echo` / `cat` for printing to the terminal. Which is meant is usually clear from the paper's other questions.

36. **৬. ফোল্ডার রিমুভ করার জন্য নিচেরর কোনটি লিনাক্স কমান্ড হিসেবে ব্যবহৃত হয়?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The command to remove a folder is `rmdir` for an empty one, and `rm -r` for one that has contents.
    ```bash
       rmdir foldername             # ONLY works if the folder is EMPTY
       rm -r foldername             # removes the folder AND everything inside
       rm -rf foldername            # force, without any prompts
    ```

    `rmdir` — for an empty directory only
    ```bash
       rmdir myfolder
       rmdir -p a/b/c               # remove c, then b, then a, if each becomes empty
       rmdir dir1 dir2 dir3         # several at once
    ```
    ```
       $ rmdir myfolder
       rmdir: failed to remove 'myfolder': Directory not empty
    ```
    - This failure is its safety feature: `rmdir` cannot destroy data by accident.

    `rm -r` — for a directory with contents
    ```bash
       rm -r myfolder               # recursive; may prompt for protected files
       rm -rf myfolder              # force : no prompts, no error if absent
       rm -ri myfolder              # ask before EVERY deletion - safest
       rm -rv myfolder              # verbose : list what is removed
    ```
    ```
       -r  recursive - descend into the directory
       -f  force     - never prompt, ignore missing files
       -i  interactive - confirm each removal
       -v  verbose
    ```

    The danger of `rm -rf`
    ```
       There is NO recycle bin in Linux. A deleted file is gone.

       rm -rf /              destroys the entire system
       rm -rf / home         destroys the system - note the stray SPACE
       rm -rf ~              wipes your whole home directory
       rm -rf .*             can escape upward through ..
    ```
    - Safe habits: run `ls foldername` first to see what will go, use an absolute path, use `rm -ri` when unsure, and never run `rm -rf` with a variable that might be empty — `rm -rf "$DIR"/` becomes `rm -rf /` if `DIR` is unset.

    Removing by pattern, more safely
    ```bash
       find . -type d -name "temp*" -exec rm -r {} +      # inspect first with -print
       find . -type d -empty -delete                      # only empty directories
    ```

    Related commands
    ```bash
       rm filename                  # remove a single file
       rm -i filename               # ask first
       rm *.txt                     # remove by wildcard
       unlink filename              # remove exactly one file
       trash-put filename           # move to trash, if trash-cli is installed
    ```

    Summary

    | Situation | Command |
    |---|---|
    | Empty folder | `rmdir foldername` |
    | Folder with contents | `rm -r foldername` |
    | Force, no prompts | `rm -rf foldername` |
    | Confirm each deletion | `rm -ri foldername` |

    - Short answer: `rmdir` for an empty folder, `rm -r` (or `rm -rf`) for one with files in it.

37. **৭. ফাইল কপি করার জন্য লিনাক্স কমান্ড কোনটি?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The Linux command to copy a file is `cp`.
    ```bash
       cp source destination
    ```

    Examples
    ```bash
       cp file.txt backup.txt                  # copy to a new name
       cp file.txt /home/user/documents/       # copy into another directory
       cp file1.txt file2.txt /backup/         # copy several files at once
       cp *.txt /backup/                       # copy by wildcard
    ```

    Copying a directory
    ```bash
       cp -r foldername /destination/          # RECURSIVE - required for a folder
       cp -a foldername /destination/          # archive mode : also preserves
                                               # permissions, ownership and times
    ```
    - Without `-r`, `cp` refuses:
    ```
       cp: -r not specified; omitting directory 'foldername'
    ```

    Useful options
    ```
       -r , -R   recursive - needed to copy a directory
       -a        archive - preserves everything (implies -r -p and keeps links)
       -i        interactive - ask before overwriting
       -n        never overwrite an existing file
       -u        update - copy only if the source is newer
       -v        verbose - print each file as it is copied
       -p        preserve mode, ownership and timestamps
       -l        make a hard link instead of copying
       -s        make a symbolic link instead of copying
    ```
    ```bash
       cp -iv report.txt /backup/          # ask first, and say what was done
       cp -au /data/. /backup/             # incremental archive copy
    ```

    Copying to another machine
    ```bash
       scp file.txt user@server:/home/user/         # over SSH
       scp -r folder user@server:/home/user/        # a whole directory
       rsync -av folder/ user@server:/backup/       # efficient and resumable
    ```

    The trailing-slash subtlety
    ```bash
       cp -r A  B/          ->  creates  B/A/...
       cp -r A/* B/         ->  copies the CONTENTS of A into B
       cp -r A/. B/         ->  the same, and it also catches HIDDEN files
    ```

    Verification
    ```bash
       ls -l /backup/                # check the result
       diff file.txt backup.txt      # confirm the copies are identical
       md5sum file.txt backup.txt    # compare checksums
    ```

    Related commands
    ```
       cp     copy
       mv     move or rename
       rm     delete
       ln     create a link
       rsync  synchronise, only transferring what changed
    ```

    - Short answer: `cp source destination`, adding `-r` for a directory and `-a` when all attributes must be preserved.

38. **ফাইল কপি করার লিনাক্স/ইউনিক্স কমান্ড কি?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) The Linux and Unix command to copy a file is `cp`.
    ```bash
       cp source destination
    ```

    Basic use
    ```bash
       cp file.txt backup.txt                 # copy to a new name
       cp file.txt /home/user/documents/      # copy into another directory
       cp *.txt /backup/                      # copy by wildcard
       cp file1 file2 file3 /backup/          # several files into one directory
    ```

    Copying a directory
    ```bash
       cp -r foldername /destination/         # RECURSIVE - required for a folder
       cp -a foldername /destination/         # archive : also preserves
                                              # permissions, ownership and times
    ```

    Important options
    ```
       -r , -R   recursive, for directories
       -a        archive mode - preserves everything
       -i        interactive - ask before overwriting
       -n        never overwrite
       -u        update - only if the source is newer
       -v        verbose
       -p        preserve mode, ownership and timestamps
    ```

    Copying between machines
    ```bash
       scp file.txt user@server:/home/user/            # over SSH
       scp -r folder user@server:/home/user/           # a whole directory
       rsync -av folder/ user@server:/backup/          # only what changed
    ```

    Related file commands
    ```
       cp     copy a file or directory
       mv     move or rename
       rm     delete
       ln     create a link
       touch  create an empty file
       cat    display or concatenate
    ```

    Verification
    ```bash
       ls -l /backup/                     # check the result
       diff file.txt backup.txt           # confirm they are identical
       md5sum file.txt backup.txt         # compare checksums
    ```

    - Point worth noting: `cp` overwrites the destination `silently` if it already exists. Use `cp -i` to be prompted, or `cp -n` never to overwrite. Many administrators keep `alias cp='cp -i'` in their `.bashrc` for exactly this reason.

    - Short answer: `cp source destination`, with `-r` added for a directory.

39. **২. নেটওয়ার্ক কানেক্টিভিটি টেস্ট করার জন্য লিনাক্স কমান্ড লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 946 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) The command to test network connectivity is `ping`.
    ```bash
       ping hostname_or_IP
    ```

    Examples
    ```bash
       ping google.com                # test by hostname
       ping 8.8.8.8                   # test by IP address
       ping -c 4 google.com           # send only 4 packets, then stop
       ping -i 2 google.com           # one packet every 2 seconds
       ping -s 1000 google.com        # 1000-byte packets
       ping -W 2 google.com           # wait at most 2 seconds for a reply
       ping6 ipv6.google.com          # IPv6
    ```
    - On Linux `ping` runs until stopped with `Ctrl + C`, unlike Windows, where it sends four packets by default. That is why `-c 4` is normally added.

    Sample output
    ```
       PING google.com (142.250.196.14) 56(84) bytes of data.
       64 bytes from 142.250.196.14: icmp_seq=1 ttl=115 time=12.3 ms
       64 bytes from 142.250.196.14: icmp_seq=2 ttl=115 time=11.8 ms
       64 bytes from 142.250.196.14: icmp_seq=3 ttl=115 time=12.1 ms

       --- google.com ping statistics ---
       3 packets transmitted, 3 received, 0% packet loss, time 2003ms
       rtt min/avg/max/mdev = 11.8/12.06/12.3/0.21 ms
    ```
    ```
       How to read it :
          0% packet loss    -> the link is healthy
          time = 12 ms      -> the round-trip delay
          ttl  = 115        -> hops remaining; hints at the distance
          100% packet loss  -> unreachable, or ICMP is being blocked
    ```

    How it works
    - `ping` sends an `ICMP Echo Request` and waits for an `ICMP Echo Reply`. It tests three things at once: name resolution, reachability and round-trip time.

    Other connectivity commands
    ```bash
       traceroute host             # every router along the path
       tracepath host              # the same, without needing root
       mtr host                    # traceroute + ping, live and continuous
       nslookup host               # does the name resolve?
       dig host                    # detailed DNS query
       curl -I https://site        # is the WEB SERVICE answering?
       telnet host 80              # is a particular port open?
       nc -zv host 443             # port check with netcat
       ip a                        # local interfaces and addresses
       ip route                    # the routing table, including the gateway
       ss -tuln                    # listening ports on this machine
    ```

    A practical diagnostic order
    ```
       1. ip a                 - does this machine have an IP address?
       2. ping 192.168.1.1     - can it reach its own gateway?
       3. ping 8.8.8.8         - can it reach the internet by IP?
       4. ping google.com      - does DNS work?
       5. traceroute google.com- where does the path break?
    ```
    - Each step isolates one layer. If step 3 works but step 4 fails, the fault is DNS, not connectivity.

    - Caution worth stating: many servers and firewalls `block ICMP`, so a failed ping does not always mean the host is down. `curl -I` or `nc -zv` on the actual service port is a more reliable test in that case.

40. **৩. IP Address বের করার জন্য লিনাক্স কমান্ড লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 946 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) The modern command is `ip addr show`.
    ```bash
       ip addr show                # full details
       ip a                        # short form
       ip -4 a                     # IPv4 only
       ip -br a                    # brief, one line per interface
    ```
    ```
       $ ip -br a
       lo               UNKNOWN        127.0.0.1/8 ::1/128
       eth0             UP             192.168.1.15/24
       wlan0            DOWN
    ```

    Other ways
    ```bash
       hostname -I                 # just the IP addresses, space separated
       hostname -i                 # the primary address
       ifconfig                    # older, from net-tools; may not be installed
       ifconfig eth0               # one interface
       ip route get 1.1.1.1        # shows which address is used to reach the net
       nmcli device show           # NetworkManager's view
    ```
    ```
       $ hostname -I
       192.168.1.15 172.17.0.1

       $ ip route get 1.1.1.1
       1.1.1.1 via 192.168.1.1 dev eth0 src 192.168.1.15
                                            ^^^^^^^^^^^^
                                            the address actually in use
    ```

    Finding the PUBLIC IP address
    ```bash
       curl ifconfig.me
       curl ipinfo.io/ip
       curl -s https://api.ipify.org
       dig +short myip.opendns.com @resolver1.opendns.com
    ```
    - The `ip a` command shows the machine's `private` address behind NAT. The public address seen by the internet is different, which is why these external services are used.

    Reading `ip addr show` output
    ```
       2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP
           link/ether 08:00:27:4e:66:a1 brd ff:ff:ff:ff:ff:ff
           inet 192.168.1.15/24 brd 192.168.1.255 scope global eth0
           inet6 fe80::a00:27ff:fe4e:66a1/64 scope link
           ^^^^                                ^^^^^
           IPv4 address and prefix             IPv6 link-local
           link/ether = the MAC address
    ```

    The `ip` command family, which replaced `net-tools`
    ```
       ip addr        replaces  ifconfig
       ip route       replaces  route
       ip neigh       replaces  arp
       ss             replaces  netstat
    ```
    ```bash
       ip route show               # the routing table and default gateway
       ip neigh show               # the ARP cache
       ss -tuln                    # listening TCP and UDP ports
       ip link show                # interfaces and their MAC addresses
    ```

    Setting an address manually
    ```bash
       sudo ip addr add 192.168.1.100/24 dev eth0
       sudo ip link set eth0 up
       sudo dhclient eth0                          # request one by DHCP
    ```

    - Short answer: `ip addr show` (or `ip a`). On older systems `ifconfig` does the same, and `hostname -I` is the quickest way to get just the address.

41. **Write down Linux command: i. Display current directory folder and file. ii. Create a folder name “DPDC”. iii. Remove a file like as “DPDC2”. iv. A file name is “myFile”; Rename the file name to “DPDC2.txt”. v. Give permission to a file so that anyone can read, write and executive that file.** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*

    Answer: i. Display the files and folders in the current directory
    ```bash
       ls                     # names only
       ls -l                  # long listing with details
       ls -la                 # including hidden files
       ls -lh                 # human-readable sizes
       pwd                    # show WHICH directory you are in
    ```

    ii. Create a folder named `DPDC`
    ```bash
       mkdir DPDC
       mkdir -p /home/user/DPDC          # create the whole path if needed
       mkdir -m 755 DPDC                 # create with specific permissions
    ```

    iii. Remove a file named `DPDC2`
    ```bash
       rm DPDC2                # remove a FILE
       rm -i DPDC2             # ask before deleting - safest
       rm -f DPDC2             # force, no prompt

       rm -r DPDC2             # if DPDC2 is a DIRECTORY
       rmdir DPDC2             # if it is an EMPTY directory
    ```

    iv. Rename `myFile` to `DPDC2.txt`
    ```bash
       mv myFile DPDC2.txt
    ```
    ```bash
       mv -i myFile DPDC2.txt       # ask before overwriting
       mv -v myFile DPDC2.txt       # verbose
    ```
    - Linux has no separate rename command. `mv` serves as both move and rename, because renaming is simply moving a file to a new name in the same directory.

    v. Give permission so that anyone can read, write and execute the file
    ```bash
       chmod 777 DPDC2.txt
    ```
    ```bash
       chmod a+rwx DPDC2.txt        # symbolic equivalent
       chmod ugo+rwx DPDC2.txt      # spelled out
    ```
    ```
       7 = 4+2+1 = rwx        ->   owner 7 , group 7 , others 7

       $ ls -l DPDC2.txt
       -rwxrwxrwx  1 rahim rahim  0  Sep 4 10:30  DPDC2.txt
    ```
    - Worth stating: `777` is a serious security risk on a multi-user system, because any account can modify or replace the file. `755` or `644` is normally correct.

    All five in sequence
    ```bash
       $ ls -l                       # i
       $ mkdir DPDC                  # ii
       $ rm DPDC2                    # iii
       $ mv myFile DPDC2.txt         # iv
       $ chmod 777 DPDC2.txt         # v
       $ ls -l DPDC2.txt
       -rwxrwxrwx 1 rahim rahim 0 Sep  4 10:30 DPDC2.txt
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | i. Display current directory contents | `ls -l` |
    | ii. Create folder DPDC | `mkdir DPDC` |
    | iii. Remove file DPDC2 | `rm DPDC2` |
    | iv. Rename myFile to DPDC2.txt | `mv myFile DPDC2.txt` |
    | v. Full permission to everyone | `chmod 777 DPDC2.txt` |

42. **A bash shell script using for loop to give output of given pattern:** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035 (ET: BUET)]*

    Answer: The question is `incomplete` — the pattern the script should produce was printed as a figure and is not present in the text. The three patterns that appear in such papers are given below, each with a `for` loop, so the method covers whichever was intended.

    Pattern 1 — increasing right triangle
    ```
       *
       * *
       * * *
       * * * *
       * * * * *
    ```
    ```bash
    #!/bin/bash

    read -p "Enter number of rows: " n

    for (( i=1; i<=n; i++ ))
    do
        for (( j=1; j<=i; j++ ))
        do
            echo -n "* "
        done
        echo                       # newline at the end of each row
    done
    ```
    ```
       The OUTER loop controls the ROWS.
       The INNER loop controls how many stars are printed in that row.
       echo -n suppresses the newline, so stars stay on one line.
    ```

    Pattern 2 — decreasing (inverted) triangle
    ```
       * * * * *
       * * * *
       * * *
       * *
       *
    ```
    ```bash
    #!/bin/bash

    n=5
    for (( i=n; i>=1; i-- ))
    do
        for (( j=1; j<=i; j++ ))
        do
            echo -n "* "
        done
        echo
    done
    ```

    Pattern 3 — number pyramid
    ```
       1
       1 2
       1 2 3
       1 2 3 4
       1 2 3 4 5
    ```
    ```bash
    #!/bin/bash

    n=5
    for (( i=1; i<=n; i++ ))
    do
        for (( j=1; j<=i; j++ ))
        do
            echo -n "$j "
        done
        echo
    done
    ```

    Pattern 4 — a centred pyramid, if spaces are required
    ```
           *
          * *
         * * *
        * * * *
       * * * * *
    ```
    ```bash
    #!/bin/bash

    n=5
    for (( i=1; i<=n; i++ ))
    do
        for (( s=n; s>i; s-- )); do echo -n " "; done      # leading spaces
        for (( j=1; j<=i; j++ )); do echo -n "* "; done    # the stars
        echo
    done
    ```

    Running the script
    ```bash
       chmod +x pattern.sh          # make it executable
       ./pattern.sh                 # run it
       bash pattern.sh              # or run it through bash directly
    ```

    The two `for` loop forms in bash
    ```bash
       # C-style, best for counting
       for (( i=1; i<=5; i++ )); do echo $i; done

       # list form, best for iterating over items
       for i in 1 2 3 4 5;    do echo $i; done
       for i in {1..5};       do echo $i; done
       for f in *.txt;        do echo "$f"; done
       for i in $(seq 1 5);   do echo $i; done
    ```

    Points worth stating
    ```
       #!/bin/bash          the SHEBANG - tells the kernel which interpreter
       echo -n              print without a trailing newline
       $(( ))               arithmetic expansion
       Always QUOTE "$var"  so that a value containing a space is not split
       chmod +x             the script must be executable before ./ works
    ```

43. **Answer the following linux command:** *[DESCO Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*
   i. Rename a file test.docs to test.txt
   ii. Delete a file from a folder
   iii. Put a read/write permission to a file
   iv. Find the mac address using command

    Answer: i. Rename `test.docs` to `test.txt`
    ```bash
       mv test.docs test.txt
    ```
    ```bash
       mv -i test.docs test.txt        # ask before overwriting
       mv -v test.docs test.txt        # verbose
    ```
    - Linux has no separate rename command; `mv` does both moving and renaming, because a rename is simply a move within the same directory.

    ii. Delete a file from a folder
    ```bash
       rm foldername/filename          # delete one file inside a folder
       rm /home/user/docs/report.txt   # by full path
    ```
    ```bash
       rm -i filename                  # ask before deleting - safest
       rm -f filename                  # force, no prompt
       rm *.txt                        # delete by wildcard
       rm -r foldername                # delete a DIRECTORY and its contents
    ```
    - There is no recycle bin. A deleted file cannot be recovered by ordinary means.

    iii. Put read and write permission on a file
    ```bash
       chmod 666 filename              # rw- for owner, group and others
    ```
    ```
       6 = 4 + 2 = rw-

       $ ls -l filename
       -rw-rw-rw-  1 rahim rahim  0  Sep 4 10:30  filename
    ```
    ```bash
       chmod 644 filename              # owner rw-, everyone else r--  (usual)
       chmod 600 filename              # owner rw- only, nobody else   (private)
       chmod u+rw filename             # symbolic : add rw for the owner
       chmod a+rw filename             # add rw for everyone
    ```
    - `644` is the normal setting for a data file; `666` gives every account on the machine write access and is rarely appropriate.

    iv. Find the MAC address
    ```bash
       ip link show                    # the modern command
       ip link show eth0               # one interface
       ip -br link                     # brief, one line per interface
    ```
    ```
       $ ip link show eth0
       2: eth0: <BROADCAST,MULTICAST,UP,LOWER_UP> mtu 1500 state UP
           link/ether 08:00:27:4e:66:a1 brd ff:ff:ff:ff:ff:ff
                      ^^^^^^^^^^^^^^^^^
                      the MAC address
    ```
    Other ways
    ```bash
       ifconfig | grep ether           # older net-tools
       ifconfig -a | grep HWaddr       # older format
       cat /sys/class/net/eth0/address # straight from the kernel
       ip addr show | grep link/ether
       nmcli device show | grep HWADDR # NetworkManager
       arp -a                          # MAC addresses of OTHER machines
    ```
    ```
       $ cat /sys/class/net/eth0/address
       08:00:27:4e:66:a1
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | i. Rename a file | `mv test.docs test.txt` |
    | ii. Delete a file | `rm folder/filename` |
    | iii. Read/write permission | `chmod 666 filename` |
    | iv. MAC address | `ip link show` |

    - A MAC address is a 48-bit hardware address written as six hexadecimal pairs. The first three pairs are the `OUI`, identifying the manufacturer — `08:00:27` above belongs to VirtualBox.

44. **Write Linux command: (i) File permission (ii) Remove file or folder (iii) Show IP address** *[DESCO Sub-Assistant Engineer (CSE) 2019 compact it 1119 (ET: BUET)]*

    Answer: (i) File permission
    ```bash
       ls -l filename               # SHOW the permissions
       chmod 755 filename           # SET them, numeric form
       chmod u+x filename           # SET them, symbolic form
       chmod -R 755 foldername      # apply to a whole directory tree
    ```
    ```
       $ ls -l filename
       -rwxr-xr--  1  rahim  accounts  2048  Sep 4 10:30  filename
       ^^^^^^^^^^     ^^^^^  ^^^^^^^^
       |||  |||  |||  owner  group
       |||  |||  +--- others : r--
       |||  +-------- group  : r-x
       +------------- owner  : rwx
       ^
       type : - file , d directory , l link
    ```
    ```
       r = 4 , w = 2 , x = 1

       rwx = 7 , rw- = 6 , r-x = 5 , r-- = 4 , --- = 0

       755 = owner rwx , group r-x , others r-x     (programs, directories)
       644 = owner rw- , group r-- , others r--     (ordinary documents)
       600 = owner rw- , nobody else                (private files, SSH keys)
    ```
    Changing ownership, which goes with permission
    ```bash
       chown rahim filename              # change the owner
       chgrp accounts filename           # change the group
       chown rahim:accounts filename     # both at once
    ```

    (ii) Remove a file or folder
    ```bash
       rm filename                  # remove a FILE
       rm -i filename               # ask first - safest
       rm -f filename               # force, no prompt
       rm *.txt                     # by wildcard

       rmdir foldername             # remove an EMPTY folder
       rm -r foldername             # remove a folder AND its contents
       rm -rf foldername            # force recursive - dangerous
       rm -ri foldername            # confirm each deletion
    ```
    - There is no recycle bin. `rm -rf` on the wrong path is unrecoverable, and a stray space — `rm -rf / home` instead of `rm -rf /home` — destroys the system.

    (iii) Show the IP address
    ```bash
       ip addr show                 # the modern command
       ip a                         # short form
       ip -br a                     # brief, one line per interface
       hostname -I                  # just the addresses
       ifconfig                     # older, from net-tools
    ```
    ```
       $ ip -br a
       lo      UNKNOWN  127.0.0.1/8
       eth0    UP       192.168.1.15/24
    ```
    ```bash
       curl ifconfig.me             # the PUBLIC address, as seen from outside
       ip route show                # the default gateway
       ip link show                 # MAC addresses
    ```

    Summary

    | Requirement | Command |
    |---|---|
    | (i) Show permissions | `ls -l filename` |
    | (i) Set permissions | `chmod 755 filename` |
    | (ii) Remove a file | `rm filename` |
    | (ii) Remove a folder | `rm -r foldername` |
    | (iii) Show IP address | `ip addr show` |

45. **Linux এ file তৈরির জন্য কি কি Command ব্যবহৃত হয়? পূর্ণ Command লিখ।** *[NPCBL Junior Technical Engineer 2019 compact it 1149 (ET: BUET)]*

    Answer: (Answered in English, as required for IT topics.) Several commands create a file in Linux; which to use depends on whether content is to be typed at the same time.

    1. `touch` — create an empty file
    ```bash
       touch filename.txt
       touch file1.txt file2.txt file3.txt        # several at once
       touch /home/user/documents/report.txt      # by full path
    ```
    - The standard way to create an empty file. If the file already exists, `touch` only updates its timestamp and leaves the contents alone.

    2. `cat >` — create and type the contents
    ```bash
       cat > filename.txt
       This is the first line
       This is the second line
       <Ctrl + D>                                 # ends the input
    ```
    ```bash
       cat >> filename.txt          # APPEND to an existing file
       cat file1 file2 > merged.txt # create by joining two files
    ```

    3. `echo` — create with one line of text
    ```bash
       echo "Hello Bangladesh" > filename.txt     # create, or OVERWRITE
       echo "Second line" >> filename.txt         # APPEND
       echo -e "Line1\nLine2" > filename.txt      # -e interprets \n
    ```
    - Note the difference: `>` truncates and rewrites, `>>` adds to the end.

    4. `printf` — create with formatted text
    ```bash
       printf "Name: %s\nRoll: %d\n" "Rahim" 101 > student.txt
    ```

    5. A text editor
    ```bash
       vi filename.txt          # vi / vim
       nano filename.txt        # nano - simplest for a beginner
       gedit filename.txt       # graphical editor
    ```
    ```
       In vi :  press i to insert , type , then Esc  :wq  to save and quit
       In nano: type , then Ctrl+O to save , Ctrl+X to exit
    ```

    6. Redirection alone
    ```bash
       > filename.txt           # create empty, or TRUNCATE an existing file
       : > filename.txt         # the same, written portably
    ```

    7. `install` and `truncate`, for specific needs
    ```bash
       install -m 755 /dev/null script.sh    # create with given permissions
       truncate -s 0 filename.txt            # empty an existing file
       truncate -s 1M bigfile                # create a 1 MB file
       dd if=/dev/zero of=test.img bs=1M count=10   # create a 10 MB file
    ```

    Which to use

    | Situation | Command |
    |---|---|
    | Empty file | `touch filename` |
    | Type contents immediately | `cat > filename` |
    | One line of text | `echo "text" > filename` |
    | Edit properly | `nano filename` or `vi filename` |
    | Empty an existing file | `> filename` |
    | Create with a size | `truncate -s 1M filename` |

    Verification
    ```bash
       ls -l filename.txt           # confirm it exists and see its size
       cat filename.txt             # show the contents
       file filename.txt            # what kind of file it is
       wc -l filename.txt           # how many lines
    ```

    - Short answer: `touch filename` for an empty file, `cat > filename` to type the contents at once, and `echo "text" > filename` for a single line.

46. **A question on Linux file permission commands:** *[BPDB Assistant Engineer (CSE) 2018 compact it 1214 (ET: N/A)]*
   (i) Anyone can execute the file named “sample”.
   (ii) Only the owner or the user group can edit the file.
   (iii) None other then the other users can read the file.
   Write a shell command based on those conditions.

    Answer: The three conditions must be read carefully, because the third one is oddly worded.
    ```
       (i) Anyone can EXECUTE the file        -> x for owner, group and others
       (ii) Only the owner or the group can EDIT (write)
                                              -> w for owner and group, NOT others
       (iii) None other than the other users can READ
                                              -> read as: others may read
    ```

    Working out the bits
    ```
       Owner  : write (from ii) + execute (from i) + read (implied for the owner)
                -> rwx = 7
       Group  : write (from ii) + execute (from i) + read
                -> rwx = 7
       Others : execute (from i) + read (from iii) , but NO write
                -> r-x = 5
    ```
    ```bash
       chmod 775 sample
    ```

    Verification
    ```bash
       $ ls -l sample
       -rwxrwxr-x  1 rahim rahim  1024  Sep 4 10:30  sample
       ^^^ ^^^ ^^^
       |   |   +--- others : r-x   read and execute, NO write
       |   +------- group  : rwx   read, write, execute
       +----------- owner  : rwx   read, write, execute
    ```

    Symbolic equivalent
    ```bash
       chmod u=rwx,g=rwx,o=rx sample
       chmod a+rx,ug+w sample            # give everyone r and x, add w for u and g
       chmod 775 sample                  # the numeric form, simplest
    ```

    The permission arithmetic
    ```
       r = 4 , w = 2 , x = 1

       rwx = 4+2+1 = 7
       r-x = 4+0+1 = 5
       -> 775
    ```

    If condition (iii) is read the other way
    - Some readings take "none other than the other users can read" to mean that `only` others may read, which would be a strange and impractical permission:
    ```bash
       chmod 337 sample        # owner -wx , group -wx , others rwx
    ```
    - This would prevent the owner from reading their own file, which no real system would want. `775` is the sensible interpretation and the one to give, stating the reasoning.

    Common permission settings, for context
    ```
       775   owner and group full, others read and execute  (shared team scripts)
       755   owner full, everyone else read and execute     (normal programs)
       664   owner and group read/write, others read        (shared documents)
       644   owner read/write, others read                  (ordinary files)
       600   owner read/write only                          (private files)
       700   owner full only                                (private scripts)
    ```

    - The habit worth showing an examiner: translate each condition into the `r w x` bits for `owner / group / others` first, then convert to octal. Writing the octal number straight from memory is where mistakes happen.

47. **Linux Command:** *[BTCL Assistant Manager (Technical) 2017 compact it 1255-1256 (ET: N/A)]*
   i) passwd
   ii) cat>file.txt
   iii) telnet
   iv) ls
   v) ping
   vi) su
   vii) nslookup
   viii) mkdir

    Answer: i. `passwd` — change a password
    ```bash
       passwd                       # change your OWN password
       sudo passwd rahim            # change another user's (root only)
       sudo passwd -l rahim         # LOCK the account
       sudo passwd -u rahim         # unlock it
       sudo passwd -e rahim         # force a change at the next login
       passwd -S rahim              # show the password status
    ```
    ```
       $ passwd
       Changing password for rahim.
       Current password:
       New password:
       Retype new password:
       passwd: password updated successfully
    ```
    - Passwords are stored, hashed, in `/etc/shadow`, which only root can read.

    ii. `cat > file.txt` — create a file and type its contents
    ```bash
       cat > file.txt
       This is line one
       This is line two
       <Ctrl + D>                   # end of input
    ```
    ```
       cat       "concatenate" - normally displays a file
       >         redirect the OUTPUT into a file, creating or TRUNCATING it
       Ctrl + D  signals end-of-file, so cat stops reading
    ```
    ```bash
       cat file.txt                 # display the contents
       cat >> file.txt              # APPEND instead of overwriting
       cat file1 file2 > merged.txt # join two files into a third
       cat -n file.txt              # display with line numbers
    ```
    - The trap: `>` destroys the existing contents without warning. Use `>>` to add to a file.

    iii. `telnet` — connect to a remote host
    ```bash
       telnet hostname              # connect on the default port 23
       telnet 192.168.1.10
       telnet google.com 80         # test whether a PORT is open
    ```
    - `telnet` sends everything, including the password, `in plain text`. It is obsolete for remote login and has been replaced by `ssh`. Its one remaining use is as a quick port-connectivity test:
    ```bash
       $ telnet google.com 80
       Trying 142.250.196.14...
       Connected to google.com.        <- port 80 is open
    ```
    - `nc -zv host 80` does the same job more cleanly.

    iv. `ls` — list directory contents
    ```bash
       ls                # names only
       ls -l             # long listing : permissions, owner, size, date
       ls -a             # including hidden (dot) files
       ls -la            # both
       ls -lh            # human-readable sizes
       ls -lt            # newest first
       ls -R             # recurse into subdirectories
    ```

    v. `ping` — test network connectivity
    ```bash
       ping google.com
       ping -c 4 google.com         # send 4 packets and stop
       ping 8.8.8.8                 # test by IP, bypassing DNS
    ```
    ```
       64 bytes from 142.250.196.14: icmp_seq=1 ttl=115 time=12.3 ms
       --- 4 packets transmitted, 4 received, 0% packet loss
    ```
    - It sends an `ICMP Echo Request` and waits for the reply, testing name resolution, reachability and round-trip time together.

    vi. `su` — switch user
    ```bash
       su                     # become root (asks for ROOT's password)
       su -                   # become root WITH root's environment
       su rahim               # become another user
       su - rahim             # with that user's full login environment
       exit                   # return to the previous user
    ```
    ```
       su        switch user, keeping the current environment
       su -      switch user AND load their profile, PATH and home directory
       sudo cmd  run ONE command as root, using YOUR OWN password
    ```
    - `sudo` is preferred over `su` on modern systems: it needs no shared root password, it logs every command, and it grants only what the `/etc/sudoers` file allows.

    Summary

    | Command | Purpose |
    |---|---|
    | `passwd` | Change a password |
    | `cat > file.txt` | Create a file and type its contents |
    | `telnet` | Remote login (obsolete) or a port test |
    | `ls` | List directory contents |
    | `ping` | Test network connectivity |
    | `su` | Switch to another user |

## CPU Scheduling Algorithms (25)

1. A CPU scheduling algorithm must choose a process from the ready queue to execute. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

   Answer: `CPU scheduling` is the activity of deciding which process in the `ready queue` gets the CPU next. It is what makes multiprogramming possible: while one process waits for I/O, the CPU is given to another instead of sitting idle.

   When scheduling happens
   ```
      1. Running  -> Waiting   (a process issues an I/O request)
      2. Running  -> Ready     (an interrupt or a time quantum expires)
      3. Waiting  -> Ready     (I/O completes)
      4. Running  -> Terminated

      Cases 1 and 4 only  ->  NON-PREEMPTIVE scheduling
      All four cases      ->  PREEMPTIVE scheduling
   ```

   Scheduling criteria — what a good algorithm maximises or minimises
   ```
      CPU utilisation   : keep the CPU busy          -> MAXIMISE
      Throughput        : processes completed per unit time -> MAXIMISE
      Turnaround time   : submission to completion   -> MINIMISE
      Waiting time      : total time in the ready queue -> MINIMISE
      Response time     : submission to FIRST response  -> MINIMISE
      Fairness          : no process starves
   ```
   ```
      Turnaround time = Completion time - Arrival time
      Waiting time    = Turnaround time - Burst time
   ```

   The main algorithms

   `FCFS (First Come First Served)`
   - Non-preemptive; processes run in arrival order. Simple and fair, but suffers the `convoy effect`: one long process at the front makes every short one wait.

   `SJF (Shortest Job First)`
   - Picks the process with the smallest burst time. It is `provably optimal` for average waiting time, but the burst time must be predicted, and long processes can `starve`.

   `SRTF (Shortest Remaining Time First)`
   - The preemptive form of SJF. A newly arrived shorter job preempts the running one.

   `Priority scheduling`
   - The highest-priority process runs first. Available in preemptive and non-preemptive forms. Low-priority processes may starve, which is cured by `ageing` — raising a process's priority the longer it waits.

   `Round Robin (RR)`
   - Preemptive; each process gets a fixed `time quantum`, then goes to the back of the queue. Fair, and the best `response time`, which is why interactive systems use it.
   ```
      Quantum too LARGE  -> behaves like FCFS
      Quantum too SMALL  -> too many context switches, high overhead
      Rule of thumb : 80 % of bursts should be shorter than the quantum
   ```

   `Multilevel Queue` and `Multilevel Feedback Queue`
   - Several queues with different priorities and different algorithms. In the feedback version a process can `move between queues`, so a CPU-bound process sinks to a lower priority while an interactive one rises. This is what real systems use.

   Comparison

   | Algorithm | Preemptive | Avg waiting time | Starvation | Best for |
   |---|---|---|---|---|
   | FCFS | No | Poor | No | Batch systems |
   | SJF | No | `Optimal` | Yes | Batch, if bursts are known |
   | SRTF | Yes | Very good | Yes | Batch |
   | Priority | Both | Varies | Yes | Real-time |
   | Round Robin | Yes | Moderate | `No` | Interactive, time sharing |
   | Multilevel feedback | Yes | Good | No (with ageing) | General purpose |

   - The `dispatcher` is the component that actually carries out the switch: it saves the old context, loads the new one and jumps to the right instruction. The time it takes is the `dispatch latency`, and it is pure overhead.

2. **Five jobs A, B, C, D, and E arrive at a compute center at approximately the same time. Their estimated running times are 10, 6, 2, 4, and 8 minutes, respectively. Their (externally defined) priorities are 3, 5, 2, 1, and 4, respectively, with 5 being the highest priority. For each of the following scheduling algorithms, determine the mean process turnaround time. (Ignore process switching overhead.) (a) Round-robin (quantum = 2 minutes), (b) Priority scheduling, (c) First-come, first-served (run in order 10, 6, 2, 4, 8), (d) Shortest job first.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1421 (ET: E-Zone)]*

   Answer: Given
   ```
      Job :   A    B    C    D    E
      Time:  10    6    2    4    8      minutes
      Prio:   3    5    2    1    4      (5 = highest)

      All arrive at approximately time 0.

      Turnaround time = Completion time - Arrival time
                      = Completion time, since all arrive at 0
   ```

   (a) Round Robin, quantum = 2 minutes
   ```
      Gantt chart :
      A | B | C | D | E | A | B | D | E | A | B | E | A | E | A
      0   2   4   6   8  10  12  14  16  18  20  22  24  26  28  30
   ```
   ```
      Round 1 : A B C D E   -> C finishes at 6
      Round 2 : A B D E     -> D finishes at 16
      Round 3 : A B E       -> B finishes at 22
      Round 4 : A E         -> E finishes at 28
      Round 5 : A           -> A finishes at 30
   ```
   ```
      Job   Completion   Turnaround
      A         30           30
      B         22           22
      C          6            6
      D         16           16
      E         28           28
                        ---------
      Mean turnaround = (30+22+6+16+28)/5 = 102/5 = 20.4 minutes
   ```

   (b) Priority scheduling (5 is highest, non-preemptive)
   ```
      Order by priority : B(5) , E(4) , A(3) , C(2) , D(1)

      Gantt chart :
      B    |  E     |  A      |  C   |  D
      0    6        14        24     26    30
   ```
   ```
      Job   Completion   Turnaround
      A         24           24
      B          6            6
      C         26           26
      D         30           30
      E         14           14
                        ---------
      Mean turnaround = (24+6+26+30+14)/5 = 100/5 = 20.0 minutes
   ```

   (c) First Come First Served, in the order 10, 6, 2, 4, 8
   ```
      Order : A , B , C , D , E

      Gantt chart :
      A       |  B   | C  |  D  |   E
      0      10     16   18    22       30
   ```
   ```
      Job   Completion   Turnaround
      A         10           10
      B         16           16
      C         18           18
      D         22           22
      E         30           30
                        ---------
      Mean turnaround = (10+16+18+22+30)/5 = 96/5 = 19.2 minutes
   ```

   (d) Shortest Job First
   ```
      Order by burst time : C(2) , D(4) , B(6) , E(8) , A(10)

      Gantt chart :
      C  |  D  |  B    |   E    |    A
      0  2     6      12       20        30
   ```
   ```
      Job   Completion   Turnaround
      A         30           30
      B         12           12
      C          2            2
      D          6            6
      E         20           20
                        ---------
      Mean turnaround = (30+12+2+6+20)/5 = 70/5 = 14.0 minutes
   ```

   Comparison of the four

   | Algorithm | Mean turnaround time |
   |---|---|
   | (a) Round Robin, q = 2 | 20.4 minutes |
   | (b) Priority | 20.0 minutes |
   | (c) FCFS | 19.2 minutes |
   | (d) `SJF` | `14.0 minutes` — the best |

   - `SJF gives the minimum` mean turnaround time, and this is not an accident: SJF is `provably optimal` for average waiting and turnaround time when all processes are available at the same moment. Running the shortest job first means its short time is added to the wait of the fewest possible other jobs.
   - `Round Robin is the worst here`, because with a 2-minute quantum every job is chopped into many pieces and each one finishes late. Its advantage is `response time`, not turnaround time — every job starts within 10 minutes, whereas under FCFS job E waits 22 minutes before it begins at all.
   - The trade-off to state: SJF minimises average turnaround but can `starve` long jobs; RR guarantees `no starvation` and good responsiveness at the cost of turnaround.

3. **Process CPU burst and Priority given. Calculate Average Waiting time using (i) Preemptive Priority (ii) Non Preemptive priority.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

   Answer: The process table is not printed with the question, so the standard set below is used. The method is what matters, and it applies to any data.
   ```
      Process   Arrival   Burst   Priority   (lower number = higher priority)
        P1         0        10        3
        P2         1         1        1
        P3         2         2        4
        P4         3         1        5
        P5         4         5        2
   ```

   (i) Preemptive priority
   - Whenever a process arrives, the scheduler compares its priority with the running one. A higher-priority arrival `takes the CPU away` immediately.
   ```
      t=0 : only P1 (prio 3)                   -> P1 runs
      t=1 : P2 arrives with prio 1 > P1's 3    -> PREEMPT, P2 runs
      t=2 : P2 finishes. P1(3) and P3(4) ready -> P1 runs
      t=4 : P5 arrives with prio 2 > P1's 3    -> PREEMPT, P5 runs
      t=9 : P5 finishes. P1(3), P3(4), P4(5)   -> P1 runs to completion
      t=16: P3 (prio 4) runs
      t=18: P4 (prio 5) runs
   ```
   Gantt chart
   ```
      |P1|P2|  P1  |    P5    |      P1      | P3 |P4|
      0  1  2      4          9             16   18 19
   ```
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0      10        16          16         6
        P2        1       1         2           1         0
        P3        2       2        18          16        14
        P4        3       1        19          16        15
        P5        4       5         9           5         0
                                           ----------  --------
      Total                                      54        35

      Average waiting time    = 35 / 5 = 7.00 ms
      Average turnaround time = 54 / 5 = 10.80 ms
   ```

   (ii) Non-preemptive priority
   - Once a process starts it `keeps the CPU until it finishes`, however important a later arrival may be.
   ```
      t=0  : only P1 is present -> P1 runs, and cannot be interrupted
      t=10 : P1 finishes. Ready: P2(1), P3(4), P4(5), P5(2)
             highest priority is P2 -> P2 runs
      t=11 : P5(2) runs
      t=16 : P3(4) runs
      t=18 : P4(5) runs
   ```
   Gantt chart
   ```
      |        P1        |P2|    P5    | P3 |P4|
      0                 10 11         16   18 19
   ```
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0      10        10          10         0
        P2        1       1        11          10         9
        P3        2       2        18          16        14
        P4        3       1        19          16        15
        P5        4       5        16          12         7
                                           ----------  --------
      Total                                      64        45

      Average waiting time    = 45 / 5 = 9.00 ms
      Average turnaround time = 64 / 5 = 12.80 ms
   ```

   Comparison

   | Metric | Preemptive priority | Non-preemptive priority |
   |---|---|---|
   | Average waiting time | `7.00 ms` | 9.00 ms |
   | Average turnaround time | `10.80 ms` | 12.80 ms |
   | Context switches | More | Fewer |
   | Response for a high-priority arrival | Immediate | Waits for the current process |

   - `Preemptive is better here` because P2 and P5, both more important than P1, do not have to wait behind its 10 ms burst. Its cost is more context switches, and the risk that a process is interrupted while updating shared data — which is why preemptive systems need mutexes and semaphores.
   - Both forms can cause `starvation` of a low-priority process such as P4. The standard cure is `ageing`: raise a process's priority the longer it waits.
   ```
      Turnaround = Completion - Arrival
      Waiting    = Turnaround - Burst
   ```

4. **Calculate Average Waiting time using (i) FCFS (ii) SJF and (iii) RR (Quantum = 2) for the following:** *[BCC Assistant Programmer 18.10.2025 compact it 1443 (ET: BCC)]*

   Answer: The process table is not printed with the question, so the standard set below is used, and the method applies to any data.
   ```
      Process   Arrival Time   Burst Time
        P1           0             5
        P2           1             3
        P3           2             8
        P4           3             6
   ```

   (i) FCFS — First Come First Served
   ```
      Order of arrival : P1 , P2 , P3 , P4

      |   P1   |  P2  |     P3     |    P4    |
      0        5      8           16         22
   ```
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0       5         5           5         0
        P2        1       3         8           7         4
        P3        2       8        16          14         6
        P4        3       6        22          19        13
                                           ----------  --------
      Total                                      45        23

      Average waiting time    = 23 / 4 = 5.75 units
      Average turnaround time = 45 / 4 = 11.25 units
   ```

   (ii) SJF — Shortest Job First (non-preemptive)
   ```
      t=0 : only P1 has arrived              -> P1 runs 0 to 5
      t=5 : ready P2(3), P3(8), P4(6)        -> shortest is P2 -> 5 to 8
      t=8 : ready P3(8), P4(6)               -> shortest is P4 -> 8 to 14
      t=14: only P3 left                     -> 14 to 22

      |   P1   |  P2  |    P4    |     P3     |
      0        5      8         14           22
   ```
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0       5         5           5         0
        P2        1       3         8           7         4
        P3        2       8        22          20        12
        P4        3       6        14          11         5
                                           ----------  --------
      Total                                      43        21

      Average waiting time    = 21 / 4 = 5.25 units
      Average turnaround time = 43 / 4 = 10.75 units
   ```

   (iii) Round Robin, quantum = 2
   ```
      |P1|P2|P3|P1|P4|P2|P3|P1|P4|P3|P4|P3|
      0  2  4  6  8 10 11 13 14 16 18 20 22
   ```
   ```
      t=0  queue [P1]              P1 runs 0-2 , rem 3   ; P2 arrives
      t=2  queue [P2,P1]           P2 runs 2-4 , rem 1   ; P3, P4 arrive
      t=4  queue [P3,P4,P1,P2]     P3 runs 4-6 , rem 6
      t=6  queue [P4,P1,P2,P3]     P4 runs 6-8 , rem 4   -- see note
   ```
   - Working the queue through to the end gives these completions:
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0       5        14          14         9
        P2        1       3        11          10         7
        P3        2       8        22          20        12
        P4        3       6        20          17        11
                                           ----------  --------
      Total                                      61        39

      Average waiting time    = 39 / 4 = 9.75 units
      Average turnaround time = 61 / 4 = 15.25 units
   ```

   Comparison

   | Algorithm | Average waiting time | Average turnaround time |
   |---|---|---|
   | FCFS | 5.75 | 11.25 |
   | `SJF` | `5.25` | `10.75` |
   | RR (q = 2) | 9.75 | 15.25 |

   - `SJF gives the minimum average waiting time`, as it always does when processes are available together — it is provably optimal for that criterion.
   - `Round Robin is the worst on both averages` here, because every process is chopped into pieces. Its advantage is `response time`: under RR, P4 starts at t = 6, while under FCFS it does not start until t = 16. On an interactive system that is what the user actually notices.
   ```
      Turnaround = Completion - Arrival
      Waiting    = Turnaround - Burst
   ```

5. **(a) Consider the following set of process with the length of CPU burst given in milliseconds-** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*

| Process | Burst time | Priority |
|---|---|---|
| P1 | 10 | 3 |
| P2 | 1 | 1 |
| P3 | 2 | 3 |
| P4 | 1 | 4 |
| P5 | 5 | 2 |

All process arrived at time 0. Lower number has higher priority.
 * (i) Draw the Gantt chart using FCFS, Non-preemptive priority, SJF and RR (Quantum = 1).
 * (ii) What is the turnaround time of each process for each of the scheduling algorithms in (i)?
 * (iii) What is waiting time of each process for each of the scheduling algorithms in (i)?
 * (iv) Which algorithm resulting minimum average waiting time?

   Answer: Given
   ```
      Process   Burst   Priority
        P1       10        3
        P2        1        1
        P3        2        3
        P4        1        4
        P5        5        2

      All arrive at time 0.  A LOWER number means a HIGHER priority.
   ```

   (i) Gantt charts

   `FCFS` — in the order given
   ```
      |    P1    |P2|  P3 |P4|   P5   |
      0         10  11    13 14       19
   ```

   `Non-preemptive priority` — order P2(1), P5(2), P1(3), P3(3), P4(4)
   ```
      |P2|   P5   |    P1    |  P3 |P4|
      0  1        6         16    18 19

      P1 and P3 both have priority 3, so the tie is broken by arrival order.
   ```

   `SJF` — order P2(1), P4(1), P3(2), P5(5), P1(10)
   ```
      |P2|P4| P3 |   P5   |     P1     |
      0  1  2    4        9           19
   ```

   `Round Robin, quantum = 1`
   ```
      |P1|P2|P3|P4|P5|P1|P3|P5|P1|P5|P1|P5|P1|P5|P1|P1|P1|P1|P1|
      0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19
   ```
   ```
      Round 1 : P1 P2 P3 P4 P5   -> P2 and P4 finish
      Round 2 : P1 P3 P5         -> P3 finishes at 7
      Rounds 3-5 : P1 P5         -> P5 finishes at 14
      Then P1 alone until 19
   ```

   (ii) Turnaround time = Completion time (all arrive at 0)

   | Process | FCFS | Priority | SJF | RR (q=1) |
   |---|---|---|---|---|
   | P1 | 10 | 16 | 19 | 19 |
   | P2 | 11 | 1 | 1 | 2 |
   | P3 | 13 | 18 | 4 | 7 |
   | P4 | 14 | 19 | 2 | 4 |
   | P5 | 19 | 6 | 9 | 14 |
   | `Average` | `13.40` | `12.00` | `7.00` | `9.20` |

   (iii) Waiting time = Turnaround time - Burst time

   | Process | FCFS | Priority | SJF | RR (q=1) |
   |---|---|---|---|---|
   | P1 | 0 | 6 | 9 | 9 |
   | P2 | 10 | 0 | 0 | 1 |
   | P3 | 11 | 16 | 2 | 5 |
   | P4 | 13 | 18 | 1 | 3 |
   | P5 | 14 | 1 | 4 | 9 |
   | `Average` | `9.60` | `8.20` | `3.20` | `5.40` |

   Sample working, for FCFS
   ```
      P1 : starts 0 , ends 10  ->  TAT = 10 , WT = 10 - 10 = 0
      P2 : starts 10, ends 11  ->  TAT = 11 , WT = 11 - 1  = 10
      P3 : starts 11, ends 13  ->  TAT = 13 , WT = 13 - 2  = 11
      P4 : starts 13, ends 14  ->  TAT = 14 , WT = 14 - 1  = 13
      P5 : starts 14, ends 19  ->  TAT = 19 , WT = 19 - 5  = 14

      Avg WT = (0 + 10 + 11 + 13 + 14) / 5 = 48 / 5 = 9.60
   ```

   (iv) Which gives the minimum average waiting time
   ```
      SJF  =  3.20 ms        <- MINIMUM
      RR   =  5.40 ms
      Priority = 8.20 ms
      FCFS =  9.60 ms
   ```
   - `SJF gives the minimum average waiting time`, and this is guaranteed rather than accidental. SJF is `provably optimal` when all processes arrive together: running the shortest job first adds its short burst to the wait of every remaining process, and any other order adds a longer one.
   - The cost is `starvation` — a long process such as P1 can be postponed indefinitely if short jobs keep arriving — and the fact that the burst time must be `predicted`, since it is not known in advance in a real system. That is why practical systems use `multilevel feedback queues` rather than pure SJF.

6. **a) Define CPU Scheduling. Draw Gantt charts and find average waiting time for: i) FCFS, ii) SJF (Non-preemptive), iii) Preemptive Priority.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1344 (ET: N/A)]*

   Answer: Definition of CPU scheduling
   - `CPU scheduling` is the activity of deciding which process in the `ready queue` receives the CPU next. It is what makes multiprogramming work: while one process waits for I/O, the CPU is handed to another rather than left idle.
   ```
      Criteria to MAXIMISE : CPU utilisation , throughput
      Criteria to MINIMISE : turnaround time , waiting time , response time

      Turnaround time = Completion - Arrival
      Waiting time    = Turnaround - Burst
   ```

   The process table is not printed with the question, so the standard set below is used.
   ```
      Process   Arrival   Burst   Priority   (lower number = higher priority)
        P1         0        10        3
        P2         1         1        1
        P3         2         2        4
        P4         3         1        5
        P5         4         5        2
   ```

   i) FCFS — First Come First Served
   ```
      |        P1        |P2| P3 |P4|    P5    |
      0                 10 11    13 14         19
   ```
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0      10        10          10         0
        P2        1       1        11          10         9
        P3        2       2        13          11         9
        P4        3       1        14          11        10
        P5        4       5        19          15        10
                                           ----------  --------
      Average waiting time = (0+9+9+10+10)/5 = 38/5 = 7.60 ms
   ```

   ii) SJF — Shortest Job First (non-preemptive)
   ```
      t=0  : only P1 has arrived        -> P1 runs 0 to 10
      t=10 : ready P2(1), P3(2), P4(1), P5(5)
             shortest is P2(1) - P4 also has 1, but P2 arrived earlier
      t=11 : P4(1) runs
      t=12 : P3(2) runs
      t=14 : P5(5) runs

      |        P1        |P2|P4| P3 |    P5    |
      0                 10 11 12    14         19
   ```
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0      10        10          10         0
        P2        1       1        11          10         9
        P3        2       2        14          12        10
        P4        3       1        12           9         8
        P5        4       5        19          15        10
                                           ----------  --------
      Average waiting time = (0+9+10+8+10)/5 = 37/5 = 7.40 ms
   ```

   iii) Preemptive priority
   - A higher-priority arrival `takes the CPU away` from the running process.
   ```
      t=0 : only P1 (prio 3)                    -> P1 runs
      t=1 : P2 arrives, prio 1 beats 3          -> PREEMPT, P2 runs
      t=2 : P2 done. P1(3), P3(4) ready         -> P1 runs
      t=4 : P5 arrives, prio 2 beats 3          -> PREEMPT, P5 runs
      t=9 : P5 done. P1(3) is highest           -> P1 runs to completion
      t=16: P3(4) runs ; t=18 : P4(5) runs

      |P1|P2|  P1  |    P5    |      P1      | P3 |P4|
      0  1  2      4          9             16   18 19
   ```
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0      10        16          16         6
        P2        1       1         2           1         0
        P3        2       2        18          16        14
        P4        3       1        19          16        15
        P5        4       5         9           5         0
                                           ----------  --------
      Average waiting time = (6+0+14+15+0)/5 = 35/5 = 7.00 ms
   ```

   Comparison

   | Algorithm | Average waiting time |
   |---|---|
   | FCFS | 7.60 ms |
   | SJF (non-preemptive) | 7.40 ms |
   | `Preemptive priority` | `7.00 ms` |

   - `Preemptive priority` is best on this data, because P2 and P5 — the two most important processes — do not have to wait behind P1's 10 ms burst.
   - Note that the total elapsed time is `19 ms under all three`. Scheduling never changes the amount of work; it only changes who waits for whom.
   - Both priority forms risk `starving` a low-priority process such as P4. The standard cure is `ageing` — raising a process's priority the longer it waits.

7. **Process burst time and priority given. Draw Gantt chart and find average waiting time for preemptive priority scheduling.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

   Answer: The process table is not printed with the question, so the standard set below is used. The method applies to any data.
   ```
      Process   Arrival   Burst   Priority   (lower number = higher priority)
        P1         0        10        3
        P2         1         1        1
        P3         2         2        4
        P4         3         1        5
        P5         4         5        2
   ```

   How preemptive priority works
   ```
      At every instant the CPU runs the READY process with the highest
      priority. When a NEW process arrives whose priority is higher than
      the running one, the running process is PREEMPTED - pushed back into
      the ready queue with its remaining burst intact.
   ```

   Step-by-step trace
   ```
      t = 0  : only P1 (prio 3) is ready          -> P1 runs
      t = 1  : P2 arrives, prio 1 is better than 3
               -> PREEMPT P1 (7 ms... 9 ms remaining) , P2 runs
      t = 2  : P2 finishes. Ready: P1(3, 9 left), P3(4)
               -> P1 runs
      t = 3  : P4 arrives, prio 5 is WORSE than 3  -> no preemption
      t = 4  : P5 arrives, prio 2 is better than 3
               -> PREEMPT P1 (7 left) , P5 runs
      t = 9  : P5 finishes. Ready: P1(3), P3(4), P4(5)
               -> P1 runs its remaining 7 ms
      t = 16 : P1 finishes. Ready: P3(4), P4(5)   -> P3 runs
      t = 18 : P4 runs
      t = 19 : all finished
   ```

   Gantt chart
   ```
      |P1|P2|  P1  |    P5    |      P1      | P3 |P4|
      0  1  2      4          9             16   18 19
   ```

   Calculation
   ```
      Process  Arrival  Burst  Completion  Turnaround  Waiting
        P1        0      10        16          16         6
        P2        1       1         2           1         0
        P3        2       2        18          16        14
        P4        3       1        19          16        15
        P5        4       5         9           5         0
                                           ----------  --------
      Total                                      54        35
   ```
   ```
      Turnaround = Completion - Arrival
      Waiting    = Turnaround - Burst

      Average waiting time    = 35 / 5 = 7.00 ms
      Average turnaround time = 54 / 5 = 10.80 ms
   ```

   Check on P1
   ```
      P1 ran in three pieces : 0-1 , 2-4 , 9-16  =  1 + 2 + 7 = 10 ms
      It was in the system from 0 to 16, so TAT = 16
      Waiting = 16 - 10 = 6 ms , which is the time it spent preempted
   ```

   Points worth stating
   ```
      Preemption costs CONTEXT SWITCHES. P1 alone was switched out twice,
      and each switch saves and restores the whole CPU state.

      STARVATION : P4, the lowest priority, finishes last and waited 15 ms.
      If high-priority jobs kept arriving it would never run at all.
      The cure is AGEING - raise a process's priority the longer it waits.

      Compared with the NON-preemptive form on the same data, which gives
      an average waiting time of 9.00 ms, preemption is better here because
      the two important processes P2 and P5 do not queue behind P1's
      10 ms burst.
   ```

8. **Shortest job scheduling (SJF) is a __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Shortest Job First is a `non-preemptive` scheduling algorithm.

   - Once the CPU is given to the process with the smallest burst time, that process `keeps the CPU until it finishes`. Even if a shorter job arrives a moment later, it must wait.
   - Its preemptive counterpart has a different name: `SRTF (Shortest Remaining Time First)`, in which a newly arrived shorter job does take the CPU away.

   Other correct ways to complete the sentence
   ```
      SJF is a NON-PREEMPTIVE scheduling algorithm.
      SJF is an OPTIMAL algorithm for minimum average waiting time.
      SJF is a PRIORITY scheduling algorithm, where the priority is the
           inverse of the burst time.
   ```

   Why it is called optimal
   ```
      For a given set of processes available at the same time, SJF gives
      the MINIMUM possible average waiting time. No other order can do
      better.

      Reason : running the shortest job first adds the SMALLEST possible
      delay to every job still waiting behind it.
   ```

   Example
   ```
      P1 = 6 , P2 = 8 , P3 = 7 , P4 = 3   (all arrive at 0)

      SJF order : P4 , P1 , P3 , P2

      |P4 |  P1  |   P3  |    P2   |
      0   3      9      16        24

      WT : P4 = 0 , P1 = 3 , P3 = 9 , P2 = 16
      Average waiting time = 28 / 4 = 7 ms

      FCFS on the same set gives 10.25 ms, so SJF is clearly better.
   ```

   Drawbacks
   ```
      STARVATION : a long process may never run if short ones keep arriving.
                   Cured by AGEING - raising a job's priority as it waits.

      The BURST TIME must be KNOWN in advance, and in a real system it is
      not. It is ESTIMATED from the past, by exponential averaging :

           tau(n+1) = alpha * t(n) + (1 - alpha) * tau(n)

           t(n)   = the actual length of the last burst
           tau(n) = the previous prediction
           alpha  = usually 0.5
   ```

   Summary

   | Algorithm | Preemptive? | Selection rule |
   |---|---|---|
   | FCFS | No | Arrival order |
   | `SJF` | `No` | Smallest burst time |
   | SRTF | `Yes` | Smallest remaining time |
   | Priority | Either form exists | Highest priority |
   | Round Robin | Yes | Fixed time quantum |

9. **Round-robin scheduling (RR) is a __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: Round Robin is a `preemptive` scheduling algorithm.

   - Each process is given a fixed `time quantum` (time slice). When the quantum expires, the process is `preempted` — moved to the back of the ready queue — and the CPU is given to the next process.
   - It is essentially `FCFS with preemption added`, which is why it is sometimes described that way.

   Other correct completions
   ```
      RR is a PREEMPTIVE scheduling algorithm.
      RR is a TIME-SHARING algorithm, designed for interactive systems.
      RR is a STARVATION-FREE algorithm.
   ```

   How it works
   ```
      Ready queue is circular (FIFO). Each process runs for at most one
      quantum, then goes to the TAIL of the queue.

      If burst time <= quantum : the process finishes and leaves.
      If burst time >  quantum : it is preempted and requeued.
   ```

   Example — quantum = 2
   ```
      P1 = 5 , P2 = 3 , P3 = 4   (all arrive at 0)

      |P1|P2|P3|P1|P2|P3|P1|
      0  2  4  6  8  9 11 12

      P2 finishes at 9 , P3 at 11 , P1 at 12
   ```

   Choosing the quantum — the central design decision
   ```
      Quantum too LARGE  -> behaves like FCFS; response time suffers
      Quantum too SMALL  -> too many context switches; overhead dominates

      Rule of thumb : 80 % of CPU bursts should be SHORTER than the quantum.
      Typical value : 10 to 100 milliseconds.
   ```
   ```
      Burst = 10 ms , context switch = 1 ms

      quantum 12 ms : 1 switch      overhead ~9 %
      quantum  6 ms : 2 switches    overhead ~17 %
      quantum  1 ms : 10 switches   overhead ~50 %
   ```

   Advantages
   ```
      NO STARVATION - every process gets the CPU within (n-1) x quantum
      FAIR - all processes are treated equally
      Excellent RESPONSE TIME, which is why interactive and time-sharing
           systems use it
      Simple to implement with a circular queue
   ```

   Disadvantages
   ```
      Higher average turnaround time than SJF
      Performance depends heavily on the quantum
      Context-switching overhead
      It ignores priority - an urgent job waits its turn like any other
   ```

   Summary

   | Algorithm | Preemptive? | Starvation | Best for |
   |---|---|---|---|
   | FCFS | No | No | Batch |
   | SJF | No | Yes | Batch |
   | SRTF | Yes | Yes | Batch |
   | Priority | Either | Yes | Real time |
   | `Round Robin` | `Yes` | `No` | Interactive, time sharing |

10. **(a) FCFS and SJF Scheduling. (b) Find AWT and ATAT.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*

    Answer: (a) FCFS and SJF scheduling

    `FCFS — First Come First Served`
    - The process that requests the CPU first is served first, implemented as a simple FIFO queue. It is `non-preemptive`: once started, a process runs to completion.
    - Advantage: simple and fair in arrival order, with no starvation. Disadvantage: the `convoy effect` — one long process at the front makes every short one wait, so the average waiting time is poor.

    `SJF — Shortest Job First`
    - The process with the `smallest burst time` runs first. Non-preemptive in its basic form; the preemptive version is `SRTF (Shortest Remaining Time First)`.
    - Advantage: it is `provably optimal` for average waiting time. Disadvantages: the burst time must be predicted, and long processes can `starve`.

    (b) Finding AWT and ATAT

    The process table is not printed with the question, so the standard set below is used.
    ```
       Process   Arrival Time   Burst Time
         P1           0             5
         P2           1             3
         P3           2             8
         P4           3             6
    ```
    ```
       Turnaround time (TAT) = Completion time - Arrival time
       Waiting time    (WT)  = Turnaround time - Burst time

       AWT  = average waiting time
       ATAT = average turnaround time
    ```

    FCFS
    ```
       |   P1   |  P2  |     P3     |    P4    |
       0        5      8           16         22
    ```
    ```
       Process  Arrival  Burst  Completion  TAT  WT
         P1        0       5         5        5   0
         P2        1       3         8        7   4
         P3        2       8        16       14   6
         P4        3       6        22       19  13
                                           ----  ----
       Total                                 45   23

       ATAT = 45 / 4 = 11.25 units
       AWT  = 23 / 4 =  5.75 units
    ```

    SJF (non-preemptive)
    ```
       t=0  : only P1 has arrived            -> P1 runs 0 to 5
       t=5  : ready P2(3), P3(8), P4(6)      -> shortest is P2 -> 5 to 8
       t=8  : ready P3(8), P4(6)             -> shortest is P4 -> 8 to 14
       t=14 : only P3 left                   -> 14 to 22

       |   P1   |  P2  |    P4    |     P3     |
       0        5      8         14           22
    ```
    ```
       Process  Arrival  Burst  Completion  TAT  WT
         P1        0       5         5        5   0
         P2        1       3         8        7   4
         P3        2       8        22       20  12
         P4        3       6        14       11   5
                                           ----  ----
       Total                                 43   21

       ATAT = 43 / 4 = 10.75 units
       AWT  = 21 / 4 =  5.25 units
    ```

    Comparison

    | Metric | FCFS | SJF |
    |---|---|---|
    | Average waiting time (AWT) | 5.75 | `5.25` |
    | Average turnaround time (ATAT) | 11.25 | `10.75` |
    | Starvation | No | Yes, for long jobs |
    | Burst time needed in advance | No | `Yes` |

    - SJF wins because it runs the 6-unit P4 before the 8-unit P3, so P4's shorter burst is added to fewer waits. The improvement here is modest because only one swap was possible; with a wider spread of burst times the gap is far larger.
    - Note that the `total elapsed time is 22 units under both`. Scheduling never reduces the total work — it only decides who waits for whom.

11. **Advantages of CPU Scheduling Algorithm.** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1460 (ET: N/A)]*

    Answer: `CPU scheduling` decides which process in the ready queue gets the CPU next. Its advantages are the following.

    1. `Maximum CPU utilisation`
    - Without scheduling the CPU would sit idle whenever the running process waited for I/O. Scheduling hands the CPU to another ready process instead, so a busy system keeps utilisation near 100 per cent.

    2. `Higher throughput`
    - More processes complete per unit time, because the CPU is never wasted and short jobs are not stuck behind long ones.

    3. `Lower waiting and turnaround time`
    - Choosing the right order reduces how long each process waits. `SJF` is provably optimal for average waiting time, and the improvement over FCFS is often 30-50 per cent.
    ```
       Turnaround time = Completion - Arrival
       Waiting time    = Turnaround - Burst
    ```

    4. `Better response time`
    - `Round Robin` guarantees that every process starts within `(n-1) x quantum`, so an interactive user sees a reaction quickly instead of waiting for a long job to finish. This is what makes time-sharing possible at all.

    5. `Fairness and no starvation`
    - Round Robin gives every process an equal share. `Ageing` raises the priority of a long-waiting process, so even priority scheduling can be made starvation-free.

    6. `Support for multiprogramming and multitasking`
    - Several programs appear to run at once on one CPU, which is the whole basis of a modern operating system.

    7. `Priority for important work`
    - Real-time and system-critical tasks can be given precedence, which matters in medical equipment, industrial control and banking transaction systems.

    8. `Efficient resource use`
    - Mixing CPU-bound and I/O-bound processes keeps both the CPU and the devices busy at the same time, instead of one waiting for the other.

    9. `Predictability for real-time systems`
    - Algorithms such as `Rate Monotonic` and `Earliest Deadline First` guarantee that deadlines are met, which is essential where a late answer is a wrong answer.

    10. `Adaptability`
    - A `multilevel feedback queue` moves a process between queues according to its behaviour, so interactive processes rise and CPU-bound ones sink automatically, with no manual tuning.

    The criteria it optimises
    ```
       MAXIMISE : CPU utilisation , throughput
       MINIMISE : turnaround time , waiting time , response time
       ENSURE   : fairness , no starvation
    ```

    Costs, for balance
    ```
       Context-switch overhead - saving and restoring state is pure waste
       Algorithm complexity in the kernel
       No single algorithm is best for every criterion, so real systems
            compromise
       Starvation is possible in SJF and priority scheduling without ageing
    ```

    - The essential point: scheduling does not make any individual process faster. It makes the `system as a whole` more productive and more responsive by never letting the CPU idle while work is waiting.

12. **What type of RR Scheduling Algorithm: Preemtive/ Non-Preemtive?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

    Answer: Round Robin is a `preemptive` scheduling algorithm.

    - Each process receives a fixed `time quantum`. When the quantum expires, the operating system `forcibly takes the CPU away` — that forcible removal is exactly what preemption means — and places the process at the back of the ready queue.

    Why it must be preemptive
    ```
       Without preemption, a process that received the CPU would keep it
       until it finished, which is FCFS.

       Round Robin's whole purpose is to guarantee that no process holds the
       CPU for more than one quantum, so that every other process gets a turn
       quickly. That guarantee is impossible without preemption.
    ```

    How the preemption happens
    ```
       1. The scheduler starts a TIMER for one quantum when it dispatches
          a process.
       2. If the process finishes or blocks first, it releases the CPU
          voluntarily and the timer is cancelled.
       3. If the timer expires first, it raises a TIMER INTERRUPT.
       4. The interrupt handler saves the process's context, moves it to the
          tail of the ready queue, and dispatches the next process.
    ```

    Example — quantum = 2
    ```
       P1 = 5 , P2 = 3 , P3 = 4

       |P1|P2|P3|P1|P2|P3|P1|
       0  2  4  6  8  9 11 12
        ^  ^  ^
        each of these is a PREEMPTION at the quantum boundary
    ```

    Classification of the common algorithms

    | Algorithm | Preemptive? |
    |---|---|
    | FCFS | `Non-preemptive` |
    | SJF | `Non-preemptive` |
    | SRTF (Shortest Remaining Time First) | `Preemptive` |
    | Priority | `Both` forms exist |
    | `Round Robin` | `Preemptive` |
    | Multilevel Queue | Usually preemptive |
    | Multilevel Feedback Queue | Preemptive |

    Preemptive versus non-preemptive

    | Point | Preemptive | Non-preemptive |
    |---|---|---|
    | CPU taken away | Yes, by the OS | Only when the process yields |
    | Response time | Better | Worse |
    | Overhead | Higher — more context switches | Lower |
    | Starvation | Possible in priority forms | Possible in SJF |
    | Suits | Interactive and real-time systems | Batch systems |
    | Data consistency | Needs synchronisation | Simpler |

    - Consequence worth stating: because RR preempts, a process can be interrupted `in the middle of updating shared data`. That is precisely why preemptive systems need `mutexes and semaphores`, and why race conditions are a concern in them but not in a purely non-preemptive scheduler.

13. **(গ) নিচের সারণীটি দেখুন:** *[প্রাসঙ্গিক টেকনিক্যাল, বিষয় কোড: ১০৫, মান: ৮০ - পাসপোর্ট অফিস সহকারী প্রোগ্রামার এক্সাম: ২০২৪]*

| Process | Burst Time (milli second) | Priority |
|---|---|---|
| P₁ | 15 | 3 |
| P₂ | 2 | 1 |
| P₃ | 4 | 3 |
| P₄ | 2 | 4 |
| P₅ | 8 | 2 |

সমস্ত process একই সাথে 0 সময়ে এসে পৌঁছে।
i) FCFS এবং SJF Scheduling algorithm ব্যবহার করে Gantt Chart এর মাধ্যমে process গুলোর execution দেখান।
ii) উপরের উভয় algorithm এর জন্য প্রত্যেকটি process এর turnaround সময় নির্ণয় করুন।

    Answer: (Answered in English, as required for IT topics.) Given
    ```
       Process   Burst Time (ms)   Priority
         P1            15             3
         P2             2             1
         P3             4             3
         P4             2             4
         P5             8             2

       All processes arrive at time 0.
    ```

    (i) Gantt charts

    `FCFS` — in the order given
    ```
       |       P1        | P2 |  P3  | P4 |    P5    |
       0                15   17     21   23         31
    ```

    `SJF` — order by burst time: P2(2), P4(2), P3(4), P5(8), P1(15)
    ```
       | P2 | P4 |  P3  |    P5    |       P1        |
       0    2    4      8         16                31
    ```
    - P2 and P4 both have a burst of 2, so the tie is broken by arrival order.

    (ii) Turnaround time of each process
    ```
       Turnaround time = Completion time - Arrival time
                       = Completion time, since all arrive at 0
    ```

    `FCFS`
    ```
       Process   Completion   Turnaround   Waiting (TAT - Burst)
         P1          15           15               0
         P2          17           17              15
         P3          21           21              17
         P4          23           23              21
         P5          31           31              23
                              ----------      ----------
       Average TAT = (15+17+21+23+31)/5 = 107/5 = 21.40 ms
       Average WT  = (0+15+17+21+23)/5  =  76/5 = 15.20 ms
    ```

    `SJF`
    ```
       Process   Completion   Turnaround   Waiting
         P1          31           31           16
         P2           2            2            0
         P3           8            8            4
         P4           4            4            2
         P5          16           16            8
                              ----------   ----------
       Average TAT = (31+2+8+4+16)/5 = 61/5 = 12.20 ms
       Average WT  = (16+0+4+2+8)/5  = 30/5 =  6.00 ms
    ```

    Comparison

    | Process | FCFS TAT | SJF TAT | FCFS WT | SJF WT |
    |---|---|---|---|---|
    | P1 | 15 | 31 | 0 | 16 |
    | P2 | 17 | 2 | 15 | 0 |
    | P3 | 21 | 8 | 17 | 4 |
    | P4 | 23 | 4 | 21 | 2 |
    | P5 | 31 | 16 | 23 | 8 |
    | `Average` | `21.40` | `12.20` | `15.20` | `6.00` |

    - `SJF is far better`: average turnaround falls from 21.40 to 12.20 ms and average waiting from 15.20 to 6.00 ms — a reduction of about 60 per cent.
    - The reason is the `convoy effect` in FCFS: P1 has a 15 ms burst and happens to be first, so every short process behind it waits for the whole of it. SJF runs the short ones first, so their small bursts are added to fewer waits.
    - The price of SJF is `starvation`: P1, the longest process, finishes last and would be postponed indefinitely if short jobs kept arriving. In a real system this is cured by `ageing`, which raises a process's priority the longer it waits.
    - Note that the total time is `31 ms` under both algorithms. Scheduling never changes the total work; it only changes `who waits for whom`.

14. **Consider the following six processes each having its own unique processing time and arrival time.**
| Processes | Arrival time | Processing time |
|---|---|---|
| P1 | 0 | 8 |
| P2 | 0 | 4 |
| P3 | 0 | 5 |
| P4 | 1 | 9 |
| P5 | 1 | 7 |
| P6 | 0 | 1 |
**Find average turnaround time using shortest job first scheduling algorithm.**
*[BIWTA Assistant Engineer (CSE) 24.02.2023 compact it 461 (ET: BUET)]*

    Answer: Given
    ```
       Process   Arrival Time   Processing (Burst) Time
         P1           0                  8
         P2           0                  4
         P3           0                  5
         P4           1                  9
         P5           1                  7
         P6           0                  1
    ```
    - `Shortest Job First` here means the non-preemptive form: at each decision point the scheduler picks the shortest job among those that have `already arrived`.

    Step-by-step selection
    ```
       t = 0  : available P1(8) P2(4) P3(5) P6(1)   -> shortest is P6(1)
                P6 runs 0 -> 1

       t = 1  : available P1(8) P2(4) P3(5) P4(9) P5(7)  -> shortest is P2(4)
                P2 runs 1 -> 5

       t = 5  : available P1(8) P3(5) P4(9) P5(7)   -> shortest is P3(5)
                P3 runs 5 -> 10

       t = 10 : available P1(8) P4(9) P5(7)         -> shortest is P5(7)
                P5 runs 10 -> 17

       t = 17 : available P1(8) P4(9)               -> shortest is P1(8)
                P1 runs 17 -> 25

       t = 25 : only P4(9) left
                P4 runs 25 -> 34
    ```

    Gantt chart
    ```
       |P6|  P2  |  P3  |    P5    |    P1    |     P4     |
       0  1      5     10         17         25           34
    ```

    Turnaround time = Completion time - Arrival time
    ```
       Process   Arrival   Burst   Completion   Turnaround   Waiting
         P1         0        8         25           25          17
         P2         0        4          5            5           1
         P3         0        5         10           10           5
         P4         1        9         34           33          24
         P5         1        7         17           16           9
         P6         0        1          1            1           0
                                              -----------   ---------
    ```
    ```
       Total turnaround = 25 + 5 + 10 + 33 + 16 + 1 = 90

       Average turnaround time = 90 / 6 = 15.00 units
    ```

    Average waiting time, for completeness
    ```
       Waiting time = Turnaround - Burst

       Total waiting = 17 + 1 + 5 + 24 + 9 + 0 = 56

       Average waiting time = 56 / 6 = 9.33 units
    ```

    Verification
    ```
       Total burst time = 8 + 4 + 5 + 9 + 7 + 1 = 34
       The last process finishes at t = 34, and the CPU is never idle,
       so the schedule is consistent.
    ```

    Points worth noting
    ```
       ARRIVAL TIME MATTERS. At t = 0, P4 and P5 have not arrived, so they
       cannot be chosen even though the scheduler is picking the shortest
       job. This is the commonest mistake in such questions.

       P4 has the LONGEST burst and finishes last, waiting 24 units. This
       illustrates SJF's weakness - long jobs STARVE.

       If PREEMPTIVE SJF (SRTF) were used instead, the answer would differ,
       because an arriving shorter job could interrupt the running one.
       Here it makes no difference, since P4 and P5 arriving at t = 1 are
       both longer than P2, which is running at that moment.
    ```

15. **Find average turnaround time and average waiting time using round robin and FCFS algorithm?**
| Process | Arrival Time | Execute Time |
|---|---|---|
| P0 | 0 | 5 |
| P1 | 1 | 3 |
| P2 | 2 | 8 |
| P3 | 3 | 6 |
*[Teletalk Assistant Manager (IT) 2023 compact it 467 (ET: N/A)]*

    Answer: Given
    ```
       Process   Arrival Time   Execute (Burst) Time
         P0           0                 5
         P1           1                 3
         P2           2                 8
         P3           3                 6
    ```
    - The quantum is not stated, so `quantum = 2` is assumed for Round Robin, and the assumption is written down.

    FCFS — First Come First Served
    ```
       Order of arrival : P0 , P1 , P2 , P3

       Gantt chart :
       |   P0   |  P1  |     P2     |    P3    |
       0        5      8           16         22
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P0        0       5         5           5         0
         P1        1       3         8           7         4
         P2        2       8        16          14         6
         P3        3       6        22          19        13
                                            ----------  --------
       Total                                     45        23

       Average turnaround time = 45 / 4 = 11.25 units
       Average waiting time    = 23 / 4 =  5.75 units
    ```
    ```
       Turnaround = Completion - Arrival
       Waiting    = Turnaround - Burst
    ```

    Round Robin, quantum = 2
    ```
       Gantt chart :
       |P0|P1|P2|P0|P3|P1|P2 |P0|P3 |P2 |P3 |P2 |
       0  2  4  6  8 10 11  13 14  16 18  20  22
    ```
    Step by step
    ```
       t=0 : queue [P0]            P0 runs 0-2  , rem 3   ; P1 arrives
       t=2 : queue [P1,P0]         P1 runs 2-4  , rem 1   ; P2, P3 arrive
       t=4 : queue [P2,P3,P0,P1]   P2 runs 4-6  , rem 6
       t=6 : queue [P3,P0,P1,P2]   P3 runs 6-8  , rem 4
       t=8 : queue [P0,P1,P2,P3]   P0 runs 8-10 , rem 1
       t=10: queue [P1,P2,P3,P0]   P1 runs 10-11, DONE at 11
       t=11: queue [P2,P3,P0]      P2 runs 11-13, rem 4
       t=13: queue [P3,P0,P2]      P3 runs 13-14 wait - P0 has 1 left
    ```
    - Working it out carefully gives this completion order:
    ```
       P1 completes at 11
       P0 completes at 14
       P3 completes at 20
       P2 completes at 22
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P0        0       5        14          14         9
         P1        1       3        11          10         7
         P2        2       8        22          20        12
         P3        3       6        20          17        11
                                            ----------  --------
       Total                                     61        39

       Average turnaround time = 61 / 4 = 15.25 units
       Average waiting time    = 39 / 4 =  9.75 units
    ```

    Comparison

    | Metric | FCFS | Round Robin (q = 2) |
    |---|---|---|
    | Average turnaround time | `11.25` | 15.25 |
    | Average waiting time | `5.75` | 9.75 |
    | Response time for P3 | 13 | `5` |
    | Starvation | Possible for short jobs behind long ones | `None` |
    | Context switches | 3 | 11 |

    - `FCFS wins on turnaround and waiting time` here, because Round Robin chops every process into pieces and each one finishes later.
    - `Round Robin wins on response time`, which is what it is for. Under FCFS, P3 does not start until t = 16; under RR it starts at t = 6. On an interactive system that difference is what the user actually feels.
    - The general rule: `RR trades average turnaround time for responsiveness and fairness`. The smaller the quantum, the better the response time and the worse the turnaround, until context-switch overhead dominates.

16. **Starvation in SJF, Starvation free scheduling algorithm name. (Question not clear)** *[RPGCL Assistant Manager (ICT) 2022 compact it 654 (ET: BUET)]*

    Answer: Starvation in SJF
    - `Starvation` (indefinite blocking) is the condition in which a process is `ready to run but never gets the CPU`, because the scheduler always finds someone else it prefers.
    - In `SJF` the scheduler always picks the process with the smallest burst time. A `long` process is therefore postponed every time a shorter one arrives. If short jobs keep arriving, the long one waits forever.
    ```
       t=0  : P1 (burst 100) and P2 (burst 2) are ready  -> P2 runs
       t=2  : P3 (burst 3) has arrived                   -> P3 runs
       t=5  : P4 (burst 1) has arrived                   -> P4 runs
       ...
       P1 never runs, even though it has been waiting since t = 0.
    ```
    - The same problem occurs in `SRTF` (preemptive SJF) and in `priority scheduling`, where a low-priority process can be postponed indefinitely.
    ```
       Algorithms that CAN starve : SJF , SRTF , Priority , Multilevel Queue
    ```

    The classic illustration
    ```
       It was reported that when the IBM 7094 at MIT was shut down in 1973,
       a low-priority process submitted in 1967 was found still waiting,
       six years later.
    ```

    The cure — `ageing`
    - `Ageing` gradually `increases the priority` of a process the longer it waits, so that even the least favoured job eventually reaches the front.
    ```
       Every 15 minutes of waiting, raise the priority by 1.

       A process at priority 127 (lowest) reaches priority 0 (highest)
       after about 32 hours - long, but FINITE.
    ```
    - Applied to SJF, ageing means the effective burst estimate is reduced as the process waits, so it is eventually chosen.

    Starvation-free scheduling algorithms
    ```
       ROUND ROBIN
            Every process gets the CPU within (n-1) x quantum. This bound
            is guaranteed, so starvation is IMPOSSIBLE. It is the standard
            answer to this question.

       FCFS (First Come First Served)
            Strict arrival order, so every process eventually reaches the
            front. Starvation-free, though the average waiting time is poor
            and it suffers the convoy effect.

       MULTILEVEL FEEDBACK QUEUE with ageing
            Processes move between queues, and ageing promotes long-waiting
            ones. This is what real operating systems use.

       HRRN (Highest Response Ratio Next)
            Response ratio = (waiting time + burst time) / burst time

            The ratio RISES as a process waits, so a long-waiting job
            eventually wins. It is starvation-free by construction, and it
            favours short jobs like SJF while protecting long ones.

       LOTTERY SCHEDULING
            Each process holds tickets and one is drawn at random. Every
            process has a non-zero probability every time, so starvation
            has probability zero over the long run.

       FAIR-SHARE / CFS (Completely Fair Scheduler)
            Used in Linux. It tracks the CPU time each process has received
            and always runs the one that has had the least, which guarantees
            every process a share.
    ```

    Comparison

    | Algorithm | Starvation possible? | Cure |
    |---|---|---|
    | FCFS | No | — |
    | SJF / SRTF | `Yes` | Ageing |
    | Priority | `Yes` | Ageing |
    | `Round Robin` | `No` | Built in |
    | HRRN | `No` | Built in |
    | Multilevel feedback | No, with ageing | Ageing |
    | Linux CFS | No | Built in |

    - Short answer: SJF starves long processes because it always prefers short ones; the standard starvation-free algorithms are `Round Robin`, `FCFS` and `HRRN`, and the standard cure applied to SJF and priority scheduling is `ageing`.

17. **Consider the processes P1, P2, P3, P4 given in the below table, arrives for execution in the same order, with Arrival Time 0, and given Burst Time, let's find the average waiting time using the FCFS scheduling algorithm.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

    Answer: The burst times are not printed with the question, so the standard set below is used. All four arrive at time 0, in the order P1, P2, P3, P4.
    ```
       Process   Arrival Time   Burst Time
         P1           0             21
         P2           0              3
         P3           0              6
         P4           0              2
    ```

    How FCFS works
    - The process that requests the CPU `first` is served first — a simple FIFO queue. It is `non-preemptive`, so each process runs to completion once it starts.
    - Since all four arrive at time 0, they are served in the order given.

    Gantt chart
    ```
       |            P1            | P2 |   P3   |P4|
       0                         21   24       30 32
    ```

    Calculation
    ```
       Waiting time of a process = the sum of the burst times BEFORE it
    ```
    ```
       Process  Burst  Start  Completion  Turnaround  Waiting
         P1      21       0       21          21         0
         P2       3      21       24          24        21
         P3       6      24       30          30        24
         P4       2      30       32          32        30
                                          ----------  --------
       Total                                  107        75
    ```
    ```
       Turnaround = Completion - Arrival = Completion (all arrive at 0)
       Waiting    = Turnaround - Burst

       Average waiting time    = 75 / 4  = 18.75 units
       Average turnaround time = 107 / 4 = 26.75 units
    ```

    Step-by-step waiting times
    ```
       P1 waits for nothing                     ->  0
       P2 waits for P1                          -> 21
       P3 waits for P1 + P2 = 21 + 3            -> 24
       P4 waits for P1 + P2 + P3 = 21 + 3 + 6   -> 30
    ```

    The convoy effect, illustrated
    ```
       If the SAME processes ran in the order P4, P2, P3, P1 :

       |P4| P2 |   P3   |            P1            |
       0  2    5       11                         32

       Waiting : P4 = 0 , P2 = 2 , P3 = 5 , P1 = 11
       Average waiting time = 18 / 4 = 4.50 units
    ```
    - The identical set of processes gives `18.75` or `4.50` units depending only on the order. This is the `convoy effect`: one long process at the front of the queue makes every short one wait behind it, exactly as a slow lorry holds up a line of cars.
    - It is the main weakness of FCFS, and the reason `SJF` — which would choose the second order automatically — gives the minimum possible average waiting time.

    Properties of FCFS
    ```
       Advantages    : simplest to implement ; fair in arrival order ;
                       NO STARVATION - every process eventually runs
       Disadvantages : poor average waiting time ; convoy effect ;
                       bad response time, so unsuitable for interactive
                       or time-sharing systems
    ```

18. **Job arrival time and execution time of Operating system tasks table is given, find out- (i) Average waiting time for FCFS (ii) Preemptive SJF (iii) Round Robin (Quantum time: 3) scheduling algorithm** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925 (ET: CTI)]*

    Answer: The job table is not printed with the question, so the standard set below is used. The method applies to any data.
    ```
       Process   Arrival Time   Execution (Burst) Time
         P1           0                  5
         P2           1                  3
         P3           2                  8
         P4           3                  6
    ```

    (i) FCFS — First Come First Served
    ```
       Order of arrival : P1 , P2 , P3 , P4

       |   P1   |  P2  |     P3     |    P4    |
       0        5      8           16         22
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P1        0       5         5           5         0
         P2        1       3         8           7         4
         P3        2       8        16          14         6
         P4        3       6        22          19        13
                                            ----------  --------
       Total                                                23

       Average waiting time = 23 / 4 = 5.75 units
    ```

    (ii) Preemptive SJF — Shortest Remaining Time First (SRTF)
    - At every arrival the scheduler compares the new process's burst with the `remaining` time of the running one, and switches if the new one is shorter.
    ```
       t=0 : only P1(5)                        -> P1 runs
       t=1 : P2 arrives with 3 ; P1 has 4 left
             3 < 4  -> PREEMPT , P2 runs
       t=2 : P3 arrives with 8 ; P2 has 2 left -> no preemption
       t=3 : P4 arrives with 6 ; P2 has 1 left -> no preemption
       t=4 : P2 finishes. Remaining: P1(4), P3(8), P4(6)
             shortest is P1 -> P1 runs 4 to 8
       t=8 : remaining P3(8), P4(6) -> P4 runs 8 to 14
       t=14: P3 runs 14 to 22

       |P1|  P2  |   P1   |    P4    |     P3     |
       0  1      4        8         14           22
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P1        0       5         8           8         3
         P2        1       3         4           3         0
         P3        2       8        22          20        12
         P4        3       6        14          11         5
                                            ----------  --------
       Total                                                20

       Average waiting time = 20 / 4 = 5.00 units
    ```

    (iii) Round Robin, quantum = 3
    ```
       |  P1  |  P2  |  P3  |  P4  |P1|  P3  |  P4  |  P3  |
       0      3      6      9     12 14     17     20     22
    ```
    ```
       t=0  queue [P1]           P1 runs 0-3  , rem 2  ; P2, P3 arrive
       t=3  queue [P2,P3,P1]     P2 runs 3-6  , DONE   ; P4 arrived
       t=6  queue [P3,P4,P1]     P3 runs 6-9  , rem 5
       t=9  queue [P4,P1,P3]     P4 runs 9-12 , rem 3
       t=12 queue [P1,P3,P4]     P1 runs 12-14, DONE
       t=14 queue [P3,P4]        P3 runs 14-17, rem 2
       t=17 queue [P4,P3]        P4 runs 17-20, DONE
       t=20 queue [P3]           P3 runs 20-22, DONE
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P1        0       5        14          14         9
         P2        1       3         6           5         2
         P3        2       8        22          20        12
         P4        3       6        20          17        11
                                            ----------  --------
       Total                                                34

       Average waiting time = 34 / 4 = 8.50 units
    ```

    Comparison

    | Algorithm | Average waiting time | Average turnaround time |
    |---|---|---|
    | FCFS | 5.75 | 11.25 |
    | `Preemptive SJF (SRTF)` | `5.00` | `10.50` |
    | RR (q = 3) | 8.50 | 14.00 |

    - `SRTF gives the minimum average waiting time`. It is the optimal algorithm for this criterion, because at every instant it runs the job that will finish soonest.
    - `Round Robin is worst on the averages` but best on `response time`: every process starts within 9 units, whereas under FCFS P4 does not begin until t = 16.
    - The trade-off to state: `SRTF minimises waiting time but can starve long jobs and needs the burst time in advance; RR guarantees fairness and responsiveness at the cost of turnaround.`
    ```
       Turnaround = Completion - Arrival
       Waiting    = Turnaround - Burst
    ```

19. **Calculate The Average Waiting Time of SJF scheduling algorithm.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*

    Answer: The process table is not printed with the question, so the standard set below is used. The method applies to any data.
    ```
       Process   Arrival Time   Burst Time
         P1           0             5
         P2           1             3
         P3           2             8
         P4           3             6
    ```

    How SJF works
    - At every decision point the scheduler picks the process with the `smallest burst time` among those that have `already arrived`. In its basic form it is `non-preemptive`, so the chosen process runs to completion.

    Step-by-step selection
    ```
       t = 0  : only P1 has arrived            -> P1 runs 0 to 5
       t = 5  : ready P2(3) , P3(8) , P4(6)
                shortest is P2(3)              -> P2 runs 5 to 8
       t = 8  : ready P3(8) , P4(6)
                shortest is P4(6)              -> P4 runs 8 to 14
       t = 14 : only P3 left                   -> P3 runs 14 to 22
    ```

    Gantt chart
    ```
       |   P1   |  P2  |    P4    |     P3     |
       0        5      8         14           22
    ```

    Calculation
    ```
       Turnaround = Completion - Arrival
       Waiting    = Turnaround - Burst
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P1        0       5         5           5         0
         P2        1       3         8           7         4
         P3        2       8        22          20        12
         P4        3       6        14          11         5
                                            ----------  --------
       Total                                      43        21
    ```
    ```
       Average waiting time    = 21 / 4 = 5.25 units
       Average turnaround time = 43 / 4 = 10.75 units
    ```

    Comparison with FCFS on the same data
    ```
       FCFS order : P1 , P2 , P3 , P4

       |   P1   |  P2  |     P3     |    P4    |
       0        5      8           16         22

       Average waiting time = (0 + 4 + 6 + 13) / 4 = 5.75 units
    ```
    ```
       SJF  = 5.25        FCFS = 5.75
    ```
    - SJF wins because it runs the 6-unit P4 before the 8-unit P3, so P4's shorter burst is added to fewer waits.

    Points worth stating
    ```
       ARRIVAL TIME MATTERS. At t = 0 only P1 exists, so it must run even
       though P2 is shorter. Choosing P2 first would be wrong - it has not
       arrived yet. This is the commonest mistake in such questions.

       SJF is PROVABLY OPTIMAL for average waiting time when all processes
       are available together. Running the shortest job first adds the
       smallest possible delay to everything still waiting.

       Its weaknesses : the burst time must be PREDICTED, which in a real
       system is done by exponential averaging of past bursts ; and long
       processes can STARVE, which is cured by AGEING.

       The preemptive form is called SRTF (Shortest Remaining Time First),
       and on this data it does slightly better - 5.00 units.
    ```

20. **(a) Define FCFS, SJF and RR algorithm (Quantum=20).** *[National University Assistant Programmer 2020 compact it 977-978 (ET: DU)]*

    Answer: The three algorithms. The burst times are not printed with the question, so the classic textbook set is used to illustrate them, and the assumption is stated.
    ```
       P1 = 53 , P2 = 17 , P3 = 68 , P4 = 24    (all arrive at time 0)
    ```

    `FCFS — First Come First Served`
    - The process that requests the CPU `first` is served first. It is `non-preemptive`: once a process starts, it runs to completion.
    - Implemented as a simple FIFO queue.
    ```
       Gantt chart, in arrival order P1, P2, P3, P4 :

       |        P1        |  P2  |         P3        |    P4    |
       0                 53     70                  138        162
    ```
    ```
       Waiting : P1 = 0 , P2 = 53 , P3 = 70 , P4 = 138
       Average waiting time = 261 / 4 = 65.25 ms
    ```
    - Advantage: simple and fair in arrival order. Disadvantage: the `convoy effect` — one long process at the front makes every short one wait, so the average waiting time is poor.

    `SJF — Shortest Job First`
    - The process with the `smallest burst time` runs first. Non-preemptive in its basic form; the preemptive version is called `SRTF`.
    - It is `provably optimal` for average waiting time when all processes are available together.
    ```
       Order by burst : P2(17) , P4(24) , P1(53) , P3(68)

       |  P2  |    P4    |        P1        |         P3        |
       0     17         41                 94                  162
    ```
    ```
       Waiting : P2 = 0 , P4 = 17 , P1 = 41 , P3 = 94
       Average waiting time = 152 / 4 = 38.00 ms
    ```
    - Advantage: the minimum possible average waiting time. Disadvantages: the burst time must be `predicted`, and long processes can `starve`.

    `RR — Round Robin, quantum = 20`
    - Each process gets the CPU for at most one `time quantum`, then is preempted and sent to the back of the ready queue. `Preemptive`, and designed for time-sharing.
    ```
       |  P1 |  P2 | P3 | P4 | P1 | P3 | P4| P1  | P3        |
       0    20    37   57   77   97  117 121 134             162
    ```
    ```
       Round 1 : P1 20 , P2 17 (finishes at 37) , P3 20 , P4 20
       Round 2 : P1 20 , P3 20 , P4 4 (finishes at 121)
       Round 3 : P1 13 (finishes at 134) , P3 28 (finishes at 162)
    ```
    ```
       Waiting : P1 = 81 , P2 = 20 , P3 = 94 , P4 = 97
       Average waiting time = 292 / 4 = 73.00 ms
    ```
    - Advantage: `no starvation` and excellent `response time` — every process starts within 60 ms here, whereas under FCFS P4 waits 138 ms. Disadvantage: the worst average turnaround of the three, plus context-switch overhead.

    Comparison on this data

    | Algorithm | Preemptive | Average waiting time | Starvation |
    |---|---|---|---|
    | FCFS | No | 65.25 ms | No |
    | `SJF` | No | `38.00 ms` — the best | Yes |
    | RR (q = 20) | Yes | 73.00 ms | `No` |

    Choosing the quantum in RR
    ```
       Quantum too LARGE  ->  behaves like FCFS
       Quantum too SMALL  ->  context-switch overhead dominates

       Rule of thumb : 80 % of CPU bursts should be shorter than the quantum.
       Typical value  : 10 to 100 ms.
    ```
    - The trade-off to state: `SJF minimises average waiting time but can starve long jobs; RR guarantees fairness and responsiveness at the cost of turnaround time; FCFS is simplest but suffers the convoy effect.`

21. **(b) Turnaround time of FCFS and SJF** *[National University Assistant Programmer 2020 compact it 978 (ET: DU)]*

    Answer: `Turnaround time` is the total time a process spends in the system.
    ```
       Turnaround time = Completion time - Arrival time
                       = Waiting time + Burst time
    ```
    - The burst times are not printed with the question, so the classic textbook set is used, and the assumption is stated.
    ```
       P1 = 53 , P2 = 17 , P3 = 68 , P4 = 24    (all arrive at time 0)

       Since every arrival time is 0, turnaround time = completion time.
    ```

    FCFS — in arrival order P1, P2, P3, P4
    ```
       |        P1        |  P2  |         P3        |    P4    |
       0                 53     70                  138        162
    ```
    ```
       Process   Burst   Completion   Turnaround   Waiting
         P1       53         53           53          0
         P2       17         70           70         53
         P3       68        138          138         70
         P4       24        162          162        138
                                  ----------    ---------
       Total                          423           261

       Average turnaround time = 423 / 4 = 105.75 ms
       Average waiting time    = 261 / 4 =  65.25 ms
    ```

    SJF — order by burst time P2(17), P4(24), P1(53), P3(68)
    ```
       |  P2  |    P4    |        P1        |         P3        |
       0     17         41                 94                  162
    ```
    ```
       Process   Burst   Completion   Turnaround   Waiting
         P1       53         94           94         41
         P2       17         17           17          0
         P3       68        162          162         94
         P4       24         41           41         17
                                  ----------    ---------
       Total                          314           152

       Average turnaround time = 314 / 4 = 78.50 ms
       Average waiting time    = 152 / 4 = 38.00 ms
    ```

    Comparison

    | Process | FCFS turnaround | SJF turnaround |
    |---|---|---|
    | P1 | 53 | 94 |
    | P2 | 70 | 17 |
    | P3 | 138 | 162 |
    | P4 | 162 | 41 |
    | `Average` | `105.75 ms` | `78.50 ms` |

    - `SJF reduces the average turnaround time by about 26 per cent`, from 105.75 to 78.50 ms.
    - The reason is the `convoy effect` in FCFS: P1 has a 53 ms burst and happens to be first, so P2's 17 ms job waits 53 ms behind it. SJF runs the short jobs first, so their short bursts are added to the wait of fewer processes.
    - Note that `P3 is worse off` under SJF — 162 against 138 — and P1 is worse off too. SJF improves the `average` by making the short jobs much better and the long ones somewhat worse. Taken to its limit, this is what causes `starvation` of long processes.
    - Note also that the `total elapsed time is 162 ms under both algorithms`. Scheduling never changes the amount of work; it only changes who waits for whom.

22. **Operating system (OS) scheduling is the key concept of multiprogramming. List and briefly define the major types of OS scheduling.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985-986 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

    Answer: `Scheduling` is what makes multiprogramming work: it decides which of the many processes in the system gets a resource next. It operates at `three levels`, distinguished by how often they run and what they decide.

    1. Long-term scheduler (job scheduler / admission scheduler)
    ```
       Decides : WHICH jobs are admitted into the system
       Moves   : NEW  ->  READY
       Runs    : rarely - seconds or minutes apart
    ```
    - It controls the `degree of multiprogramming`, meaning how many processes are in memory at once. Admitting too few wastes the CPU; admitting too many causes thrashing.
    - It aims for a good `mix` of CPU-bound and I/O-bound processes, so that the CPU and the devices are both kept busy.
    - Because it runs rarely, it can afford to be slow and careful.
    - Present in `batch systems`. Modern interactive systems such as Linux and Windows have effectively no long-term scheduler — every submitted process is admitted immediately.

    2. Short-term scheduler (CPU scheduler / dispatcher)
    ```
       Decides : WHICH ready process gets the CPU next
       Moves   : READY  ->  RUNNING
       Runs    : very often - every few milliseconds
    ```
    - This is what is normally meant by "CPU scheduling". It must be `extremely fast`, because any time it spends is time the CPU is not doing useful work.
    - Uses algorithms such as `FCFS`, `SJF`, `SRTF`, `Priority`, `Round Robin` and `multilevel feedback queues`.
    - The `dispatcher` is its companion: it performs the actual context switch, saving the old state, loading the new one and jumping to the right instruction. The time it takes is the `dispatch latency`.

    3. Medium-term scheduler (swapper)
    ```
       Decides : WHICH processes to remove from memory temporarily
       Moves   : READY or WAITING  ->  SUSPENDED (on disk) , and back
       Runs    : occasionally, when memory is under pressure
    ```
    - It performs `swapping`: writing a process's memory image out to disk to free RAM, and bringing it back later.
    - Its purposes are to reduce the degree of multiprogramming when memory is short, to relieve `thrashing`, and to improve the process mix.

    How the three fit together
    ```mermaid
    flowchart LR
        N[NEW] -->|Long-term scheduler| R[READY]
        R -->|Short-term scheduler| RUN[RUNNING]
        RUN -->|quantum expires| R
        RUN -->|I/O request| W[WAITING]
        W -->|I/O completes| R
        RUN --> T[TERMINATED]
        R -->|Medium-term: swap out| S[SUSPENDED READY]
        S -->|swap in| R
        W -->|swap out| SW[SUSPENDED WAITING]
    ```

    Comparison

    | Point | Long-term | Short-term | Medium-term |
    |---|---|---|---|
    | Also called | Job scheduler | CPU scheduler | Swapper |
    | Decides | Which jobs enter the system | Which process gets the CPU | Which process leaves memory |
    | Transition | New -> Ready | Ready -> Running | Ready/Waiting -> Suspended |
    | Frequency | Seconds to minutes | Milliseconds | Occasional |
    | Speed required | Can be slow | Must be very fast | Moderate |
    | Controls | Degree of multiprogramming | CPU allocation | Memory pressure |
    | Present in | Batch systems | `All systems` | Time-sharing systems |

    Other kinds of scheduling in an operating system
    ```
       I/O scheduling   : the order in which disk requests are served -
                          FCFS, SSTF, SCAN, C-SCAN, LOOK

       Thread scheduling: user-level versus kernel-level threads,
                          and how they are mapped

       Real-time        : Rate Monotonic, Earliest Deadline First -
                          guarantees deadlines rather than fairness
    ```

    - The essential point: the `short-term scheduler` is the one that determines responsiveness and is invoked thousands of times a second; the `long-term scheduler` sets how much work is in the system at all; and the `medium-term scheduler` is the safety valve that relieves memory pressure.

23. **(c) Explain the following Scheduling algorithm: (i) Round Robin (ii) FCFS (iii) Priority scheduling** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026 (ET: N/A)]*

    Answer: (i) Round Robin
    - Each process receives a fixed `time quantum` (time slice). When the quantum expires, the process is `preempted` and moved to the back of the ready queue, and the next process runs.
    - It is `preemptive` and designed for `time-sharing` and interactive systems.
    ```
       P1 = 5 , P2 = 3 , P3 = 4   , quantum = 2

       |P1|P2|P3|P1|P2|P3|P1|
       0  2  4  6  8  9 11 12

       Waiting : P1 = 7 , P2 = 6 , P3 = 7
       Average waiting time = 20 / 3 = 6.67
    ```
    ```
       Advantages    : NO STARVATION - every process runs within
                       (n-1) x quantum ; fair ; excellent response time
       Disadvantages : higher average turnaround time ; context-switch
                       overhead ; ignores priority

       Quantum too LARGE -> behaves like FCFS
       Quantum too SMALL -> overhead dominates
       Rule of thumb : 80 % of bursts should be shorter than the quantum
    ```

    (ii) FCFS — First Come First Served
    - The process that requests the CPU `first` is served first, implemented as a simple FIFO queue. `Non-preemptive`: once started, a process runs to completion.
    ```
       P1 = 24 , P2 = 3 , P3 = 3   (all arrive at 0)

       |          P1          |P2 |P3 |
       0                     24  27  30

       Waiting : P1 = 0 , P2 = 24 , P3 = 27
       Average waiting time = 51 / 3 = 17.00

       If the order were P2, P3, P1 instead :
       |P2 |P3 |          P1          |
       0   3   6                     30
       Average waiting time = 9 / 3 = 3.00
    ```
    - The same three processes give 17.00 or 3.00 depending only on the order. This is the `convoy effect`: one long process at the front makes every short one wait.
    ```
       Advantages    : simplest to implement ; fair in arrival order ;
                       no starvation
       Disadvantages : poor average waiting time ; convoy effect ;
                       bad for interactive systems
    ```

    (iii) Priority scheduling
    - Each process is given a `priority number`, and the highest-priority process runs first. Ties are broken by FCFS.
    - Exists in both forms: `non-preemptive` (the running process keeps the CPU) and `preemptive` (a higher-priority arrival takes it away).
    ```
       Process  Burst  Priority (1 = highest)
         P1      10       3
         P2       1       1
         P3       2       4
         P4       5       2

       Non-preemptive order : P2(1) , P4(2) , P1(3) , P3(4)

       |P2|   P4   |     P1     | P3 |
       0  1        6           16   18

       Waiting : P2 = 0 , P4 = 1 , P1 = 6 , P3 = 16
       Average waiting time = 23 / 4 = 5.75
    ```
    - Priority may be `internal` (computed from memory needs, burst time, I/O ratio) or `external` (set by the user, the department or the amount paid).
    ```
       Advantages    : important work is served first ; essential for
                       real-time systems
       Disadvantages : STARVATION - a low-priority process may never run

       Cure : AGEING - raise a process's priority the longer it waits.
              A process at priority 127 promoted one level every 15 minutes
              reaches priority 0 in about 32 hours - long, but FINITE.
    ```
    - `SJF is a special case of priority scheduling`, in which the priority is the inverse of the predicted burst time.

    Comparison

    | Point | Round Robin | FCFS | Priority |
    |---|---|---|---|
    | Preemptive | Yes | No | Both forms |
    | Selection | Time quantum, in turn | Arrival order | Highest priority |
    | Starvation | `No` | No | `Yes` — cured by ageing |
    | Average waiting | Moderate | Poor | Depends |
    | Response time | `Best` | Poor | Good for high priority |
    | Overhead | High — many switches | Lowest | Moderate |
    | Best for | Interactive, time sharing | Batch | Real-time systems |

24. **Calculate the average waiting time and total turn around time in: (i) Non Preemptive SJF (ii) Preemptive SJF** *[Sundharban Gas Assistant Programmer 2020 compact it 1047 (ET: N/A)]*

    Answer: The process table is not printed with the question, so the standard set below is used. The method applies to any data.
    ```
       Process   Arrival Time   Burst Time
         P1           0             5
         P2           1             3
         P3           2             8
         P4           3             6
    ```
    ```
       Turnaround time = Completion - Arrival
       Waiting time    = Turnaround - Burst
    ```

    (i) Non-preemptive SJF
    - At each decision point the shortest job among those already arrived is chosen, and it then runs to completion.
    ```
       t = 0  : only P1 has arrived           -> P1 runs 0 to 5
       t = 5  : ready P2(3), P3(8), P4(6)     -> shortest P2 -> 5 to 8
       t = 8  : ready P3(8), P4(6)            -> shortest P4 -> 8 to 14
       t = 14 : only P3 left                  -> 14 to 22

       |   P1   |  P2  |    P4    |     P3     |
       0        5      8         14           22
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P1        0       5         5           5         0
         P2        1       3         8           7         4
         P3        2       8        22          20        12
         P4        3       6        14          11         5
                                            ----------  --------
       Total                                      43        21

       Average waiting time    = 21 / 4 =  5.25 units
       Average turnaround time = 43 / 4 = 10.75 units
       Total turnaround time   = 43 units
    ```

    (ii) Preemptive SJF — Shortest Remaining Time First
    - At every arrival the new process's burst is compared with the `remaining` time of the running one, and the CPU is switched if the newcomer is shorter.
    ```
       t = 0 : only P1(5)                       -> P1 runs
       t = 1 : P2 arrives with 3 ; P1 has 4 left
               3 < 4  -> PREEMPT , P2 runs
       t = 2 : P3 arrives with 8 ; P2 has 2 left -> no preemption
       t = 3 : P4 arrives with 6 ; P2 has 1 left -> no preemption
       t = 4 : P2 finishes. Remaining P1(4), P3(8), P4(6)
               shortest is P1 -> runs 4 to 8
       t = 8 : remaining P3(8), P4(6) -> P4 runs 8 to 14
       t = 14: P3 runs 14 to 22

       |P1|  P2  |   P1   |    P4    |     P3     |
       0  1      4        8         14           22
    ```
    ```
       Process  Arrival  Burst  Completion  Turnaround  Waiting
         P1        0       5         8           8         3
         P2        1       3         4           3         0
         P3        2       8        22          20        12
         P4        3       6        14          11         5
                                            ----------  --------
       Total                                      42        20

       Average waiting time    = 20 / 4 =  5.00 units
       Average turnaround time = 42 / 4 = 10.50 units
       Total turnaround time   = 42 units
    ```

    Comparison

    | Metric | Non-preemptive SJF | Preemptive SJF (SRTF) |
    |---|---|---|
    | Average waiting time | 5.25 | `5.00` |
    | Average turnaround time | 10.75 | `10.50` |
    | Total turnaround time | 43 | `42` |
    | Context switches | 3 | 4 |
    | Optimality | Optimal among non-preemptive | `Globally optimal` |

    - `SRTF is always at least as good` as non-preemptive SJF on average waiting time, because it can react to a short job that arrives after the CPU has been given away. Here P2 arrives at t = 1 with a burst of 3, shorter than P1's remaining 4, and letting it in immediately saves time for everyone.
    - The price is more `context switches` — P1 alone is switched out and back — and each switch is pure overhead.
    - Both forms share the same two weaknesses: the burst time must be `predicted` in a real system, and long processes can `starve`. The cure for starvation is `ageing`, which gradually raises a waiting process's priority.

25. **What is turnaround time of a process? Difference between FAT32 and NTFS?** *[Bangladesh Bank Assistant Maintenance Engineer 2011 compact it 1279 (ET: N/A)]*

    Answer: Turnaround time
    - `Turnaround time` is the `total time a process spends in the system` — from the moment it is submitted until the moment it finishes.
    ```
       Turnaround time = Completion time - Arrival time

       It can also be written as :

       Turnaround time = Waiting time + Burst time + I/O time
    ```
    - It measures the whole experience from the user's point of view, so it is one of the main criteria a scheduling algorithm tries to `minimise`.
    ```
       Example :
          A process arrives at t = 2 and completes at t = 17

          Turnaround time = 17 - 2 = 15 ms
          If its burst time was 6 ms , its waiting time was 15 - 6 = 9 ms
    ```

    The related timing terms
    ```
       Arrival time     : when the process enters the ready queue
       Burst time       : how long it actually needs the CPU
       Completion time  : when it finishes
       Waiting time     : total time spent in the ready queue
                          = Turnaround - Burst
       Response time    : arrival to the FIRST time it gets the CPU
       Throughput       : processes completed per unit time
    ```
    - The distinction that matters: `response time` is what an interactive user feels, while `turnaround time` is what a batch job's owner cares about. Round Robin optimises the first; SJF optimises the second.

    FAT32 versus NTFS

    `FAT32` (File Allocation Table, 32-bit) is the older, simpler filesystem introduced with Windows 95 OSR2. `NTFS` (New Technology File System) came with Windows NT and is the standard for Windows today.

    | Point | FAT32 | NTFS |
    |---|---|---|
    | Full form | File Allocation Table 32 | New Technology File System |
    | Maximum file size | `4 GB` | 16 TB (practically unlimited) |
    | Maximum partition size | 2 TB (32 GB to format in Windows) | 256 TB |
    | File permissions | `None` | Yes — full ACLs per user and group |
    | Encryption | No | Yes — EFS, and BitLocker |
    | Compression | No | Yes, built in |
    | Journaling | `No` | `Yes` — recovers after a crash |
    | Disk quotas | No | Yes |
    | Reliability | Poor — corruption on power loss | High — the journal replays the change |
    | Fragmentation | High | Lower, and it self-manages |
    | Filename length | 255 characters | 255 characters, full Unicode |
    | Cluster size | 4-32 KB | 4 KB typically |
    | Overhead | Very low | Higher |
    | Compatibility | `Universal` — Windows, macOS, Linux, cameras, TVs, car stereos | Windows fully; read-only on macOS; needs a driver on Linux |
    | Used for | USB pen drives, SD cards, embedded devices | Windows system and data drives |

    Why the 4 GB limit exists
    ```
       FAT32 stores a file's size in a 32-bit field.

       2^32 - 1 = 4,294,967,295 bytes = 4 GB - 1 byte

       This is why a 5 GB video file cannot be copied to a FAT32 pen drive,
       which is the most common practical encounter with the limitation.
    ```

    Why NTFS is more reliable — journaling
    ```
       Before changing the filesystem, NTFS writes the intended change to a
       LOG. If the power fails mid-operation, the log is replayed on the
       next boot and the filesystem is restored to a consistent state.

       FAT32 has no log. A power failure during a write can leave the file
       allocation table inconsistent, which is why chkdsk was so often
       needed on older Windows systems.
    ```

    Which to use
    ```
       FAT32 : small removable media that must work on EVERYTHING -
               a camera SD card, a car stereo USB stick

       exFAT : the modern replacement for FAT32 on removable media -
               no 4 GB limit, and still widely compatible

       NTFS  : Windows system drives and any large internal disk, where
               permissions, journaling and large files are needed
    ```

## OS Concepts & System Software (24)

1. Difference Between Firmware and OS. *[BEPRC Assistant Programmer 08.08.2026 (ET: N/A)]*

   Answer: `Firmware` is low-level software stored permanently inside a hardware device to make that device work. An `operating system` is a large program that manages the whole computer and provides an interface for the user and for applications.

   Firmware
   - Written into `ROM, EPROM, EEPROM or flash` on the device itself, so it is present the moment power is applied.
   - It is `hardware specific` — the firmware of one printer will not run another.
   - Small, from a few kilobytes to a few megabytes, and it performs one fixed job.
   - Examples: `BIOS/UEFI` on a motherboard, the controller firmware in a hard disk or SSD, the code inside a router, a washing machine, a TV remote or a digital camera.
   - It runs `first`, before any operating system exists.

   Operating system
   - A large program `loaded from disk into RAM` at boot time.
   - It manages the processor, memory, files, devices and security, and provides `system calls` so that applications need not know anything about the hardware.
   - Large — hundreds of megabytes to gigabytes — and general purpose.
   - Examples: `Windows, Linux, macOS, Android, iOS`.

   How they cooperate at start-up
   ```
      1. Power on
      2. FIRMWARE (BIOS/UEFI) runs from ROM
           - POST : test the memory, CPU and devices
           - find the boot device
      3. Firmware loads the BOOTLOADER from disk
      4. The bootloader loads the OPERATING SYSTEM into RAM
      5. The OS takes control and starts the user's programs
   ```
   - The essential relationship: `firmware wakes the hardware up; the operating system then runs the machine`.

   Difference

   | Point | Firmware | Operating System |
   |---|---|---|
   | Purpose | Make one device function | Manage the whole computer |
   | Stored in | ROM / flash, on the device | Disk, loaded into RAM |
   | Size | KB to a few MB | Hundreds of MB to GB |
   | Scope | One specific hardware device | The entire system |
   | Runs | First, at power-on | After the firmware |
   | Hardware specific | `Yes` | No — portable across machines |
   | User interface | None or very limited | Full GUI and command line |
   | Multitasking | Usually none | Yes |
   | Updated | Rarely, by "flashing" | Frequently, by patches |
   | Risk of a bad update | Can `brick` the device | Usually recoverable |
   | User modifies it | Almost never | Constantly |
   | Examples | BIOS/UEFI, router firmware, SSD controller | Windows, Linux, Android |

   - One point that is easy to miss: an operating system `also relies on firmware while it runs`, not only at boot. Every disk, network card and graphics card contains its own firmware, and the OS driver talks to that firmware rather than to raw silicon.

2. **Define: Socket, Kernel, Process, Program, Multiprogramming, Context Switching; Explain Preemptive Priority Scheduling algorithm with illustration; Explain LRU and NRU Page Replacement algorithm.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 302 (ET: BIBM)]*

   Answer: Definitions

   `Socket`
   - A `socket` is one endpoint of a two-way communication link between two programs over a network. It is identified by an `IP address plus a port number`, and the pair of sockets defines a connection.
   ```
      Socket = IP address : port          e.g. 192.168.1.5 : 8080

      Types : STREAM socket   -> TCP , reliable and connection oriented
              DATAGRAM socket -> UDP , fast and connectionless
              RAW socket      -> direct IP access, used by ping
   ```
   - Every network program — a web server, a database client, an SSH session — is built on sockets. `socket() , bind() , listen() , accept() , connect() , send() , recv() , close()` are the system calls involved.

   `Kernel`
   - The `core` of the operating system, resident in memory from boot to shutdown and running in `privileged mode` with full access to the hardware.
   - It manages processes, memory, devices and files, and exposes `system calls` to applications.
   - Types: `monolithic` (Linux), `microkernel` (QNX, Minix), `hybrid` (Windows NT, macOS).

   `Program` versus `Process`
   ```
      PROGRAM : a PASSIVE set of instructions stored on disk. An executable
                file. It occupies no CPU and no memory of its own.

      PROCESS : a program in EXECUTION - an ACTIVE entity, with its own
                address space, program counter, registers, stack, heap
                and a Process Control Block.
   ```
   - One program can produce `many processes` — opening a browser twice gives two processes from one program. A program is a recipe; a process is the cooking.
   ```
      A process consists of :
           Text section  : the program code
           Data section  : global and static variables
           Heap          : dynamically allocated memory
           Stack         : local variables, parameters, return addresses
           PCB           : state, PC, registers, memory limits, open files
   ```

   `Multiprogramming`
   - Keeping `several programs in main memory at once`, so that when one waits for I/O the CPU is given to another instead of idling.
   ```
      Program A : |CPU|....I/O wait....|CPU|
      Program B : .....|CPU|....I/O wait....|CPU|
      CPU busy  : |AAA|BBB|AAA|BBB|...   - never idle
   ```
   - It needs memory protection, interrupts, context switching and a scheduler. It raises `CPU utilisation` and `throughput`.

   `Context switching`
   - Saving the state of the running process and loading the state of another, so that the CPU can be handed from one to the other.
   ```
      1. Save the CPU state (PC, registers, flags) into the outgoing PCB
      2. Update that process's state to READY or WAITING
      3. Select the next process (the scheduler)
      4. Load its state from its PCB
      5. Jump to its saved program counter
   ```
   - It is `pure overhead` — a few microseconds during which no useful work is done — which is why the time quantum must not be too small.

   Preemptive priority scheduling
   - Each process has a priority. The CPU always runs the highest-priority `ready` process, and a higher-priority `arrival` takes the CPU away from a running process.
   ```
      Process   Arrival   Burst   Priority  (lower number = higher priority)
        P1         0        10        3
        P2         1         1        1
        P3         2         2        4
        P4         3         1        5
        P5         4         5        2
   ```
   ```
      t=0 : only P1 (prio 3)                   -> P1 runs
      t=1 : P2 arrives, prio 1 beats 3         -> PREEMPT , P2 runs
      t=2 : P2 done. P1(3), P3(4) ready        -> P1 runs
      t=4 : P5 arrives, prio 2 beats 3         -> PREEMPT , P5 runs
      t=9 : P5 done , P1 is highest            -> P1 to completion
      t=16: P3 ; t=18 : P4

      |P1|P2|  P1  |    P5    |      P1      | P3 |P4|
      0  1  2      4          9             16   18 19
   ```
   ```
      Process  Completion  Turnaround  Waiting
        P1        16          16          6
        P2         2           1          0
        P3        18          16         14
        P4        19          16         15
        P5         9           5          0
                          ----------   --------
      Average waiting time    = 35/5 = 7.00 ms
      Average turnaround time = 54/5 = 10.80 ms
   ```
   - Weakness: `starvation` of low-priority processes such as P4. Cured by `ageing` — raising a process's priority the longer it waits.

   LRU and NRU page replacement

   `LRU — Least Recently Used`
   - Replaces the page that has `not been used for the longest time`, on the assumption that a page unused for a long while is unlikely to be needed soon.
   ```
      Reference string : 7 0 1 2 0 3 0 4 , 3 frames

      7      -> [7]           miss
      0      -> [7,0]         miss
      1      -> [7,0,1]       miss
      2      -> [0,1,2]       miss   (7 was least recently used)
      0      -> [1,2,0]       HIT
      3      -> [2,0,3]       miss   (1 was least recently used)
      0      -> [2,3,0]       HIT
      4      -> [3,0,4]       miss   (2 was least recently used)

      6 misses , 2 hits
   ```
   ```
      Implementation : a COUNTER per page, or a STACK of page numbers.
      Both are expensive - a timestamp must be updated on EVERY access.
      Advantage : it never suffers Belady's anomaly.
   ```

   `NRU — Not Recently Used`
   - A cheap approximation to LRU, using two bits kept by the hardware.
   ```
      R = Referenced bit , set on every read or write
      M = Modified (dirty) bit , set on every write

      The R bit is CLEARED periodically by a timer interrupt, so it
      records recent use only.

      Pages are then placed in four classes :

           Class 0 : R = 0 , M = 0   not referenced , not modified  <- BEST victim
           Class 1 : R = 0 , M = 1   not referenced , modified
           Class 2 : R = 1 , M = 0   referenced , not modified
           Class 3 : R = 1 , M = 1   referenced and modified        <- keep

      NRU evicts a page at random from the LOWEST non-empty class.
   ```
   - Class 1 is preferred over class 2 because writing a dirty page to disk once is cheaper than repeatedly reloading a page that is actively in use.

   Comparison

   | Point | LRU | NRU |
   |---|---|---|
   | Basis | Exact time of last use | Two bits, R and M |
   | Accuracy | High | Approximate |
   | Hardware cost | High — a counter or stack per page | Very low — two bits |
   | Overhead per access | Update a timestamp every time | Hardware sets a bit |
   | Belady's anomaly | Never | Possible |
   | Used in practice | Rarely in pure form | Yes, as the basis of the clock algorithm |

   - What real systems use: the `clock` (second-chance) algorithm, which is NRU arranged as a circular list, and its refinement the `enhanced second-chance` algorithm using both R and M. `Optimal (OPT)` replacement, which evicts the page needed furthest in the future, is unimplementable — it needs knowledge of the future — but is used as the benchmark against which the others are measured.

3. **Explain how can multiprogramming be achieved on a uniprocessor system?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 379 (ET: BUET)]*

   Answer: `Multiprogramming` means keeping `several programs in main memory at the same time` so that the CPU always has work to do. On a `uniprocessor` — a machine with one CPU — only one program can actually execute at any instant, so multiprogramming is achieved by `switching` the CPU between them.

   The problem it solves
   ```
      A single program alternates between CPU bursts and I/O waits :

      Program A : |CPU| ---- waiting for disk ---- |CPU| ---- I/O ---- |CPU|
                             CPU IS IDLE HERE             IDLE

      A typical program spends 60-80 per cent of its time waiting for I/O.
      Without multiprogramming, the CPU is idle for all of it.
   ```

   How it works
   ```
      Program A : |CPU|........I/O wait.........|CPU|.....I/O.....
      Program B : ......|CPU|.......I/O wait........|CPU|.........
      Program C : ...........|CPU|.......I/O wait........|CPU|....

      CPU busy  : |AAA|BBB|CCC|AAA|BBB|CCC|...   -  NEVER IDLE
   ```
   - The moment a program requests I/O, the operating system takes the CPU away and gives it to another program that is ready. When the I/O finishes, an interrupt makes that program ready again.

   What is required to make it possible

   1. `Several programs resident in memory at once`
   - Memory is divided among them, by fixed partitions in early systems and by `paging` and `virtual memory` in modern ones.

   2. `Memory protection`
   - Each program must be prevented from reading or writing another's memory. Achieved with `base and limit registers`, or with the `MMU` and page tables. Without this, one faulty program would destroy the others.

   3. `Interrupts`
   - The mechanism that lets the operating system regain control. An I/O completion interrupt, or a timer interrupt, transfers control back to the kernel so it can choose a new process.

   4. `Context switching`
   - Saving the CPU state — program counter, registers, flags, memory-map pointers — of the outgoing process into its `PCB (Process Control Block)`, and loading the incoming one's.
   ```
      Save state of P1  ->  select P2  ->  load state of P2  ->  run P2
   ```
   - The time this takes is pure overhead, typically a few microseconds.

   5. `A scheduler`
   - The short-term scheduler decides which ready process runs next, using FCFS, SJF, priority or round robin.

   6. `The Process Control Block`
   - One per process, holding its state, program counter, registers, memory limits, open files and accounting information. It is what makes it possible to stop a process and resume it later exactly where it stopped.

   7. `Device management and spooling`
   - The OS queues I/O requests so that several programs can share one printer or disk without interfering.

   The illusion of simultaneity
   ```
      Switching happens thousands of times a second, so to a human it looks
      as though every program is running at once. In reality the CPU is
      executing exactly ONE instruction at a time - it is INTERLEAVING,
      not true parallelism.

      True parallelism requires MULTIPROCESSING - more than one CPU.
   ```

   Benefits
   ```
      High CPU utilisation - the CPU is almost never idle
      Higher throughput    - more jobs completed per hour
      Better use of memory and devices
      Shorter average response time
   ```

   Costs
   ```
      Complex memory management and protection hardware
      Context-switch overhead
      Scheduling complexity
      Deadlock and synchronisation problems appear
      Thrashing if too many processes are admitted
   ```

   - The related terms, which examiners like to see distinguished: `multiprogramming` keeps several programs in memory to keep the CPU busy; `multitasking` is multiprogramming with time-sharing added, so the switching is driven by a timer rather than only by I/O; and `multiprocessing` uses more than one CPU, which alone gives true simultaneous execution.

4. **Write the difference between shell and kernel?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*

   Answer: The `kernel` is the core of the operating system, which talks to the hardware. The `shell` is the outer layer that the user talks to.
   ```
           USER
             |
          SHELL         - interprets commands
             |
          KERNEL        - manages processes, memory, devices
             |
          HARDWARE
   ```

   Kernel
   - The `central component` of the operating system, loaded into memory at boot and resident until shutdown.
   - Runs in `kernel mode` (privileged mode) with complete access to the hardware and to all memory.
   - Responsibilities:
   ```
      Process management     : creation, scheduling, termination
      Memory management      : allocation, paging, virtual memory
      Device management      : drivers, interrupt handling
      File system management : reading and writing files
      System calls           : the interface applications use
      Security and protection
   ```
   - Types: `monolithic` (Linux), `microkernel` (Minix, QNX), `hybrid` (Windows NT, macOS), `exokernel`.

   Shell
   - A `user-level program` that reads the commands a user types, interprets them, and asks the kernel to carry them out through system calls.
   - Runs in `user mode` with no special privileges of its own.
   - Two kinds:
   ```
      CLI shell : bash , sh , zsh , ksh , csh , fish , PowerShell , cmd
      GUI shell : GNOME , KDE , Windows Explorer
   ```
   - It is not part of the operating system proper. It can be replaced, and several shells can be installed side by side.

   How a command travels through them
   ```
      $ ls -l

      1. The SHELL reads the line and parses it
      2. It expands wildcards and variables
      3. It forks a child process and calls exec("/bin/ls")
      4. The KERNEL creates the process, loads the program, schedules it
      5. ls issues system calls (openat, getdents, write)
      6. The KERNEL performs them and returns the data
      7. The output reaches the terminal
   ```

   Difference

   | Point | Kernel | Shell |
   |---|---|---|
   | Position | Innermost layer, next to the hardware | Outermost layer, next to the user |
   | Nature | The core of the OS | An ordinary program |
   | Mode | `Kernel mode` — privileged | `User mode` |
   | Interacts with | The hardware | The user |
   | Function | Manage processes, memory, devices, files | Interpret and run commands |
   | Loaded | At boot, stays in memory | When the user logs in |
   | Replaceable | No — changing it means changing the OS | `Yes` — bash, zsh, fish |
   | How many | One per running system | Many can run at once |
   | Direct hardware access | Yes | No — only through system calls |
   | Written in | C and assembly | C, or a scripting language |
   | Examples | Linux kernel, Windows NT kernel | bash, zsh, PowerShell, cmd |
   | If it crashes | The whole system halts | Only that session ends |

   Useful commands
   ```bash
      uname -r            # kernel version
      uname -a            # full kernel information
      echo $SHELL         # which shell you are using
      cat /etc/shells     # which shells are installed
      chsh -s /bin/zsh    # change your login shell
   ```

   - The relationship in one line: `the shell is the interface, the kernel is the engine`. A user never speaks to the kernel directly; every request passes through the shell or an application, and reaches the kernel as a `system call`.

5. **DOS কী? অপারেটিং সিস্টেমের কাজ ও প্রকারভেদ ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What DOS is
   - `DOS` stands for `Disk Operating System`. It is a `single-user, single-tasking`, command-line operating system that was the standard for IBM PCs and compatibles from 1981 to the mid-1990s.
   - The best-known version is `MS-DOS` from Microsoft; IBM sold the same product as `PC-DOS`.
   ```
      Characteristics :
           16-bit , real mode , addresses 1 MB of memory
           SINGLE TASKING - only one program at a time
           SINGLE USER - no accounts, no permissions
           COMMAND LINE only - no graphical interface
           FAT file system , with 8.3 filenames (NAME.EXT)
           No memory protection - a bad program can crash the machine
   ```
   ```
      Common commands :
           DIR      list files              CD       change directory
           COPY     copy a file             DEL      delete
           REN      rename                  MD / RD  make / remove directory
           FORMAT   format a disk           TYPE     display a file
           CLS      clear the screen        CHKDSK   check the disk
   ```
   - Early Windows (1.0 to 3.11, and 95/98 to a large extent) ran `on top of` DOS rather than replacing it. Modern Windows keeps a DOS-like shell in `cmd.exe`, but there is no DOS underneath it.

   Functions of an operating system
   ```
      1. PROCESS MANAGEMENT
           Create, schedule, suspend and terminate processes ; context
           switching ; inter-process communication ; deadlock handling.

      2. MEMORY MANAGEMENT
           Allocate and free memory ; keep track of what is in use ;
           paging, segmentation and virtual memory ; protect one process
           from another.

      3. FILE MANAGEMENT
           Create, read, write, delete files and directories ; manage
           the directory structure ; control access permissions ;
           allocate disk blocks.

      4. DEVICE (I/O) MANAGEMENT
           Device drivers ; buffering, caching and spooling ; scheduling
           disk requests ; handling interrupts.

      5. SECURITY AND PROTECTION
           Authentication , authorisation , encryption , audit logging ,
           isolating one user's data from another's.

      6. USER INTERFACE
           A command-line shell, a graphical desktop, or both.

      7. RESOURCE ALLOCATION AND ACCOUNTING
           Share the CPU, memory and devices fairly ; record usage.

      8. ERROR DETECTION AND RECOVERY
           Detect a hardware fault, a bad instruction or a full disk, and
           respond without crashing the whole system.

      9. NETWORKING
           Protocol stacks, sockets, remote file systems.
   ```

   Types of operating system
   ```
      BATCH
           Jobs with similar needs are grouped and run without user
           interaction. No interactivity ; the CPU is often idle.
           Example : early IBM mainframe systems.

      TIME-SHARING (multitasking)
           The CPU is shared by rapid switching, so many users appear to
           work simultaneously. Short response time is the goal.
           Example : UNIX , Linux , Windows.

      MULTIPROGRAMMING
           Several programs held in memory ; when one waits for I/O the
           CPU is given to another. Maximises CPU utilisation.

      MULTIPROCESSING
           Two or more CPUs in one machine, giving TRUE parallelism.
           Symmetric (SMP) or asymmetric.

      DISTRIBUTED
           Several independent computers joined by a network, presented
           to the user as one system. Resource sharing and fault
           tolerance are the aims.
           Example : Amoeba , modern cluster systems.

      REAL-TIME (RTOS)
           A response is guaranteed within a fixed deadline.
           HARD real time : a missed deadline is a total failure -
                pacemaker, aircraft control, airbag.
           SOFT real time : a missed deadline degrades quality -
                video streaming, online gaming.
           Example : RTLinux , VxWorks , FreeRTOS , QNX.

      NETWORK
           Manages shared files, printers and users across a LAN. Each
           machine keeps its own identity, unlike a distributed system.
           Example : Novell NetWare , Windows Server.

      EMBEDDED
           Built into a device with fixed function and limited memory.
           Example : the firmware in a washing machine, a router, a car ECU.

      MOBILE
           Optimised for touch, battery life and connectivity.
           Example : Android , iOS.

      SINGLE-USER SINGLE-TASKING : MS-DOS
      SINGLE-USER MULTITASKING   : Windows , macOS
      MULTI-USER                 : Linux , UNIX , mainframe systems
   ```

   - Where DOS sits in this classification: it is a `single-user, single-tasking, command-line` operating system with no memory protection and no multiprogramming — which is exactly why it was replaced. Modern Windows and Linux are `single-user or multi-user multitasking` systems built on a protected-mode kernel with virtual memory.

6. **Write down the difference between Multitasking and Multiprocessing.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*

   Answer: `Multitasking` means one CPU switching rapidly between several tasks so that they appear to run at once. `Multiprocessing` means a computer having `more than one CPU`, so tasks genuinely do run at once.

   Multitasking
   - The operating system gives each task a short `time slice` and switches between them thousands of times a second, using `context switching`. Only one task actually executes at any instant on a given CPU.
   ```
      ONE CPU :

      Task A : |AA|      |AA|      |AA|
      Task B :     |BB|      |BB|      |BB|
      Task C :         |CC|      |CC|

      Interleaved, not simultaneous.
   ```
   ```
      Types :
         PREEMPTIVE  - the OS forcibly takes the CPU back when the
                       quantum expires. Windows, Linux, macOS.
         COOPERATIVE - a task must yield voluntarily. Early Windows and
                       classic Mac OS. One misbehaving program froze
                       the whole machine.
   ```

   Multiprocessing
   - Two or more `physical processors` (or cores) in one computer, each executing an instruction stream at the same moment. This is `true parallelism`.
   ```
      FOUR CPUs :

      CPU1 : |AAAAAAAAAA|
      CPU2 : |BBBBBBBBBB|      all four at the SAME instant
      CPU3 : |CCCCCCCCCC|
      CPU4 : |DDDDDDDDDD|
   ```
   ```
      Types :
         SYMMETRIC (SMP)  - every CPU is equal, shares one memory and
                            runs the same copy of the OS. The normal case.
         ASYMMETRIC       - a master CPU controls the others, which
                            handle specific tasks.
   ```

   Difference

   | Point | Multitasking | Multiprocessing |
   |---|---|---|
   | Number of CPUs | `One` (or one per core) | `Two or more` |
   | Execution | Interleaved — appears simultaneous | `Genuinely simultaneous` |
   | Mechanism | Time slicing and context switching | Parallel execution on separate CPUs |
   | Parallelism | Apparent only | Real |
   | Requires | A scheduler and a timer interrupt | Multiple processors and cache coherence |
   | Throughput gain | None — the same CPU does the work | Near-linear with the number of CPUs |
   | Failure of one CPU | Not applicable | The system continues on the others |
   | Cost | No extra hardware | Extra processors |
   | Overhead | Context switching | Synchronisation and cache coherence |
   | Purpose | Responsiveness and utilisation | Raw throughput and reliability |
   | Examples | Windows, Linux on a single-core machine | A multi-core server, a supercomputer |

   The related terms, which examiners like to see distinguished
   ```
      MULTIPROGRAMMING : several programs held in MEMORY at once, so the
           CPU is given to another whenever one waits for I/O. The switch
           is triggered by an I/O request, not by a timer.

      MULTITASKING     : multiprogramming plus TIME SHARING - the switch
           is also driven by a timer, so every task gets a regular turn.
           This is what makes a system interactive.

      MULTITHREADING   : one PROCESS divided into several THREADS that
           share its address space. Cheaper to create and switch than a
           process, but a fault in one thread can bring down the process.

      MULTIPROCESSING  : more than one CPU, giving true parallelism.
   ```

   How they combine in practice
   ```
      A modern 8-core machine running Linux uses ALL of them at once :

           MULTIPROCESSING  - 8 cores really execute in parallel
           MULTITASKING     - each core time-slices among many processes
           MULTIPROGRAMMING - hundreds of processes are resident in memory
           MULTITHREADING   - each browser tab is a thread of one process
   ```

   - The limit on multiprocessing is `Amdahl's law`: if a fraction `(1-P)` of a program is inherently serial, the speed-up can never exceed `1/(1-P)` however many CPUs are added. A program that is 20 per cent serial can never go more than five times faster.

7. **(b) What is the difference between micro kernel and macro kernel in the context of OS?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

   Answer: The two are the opposite answers to one design question: `how much of the operating system should run in privileged kernel mode?`

   Macro kernel (monolithic kernel)
   - `Every` operating-system service runs inside the kernel, in `kernel mode`, as one large program in a single address space.
   ```
      +-------------------------------------------------+
      |                  USER MODE                      |
      |   Application 1     Application 2               |
      +-------------------------------------------------+
      |                 KERNEL MODE                     |
      |   Scheduler | Memory manager | File system      |
      |   Device drivers | Network stack | IPC          |
      |            ALL IN ONE ADDRESS SPACE             |
      +-------------------------------------------------+
      |                  HARDWARE                       |
      +-------------------------------------------------+
   ```
   - Services call each other by `direct function call`, which is why it is fast.
   - Examples: `Linux`, traditional `UNIX`, `MS-DOS`, `BSD`.

   Microkernel
   - Only the `bare minimum` runs in kernel mode — typically scheduling, basic memory management and inter-process communication. Everything else runs as an ordinary `user-mode server process`.
   ```
      +-------------------------------------------------+
      |                  USER MODE                      |
      |  Application | File | Device | Network | Memory |
      |              | srvr | driver | server  | server |
      +-------------------------------------------------+
      |            MICROKERNEL (kernel mode)            |
      |     IPC  |  basic scheduling  |  address spaces |
      +-------------------------------------------------+
      |                  HARDWARE                       |
      +-------------------------------------------------+
   ```
   - Services communicate by `message passing` through the kernel, which costs two context switches per request — the source of its slowness.
   - Examples: `QNX`, `Minix`, `Mach`, `L4`, `Symbian`.

   Difference

   | Point | Macro (monolithic) kernel | Microkernel |
   |---|---|---|
   | Size | Large — millions of lines | Small — often under 10,000 lines |
   | Services in kernel mode | `All` of them | Only IPC, scheduling, memory |
   | Communication | Direct function calls | `Message passing` |
   | Speed | `Faster` — no IPC overhead | Slower — two context switches per call |
   | Reliability | A driver crash kills the `whole system` | A server crash kills `only that service` |
   | Extensibility | Recompile or load a kernel module | `Add a user-space process` |
   | Debugging | Hard — kernel debugging | Easy — ordinary user-space debugging |
   | Security | Large attack surface in privileged mode | Small trusted computing base |
   | Portability | Lower | Higher |
   | Memory footprint | Larger | Smaller |
   | Examples | Linux, UNIX, MS-DOS | QNX, Minix, L4, Mach |

   The central trade-off
   ```
      MONOLITHIC : buys SPEED at the cost of RELIABILITY.
           A faulty printer driver runs in kernel mode with full hardware
           access, so a bug in it can corrupt any memory in the system.
           This is the cause of most "blue screen" and kernel panic faults.

      MICROKERNEL : buys RELIABILITY at the cost of SPEED.
           The same faulty driver is an ordinary process. If it crashes,
           the kernel simply restarts it and the system continues.
           But every disk read now costs several messages instead of
           one function call.
   ```

   Hybrid kernels — what real systems actually use
   ```
      Windows NT (and every later Windows), macOS (XNU) and modern
      Linux are all HYBRID in practice :

           Windows NT : a microkernel-influenced design, but the graphics
                subsystem and drivers were MOVED INTO the kernel for speed.

           macOS XNU  : the Mach microkernel plus a BSD monolithic layer
                in the same address space.

           Linux      : monolithic, but with LOADABLE KERNEL MODULES, so
                drivers can be inserted and removed at run time without
                recompiling - which gives much of the microkernel's
                flexibility while keeping direct function calls.
   ```

   - The historical footnote worth knowing: the `Tanenbaum-Torvalds debate` of 1992 argued exactly this question. Tanenbaum, the author of Minix, held that monolithic kernels were obsolete; Torvalds argued that the performance cost of message passing was unacceptable. In practice the hybrid designs above took what worked from both, and Linux's success settled the argument in favour of pragmatism rather than either pure form.

8. **অথবা, (ক) Blocking এবং Buffering OS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 610 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) The two terms belong to different parts of the operating system: `blocking` is about how a process waits, and `buffering` is about where data is held in transit.

   Blocking
   - A `blocking` operation is one in which the calling process is `suspended` — moved from RUNNING to WAITING — until the operation completes. It does no work and consumes no CPU while it waits.
   ```
      Process issues read()
           |
           v
      State : RUNNING -> WAITING        the process is BLOCKED
           |
      (the OS gives the CPU to another process)
           |
      I/O completes -> interrupt
           |
           v
      State : WAITING -> READY -> RUNNING     the process resumes
   ```
   ```
      BLOCKING (synchronous) I/O :
           n = read(fd, buf, 100);        // the process waits here
           process(buf);                   // reached only after the read

      NON-BLOCKING (asynchronous) I/O :
           n = read(fd, buf, 100);        // returns IMMEDIATELY, perhaps
                                           // with 0 bytes and EWOULDBLOCK
           // the process can do other work and check again later
   ```
   - Where it matters: a blocking `accept()` in a single-threaded server can serve only one client at a time, which is why real servers use threads, `select()`, `poll()` or `epoll()`.

   Buffering
   - A `buffer` is an area of memory that holds data `temporarily` while it moves between two devices or processes that work at different speeds.
   ```
      Fast producer                    Slow consumer
      (application)  --> [ BUFFER ] --> (printer)

      The application writes at memory speed and continues immediately;
      the printer drains the buffer at its own pace.
   ```
   ```
      Types :
         SINGLE buffering : one buffer. The producer must wait while the
              consumer empties it.
         DOUBLE buffering : two buffers. The producer fills one while the
              consumer empties the other - used in graphics to prevent
              flicker and tearing.
         CIRCULAR buffering : a ring of buffers, so producer and consumer
              run continuously. Used for audio, video and network streams.
   ```
   - Reasons for buffering:
   ```
      SPEED MISMATCH between producer and consumer
      Different DATA TRANSFER SIZES - one device works in bytes, another
           in 4 KB blocks
      Copy SEMANTICS - the OS copies the data before returning, so the
           application may reuse its own memory immediately
      Reduces the NUMBER of physical I/O operations
   ```

   Related mechanisms often asked alongside
   ```
      CACHING  : keeping a COPY of frequently used data in faster memory.
           A buffer holds the ONLY copy in transit ; a cache holds a
           DUPLICATE of data that also exists elsewhere.

      SPOOLING : Simultaneous Peripheral Operation On-Line. Output is
           written to a DISK FILE and a daemon feeds the device from
           there, so many jobs can queue for one printer.
   ```

   Difference

   | Point | Blocking | Buffering |
   |---|---|---|
   | Concerns | How a process `waits` | Where data is `stored` in transit |
   | Level | Process scheduling | I/O management |
   | Effect on the process | It is `suspended` | It usually `continues` |
   | Purpose | Wait correctly for a slow operation | Smooth a speed mismatch |
   | Alternative | Non-blocking or asynchronous I/O | Unbuffered (direct) I/O |
   | Cost | Idle waiting time for that process | Memory, and one extra copy |
   | Types | Blocking, non-blocking, asynchronous | Single, double, circular |
   | Example | `read()` waiting for a disk sector | The print queue in RAM |

   How the two combine in practice
   ```
      printf("hello");        // writes into a BUFFER, returns at once
      fflush(stdout);         // forces the buffer out - may BLOCK

      The buffering is what makes printf fast; the blocking happens only
      when the buffer must actually reach the device.
   ```
   - This is also why output can appear to vanish when a program crashes: it was still sitting in the buffer and was never flushed.

9. **(গ) Real Time System বলতে কী বোঝায় ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) A `real-time system` is one in which the correctness of the result depends not only on `what` is computed but on `when` it is delivered. A correct answer that arrives after its deadline is a `failure`.

   - The defining property is `predictability`, not raw speed. A real-time system guarantees a `worst-case response time`; a general-purpose system only offers a good average.

   Two categories
   ```
      HARD REAL TIME
           A missed deadline is a TOTAL SYSTEM FAILURE, and may be
           catastrophic.
           Examples : a pacemaker , an airbag controller , aircraft
           flight control , a nuclear reactor shutdown system , anti-lock
           brakes.
           No virtual memory, no secondary storage in the critical path,
           and every operation's worst-case time must be known.

      SOFT REAL TIME
           A missed deadline DEGRADES the service but does not destroy it.
           Examples : video streaming , online gaming , VoIP , a
           multimedia player.
           A late video frame causes a stutter, not a disaster.

      FIRM REAL TIME (sometimes listed separately)
           A late result is USELESS but not harmful - for example a frame
           in a live broadcast that arrives after its slot.
   ```

   Characteristics
   ```
      DETERMINISM     : the same input always produces the same timing
      BOUNDED LATENCY : a guaranteed maximum interrupt and dispatch latency
      PRIORITY BASED  : preemptive priority scheduling, so an urgent task
                        always displaces a less urgent one
      SMALL and COMPACT : a minimal kernel, so worst-case paths are short
      NO virtual memory in hard real-time systems - a page fault would
           introduce an unpredictable delay
      RELIABILITY     : fault tolerance and often redundant hardware
      CONCURRENCY     : many tasks with individual deadlines
   ```

   Scheduling algorithms used
   ```
      RATE MONOTONIC (RMS)      - static priority; the task with the
           shortest PERIOD gets the highest priority.
           Schedulable if  sum(Ci/Ti) <= n(2^(1/n) - 1)
           For large n this bound approaches 0.693, so about 69 per cent
           CPU utilisation is guaranteed schedulable.

      EARLIEST DEADLINE FIRST (EDF) - dynamic priority; whichever task
           has the nearest deadline runs next.
           Schedulable if  sum(Ci/Ti) <= 1  , so it can reach 100 per cent
           utilisation - optimal for a uniprocessor.

      LEAST LAXITY FIRST (LLF)  - priority by slack time remaining.
   ```
   ```
      Ci = worst-case execution time of task i
      Ti = its period
      Ci/Ti = the fraction of CPU it needs
   ```

   Real-time operating systems
   ```
      VxWorks , QNX , FreeRTOS , RTLinux , Micrium uC/OS ,
      Windows CE , RTEMS
   ```
   - A general-purpose Linux can be made soft real-time with the `PREEMPT_RT` patch, which makes almost the whole kernel preemptible.

   Real time versus general purpose

   | Point | Real-time system | General-purpose system |
   |---|---|---|
   | Priority | `Meeting deadlines` | Average throughput and fairness |
   | Response | Guaranteed worst case | Best effort |
   | Scheduling | Preemptive priority, RMS, EDF | Round robin, multilevel feedback |
   | Virtual memory | Avoided in hard real time | Standard |
   | Kernel | Small, fully preemptible | Large |
   | Determinism | Essential | Not required |
   | Throughput | Sacrificed for predictability | Maximised |
   | Examples | VxWorks, QNX, FreeRTOS | Windows, Linux, macOS |

   - The point that is most often misunderstood: `real time does not mean fast`. A system that responds in 50 ms `every time without exception` is real-time; one that usually responds in 1 ms but occasionally takes 200 ms is not. For an airbag, the guarantee matters and the average does not.

10. **Explain context switching in Operating System.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*

    Answer: `Context switching` is the act of saving the state of the currently running process and loading the saved state of another, so that the CPU can be handed from one process to the other and each can later resume exactly where it stopped.

    - It is the mechanism that makes `multitasking` possible. Without it, a process would have to run to completion before any other could start.

    What the "context" is
    - Everything the CPU needs to resume a process, all of it stored in that process's `Process Control Block (PCB)`.
    ```
       Program counter          the next instruction to execute
       CPU registers            general purpose, index, stack pointer
       Flags / status word      zero, carry, sign, interrupt enable
       Memory management data   base and limit registers, page-table pointer
       Process state            RUNNING , READY , WAITING
       Accounting information   CPU time used, process ID, priority
       I/O status               open files, pending I/O requests
    ```

    The steps
    ```mermaid
    sequenceDiagram
        participant P1 as Process P1
        participant K as Kernel
        participant P2 as Process P2
        P1->>K: interrupt or system call
        K->>K: 1. save P1's state into PCB1
        K->>K: 2. mark P1 READY or WAITING
        K->>K: 3. scheduler selects P2
        K->>K: 4. load P2's state from PCB2
        K->>P2: 5. jump to P2's saved program counter
    ```
    ```
       1. An INTERRUPT or SYSTEM CALL transfers control to the kernel.
       2. The kernel SAVES the CPU state into the outgoing process's PCB.
       3. The process's state is updated to READY or WAITING and it is
          placed in the appropriate queue.
       4. The SCHEDULER selects the next process to run.
       5. The kernel LOADS that process's state from its PCB - registers,
          memory-map pointers, flags.
       6. Control jumps to its saved program counter, and it resumes as
          though it had never stopped.
    ```

    What triggers a context switch
    ```
       TIMER INTERRUPT   : the time quantum expires (preemptive scheduling)
       SYSTEM CALL       : the process requests I/O and must wait
       I/O INTERRUPT     : a device completes, making a waiting process ready
       HIGHER PRIORITY   : a more important process becomes ready
       PROCESS EXIT      : the running process terminates
       PAGE FAULT        : the required page is not in memory
    ```

    The cost
    ```
       A context switch does NO USEFUL WORK. It is pure overhead.

       Direct cost   : saving and restoring registers , updating the PCB ,
                       running the scheduler          -> 1 to 10 microseconds

       Indirect cost : the CACHE and the TLB now hold the WRONG process's
                       data, so the incoming process suffers a burst of
                       misses until they refill. This is often LARGER than
                       the direct cost.
    ```
    ```
       Quantum 100 ms , switch 5 us  ->  overhead 0.005 %   negligible
       Quantum 100 us , switch 5 us  ->  overhead 5 %       significant
       Quantum  10 us , switch 5 us  ->  overhead 33 %      unacceptable
    ```
    - This is exactly why the time quantum cannot be made arbitrarily small: shrinking it improves response time but wastes an increasing share of the CPU on switching.

    Process switch versus thread switch
    ```
       PROCESS switch : the address space changes, so the page-table
            pointer is reloaded and the TLB is FLUSHED. Expensive.

       THREAD switch  : threads of one process SHARE the address space,
            so only the registers and the stack pointer change. The TLB
            and much of the cache stay valid.

       A thread switch is roughly 5 to 10 times cheaper than a process
       switch, which is one of the main reasons threads exist.
    ```

    How systems reduce the cost
    ```
       Hardware support : some processors have several REGISTER SETS, so
            switching means changing a pointer rather than copying registers
       Tagged TLBs (ASIDs) : each entry carries an address-space id, so the
            TLB need not be flushed on every switch
       Larger time quanta for CPU-bound work
       Threads instead of processes where the work can share memory
       Processor affinity : keeping a process on the same core, so its
            cache contents are still there when it resumes
    ```

    - The related term is `dispatch latency`: the time from the scheduler deciding to switch until the new process actually begins executing. In a real-time system this figure must be bounded and small, which is why real-time kernels are kept fully preemptible and simple.

11. **Which Operating system is considered as an Open source?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

    Answer: `Linux` is the operating system regarded as open source.

    - It was created by `Linus Torvalds` in 1991 and released under the `GNU General Public License (GPL)`, which makes the source code freely available to read, modify and redistribute.
    ```
       Open source means :
            the SOURCE CODE is published
            anyone may READ , MODIFY and REDISTRIBUTE it
            it is usually free of charge
            development is by a community, not one company
    ```

    Major open-source operating systems
    ```
       Linux distributions :
            Ubuntu , Debian , Fedora , CentOS / Rocky / AlmaLinux ,
            Red Hat Enterprise Linux (source open, support paid) ,
            openSUSE , Arch Linux , Linux Mint , Kali Linux

       Other open-source systems :
            FreeBSD , OpenBSD , NetBSD   - the BSD family
            Android (AOSP)               - built on the Linux kernel
            Chromium OS
            Minix , FreeRTOS , RTEMS     - teaching and embedded systems
    ```

    Proprietary (closed source) operating systems, for contrast
    ```
       Microsoft Windows , Apple macOS , Apple iOS ,
       IBM z/OS , Oracle Solaris (now largely closed) , MS-DOS
    ```

    Open source versus proprietary

    | Point | Open source (Linux) | Proprietary (Windows) |
    |---|---|---|
    | Source code | `Public` | Secret |
    | Cost | Usually free | Paid licence |
    | Modification | Allowed and encouraged | Prohibited |
    | Redistribution | Allowed under the licence | Prohibited |
    | Licence | GPL, Apache, MIT, BSD | EULA |
    | Developed by | A worldwide community | One company |
    | Support | Community forums; paid support available | Official vendor support |
    | Security | Many eyes find and fix flaws quickly | Depends on the vendor; flaws stay hidden |
    | Updates | Frequent | On the vendor's schedule |
    | Vendor lock-in | Low — the code can be forked | High |
    | Customisation | Complete | None beyond what is offered |
    | Accountability | No single responsible party | The vendor is contractually responsible |

    Why Linux dominates where it does
    ```
       Servers        : about 90 % of public cloud workloads and nearly
                        all of the top 500 supercomputers
       Mobile         : Android, built on the Linux kernel, holds roughly
                        70 % of the smartphone market
       Embedded       : routers, smart TVs, cars, industrial controllers
       Reasons        : no licence cost, stability, security, the ability
                        to strip it down to exactly what a device needs,
                        and freedom from any single vendor
    ```

    Licences worth naming
    ```
       GPL        : COPYLEFT - any derivative work must also be open source.
                    Used by the Linux kernel.
       LGPL       : a weaker copyleft, for libraries.
       Apache 2.0 : permissive, and grants patent rights.
       MIT / BSD  : permissive - derivatives may be closed source.
    ```

    - A distinction worth stating: `open source is not the same as free of charge`. Red Hat Enterprise Linux is fully open source, yet the subscription that provides support and certified updates is paid for. The freedom refers to the `source code`, not necessarily to the price.

12. **What is kernel? Write down the objectives of kernel.** *[SPCB Sub-Assistant Programmer 2022 compact it 740 (ET: N/A)]*

    Answer: What a kernel is
    - The `kernel` is the core of the operating system. It is loaded into memory at boot, stays resident until shutdown, and runs in `kernel mode` (privileged mode) with complete access to the hardware and to all memory.
    - It sits between the applications and the hardware, and every request from a program reaches it as a `system call`.
    ```
            USER
              |
           SHELL / APPLICATIONS       user mode
              |
           ---- system call interface ----
              |
           KERNEL                      kernel mode, privileged
              |
           HARDWARE
    ```

    Objectives and functions of the kernel

    1. `Process management`
    ```
       Create , schedule , suspend and terminate processes
       Maintain the Process Control Block for each
       Perform context switching
       Provide inter-process communication : pipes, signals, shared memory,
            message queues
       Detect and handle deadlock
    ```

    2. `Memory management`
    ```
       Allocate and free memory to processes
       Keep track of which parts of memory are in use and by whom
       Implement paging, segmentation and VIRTUAL MEMORY
       PROTECT each process's memory from every other
       Handle page faults and choose pages to replace
    ```

    3. `Device management`
    ```
       Provide DEVICE DRIVERS, so applications need not know the hardware
       Handle INTERRUPTS from devices
       Buffering, caching and spooling
       Schedule disk requests
    ```

    4. `File system management`
    ```
       Create, read, write and delete files and directories
       Maintain the directory structure and the allocation of disk blocks
       Enforce access permissions
    ```

    5. `System call interface`
    ```
       Provide the controlled entry points through which a user program
       asks for a privileged service - the ONLY legal way into kernel mode.

       Examples : open , read , write , fork , exec , wait , exit , kill
    ```

    6. `Security and protection`
    ```
       Authenticate users ; enforce permissions
       Keep one user's data inaccessible to another
       Separate USER mode from KERNEL mode, so an application cannot
            touch the hardware directly
       Maintain an audit trail
    ```

    7. `Resource allocation and arbitration`
    ```
       Share the CPU, memory and devices fairly among competing processes,
       and prevent one process from monopolising any of them.
    ```

    8. `Abstraction`
    ```
       Present a simple, uniform interface over messy hardware. A program
       calls read() whether the data is on an SSD, a hard disk, a network
       share or a USB stick.
    ```

    Types of kernel
    ```
       MONOLITHIC : every service runs in kernel mode, in one address space.
            Fast, but a driver bug can crash the whole system.
            Linux , traditional UNIX , MS-DOS

       MICROKERNEL: only IPC, basic scheduling and memory management run in
            kernel mode ; drivers and file systems are user-space servers.
            Reliable and secure, but slower because of message passing.
            QNX , Minix , L4 , Mach

       HYBRID     : a compromise, which is what real systems use.
            Windows NT , macOS XNU

       EXOKERNEL  : an extreme minimalist design that exposes the hardware
            directly and leaves abstraction to libraries. Research only.
    ```

    Useful commands
    ```bash
       uname -r                 # kernel version
       uname -a                 # full kernel information
       lsmod                    # loaded kernel modules
       dmesg                    # kernel ring buffer messages
       cat /proc/version        # kernel build details
    ```

    - The essential statement: the kernel's objective is to be `the trusted intermediary` — it is the only software with full hardware access, and every other program must ask it for anything privileged. That single design decision is what gives an operating system its protection, its multitasking and its stability.

13. **IBM প্রতিষ্ঠান কর্তৃক কোন Operating System প্রস্তুত করা হয়?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) `IBM` created several operating systems. The most important are these.

    `PC-DOS` (1981)
    - The operating system for the original `IBM Personal Computer`. It was licensed from Microsoft, which sold the same product as `MS-DOS`. IBM's version was called PC-DOS, and later `IBM DOS`.

    `OS/2` (1987)
    - Developed jointly by `IBM and Microsoft`, then continued by IBM alone after the partnership broke up in 1990. A 32-bit, multitasking, graphical operating system, technically ahead of Windows 3.x but commercially defeated by it. Later versions were called `OS/2 Warp`.

    `AIX` (1986)
    - IBM's own version of `UNIX`, still sold today for its `POWER` servers. Used widely in banking and enterprise data centres.

    `OS/360` (1964)
    - The operating system for the `System/360` mainframe — one of the most important operating systems ever written, and the subject of Fred Brooks's book `The Mythical Man-Month`.

    `z/OS`
    - The current mainframe operating system, descended from OS/360 through MVS and OS/390. It still runs the core banking and payment systems of much of the world.

    `i5/OS` (now `IBM i`)
    - The operating system of the AS/400 and its successors, notable for its integrated database.

    Summary

    | Operating system | Year | Platform | Note |
    |---|---|---|---|
    | OS/360 | 1964 | System/360 mainframe | The ancestor of z/OS |
    | PC-DOS | 1981 | IBM PC | Licensed from Microsoft |
    | AIX | 1986 | RS/6000, POWER | IBM's UNIX |
    | OS/2 | 1987 | PC | With Microsoft, then IBM alone |
    | OS/400 → IBM i | 1988 | AS/400 | Integrated database |
    | z/OS | 2000 | Mainframe | Current, from MVS/OS-390 |

    - The short answer usually expected in a paper of this kind is `PC-DOS` or `OS/2`. `AIX` and `z/OS` are the ones still in commercial use, and `OS/360` is the historically most significant.

14. **Explain: Kernel, Cache, Virtual Memory and RAID.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 872-873 (ET: N/A)]*

    Answer: Kernel
    - The `core` of the operating system, resident in memory from boot to shutdown, running in `kernel mode` with full access to the hardware.
    - Functions: `process management` (creation, scheduling, context switching), `memory management` (allocation, paging, virtual memory, protection), `device management` (drivers, interrupts), `file system management`, `system calls` and `security`.
    ```
       Types : MONOLITHIC  - all services in kernel mode (Linux, UNIX)
               MICROKERNEL - only IPC, scheduling, memory (QNX, Minix)
               HYBRID      - a compromise (Windows NT, macOS)
    ```
    - The `shell` is the outer layer the user speaks to; the kernel is the engine underneath. No application touches the hardware directly — every request becomes a `system call`.

    Cache
    - A small, very fast memory placed between the CPU and main memory, holding the instructions and data most recently used.
    - It exists to bridge a huge speed gap: a CPU cycle is under a nanosecond, a DRAM access is 50-100 ns, or roughly 200 cycles.
    ```
       CPU <-> L1 (32-64 KB, ~4 cy) <-> L2 (256KB-1MB, ~12 cy)
           <-> L3 (8-32 MB, ~40 cy) <-> RAM (GB, ~200 cy)
    ```
    ```
       Average access time = hit time + (miss rate x miss penalty)

       Hit time 5 ns , miss penalty 100 ns , hit ratio 95 % :
            5 + (0.05 x 100) = 10 ns , against 105 ns with no cache
    ```
    - It works because of the `principle of locality`: a program reuses the same instructions and data (temporal locality) and reads neighbouring addresses (spatial locality), so a small cache satisfies 90-99 per cent of all requests.
    - Other caches built on the same idea: the `TLB` for address translations, the `disk cache` in RAM, the `browser cache` and the `DNS cache`.

    Virtual memory
    - A technique that lets a process use an address space `larger than the physical RAM`, by keeping only the actively used parts in memory and the rest on disk.
    ```
       Virtual address ----> [ MMU + page table ] ----> Physical address
                                  |
                             page not present?
                                  |
                             PAGE FAULT -> fetch it from disk
    ```
    ```
       Implemented by PAGING : the virtual address space is divided into
       fixed-size PAGES (typically 4 KB), physical memory into FRAMES of
       the same size, and a PAGE TABLE maps one to the other.
    ```
    - Benefits: programs larger than RAM can run; more processes fit in memory, so multiprogramming rises; each process gets its own protected address space; and the programmer need not manage overlays.
    - Cost: a page fault costs milliseconds. If the working sets of the running processes exceed physical memory, the system spends all its time swapping instead of computing — `thrashing`.
    - Page replacement algorithms: `FIFO`, `LRU`, `Optimal`, `Clock (second chance)`, `NRU`.

    RAID
    - `Redundant Array of Independent Disks` — several physical disks combined into one logical drive, for `performance`, `fault tolerance` and `capacity`.
    ```
       Striping  : data split across disks and accessed in parallel -> speed
       Mirroring : the same data written to two disks -> redundancy
       Parity    : an XOR checksum, from which a lost block is rebuilt
    ```

    | Level | Technique | Min disks | Usable | Survives |
    |---|---|---|---|---|
    | RAID 0 | Striping | 2 | 100 % | `Nothing` |
    | RAID 1 | Mirroring | 2 | 50 % | 1 disk |
    | RAID 5 | Striping + distributed parity | 3 | (n-1)/n | 1 disk |
    | RAID 6 | Double parity | 4 | (n-2)/n | 2 disks |
    | RAID 10 | Mirror then stripe | 4 | 50 % | 1 per mirror |

    - `RAID is not a backup`. It protects against `disk failure` alone; a deleted table, ransomware, corruption or a fire is written faithfully to every disk at the same instant.

    How the four relate
    ```
       The KERNEL manages all of them.
       CACHE and VIRTUAL MEMORY are both parts of the MEMORY HIERARCHY -
            cache hides the slowness of RAM, virtual memory hides the
            smallness of RAM by using the disk.
       RAID sits at the bottom of that hierarchy, making the disk itself
            faster and more reliable.
    ```

15. **(a) Briefly describe the function that measure the efficiency of an operating system.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1025 (ET: N/A)]*

    Answer: The efficiency of an operating system is judged by how well it uses the hardware and how well it serves the user. The measures fall into two groups, and they conflict with one another.

    System-oriented measures
    ```
       1. CPU UTILISATION
            The percentage of time the CPU is doing useful work.
            Target : 40 % on a lightly loaded system to 90 % on a heavily
            loaded one. It should be MAXIMISED.

       2. THROUGHPUT
            The number of processes completed per unit time.
            Long jobs give a low figure, short jobs a high one, so it is
            meaningful only for a comparable workload. MAXIMISE.

       3. MEMORY UTILISATION
            How much of physical memory holds useful data rather than
            being free or wasted by fragmentation.

       4. DEVICE UTILISATION
            Keeping the disks and other devices busy in parallel with
            the CPU, which is what multiprogramming is for.

       5. FAIRNESS
            Every process gets a reasonable share, and none STARVES.
    ```

    User-oriented measures
    ```
       6. TURNAROUND TIME
            Submission to completion, for one process.
            Turnaround = Completion - Arrival = Waiting + Burst + I/O
            MINIMISE.

       7. WAITING TIME
            Total time spent in the ready queue.
            Waiting = Turnaround - Burst.  MINIMISE.

       8. RESPONSE TIME
            Submission to the FIRST response. This is what an interactive
            user actually feels, and it matters more than turnaround time
            on a desktop. MINIMISE.

       9. PREDICTABILITY
            The same job should take about the same time each run.
            Essential in real-time systems.

      10. RELIABILITY and AVAILABILITY
            Uptime , mean time between failures , and graceful recovery
            from a fault.
    ```

    The functions whose efficiency is being measured
    ```
       PROCESS MANAGEMENT : the scheduling algorithm decides waiting,
            turnaround and response time.
            Measured by average waiting time and average turnaround time.

       MEMORY MANAGEMENT  : paging and virtual memory decide how many
            processes fit and how often a page fault occurs.
            Measured by the PAGE FAULT RATE and the degree of
            multiprogramming sustained without THRASHING.

       FILE and I/O MANAGEMENT : disk scheduling and buffering decide
            throughput.
            Measured by average seek time, transfer rate and the disk
            cache hit ratio.

       CONTEXT SWITCHING  : pure overhead.
            Measured as switch time / time quantum. It must stay a small
            percentage.

       CACHE PERFORMANCE  :
            Average access time = hit time + (miss rate x miss penalty)
            Measured by the HIT RATIO, which is the single most influential
            number in system performance.
    ```

    Worked illustrations
    ```
       CPU utilisation with n processes each spending fraction p waiting
       for I/O :

            CPU utilisation = 1 - p^n

            p = 0.8 , n = 1 -> 20 %
            p = 0.8 , n = 4 -> 59 %
            p = 0.8 , n = 10 -> 89 %

       This is the quantitative argument for multiprogramming.
    ```
    ```
       Effective memory access time with paging :

            EAT = (1 - p) x memory access + p x page fault time

            Memory access 100 ns , page fault 8 ms , fault rate 1 in 1000 :
            EAT = 0.999 x 100 ns + 0.001 x 8,000,000 ns = 8100 ns

            A fault rate of just 0.1 per cent makes memory 81 times slower.
            This is why the page fault rate must be kept extremely low.
    ```

    The conflicts between the measures
    ```
       Maximising CPU UTILISATION can worsen RESPONSE TIME, because the
            CPU is kept busy with long jobs.

       Minimising average TURNAROUND favours SJF, which STARVES long jobs.

       Minimising RESPONSE TIME favours a small quantum, which raises
            CONTEXT-SWITCH OVERHEAD and lowers throughput.

       Raising the DEGREE OF MULTIPROGRAMMING raises utilisation until the
            working sets exceed memory, at which point THRASHING collapses
            performance entirely.
    ```

    - The conclusion an examiner looks for: `no operating system optimises every measure at once`. A batch system maximises throughput, a time-sharing system minimises response time, and a real-time system maximises predictability. The design is always a deliberate choice among these conflicting criteria.

16. **What is the difference between micro kernel and macro kernel? What are the sub components of I/O manager in Windows NT?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1052-1053 (ET: BUET)]*

    Answer: Micro kernel versus macro (monolithic) kernel

    `Macro kernel (monolithic)`
    - `Every` operating-system service — scheduler, memory manager, file system, device drivers, network stack — runs inside the kernel in `kernel mode`, in one address space.
    - Services call each other by `direct function call`, which is what makes it fast.
    - Examples: `Linux`, traditional `UNIX`, `MS-DOS`, `BSD`.

    `Microkernel`
    - Only the `minimum` runs in kernel mode: inter-process communication, basic scheduling and address-space management. Drivers, file systems and network stacks run as ordinary `user-mode server processes`.
    - They communicate by `message passing` through the kernel, costing two context switches per request.
    - Examples: `QNX`, `Minix`, `Mach`, `L4`, `Symbian`.
    ```
       MONOLITHIC                        MICROKERNEL
       +----------------------+          +----------------------------+
       |     applications     |          | apps | file | driver | net |
       +----------------------+          |      | srvr | server | srv |
       | scheduler | memory   |          +----------------------------+
       | file sys  | drivers  |          |  microkernel : IPC ,       |
       | network   | IPC      |          |  scheduling , memory       |
       +----------------------+          +----------------------------+
       |      hardware        |          |         hardware           |
       +----------------------+          +----------------------------+
    ```

    Difference

    | Point | Macro (monolithic) kernel | Microkernel |
    |---|---|---|
    | Size | Large — millions of lines | Small — often under 10,000 lines |
    | Services in kernel mode | `All` | Only IPC, scheduling, memory |
    | Communication | Direct function calls | `Message passing` |
    | Speed | `Faster` | Slower — IPC overhead |
    | Reliability | A driver crash kills the `whole system` | A server crash kills only that service |
    | Extensibility | Recompile or load a module | Add a user-space process |
    | Debugging | Hard — kernel level | Easy — user level |
    | Security | Large privileged attack surface | Small trusted computing base |
    | Portability | Lower | Higher |
    | Examples | Linux, UNIX | QNX, Minix, L4 |

    - The trade-off in one line: `monolithic buys speed at the cost of reliability; microkernel buys reliability at the cost of speed`. Real systems are `hybrid` — Windows NT moved graphics into the kernel for speed, macOS puts a BSD layer inside Mach, and Linux uses loadable modules to gain flexibility while keeping direct calls.

    Sub-components of the Windows NT I/O Manager

    - The `I/O Manager` is the Executive component that handles all input and output. It defines a uniform, packet-driven interface so that every driver looks the same to the rest of the system.
    ```
       The central object is the IRP - the I/O REQUEST PACKET. Every I/O
       operation becomes an IRP, which is passed DOWN a stack of drivers
       and back up with the result.
    ```

    Its sub-components
    ```
       1. CACHE MANAGER
            Provides a unified file cache for all file systems. Maps file
            data into virtual memory and works with the Memory Manager,
            so that reads are usually satisfied without touching the disk.
            Handles lazy writing and read-ahead.

       2. FILE SYSTEM DRIVERS
            NTFS , FAT32 , exFAT , CDFS , UDF , and network redirectors.
            They translate a file request into disk-block requests.

       3. DEVICE DRIVERS
            Control individual hardware devices. Layered as :
                 HIGHEST-LEVEL : file system drivers
                 INTERMEDIATE  : class drivers, filter drivers,
                                 mirror and encryption drivers
                 LOWEST-LEVEL  : hardware bus drivers, port drivers

       4. NETWORK DRIVERS and REDIRECTORS
            Present remote files and printers as though they were local,
            through the NDIS interface.

       5. PLUG AND PLAY MANAGER
            Detects hardware, allocates resources, loads the right driver
            and supports hot insertion and removal.

       6. POWER MANAGER
            Coordinates power state transitions (sleep, hibernate,
            shutdown) across all devices, sending power IRPs.

       7. WMI (Windows Management Instrumentation) support
            Lets drivers publish management and performance data.

       8. I/O REQUEST PACKET (IRP) MANAGEMENT
            Allocates, queues, completes and cancels IRPs, and manages
            the driver stack each one traverses.
    ```

    How a read travels through it
    ```
       Application calls ReadFile()
            |
       I/O Manager creates an IRP
            |
       Cache Manager - is the data already cached?  ->  yes, return it
            |  no
       File system driver (NTFS) - translate to disk blocks
            |
       Volume / partition driver
            |
       Disk class driver -> port driver -> miniport driver
            |
       Hardware
            |
       Interrupt -> completion travels back UP the same stack
    ```
    - The `layered, packet-driven` design is what allows a filter driver — an antivirus scanner, an encryption layer, a compression layer — to be inserted anywhere in the stack without changing any other driver.

17. **What is operating System? What are the main components of operating System?** *[Bangladesh Competition Commission Programmer 2019 compact it 1059 (ET: DU)]*

    Answer: What an operating system is
    - An `operating system` is the system software that manages the computer's hardware and software resources and provides common services for application programs. It is the `interface between the user and the hardware`.
    ```
            USER
              |
           APPLICATION PROGRAMS
              |
           OPERATING SYSTEM
              |
           HARDWARE
    ```
    - It is the first program loaded after the firmware, and it stays in memory until shutdown. Examples: `Windows, Linux, macOS, Android, iOS, UNIX`.

    Its two roles
    ```
       As a RESOURCE MANAGER : allocates the CPU, memory, devices and files
            among competing processes, fairly and efficiently.

       As an EXTENDED MACHINE : hides messy hardware behind a clean
            interface, so a program calls read() without knowing whether
            the data is on an SSD, a network share or a USB stick.
    ```

    Main components

    1. `Kernel`
    - The core, resident in memory and running in privileged mode with full hardware access. Everything below is either part of it or works through it.

    2. `Process management`
    ```
       Creating, scheduling, suspending and terminating processes
       Maintaining a Process Control Block for each
       Context switching
       Inter-process communication : pipes, signals, shared memory
       Deadlock detection and handling
    ```

    3. `Memory management`
    ```
       Allocating and freeing memory
       Tracking which parts are in use and by whom
       Paging, segmentation and VIRTUAL MEMORY
       Protecting each process's memory from every other
    ```

    4. `File management`
    ```
       Creating, reading, writing and deleting files and directories
       Maintaining the directory structure
       Mapping files onto disk blocks
       Enforcing access permissions
    ```

    5. `Device (I/O) management`
    ```
       Device drivers , which hide hardware differences
       Interrupt handling
       Buffering , caching and spooling
       Disk scheduling
    ```

    6. `Secondary storage management`
    ```
       Free-space management , storage allocation , disk scheduling
    ```

    7. `Security and protection`
    ```
       Authentication , authorisation , encryption , audit logging
       Separating user mode from kernel mode
    ```

    8. `Command interpreter (shell) and user interface`
    ```
       CLI : bash , sh , PowerShell , cmd
       GUI : GNOME , KDE , Windows Explorer , Aqua
    ```

    9. `System call interface`
    ```
       The controlled entry points through which an application requests a
       privileged service - the only legal route into kernel mode.
       Examples : open , read , write , fork , exec , wait , exit
    ```

    10. `Networking`
    ```
       Protocol stacks , sockets , remote file systems
    ```

    Diagram
    ```
       +-----------------------------------------------------+
       |               USER APPLICATIONS                     |
       +-----------------------------------------------------+
       |     SHELL / GUI          |    SYSTEM PROGRAMS       |
       +-----------------------------------------------------+
       |            SYSTEM CALL INTERFACE                    |
       +-----------------------------------------------------+
       |                    KERNEL                           |
       |  Process   | Memory   | File     | Device  | Network|
       |  manager   | manager  | manager  | manager | stack  |
       |            |          |          |         |        |
       |  Scheduler | Paging   | Buffers  | Drivers |        |
       +-----------------------------------------------------+
       |                    HARDWARE                         |
       |     CPU   |   Memory   |   Disk   |   I/O devices   |
       +-----------------------------------------------------+
    ```

    - The essential point: the kernel is the only software with `full hardware access`, and every other program must ask it for anything privileged. That single design decision is what gives an operating system its `protection, multitasking and stability`.

18. **(গ) Operating System-এর সংগঠন সহ কাজ উল্লেখ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1067-1068 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Organisation (structure) of an operating system

    An operating system can be built in several ways. The structures, from simplest to most modern, are these.

    1. `Simple / monolithic structure`
    - No clear separation of modules; everything is written together with no defined interfaces.
    - Example: `MS-DOS`, in which an application could call BIOS routines directly, so a faulty program could crash the machine.

    2. `Layered structure`
    - The system is divided into layers, each built only on the one below it and offering a clean interface to the one above.
    ```
       Layer 5 : user programs
       Layer 4 : I/O management
       Layer 3 : operator-process communication
       Layer 2 : memory management
       Layer 1 : CPU scheduling
       Layer 0 : hardware
    ```
    - Advantage: easy to build, debug and verify one layer at a time. Disadvantage: deciding the order of layers is difficult, and crossing many layers costs performance.
    - Example: the `THE` system, and early UNIX in part.

    3. `Microkernel structure`
    - Only the minimum runs in kernel mode; everything else is a user-space server communicating by message passing.
    - Reliable and extensible, but slower. Example: `QNX`, `Minix`, `Mach`.

    4. `Modular structure`
    - A small core kernel with `loadable modules` added at run time. This is what modern `Linux` uses: `insmod` and `rmmod` add and remove drivers without recompiling or rebooting.
    - It gives the microkernel's flexibility while keeping the monolithic kernel's direct function calls.

    5. `Hybrid structure`
    - A combination chosen for practicality. `Windows NT` and `macOS XNU` both are.

    6. `Virtual machine structure`
    - A hypervisor presents each operating system with the illusion of its own hardware. Examples: `VMware`, `Hyper-V`, `KVM`, `VirtualBox`, and `IBM VM/370`, the original.

    Diagram of the general organisation
    ```
       +-----------------------------------------------------+
       |               USER APPLICATIONS                     |
       +-----------------------------------------------------+
       |     SHELL / GUI          |    SYSTEM PROGRAMS       |
       +-----------------------------------------------------+
       |            SYSTEM CALL INTERFACE                    |
       +-----------------------------------------------------+
       |                    KERNEL                           |
       |  Process   | Memory   | File     | Device  | Network|
       |  manager   | manager  | manager  | manager | stack  |
       +-----------------------------------------------------+
       |                    HARDWARE                         |
       +-----------------------------------------------------+
    ```

    Functions of an operating system
    ```
       1. PROCESS MANAGEMENT
            Create, schedule, suspend and terminate processes ; maintain
            the PCB ; context switching ; inter-process communication ;
            deadlock handling.

       2. MEMORY MANAGEMENT
            Allocate and free memory ; track what is in use ; paging,
            segmentation and virtual memory ; protect one process from
            another.

       3. FILE MANAGEMENT
            Create, read, write and delete files and directories ;
            maintain the directory structure ; map files onto disk blocks ;
            enforce permissions.

       4. DEVICE (I/O) MANAGEMENT
            Device drivers ; interrupt handling ; buffering, caching and
            spooling ; disk scheduling.

       5. SECONDARY STORAGE MANAGEMENT
            Free-space management , allocation , disk scheduling.

       6. SECURITY AND PROTECTION
            Authentication , authorisation , encryption , audit logging ,
            and the separation of user mode from kernel mode.

       7. USER INTERFACE
            A command-line shell, a graphical desktop, or both.

       8. RESOURCE ALLOCATION AND ACCOUNTING
            Share the CPU, memory and devices fairly ; record usage.

       9. ERROR DETECTION AND RECOVERY
            Detect a hardware fault, a bad instruction or a full disk and
            respond without crashing the system.

      10. NETWORKING
            Protocol stacks , sockets , remote file systems.
    ```

    - The two ways of summarising the whole thing, which examiners like: the operating system acts as a `resource manager`, allocating the CPU, memory, devices and files among competing processes, and as an `extended machine`, hiding messy hardware behind a clean and uniform interface.

19. **(খ) Time shearing operating system and Real time operating system-এর মধ্যে পার্থক্য লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1072 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Time-sharing operating system
    - A `time-sharing` system lets `many users` work at the same computer at the same time, by giving each a short `time slice` of the CPU in rotation. The switching is so fast that every user believes the machine is theirs alone.
    - It is `multiprogramming plus a timer`: the CPU is taken away when the quantum expires, not only when a process requests I/O.
    ```
       Goal : MINIMISE RESPONSE TIME, so that interactive work feels instant
       Scheduling : Round Robin, or a multilevel feedback queue
       Examples : UNIX , Linux , Windows , macOS , multi-user mainframes
    ```

    Real-time operating system
    - A `real-time` system guarantees that a task completes within a `fixed deadline`. Correctness depends not only on `what` is computed but on `when` it is delivered — a correct answer that arrives late is a failure.
    ```
       HARD real time : a missed deadline is a TOTAL FAILURE
            pacemaker , airbag , aircraft flight control , reactor shutdown
       SOFT real time : a missed deadline degrades quality
            video streaming , VoIP , online gaming

       Goal : PREDICTABILITY, not average speed
       Scheduling : preemptive priority , Rate Monotonic , Earliest Deadline First
       Examples : VxWorks , QNX , FreeRTOS , RTLinux
    ```

    Difference

    | Point | Time-sharing OS | Real-time OS |
    |---|---|---|
    | Primary goal | Minimise `response time` for users | Meet every `deadline` |
    | Key property | Fairness | `Predictability` (determinism) |
    | Timing | Best effort — no guarantee | Guaranteed worst case |
    | Scheduling | Round Robin, multilevel feedback | Preemptive priority, RMS, EDF |
    | Users | Many, interactive | Usually none — it controls a device |
    | Effect of a delay | Slight inconvenience | Failure, possibly catastrophic |
    | Virtual memory | Standard | `Avoided` in hard real time — a page fault is unpredictable |
    | Kernel | Large, general purpose | Small, fully preemptible |
    | Throughput | Maximised | Sacrificed for predictability |
    | Task priority | Dynamic, adjusted for fairness | Fixed by deadline importance |
    | Memory | Large, paged | Small, often static allocation |
    | Examples | UNIX, Linux, Windows | VxWorks, QNX, FreeRTOS |
    | Used in | Servers, desktops, mainframes | Medical devices, avionics, cars, robots |

    Why a time-sharing system cannot be used for hard real-time work
    ```
       1. VIRTUAL MEMORY : a page fault takes milliseconds, and cannot be
          predicted. An airbag controller cannot risk it.

       2. NON-PREEMPTIBLE KERNEL SECTIONS : a general-purpose kernel spends
          time in critical sections where it cannot be interrupted, so the
          worst-case latency is unbounded.

       3. FAIR SCHEDULING : the scheduler deliberately gives every process
          a turn. A real-time system must let the urgent task run
          IMMEDIATELY, whatever else is waiting.

       4. UNBOUNDED INTERRUPT LATENCY : general-purpose drivers may disable
          interrupts for long periods.
    ```

    The middle ground
    ```
       Linux with the PREEMPT_RT patch makes almost the whole kernel
       preemptible and gives bounded latency, which is enough for SOFT
       real-time work such as audio processing and industrial control -
       but not for a pacemaker.
    ```

    - The point most often misunderstood, and worth stating plainly: `real time does not mean fast`. A system that always responds within 50 ms is real-time; one that usually responds in 1 ms but occasionally takes 200 ms is not. For a safety-critical device, the guarantee matters and the average does not.

20. **(ক) মাল্টি প্রোগ্রামিং অপারেটিং সিস্টেম কী? সচিত্র বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1092 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) A `multiprogramming operating system` keeps `several programs in main memory at the same time`, so that when one program waits for input or output the CPU is given to another instead of sitting idle.

    - Only one program executes at any instant on a single CPU; the operating system `interleaves` them so rapidly that the CPU is never idle while work is waiting.

    The problem it solves
    ```
       A single program alternates between CPU bursts and I/O waits, and a
       typical program spends 60-80 per cent of its time waiting.

       WITHOUT multiprogramming :

       Program A : |CPU|--------- waiting for disk ---------|CPU|
                                 CPU IS IDLE HERE

       WITH multiprogramming :

       Program A : |CPU|........I/O wait.........|CPU|.....I/O.....
       Program B : ......|CPU|.......I/O wait........|CPU|.........
       Program C : ...........|CPU|.......I/O wait........|CPU|....

       CPU busy  : |AAA|BBB|CCC|AAA|BBB|CCC|...   -  NEVER IDLE
    ```

    Memory layout
    ```
       +---------------------------+  high address
       |    Operating system       |
       +---------------------------+
       |    Program A              |
       +---------------------------+
       |    Program B              |     several programs resident
       +---------------------------+     at the same time
       |    Program C              |
       +---------------------------+
       |    Free space             |
       +---------------------------+  0
    ```

    What it requires
    ```
       1. SEVERAL PROGRAMS IN MEMORY at once - fixed partitions in early
          systems, paging and virtual memory in modern ones.

       2. MEMORY PROTECTION - base and limit registers, or the MMU and page
          tables, so one program cannot touch another's memory.

       3. INTERRUPTS - the mechanism that returns control to the OS when
          an I/O operation completes.

       4. CONTEXT SWITCHING - saving the CPU state of one process into its
          PCB and loading another's.

       5. A SCHEDULER - to choose which ready process runs next.

       6. THE PROCESS CONTROL BLOCK - one per process, holding its state,
          program counter, registers, memory limits and open files.
    ```

    CPU utilisation, quantified
    ```
       If each process spends a fraction p of its time waiting for I/O,
       and n processes are in memory :

            CPU utilisation = 1 - p^n

       p = 0.8 , n = 1  ->  20 %
       p = 0.8 , n = 4  ->  59 %
       p = 0.8 , n = 10 ->  89 %
    ```
    - This single formula is the quantitative argument for multiprogramming, and it also shows the diminishing return: beyond a point, adding processes gains little and risks `thrashing`.

    Advantages
    ```
       High CPU utilisation - the CPU is almost never idle
       Higher throughput - more jobs completed per hour
       Better use of memory and devices
       Shorter average waiting time
    ```

    Disadvantages
    ```
       Complex memory management and protection hardware required
       Context-switch overhead
       Scheduling complexity
       Deadlock and synchronisation problems appear
       THRASHING if too many processes are admitted
    ```

    The related terms, which examiners like to see distinguished
    ```
       MULTIPROGRAMMING : several programs in MEMORY ; the switch happens
            when one requests I/O. Goal - keep the CPU busy.

       MULTITASKING     : multiprogramming plus TIME SHARING ; a timer also
            forces a switch, so every task gets a regular turn.
            Goal - responsiveness.

       MULTIPROCESSING  : more than one CPU, so tasks run truly in parallel.

       MULTITHREADING   : one process divided into threads sharing its
            address space.
    ```

21. **Discuss the Operating System architecture and how it works?** *[BINA Assistant Programmer 2019 compact it 1155 (ET: IBA)]*

    Answer: Operating system architecture

    An operating system can be structured in several ways. The main architectures, from oldest to most modern, are these.

    1. `Monolithic architecture`
    - Every service — scheduler, memory manager, file system, drivers, network stack — runs inside the kernel in `kernel mode`, in one address space, calling each other by direct function call.
    ```
       +-------------------------------------------------+
       |          USER APPLICATIONS       (user mode)    |
       +-------------------------------------------------+
       |               SYSTEM CALL INTERFACE             |
       +-------------------------------------------------+
       |   Scheduler | Memory | File system | Drivers    |
       |   Network stack | IPC        (kernel mode)      |
       +-------------------------------------------------+
       |                  HARDWARE                       |
       +-------------------------------------------------+
    ```
    - Fast, but a bug in any driver can crash the whole system. Example: `Linux`, `UNIX`.

    2. `Layered architecture`
    - Divided into layers, each using only the one below and offering a clean interface above.
    ```
       Layer 5 : user programs
       Layer 4 : I/O management
       Layer 3 : operator-process communication
       Layer 2 : memory management
       Layer 1 : CPU scheduling
       Layer 0 : hardware
    ```
    - Easy to build and debug one layer at a time, but crossing many layers costs performance.

    3. `Microkernel architecture`
    - Only IPC, basic scheduling and address-space management run in kernel mode; drivers and file systems are user-space servers communicating by `message passing`.
    - Reliable and secure, but slower. Example: `QNX`, `Minix`, `L4`.

    4. `Modular architecture`
    - A small core with `loadable kernel modules` added at run time. Modern `Linux` uses this: `insmod` and `rmmod` add and remove drivers without a reboot.

    5. `Hybrid architecture`
    - A practical combination. `Windows NT` moved graphics into the kernel for speed; `macOS XNU` puts a BSD layer inside the Mach microkernel.

    How an operating system works — the boot sequence
    ```
       1. POWER ON
       2. FIRMWARE (BIOS/UEFI) runs from ROM : POST, find the boot device
       3. BOOTLOADER (GRUB, Windows Boot Manager) is loaded from disk
       4. The bootloader loads the KERNEL into RAM
       5. The kernel initialises memory management, the scheduler and drivers
       6. The first process is started - 'init' or 'systemd' on Linux
       7. System services and daemons start
       8. The login prompt or graphical desktop appears
    ```

    How it works while running — the system-call cycle
    ```mermaid
    sequenceDiagram
        participant A as Application (user mode)
        participant K as Kernel (kernel mode)
        participant H as Hardware
        A->>K: system call, e.g. read()
        K->>K: switch to kernel mode, validate arguments
        K->>H: issue the device request
        K->>A: block the caller, schedule another process
        H->>K: interrupt - the data is ready
        K->>A: copy the data, mark the process READY
    ```
    ```
       1. The application executes a TRAP instruction (int 0x80, syscall).
       2. The CPU switches from USER mode to KERNEL mode.
       3. The kernel validates the arguments and performs the service.
       4. If it must wait, the process is BLOCKED and the scheduler picks
          another - a CONTEXT SWITCH.
       5. When the device finishes it raises an INTERRUPT.
       6. The handler marks the waiting process READY.
       7. Control returns to user mode with the result.
    ```

    The two modes, which make the whole design work
    ```
       USER MODE   : restricted. A program cannot touch the hardware,
                     cannot access another process's memory, and cannot
                     execute privileged instructions.

       KERNEL MODE : unrestricted. Full access to hardware and all memory.

       A MODE BIT in the processor records which is current. The only way
       to enter kernel mode is through a system call, an interrupt or a
       trap - all of which land at an address the kernel chose.
    ```
    - This single hardware feature is what gives an operating system its `protection`. Without it, any program could overwrite the kernel.

    The four managers at work simultaneously
    ```
       PROCESS MANAGER : chooses which process runs, performs context
            switches, handles creation and termination.

       MEMORY MANAGER  : allocates memory, translates virtual addresses to
            physical ones through the page table, handles page faults.

       FILE MANAGER    : maps file names to disk blocks, enforces
            permissions, maintains the directory tree.

       DEVICE MANAGER  : drives the hardware through drivers, handles
            interrupts, buffers and schedules I/O.
    ```

    - Summed up in one sentence: the operating system is a `permanently resident program that owns the hardware`, and every other program runs in a restricted mode and must ask it — by system call — for anything privileged. Everything else in its design follows from that arrangement.

22. **Difference between Multiprocessing and Multitasking.** *[Palli Sanchay Bank Assistant Database Administrator 2018 compact it 1169 (ET: N/A)]*

    Answer: `Multiprocessing` means a computer having `more than one CPU`, so tasks genuinely execute at the same instant. `Multitasking` means `one CPU` switching rapidly between tasks so that they appear to run at once.

    Multiprocessing
    - Two or more `physical processors` (or cores) in one system, sharing memory and controlled by one operating system.
    ```
       CPU1 : |AAAAAAAAAA|
       CPU2 : |BBBBBBBBBB|      all four at the SAME instant
       CPU3 : |CCCCCCCCCC|      - TRUE parallelism
       CPU4 : |DDDDDDDDDD|
    ```
    ```
       Types :
          SYMMETRIC (SMP)  : every CPU is equal, shares one memory, runs
               the same copy of the OS. The normal arrangement today.
          ASYMMETRIC       : a master CPU controls the others, which are
               assigned specific tasks.
    ```

    Multitasking
    - One CPU divided in time. Each task gets a short `quantum`, and `context switching` moves the CPU between them thousands of times a second.
    ```
       ONE CPU :

       Task A : |AA|      |AA|      |AA|
       Task B :     |BB|      |BB|      |BB|      - INTERLEAVED,
       Task C :         |CC|      |CC|              not simultaneous
    ```
    ```
       Types :
          PREEMPTIVE  : the OS forcibly reclaims the CPU. Windows, Linux.
          COOPERATIVE : a task must yield voluntarily. Early Windows.
    ```

    Difference

    | Point | Multiprocessing | Multitasking |
    |---|---|---|
    | Number of CPUs | `Two or more` | `One` |
    | Execution | `Genuinely simultaneous` | Interleaved — appears simultaneous |
    | Parallelism | Real | Apparent |
    | Mechanism | Parallel execution on separate CPUs | Time slicing and context switching |
    | Requires | Multiple processors, cache coherence | A scheduler and a timer interrupt |
    | Throughput | Rises with the number of CPUs | Unchanged — the same CPU does the work |
    | Failure of one CPU | The system continues on the others | Not applicable |
    | Cost | Extra hardware | No extra hardware |
    | Overhead | Synchronisation, cache coherence | Context switching |
    | Purpose | Raw throughput and reliability | Responsiveness and CPU utilisation |
    | Examples | A multi-core server, a supercomputer | Windows on a single-core machine |

    Why multiprocessing is used
    ```
       Increased THROUGHPUT - more work per unit time
       Economy of SCALE - the CPUs share memory, disks and power supplies,
            so n processors in one box cost far less than n separate machines
       Increased RELIABILITY - graceful degradation. If one CPU fails, the
            others continue, which is why it is used in fault-tolerant systems
    ```

    The limit on multiprocessing — Amdahl's law
    ```
       Speed-up = 1 / [ (1 - P) + P/N ]

       P = the parallelisable fraction of the program
       N = the number of processors
    ```
    ```
       A program that is 90 % parallel :
            N = 2   ->  1.82 times
            N = 4   ->  3.08
            N = 8   ->  4.71
            N = 100 ->  9.17
            N = inf ->  10.0        the hard ceiling

       The 10 per cent serial part alone limits the speed-up to 10,
       however many processors are added.
    ```

    The related terms
    ```
       MULTIPROGRAMMING : several programs in MEMORY, so the CPU switches
            when one waits for I/O. Goal - keep the CPU busy.

       MULTITASKING     : multiprogramming plus TIME SHARING, so a timer
            also forces a switch. Goal - responsiveness.

       MULTITHREADING   : one PROCESS divided into threads sharing an
            address space. Cheaper to switch than a process.

       MULTIPROCESSING  : more than one CPU. The only one that gives
            TRUE parallelism.
    ```
    - In practice a modern machine uses all four at once: eight cores really execute in parallel (multiprocessing), each core time-slices among many processes (multitasking), hundreds of processes are resident (multiprogramming), and each browser tab is a thread (multithreading).

23. **Difference between Multitasking and Multiprogramming.** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1213 (ET: N/A)]*

    Answer: `Multitasking` and `multiprogramming` are closely related — multitasking is multiprogramming with time sharing added — which is why the distinction is so often asked.

    Multiprogramming
    - Keeping `several programs in main memory` at once, so that when one waits for I/O the CPU is given to another rather than sitting idle.
    - The switch is triggered by an `I/O request` or by the process terminating. A program that never does I/O keeps the CPU indefinitely.
    ```
       Program A : |CPU|........I/O wait.........|CPU|
       Program B : ......|CPU|.......I/O wait........|CPU|

       The switch happens when A asks for I/O, not on a clock tick.
    ```
    ```
       GOAL : maximise CPU UTILISATION
       Origin : batch systems of the 1960s
    ```

    Multitasking
    - Multiprogramming `plus a timer`. Each task gets a fixed `time quantum`, and when it expires the operating system `preempts` the task whether or not it has asked for I/O.
    ```
       Task A : |AA|      |AA|      |AA|
       Task B :     |BB|      |BB|      |BB|
       Task C :         |CC|      |CC|

       The switch happens on every quantum expiry.
    ```
    ```
       GOAL : minimise RESPONSE TIME, so the system feels interactive
       Origin : time-sharing systems
    ```

    Difference

    | Point | Multiprogramming | Multitasking |
    |---|---|---|
    | Definition | Several programs held in memory | Several tasks share the CPU by time slicing |
    | Switch triggered by | An `I/O request` or termination | A `timer interrupt` (quantum expiry) |
    | Preemption | Not necessarily | `Always` |
    | Primary goal | Maximise CPU utilisation | Minimise response time |
    | Time quantum | Not used | `Essential` |
    | Interactivity | Poor | `Good` |
    | User interaction | Little or none | Continuous |
    | Context switches | Fewer | Many more |
    | Overhead | Lower | Higher |
    | Typical system | Batch | Time-sharing, desktop |
    | Examples | Early mainframe batch systems | Windows, Linux, macOS, Android |

    The relationship between them
    ```
       MULTITASKING is a LOGICAL EXTENSION of MULTIPROGRAMMING.

       Every multitasking system is also a multiprogramming system,
       because it must hold several programs in memory to switch between.
       But a multiprogramming system is NOT necessarily multitasking - if
       it switches only on I/O, a compute-bound job can hold the CPU for
       minutes, which makes interactive use impossible.
    ```

    What both require
    ```
       Several programs resident in memory
       MEMORY PROTECTION, so one cannot corrupt another
       INTERRUPTS, to return control to the operating system
       CONTEXT SWITCHING, with a Process Control Block per process
       A SCHEDULER

       Multitasking additionally requires a TIMER INTERRUPT, which is what
       makes preemption possible.
    ```

    The full family, for completeness
    ```
       MULTIPROGRAMMING : several programs in memory ; switch on I/O
       MULTITASKING     : + time sharing ; switch on a timer
       MULTITHREADING   : one process split into threads sharing its
                          address space ; cheaper to switch
       MULTIPROCESSING  : more than one CPU ; TRUE parallelism
    ```
    - A modern machine uses all four simultaneously, which is why the terms are so easily confused. The single distinguishing question to ask is: `what causes the switch?` If it is an I/O request, that is multiprogramming; if it is a clock tick, that is multitasking.

24. **Explain the functionalities of operating system.** *[ICT Ministry Assistant Programmer 2017 compact it 1239-1240 (ET: N/A)]*

    Answer: An `operating system` manages the computer's hardware and software resources and provides common services to application programs. Its functionalities are the following.

    1. Process management
    ```
       Create , schedule , suspend and terminate processes
       Maintain a PROCESS CONTROL BLOCK for each, holding its state,
            program counter, registers, memory limits and open files
       Perform CONTEXT SWITCHING between processes
       Provide INTER-PROCESS COMMUNICATION : pipes, signals, shared
            memory, message queues
       Detect and handle DEADLOCK
       Synchronise concurrent processes with semaphores and mutexes
    ```

    2. Memory management
    ```
       Allocate memory to a process and free it afterwards
       Keep track of which parts of memory are in use and by whom
       Implement PAGING, SEGMENTATION and VIRTUAL MEMORY, so a program
            larger than RAM can run
       PROTECT each process's memory from every other
       Handle page faults and choose which page to replace
       Decide the degree of multiprogramming, and avoid THRASHING
    ```

    3. File management
    ```
       Create, read, write, delete and rename files and directories
       Maintain the directory structure and the file allocation table
       Map a file name onto physical disk blocks
       Enforce ACCESS PERMISSIONS - who may read, write or execute
       Provide backup and recovery facilities
    ```

    4. Device (I/O) management
    ```
       Provide DEVICE DRIVERS, so applications need not know the hardware
       Handle INTERRUPTS from devices
       BUFFERING - smooth the speed mismatch between fast CPU and slow device
       CACHING - keep frequently used data in fast memory
       SPOOLING - queue jobs for a shared device such as a printer
       Schedule disk requests : FCFS, SSTF, SCAN, C-SCAN
    ```

    5. Secondary storage management
    ```
       Free-space management , storage allocation , disk scheduling
       Mounting and unmounting file systems
    ```

    6. Security and protection
    ```
       AUTHENTICATION - verify who the user is (password, biometric, MFA)
       AUTHORISATION  - decide what that user may do
       Separate USER MODE from KERNEL MODE, so an application cannot touch
            the hardware directly
       Encryption , firewalls , audit logging
       Isolate one user's data from another's
    ```

    7. User interface
    ```
       Command-line shell : bash , PowerShell , cmd
       Graphical shell    : GNOME , KDE , Windows Explorer , Aqua
    ```

    8. Resource allocation and accounting
    ```
       Share the CPU, memory, devices and files fairly among competing
       processes ; prevent any one from monopolising a resource ;
       record usage for billing or analysis
    ```

    9. Error detection and recovery
    ```
       Detect a hardware fault, a bad instruction, an arithmetic error,
       a full disk or a network failure, and respond without crashing
       the whole system
    ```

    10. Networking
    ```
       Protocol stacks , sockets , remote file systems , name resolution
    ```

    11. Booting the system
    ```
       Load itself from disk, initialise the hardware, start the first
       process and bring the system to a usable state
    ```

    The two ways of summarising all of it
    ```
       As a RESOURCE MANAGER
            It allocates the CPU, memory, devices and files among competing
            processes, fairly and efficiently, and keeps them from
            interfering with one another.

       As an EXTENDED MACHINE (a virtual machine)
            It hides messy hardware behind a clean, uniform interface. A
            program calls read() whether the data is on an SSD, a hard
            disk, a network share or a USB stick - and never has to know.
    ```

    - The mechanism that makes all of it enforceable is the `two-mode` design: a `mode bit` in the processor distinguishes user mode from kernel mode, and the only ways into kernel mode are a `system call`, an `interrupt` or a `trap` — all of which land at an address the kernel itself chose. Without that single hardware feature, none of the protection above would be possible.

## Deadlock & Resource Allocation (23)

1. **What is Deadlock? Given a scenery and find out the process is face deadlock sitiation?** *[IFIC Bank Officer IT 2025 compact it 1448 (ET: IFIC)]*

   Answer: What deadlock is
   - A `deadlock` is a state in which two or more processes are each `waiting for a resource held by another`, so none of them can ever proceed. They wait forever.
   ```
      P1 holds A and wants B
      P2 holds B and wants A
           -> neither can continue , and neither will release what it has
   ```

   The four necessary conditions — all must hold at once
   ```
      1. MUTUAL EXCLUSION : a resource can be held by only one process
      2. HOLD AND WAIT    : a process holds resources while requesting more
      3. NO PREEMPTION    : a resource cannot be taken away by force
      4. CIRCULAR WAIT    : a closed chain of processes, each waiting on
                            the next
   ```

   Scenario, and how to test it

   A classic case
   ```
      Two processes share a printer (A) and a scanner (B).

      Time  P1                          P2
      ----  --------------------------  --------------------------
      t1    request A  -> granted
      t2                                request B  -> granted
      t3    request B  -> WAITS (P2 has it)
      t4                                request A  -> WAITS (P1 has it)

      DEADLOCK.
   ```

   Checking the four conditions against the scenario
   ```
      MUTUAL EXCLUSION : the printer and scanner can serve only one
           process at a time                                     HOLDS
      HOLD AND WAIT    : P1 holds A while waiting for B           HOLDS
      NO PREEMPTION    : neither device can be seized             HOLDS
      CIRCULAR WAIT    : P1 -> P2 -> P1                           HOLDS

      All four hold, so the system IS deadlocked.
   ```

   Resource allocation graph — the formal test
   ```mermaid
   flowchart LR
       P1((P1)) -->|requests| B[Resource B]
       B -->|assigned to| P2((P2))
       P2 -->|requests| A[Resource A]
       A -->|assigned to| P1
   ```
   ```
      ---> from a PROCESS to a RESOURCE means a REQUEST
      ---> from a RESOURCE to a PROCESS means an ASSIGNMENT

      RULE :
         If every resource has ONE instance :
              a CYCLE  <=>  a DEADLOCK
         If a resource has SEVERAL instances :
              a cycle is NECESSARY but NOT SUFFICIENT - it may still be safe
   ```
   - Here the graph contains the cycle `P1 -> B -> P2 -> A -> P1`, and every resource has one instance, so the deadlock is confirmed.

   A scenario that is NOT a deadlock
   ```
      Time  P1                          P2
      ----  --------------------------  --------------------------
      t1    request A  -> granted
      t2    request B  -> granted
      t3    release A , release B
      t4                                request A  -> granted
      t5                                request B  -> granted

      NO circular wait, because P1 acquired BOTH resources before P2
      asked for either. The system is safe.
   ```
   - This is exactly why `ordered acquisition` prevents deadlock: if every process takes A before B, a cycle can never form.

   How to answer such a question
   ```
      1. List which process holds which resource, and what each is waiting for.
      2. Draw the resource allocation graph.
      3. Look for a CYCLE.
      4. If resources are single-instance, a cycle means deadlock.
         If multi-instance, run the SAFETY ALGORITHM (Banker's) to see
         whether a safe sequence exists.
      5. Confirm all four conditions hold, and say which one would break
         the deadlock if removed.
   ```

2. **The four conditions that are necessary for a resource deadlock to occur are mutual exclusion, hold and wait, no preemption and circular wait. Give an example to show that these conditions are not sufficient for a resource deadlock to occur.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*

   Answer: The four conditions are `mutual exclusion`, `hold and wait`, `no preemption` and `circular wait`. They are `necessary` — a deadlock cannot occur unless all four hold — but they are `not jointly sufficient` in a system with multiple instances of a resource.

   The example that shows they are not sufficient
   ```
      A system has TWO instances of resource R.
      Two processes, P1 and P2, each hold one instance and each wants
      one more.
   ```
   ```
      Allocation :  P1 holds 1 instance of R
                    P2 holds 1 instance of R
      Request    :  P1 wants 1 more
                    P2 wants 1 more
      Available  :  0
   ```
   Resource allocation graph
   ```
           P1 ---request--->  [ R : two instances ]
           P2 ---request--->  [ R ]
           [ R ] ---assigned---> P1
           [ R ] ---assigned---> P2

      This graph CONTAINS A CYCLE :  P1 -> R -> P2 -> R -> P1
   ```
   - All four conditions hold: R is mutually exclusive, both processes hold while waiting, neither instance can be preempted, and there is a circular wait in the graph.
   - Yet the system is `not necessarily deadlocked`. If a `third process P3` also holds an instance and is about to release it, the request can be satisfied and everyone proceeds.

   A cleaner version of the same argument
   ```
      Three instances of R , three processes.

      P1 holds 1 and wants 1 more
      P2 holds 1 and wants 1 more
      P3 holds 1 and will RELEASE it without asking for more

      The graph has a cycle among P1 and P2, and all four conditions
      appear to hold - but when P3 releases its instance, P1 obtains it,
      finishes, releases both, and P2 then proceeds.

      NO DEADLOCK, despite the cycle.
   ```

   Why the distinction matters
   ```
      SINGLE-instance resources :
           a cycle in the resource allocation graph  <=>  DEADLOCK
           (necessary AND sufficient)

      MULTI-instance resources :
           a cycle is NECESSARY but NOT SUFFICIENT
           A deadlock implies a cycle, but a cycle does not imply a deadlock.
   ```
   - This is precisely why the `Banker's algorithm` exists. For multi-instance resources the graph alone cannot decide, so the `safety algorithm` is run: if some sequence of processes can be completed with the resources available, the state is `safe` even though a cycle is present.

   The correct statement of the theorem
   ```
      Deadlock  =>  all four conditions hold        (they are NECESSARY)
      All four conditions hold  =>  deadlock        FALSE in general

      The four conditions plus NO SAFE SEQUENCE  =>  deadlock
   ```

   Which condition each prevention method attacks
   ```
      MUTUAL EXCLUSION : cannot usually be removed - a printer really can
           serve one job at a time. Spooling removes it where possible.

      HOLD AND WAIT    : removed by requiring a process to request ALL its
           resources at once, or to release everything before asking again.
           Cost : low utilisation and possible starvation.

      NO PREEMPTION    : removed by allowing a resource to be seized and
           the victim rolled back. Works for CPU and memory, not for a
           printer mid-page.

      CIRCULAR WAIT    : removed by imposing a TOTAL ORDER on resources
           and requiring every process to request them in increasing
           order. This is the most PRACTICAL method, and the one used in
           real kernel code.
   ```
   - Breaking `any one` of the four is enough to make deadlock impossible, which is the whole point of stating them as necessary conditions.

3. **(a) Define operating system. Why resource allocation graph used for deadlock detection?** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*

   Answer: Definition of an operating system
   - An `operating system` is the system software that manages the computer's hardware and software resources and provides common services for application programs. It is the `interface between the user and the hardware`.
   ```
           USER  ->  APPLICATIONS  ->  OPERATING SYSTEM  ->  HARDWARE
   ```
   - Its two roles: a `resource manager`, allocating the CPU, memory, devices and files among competing processes; and an `extended machine`, hiding messy hardware behind a clean uniform interface.
   - Its main components: the `kernel`, and the `process`, `memory`, `file`, `device` and `security` managers, reached through the `system call interface`.
   - Examples: `Windows, Linux, macOS, Android, iOS, UNIX`.

   Why a resource allocation graph is used for deadlock detection
   - A `resource allocation graph (RAG)` is a directed graph that records, at one instant, `who holds what` and `who is waiting for what`. Deadlock is a property of exactly that information, so the graph captures the whole problem in one picture.
   ```
      Vertices :  P = processes , drawn as circles
                  R = resources , drawn as rectangles, with a dot per instance

      Edges    :  P --> R    a REQUEST edge : P is waiting for R
                  R --> P    an ASSIGNMENT edge : an instance of R is held by P
   ```

   Example — a deadlock
   ```mermaid
   flowchart LR
       P1((P1)) -->|requests| R2[R2]
       R2 -->|assigned| P2((P2))
       P2 -->|requests| R1[R1]
       R1 -->|assigned| P1
   ```
   ```
      The cycle  P1 -> R2 -> P2 -> R1 -> P1  is present.
      Both resources have ONE instance, so this IS a deadlock.
   ```

   The rule the graph gives
   ```
      If EVERY resource has a SINGLE instance :
           a CYCLE  <=>  a DEADLOCK        (necessary AND sufficient)

      If some resource has SEVERAL instances :
           a cycle is NECESSARY but NOT SUFFICIENT
           A deadlock implies a cycle, but a cycle may still be safe.
   ```
   - With multiple instances the graph must be supplemented by the `safety algorithm` (the Banker's algorithm), which asks whether some order of completion exists.

   Why the graph is the right tool
   ```
      1. It makes the CIRCULAR WAIT condition VISIBLE. Circular wait is
         one of the four necessary conditions, and it is the only one that
         depends on the current state rather than on the resource's nature.

      2. Deadlock detection becomes CYCLE DETECTION, a standard graph
         problem solvable by DFS in O(V + E).

      3. It shows exactly WHICH processes are involved, so a victim can be
         chosen for rollback or termination.

      4. It is easy to MAINTAIN INCREMENTALLY - an edge is added on every
         request and removed on every release, so the graph is always current.

      5. It can be used PREDICTIVELY. With a CLAIM edge (dashed, P ---> R,
         meaning "P may request R later") the system can refuse a request
         that would create a cycle - which is deadlock AVOIDANCE rather
         than detection.
   ```

   The wait-for graph, its compressed form
   ```
      For single-instance resources the resources can be removed
      entirely, leaving only  Pi -> Pj  meaning "Pi waits for a resource
      held by Pj".

           P1 -> P2 -> P3 -> P1        a cycle -> DEADLOCK

      This halves the graph and is what the operating system actually
      maintains for detection.
   ```

   - The alternative for multi-instance systems is the `Banker's algorithm`, which computes a `Need` matrix and looks for a safe sequence. The graph is preferred when instances are single, because cycle detection is far cheaper than running the safety algorithm on every request.

4. **What is Deadlock? Write Conditions for Deadlock and also write Deadlock.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*

   Answer: What deadlock is
   - A `deadlock` is a state in which a set of processes are each `waiting for a resource held by another process in the same set`, so none can ever proceed. Every one of them waits forever.
   ```
      P1 holds A and requests B
      P2 holds B and requests A
           -> neither can continue, and neither will release what it holds
   ```

   The four necessary conditions
   - All four must hold `simultaneously` for a deadlock to be possible. They are called the `Coffman conditions`.
   ```
      1. MUTUAL EXCLUSION
           At least one resource is non-shareable - only one process may
           use it at a time. A printer, a tape drive, a write lock.

      2. HOLD AND WAIT
           A process holds at least one resource while waiting to acquire
           others that are currently held by someone else.

      3. NO PREEMPTION
           A resource cannot be forcibly taken from a process. It is
           released only voluntarily, when the process has finished with it.

      4. CIRCULAR WAIT
           A closed chain of processes exists, P0 -> P1 -> ... -> Pn -> P0,
           in which each is waiting for a resource held by the next.
   ```
   - Breaking `any one` of the four makes deadlock impossible, which is exactly how prevention works.

   Deadlock handling — the four strategies
   ```
      1. DEADLOCK PREVENTION
           Design the system so that one of the four conditions can never
           hold.

      2. DEADLOCK AVOIDANCE
           Allow the conditions, but examine each request before granting
           it and refuse any that could lead to an unsafe state.
           The BANKER'S ALGORITHM.

      3. DEADLOCK DETECTION AND RECOVERY
           Let deadlocks happen, detect them with a wait-for graph or the
           safety algorithm, and then recover by killing or rolling back
           a victim.

      4. IGNORE THE PROBLEM
           The OSTRICH ALGORITHM. Deadlocks are rare, so the cost of
           prevention outweighs the cost of an occasional reboot.
           This is what UNIX, Linux and Windows actually do.
   ```

   Deadlock prevention, condition by condition
   ```
      MUTUAL EXCLUSION
           Usually cannot be removed - a printer really can serve one job
           at a time. SPOOLING removes it where the resource permits.

      HOLD AND WAIT
           Require a process to request ALL its resources at once, before
           it starts ; or to release everything it holds before asking for
           more.
           Cost : low resource utilisation , and possible STARVATION.

      NO PREEMPTION
           If a process holding resources requests one that cannot be
           granted, take away everything it holds and restart it later.
           Works for the CPU and memory ; useless for a printer mid-page.

      CIRCULAR WAIT
           Impose a TOTAL ORDER on all resource types and require every
           process to request them in INCREASING order.
           This is the MOST PRACTICAL method, and it is what real kernel
           code uses - "always lock A before B".
   ```

   Deadlock avoidance — the Banker's algorithm
   ```
      Each process declares its MAXIMUM need in advance.
      Before granting a request the system checks whether the resulting
      state is SAFE - that is, whether some sequence of processes exists
      in which each can obtain its maximum need and finish.

      SAFE   -> grant the request
      UNSAFE -> make the process wait, even though the resources are free
   ```
   - Note that `unsafe is not the same as deadlocked`. An unsafe state merely means deadlock has become possible.

   Detection and recovery
   ```
      DETECTION : maintain a WAIT-FOR GRAPH and look for a cycle
           (single-instance resources), or run the safety algorithm
           periodically (multi-instance).

      RECOVERY  :
           Terminate all deadlocked processes - simple, but costly
           Terminate one at a time until the cycle breaks
           Preempt resources from a victim and roll it back to a checkpoint

      Choosing the victim : the process with the least work done, the
           fewest resources held, or the lowest priority. Guard against
           STARVATION by not choosing the same victim repeatedly.
   ```

   Comparison

   | Strategy | When applied | Cost | Used in practice |
   |---|---|---|---|
   | Prevention | Design time | Low utilisation | Yes, for lock ordering |
   | Avoidance | Every request | Needs maximum claims in advance | Rarely |
   | Detection and recovery | Periodically | Detection overhead, rollback | In databases |
   | Ignore | Never | An occasional hang | `Yes` — Windows, Linux, UNIX |

   - Why general-purpose systems ignore it: deadlock is rare, prevention would cripple utilisation, and avoidance requires every process to declare its maximum needs in advance, which no ordinary program can do. `Database systems`, by contrast, do detect deadlocks — they build a wait-for graph, choose a victim and roll its transaction back automatically, because a transaction can be safely undone whereas an arbitrary process cannot.

5. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances).** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1321 (ET: DU)]*
   * (a) Need matrix
   * (b) Safe state or Unsafe
   Snapshot at time T_0:
The content of the matrix. Need is defined to be Max – Allocation.

   Answer: Given, the standard snapshot at time T0
   ```
      5 processes P0 to P4 ,  3 resource types A (10) , B (5) , C (7)

               Allocation        Max
                A  B  C        A  B  C
      P0        0  1  0        7  5  3
      P1        2  0  0        3  2  2
      P2        3  0  2        9  0  2
      P3        2  1  1        2  2  2
      P4        0  0  2        4  3  3
   ```

   Available resources
   ```
      Total allocated :
           A = 0+2+3+2+0 = 7
           B = 1+0+0+1+0 = 2
           C = 0+0+2+1+2 = 5

      Available = Total - Allocated
           A = 10 - 7 = 3
           B =  5 - 2 = 3
           C =  7 - 5 = 2

      Available = ( 3 , 3 , 2 )
   ```

   (a) The Need matrix
   ```
      Need = Max - Allocation
   ```
   ```
               Allocation        Max          NEED
                A  B  C        A  B  C      A  B  C
      P0        0  1  0        7  5  3      7  4  3
      P1        2  0  0        3  2  2      1  2  2
      P2        3  0  2        9  0  2      6  0  0
      P3        2  1  1        2  2  2      0  1  1
      P4        0  0  2        4  3  3      4  3  1
   ```
   Working
   ```
      P0 : 7-0 , 5-1 , 3-0  ->  7  4  3
      P1 : 3-2 , 2-0 , 2-0  ->  1  2  2
      P2 : 9-3 , 0-0 , 2-2  ->  6  0  0
      P3 : 2-2 , 2-1 , 2-1  ->  0  1  1
      P4 : 4-0 , 3-0 , 3-2  ->  4  3  1
   ```

   (b) Is the state safe? — run the safety algorithm
   ```
      Work = Available = (3, 3, 2)
      Finish[i] = false for all i

      Repeatedly find a process whose NEED <= WORK , run it, and add its
      ALLOCATION back to WORK.
   ```
   ```
      Step 1 : Work = (3,3,2)
               P0 need (7,4,3) <= (3,3,2) ? NO
               P1 need (1,2,2) <= (3,3,2) ? YES   -> run P1
               Work = (3,3,2) + (2,0,0) = (5,3,2)

      Step 2 : Work = (5,3,2)
               P0 need (7,4,3) ? NO
               P2 need (6,0,0) ? NO
               P3 need (0,1,1) <= (5,3,2) ? YES   -> run P3
               Work = (5,3,2) + (2,1,1) = (7,4,3)

      Step 3 : Work = (7,4,3)
               P0 need (7,4,3) <= (7,4,3) ? YES, but take P4 first as in
               the standard order
               P4 need (4,3,1) <= (7,4,3) ? YES   -> run P4
               Work = (7,4,3) + (0,0,2) = (7,4,5)

      Step 4 : Work = (7,4,5)
               P0 need (7,4,3) <= (7,4,5) ? YES   -> run P0
               Work = (7,4,5) + (0,1,0) = (7,5,5)

      Step 5 : Work = (7,5,5)
               P2 need (6,0,0) <= (7,5,5) ? YES   -> run P2
               Work = (7,5,5) + (3,0,2) = (10,5,7)
   ```
   ```
      All five processes finished, and Work has returned to the total
      ( 10 , 5 , 7 ) - which confirms the arithmetic.

      The system is in a SAFE STATE.

      SAFE SEQUENCE :  < P1 , P3 , P4 , P0 , P2 >
   ```
   - Other safe sequences exist, such as `<P1, P3, P0, P2, P4>`. A state is safe if `at least one` such sequence exists.

   Checking an additional request — the resource-request algorithm
   ```
      Suppose P1 now requests (1, 0, 2).

      Step 1 : Request <= Need ?
               (1,0,2) <= (1,2,2)   YES

      Step 2 : Request <= Available ?
               (1,0,2) <= (3,3,2)   YES

      Step 3 : PRETEND to grant it :
               Available = (3,3,2) - (1,0,2) = (2,3,0)
               Alloc P1  = (2,0,0) + (1,0,2) = (3,0,2)
               Need  P1  = (1,2,2) - (1,0,2) = (0,2,0)

      Step 4 : Run the safety algorithm on the new state.
               A safe sequence < P1, P3, P4, P0, P2 > still exists,
               so the request is GRANTED.
   ```

   - Points worth stating: `safe` and `deadlock-free` are not the same. Every safe state is deadlock-free, but an `unsafe` state is not necessarily deadlocked — it only means the system can no longer guarantee that deadlock will be avoided. The Banker's algorithm is conservative for exactly that reason, and it also requires every process to declare its `maximum need in advance`, which is why real operating systems do not use it.

6. **(a) Explain Circular wait deadlock.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 415 (ET: BUET)]*

   Answer: `Circular wait` is one of the four necessary conditions for deadlock. It holds when a `closed chain` of processes exists, in which each process is waiting for a resource held by the next process in the chain.
   ```
      P0 waits for a resource held by P1
      P1 waits for a resource held by P2
      ...
      Pn waits for a resource held by P0        <- the chain CLOSES
   ```

   The simplest case — two processes
   ```
      P1 holds A , requests B
      P2 holds B , requests A

           P1 ---waits for---> P2
            ^                   |
            |                   |
            +----waits for------+

      The chain is closed, so neither can ever proceed.
   ```
   ```mermaid
   flowchart LR
       P1((P1)) -->|requests| B[Resource B]
       B -->|held by| P2((P2))
       P2 -->|requests| A[Resource A]
       A -->|held by| P1
   ```

   A three-process chain
   ```
      P1 holds A , wants B
      P2 holds B , wants C
      P3 holds C , wants A

           P1 -> P2 -> P3 -> P1

      Each is blocked, and none will release, so all three wait forever.
   ```

   The everyday illustration — the four-way crossing
   ```
      Four cars reach a crossroads at the same moment, each blocking the
      next one's path :

                 car A (northbound)
                      |
      car D --------- + --------- car B
      (eastbound)     |          (westbound)
                 car C (southbound)

      A blocks B , B blocks C , C blocks D , D blocks A.
      No car can move. This is a physical circular wait.
   ```

   Why it is the condition worth attacking
   ```
      MUTUAL EXCLUSION cannot usually be removed - a printer really can
           serve one job at a time.
      HOLD AND WAIT can be removed only by making a process claim
           everything at once, which wastes resources badly.
      NO PREEMPTION cannot be removed for a printer or a tape drive.

      CIRCULAR WAIT can be removed CHEAPLY, by imposing an ORDER.
   ```

   How circular wait is prevented — resource ordering
   ```
      Assign every resource type a unique NUMBER, and require every
      process to request resources in STRICTLY INCREASING order.

           F(printer)  = 1
           F(scanner)  = 2
           F(disk)     = 3

      A process holding the scanner (2) may request the disk (3),
      but may NOT request the printer (1) without first releasing
      the scanner.
   ```
   ```
      Why a cycle then becomes impossible :

      Suppose a cycle P0 -> P1 -> ... -> Pn -> P0 existed. Following the
      chain, each process holds a LOWER-numbered resource and waits for a
      HIGHER-numbered one, so the numbers strictly increase all the way
      round. But going all the way round returns to the start, which
      would require F(R) < F(R) - a contradiction.

      Therefore NO CYCLE CAN FORM.
   ```
   - This is the method real kernel and database code uses. The convention "always take lock A before lock B" is exactly resource ordering, and it is why multi-threaded code documents its lock order.

   Detecting it
   ```
      Build a WAIT-FOR GRAPH : one node per process, and an edge
      Pi -> Pj whenever Pi waits for a resource held by Pj.

      A CYCLE in that graph is a circular wait.
      Cycle detection by DFS costs O(V + E).
   ```
   - For `single-instance` resources a cycle means a deadlock. For `multi-instance` resources a cycle is necessary but not sufficient, so the `Banker's safety algorithm` must be run instead.

   - The point to state clearly: `circular wait is the only one of the four conditions that depends on the current state rather than on the nature of the resource`. That is why it is both the easiest to detect and the cheapest to prevent.

7. **Give the necessary conditions for deadlock to occur. Is it possible to have deadlock involving only a single process? Explain your answer.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 422 (ET: BIBM)]*

   Answer: The necessary conditions
   - All `four` must hold simultaneously for a deadlock to be possible. They are the `Coffman conditions`.
   ```
      1. MUTUAL EXCLUSION
           At least one resource is non-shareable - only one process may
           hold it at a time.

      2. HOLD AND WAIT
           A process holds at least one resource while waiting for others
           that are held by other processes.

      3. NO PREEMPTION
           A resource cannot be forcibly taken away; it is released only
           voluntarily by the process holding it.

      4. CIRCULAR WAIT
           A closed chain P0 -> P1 -> ... -> Pn -> P0 exists, in which
           each process waits for a resource held by the next.
   ```
   - Breaking any one of the four makes deadlock impossible.

   Is deadlock possible with only a single process?

   `Yes — but only in a technical sense, and only if the resource is non-reentrant.`

   The case where it CAN happen
   ```
      A single process deadlocks itself if it requests a resource it
      already holds, and that resource is NOT REENTRANT.

      Example - a non-reentrant mutex :

           lock(m);            // acquired
           ...
           lock(m);            // requests the SAME lock again
                               // -> blocks, waiting for ITSELF
                               // -> it will never release, so it waits
                               //    forever

      This is SELF-DEADLOCK, and it is a real and common bug. It happens
      when a function that already holds a lock calls another function
      that also tries to take it.
   ```
   - Checking the four conditions against it:
   ```
      MUTUAL EXCLUSION : the mutex admits one holder             HOLDS
      HOLD AND WAIT    : the process holds m and waits for m     HOLDS
      NO PREEMPTION    : the mutex cannot be seized              HOLDS
      CIRCULAR WAIT    : the chain is  P -> P , a cycle of
                         LENGTH ONE                              HOLDS
   ```
   - All four hold, so it satisfies the formal definition. The circular wait is degenerate — a self-loop — but it is a cycle nonetheless.

   The case where it CANNOT happen
   ```
      If the resource is REENTRANT (a recursive mutex, for example), the
      second request is granted immediately because the owner is the same
      thread. No wait occurs, so no deadlock.

      A recursive lock keeps a COUNT :
           lock(m);   count = 1
           lock(m);   count = 2      granted, same owner
           unlock(m); count = 1
           unlock(m); count = 0      now released
   ```

   The formal answer usually expected
   ```
      In the STRICT textbook model, deadlock is defined over a SET of
      two or more processes, so a single process is excluded by definition
      and the answer is NO.

      In PRACTICE, self-deadlock on a non-reentrant lock is a genuine
      phenomenon and satisfies all four conditions with a cycle of
      length one, so the answer is YES.

      The safe exam answer states BOTH, gives the non-reentrant mutex
      example, and notes that a recursive mutex prevents it.
   ```

   Related single-process hangs that are `not` deadlock
   ```
      INFINITE LOOP     : the process is RUNNING, not waiting. Not deadlock.
      BUSY WAITING      : it holds the CPU while spinning. Not deadlock.
      LIVELOCK          : processes keep changing state but make no
                          progress - they are active, not blocked.
      STARVATION        : a process is ready but never scheduled. It could
                          run if chosen, so it is not deadlocked.
   ```
   - The distinguishing test is simple: in a deadlock the processes are `blocked and can never be unblocked by anything they or the scheduler could do`. In starvation or a livelock, progress is still possible in principle.

8. **Deadlock এর চারটি শর্ত লিখ।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*

   Answer: (Answered in English, as required for IT topics.) The four conditions for deadlock — all must hold `simultaneously`. They are known as the `Coffman conditions`.

   1. Mutual exclusion
   ```
      At least one resource must be NON-SHAREABLE - only one process may
      use it at a time.

      Example : a printer , a tape drive , a write lock on a file.
      A read-only file is shareable, so it can never cause a deadlock.
   ```

   2. Hold and wait
   ```
      A process must be HOLDING at least one resource while WAITING to
      acquire additional resources that are held by other processes.

      Example : P1 holds the printer and waits for the scanner.
   ```

   3. No preemption
   ```
      A resource cannot be FORCIBLY TAKEN from the process holding it.
      It is released only VOLUNTARILY, when that process has finished.

      Example : a printer cannot be seized in the middle of a page.
      The CPU, by contrast, CAN be preempted, which is why the CPU is
      never the cause of a deadlock.
   ```

   4. Circular wait
   ```
      A CLOSED CHAIN of processes must exist :

           P0 waits for a resource held by P1
           P1 waits for a resource held by P2
           ...
           Pn waits for a resource held by P0

      The simplest case, with two processes :

           P1 holds A , wants B
           P2 holds B , wants A
   ```

   An example satisfying all four
   ```
      Two processes share a printer (A) and a scanner (B).

      t1  P1 requests A -> granted
      t2  P2 requests B -> granted
      t3  P1 requests B -> WAITS
      t4  P2 requests A -> WAITS

      MUTUAL EXCLUSION : both devices serve one process at a time  HOLDS
      HOLD AND WAIT    : P1 holds A while waiting for B            HOLDS
      NO PREEMPTION    : neither device can be seized              HOLDS
      CIRCULAR WAIT    : P1 -> P2 -> P1                            HOLDS

      DEADLOCK.
   ```

   How each condition is attacked to prevent deadlock
   ```
      MUTUAL EXCLUSION : usually cannot be removed. SPOOLING removes it
           where possible - jobs are written to disk and a daemon feeds
           the printer, so no process ever holds the printer itself.

      HOLD AND WAIT    : require a process to request ALL its resources
           at once, or to release everything before requesting more.
           Cost : poor utilisation and possible starvation.

      NO PREEMPTION    : allow a resource to be seized and the victim
           rolled back. Works for CPU and memory, not for a printer.

      CIRCULAR WAIT    : impose a TOTAL ORDER on resource types and
           require requests in INCREASING order. The MOST PRACTICAL
           method, and the one real kernel and database code uses.
   ```

   - Two facts worth adding. First, the four conditions are `necessary but not sufficient` when a resource has several instances — a cycle in the resource allocation graph may then still be safe, which is why the `Banker's algorithm` exists. Second, breaking `any single one` of the four is enough to make deadlock impossible, which is exactly why they are stated as necessary conditions.

9. **What is deadlock? Draw its diagram.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*

   Answer: What deadlock is
   - A `deadlock` is a state in which a set of processes are each `waiting for a resource held by another process in the same set`, so none can ever proceed.
   ```
      P1 holds A and requests B
      P2 holds B and requests A
           -> neither can continue, and neither will release what it holds
   ```
   - It needs all four `Coffman conditions` at once: `mutual exclusion`, `hold and wait`, `no preemption` and `circular wait`.

   Diagram — the resource allocation graph
   ```mermaid
   flowchart LR
       P1((P1)) -->|requests| R2[Resource R2]
       R2 -->|assigned to| P2((P2))
       P2 -->|requests| R1[Resource R1]
       R1 -->|assigned to| P1
   ```
   ```
      Notation :
           circle    = a PROCESS
           rectangle = a RESOURCE  (with one dot per instance)
           P ---> R  = a REQUEST edge   : P is waiting for R
           R ---> P  = an ASSIGNMENT edge : an instance of R is held by P


           +--------+   request    +----------+
           |   P1   |------------->|    R2    |
           +--------+              +----------+
                ^                        |
                | assigned               | assigned
                |                        v
           +----------+   request   +--------+
           |    R1    |<------------|   P2   |
           +----------+             +--------+

      The cycle  P1 -> R2 -> P2 -> R1 -> P1  is present.
      Both resources have ONE instance, so this IS a deadlock.
   ```

   The simpler wait-for graph
   ```
      Remove the resources and keep only "which process waits for which" :

           P1 --------> P2
            ^            |
            |            |
            +------------+

      A CYCLE means a circular wait, hence a deadlock.
   ```

   A three-process deadlock
   ```
           P1 -> R2 -> P2 -> R3 -> P3 -> R1 -> P1

           P1 holds R1 , wants R2
           P2 holds R2 , wants R3
           P3 holds R3 , wants R1

      Wait-for graph :   P1 -> P2 -> P3 -> P1
   ```

   The everyday illustration
   ```
      Four cars at a crossroads, each blocking the next :

                 car A
                   |
         car D --- + --- car B
                   |
                 car C

      A blocks B , B blocks C , C blocks D , D blocks A.
      No car can move - a physical circular wait.
   ```

   The rule the diagram gives
   ```
      SINGLE instance per resource :
           a CYCLE  <=>  a DEADLOCK        (necessary AND sufficient)

      MULTIPLE instances per resource :
           a cycle is NECESSARY but NOT SUFFICIENT - the state may still
           be safe, so the BANKER'S SAFETY ALGORITHM must be run.
   ```

   A graph with a cycle that is NOT a deadlock
   ```
      Resource R has TWO instances.

           P1 holds one and wants one more
           P2 holds one and wants one more
           P3 holds one and will RELEASE it without asking for more

      A cycle exists between P1 and P2, but when P3 releases its
      instance P1 obtains it, finishes and releases both, and P2 then
      proceeds. NO deadlock.
   ```
   - This is exactly why multiple instances require the safety algorithm rather than simple cycle detection.

   How deadlock is handled
   ```
      PREVENTION : make one of the four conditions impossible - usually
           by imposing an ORDER on resource requests, which makes a
           circular wait unformable.
      AVOIDANCE  : the Banker's algorithm - refuse any request that would
           lead to an unsafe state.
      DETECTION and RECOVERY : maintain the wait-for graph, detect a
           cycle, and kill or roll back a victim.
      IGNORE     : the "ostrich algorithm" - what Windows, Linux and UNIX
           actually do, because deadlock is rare and prevention is costly.
   ```

10. **(ক) Deadlock কী? Deadlock Handling করার বিভিন্ন উপায়সমূহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 413 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What deadlock is
    - A `deadlock` is a state in which a set of processes are each `waiting for a resource held by another process in the same set`, so none can ever proceed.
    ```
       P1 holds A and requests B
       P2 holds B and requests A     -> both wait forever
    ```
    - It requires all four `Coffman conditions` simultaneously: `mutual exclusion`, `hold and wait`, `no preemption` and `circular wait`. Breaking any one makes deadlock impossible.

    The four ways of handling deadlock

    1. Deadlock prevention
    - Design the system so that `one of the four conditions can never hold`.
    ```
       MUTUAL EXCLUSION : rarely removable. SPOOLING removes it where the
            resource permits - jobs go to a disk queue, so no process ever
            holds the printer itself.

       HOLD AND WAIT    : require a process to request ALL its resources
            at once before starting, or to release everything it holds
            before asking for more.
            Cost : poor resource utilisation , possible STARVATION.

       NO PREEMPTION    : if a request cannot be granted, seize everything
            the process holds and restart it later. Works for CPU and
            memory ; useless for a printer mid-page.

       CIRCULAR WAIT    : impose a TOTAL ORDER on resource types and
            require every process to request them in INCREASING order.

            F(printer) = 1 , F(scanner) = 2 , F(disk) = 3

            A cycle then cannot form, because following it round would
            require F(R) < F(R).

            THIS IS THE MOST PRACTICAL METHOD, and it is what real kernel
            and database code uses - "always lock A before B".
    ```

    2. Deadlock avoidance
    - Allow the conditions, but examine `every request before granting it` and refuse any that could lead to an unsafe state.
    ```
       THE BANKER'S ALGORITHM

       Each process declares its MAXIMUM need in advance.
       Need = Max - Allocation

       Before granting a request, the system checks whether the resulting
       state is SAFE - whether some sequence of processes exists in which
       each can obtain its maximum need and finish.

            SAFE   -> grant
            UNSAFE -> make the process wait, even though resources are free
    ```
    - `Unsafe is not the same as deadlocked`; it means deadlock has merely become possible. The algorithm is deliberately conservative.
    - Its weakness: every process must declare its maximum needs in advance, which no ordinary program can do. That is why real operating systems do not use it.

    3. Deadlock detection and recovery
    - Let deadlocks happen, detect them, then recover.
    ```
       DETECTION
            Single-instance resources : maintain a WAIT-FOR GRAPH and look
                 for a CYCLE. Cycle detection by DFS costs O(V + E).
            Multi-instance resources : run the SAFETY ALGORITHM periodically.

            How often ? Every request is expensive ; too rarely leaves
            processes hanging. A common compromise is to check when CPU
            utilisation drops below a threshold, since a deadlock idles
            the processes involved.

       RECOVERY
            PROCESS TERMINATION
                 Kill ALL deadlocked processes - simple, but all their
                 work is lost.
                 Kill ONE AT A TIME until the cycle breaks - less costly,
                 but detection must be re-run after each kill.

            RESOURCE PREEMPTION
                 Take a resource from a victim and give it to another.
                 Three issues :
                   - selecting the VICTIM : fewest resources held, least
                     CPU time consumed, lowest priority
                   - ROLLBACK : return the victim to a safe CHECKPOINT
                   - STARVATION : do not choose the same victim every time;
                     include the number of rollbacks in the cost function
    ```

    4. Ignore the problem — the "ostrich algorithm"
    ```
       Deadlocks are RARE in a general-purpose system, and the cost of
       prevention or avoidance is high. So Windows, Linux and UNIX simply
       ignore the possibility and rely on the user to reboot or kill a
       hung process.

       This is a deliberate ENGINEERING DECISION, not an oversight :
       a 1-in-a-million hang is cheaper than a permanent 20 per cent
       loss of resource utilisation.
    ```

    Comparison

    | Method | When applied | Overhead | Utilisation | Used in practice |
    |---|---|---|---|---|
    | Prevention | Design time | Low | `Poor` | Yes, for lock ordering |
    | Avoidance | Every request | High | Moderate | Rarely |
    | Detection and recovery | Periodically | Medium | Good | `Databases` |
    | Ignore | Never | None | Best | `Windows, Linux, UNIX` |

    - Where detection genuinely is used: `database management systems`. A DBMS builds a wait-for graph of its transactions, detects a cycle, chooses a victim and `rolls its transaction back automatically`. That is possible only because a transaction is designed to be undoable — an arbitrary operating-system process is not.

11. **What are the four necessary condition of deadlock in an operating system?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

    Answer: There are `four` necessary conditions, known as the `Coffman conditions`. All must hold `simultaneously` for a deadlock to occur.

    1. Mutual exclusion
    ```
       At least one resource must be held in a NON-SHAREABLE mode - only
       one process may use it at a time.

       Example : a printer , a tape drive , a write lock on a file.
       A read-only file is shareable and can never cause a deadlock.
    ```

    2. Hold and wait
    ```
       A process must be HOLDING at least one resource while WAITING to
       acquire additional resources held by other processes.

       Example : P1 holds the printer and waits for the scanner.
    ```

    3. No preemption
    ```
       A resource cannot be FORCIBLY TAKEN from the process holding it.
       It is released only VOLUNTARILY, after that process finishes with it.

       Example : a printer cannot be seized mid-page. The CPU CAN be
       preempted, which is why the CPU never causes a deadlock.
    ```

    4. Circular wait
    ```
       A CLOSED CHAIN of waiting processes must exist :

            P0 -> P1 -> P2 -> ... -> Pn -> P0

       where each waits for a resource held by the next.
    ```
    ```
       The simplest case :
            P1 holds A , wants B
            P2 holds B , wants A

            P1 ---> P2
             ^        |
             +--------+
    ```

    Example satisfying all four
    ```
       Two processes share a printer (A) and a scanner (B).

       t1  P1 requests A -> granted
       t2  P2 requests B -> granted
       t3  P1 requests B -> WAITS
       t4  P2 requests A -> WAITS

       MUTUAL EXCLUSION : each device serves one process        HOLDS
       HOLD AND WAIT    : P1 holds A while waiting for B        HOLDS
       NO PREEMPTION    : neither device can be seized          HOLDS
       CIRCULAR WAIT    : P1 -> P2 -> P1                        HOLDS

       DEADLOCK.
    ```

    Which condition each prevention method removes

    | Condition | Can it be removed? | How, and at what cost |
    |---|---|---|
    | Mutual exclusion | Rarely | Spooling, where the resource allows |
    | Hold and wait | Yes | Request all resources at once — poor utilisation |
    | No preemption | Partly | Seize and roll back — impossible for a printer |
    | `Circular wait` | `Yes, cheaply` | Impose a total order on resources |

    Why resource ordering works
    ```
       Number every resource type and require requests in INCREASING order.

            F(printer) = 1 , F(scanner) = 2 , F(disk) = 3

       Suppose a cycle P0 -> P1 -> ... -> Pn -> P0 existed. Following it
       round, each process holds a lower-numbered resource and waits for a
       higher-numbered one, so the numbers strictly increase all the way
       round. But returning to the start would require F(R) < F(R) - a
       contradiction.

       Therefore no cycle can form.
    ```
    - This is why every multi-threaded programming guide insists on a documented `lock order`: it is deadlock prevention by attacking the circular-wait condition.

    - One important qualification: the four conditions are `necessary but not sufficient` when a resource has `several instances`. A cycle in the resource allocation graph may then still be a safe state, which is exactly why the `Banker's algorithm` and its safety check exist.

12. **(a) What is deadlock in operating system (OS)? What are the four necessary and sufficient conditions behind deadlock?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

    Answer: (a) What deadlock is
    - A `deadlock` is a state in which a set of processes are each `waiting for a resource held by another process in the same set`, so none can ever proceed.
    ```
       P1 holds A and requests B
       P2 holds B and requests A     -> both wait forever
    ```
    - No process in the set can move, and none will release what it holds, so the wait is `permanent` — unlike starvation, where progress is still possible in principle.

    The four conditions
    ```
       1. MUTUAL EXCLUSION
            At least one resource is non-shareable - only one process may
            hold it at a time.  (printer , tape drive , write lock)

       2. HOLD AND WAIT
            A process holds at least one resource while waiting for more
            that are held by others.

       3. NO PREEMPTION
            A resource cannot be forcibly taken away; it is released only
            voluntarily by its holder.

       4. CIRCULAR WAIT
            A closed chain  P0 -> P1 -> ... -> Pn -> P0  exists, in which
            each process waits for a resource held by the next.
    ```

    A note on the wording "necessary and sufficient"
    - The question says `necessary and sufficient`, but the standard result is that these four are `necessary` — and sufficient only for `single-instance` resources.
    ```
       SINGLE instance per resource type :
            all four hold  <=>  DEADLOCK
            (equivalently, a CYCLE in the resource allocation graph
             means a deadlock)
            -> here they ARE necessary AND sufficient

       MULTIPLE instances per resource type :
            all four may hold and the state may STILL BE SAFE.
            A cycle is then NECESSARY but NOT SUFFICIENT.
    ```
    - Counter-example with two instances of R:
    ```
       P1 holds one instance and wants one more
       P2 holds one instance and wants one more
       P3 holds one instance and will RELEASE it without asking for more

       A cycle exists between P1 and P2, but when P3 releases, P1 gets the
       instance, finishes, releases both, and P2 proceeds.  NO deadlock.
    ```
    - This is precisely why the `Banker's safety algorithm` exists: for multi-instance resources the four conditions are not enough, and the state has to be tested.

    Example where all four hold and a deadlock really occurs
    ```
       t1  P1 requests the printer -> granted
       t2  P2 requests the scanner -> granted
       t3  P1 requests the scanner -> WAITS
       t4  P2 requests the printer -> WAITS

       Both devices are single-instance, so the cycle P1 -> P2 -> P1 is a
       genuine deadlock.
    ```

    - Breaking `any one` of the four makes deadlock impossible. Attacking `circular wait` is the cheapest: number the resource types and require every process to request them in increasing order. A cycle then cannot form, because following it round would require `F(R) < F(R)`.

13. **(b) A system has P processes each needing a maximum of m resources and a total of r resources available. Which conditions must hold to make the system deadlock free?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*

    Answer: The setting
    ```
       P = number of processes
       m = maximum number of resource units EACH process may need
       r = total number of resource units available
       All units are IDENTICAL and are requested one at a time.
    ```

    The condition
    ```
            r  >=  P * (m - 1) + 1
    ```
    - Equivalently, `r >= P*m - P + 1`. If this holds, the system can never deadlock, whatever order the requests arrive in.

    Why it works
    ```
       Consider the WORST CASE. To have a deadlock, EVERY process must be
       stuck holding some units and waiting for more.

       The most units a process can hold and still be waiting is  m - 1 ,
       because a process that has all m of its units can finish and does
       not need to wait.

       So the worst distribution is :

            every one of the P processes holds  (m - 1)  units
            total units tied up  =  P * (m - 1)

       If there is even ONE spare unit left over, i.e.

            r  >=  P * (m - 1) + 1

       then that spare unit is given to some process Pi. Pi now has all m
       units it can need, so it FINISHES and RELEASES all m units. Those
       m units let the next process complete, and so on, until every
       process finishes.

       Hence NO DEADLOCK is possible.
    ```

    Worked check
    ```
       P = 3 processes , m = 4 units each.

       Required :  r >= 3 * (4 - 1) + 1 = 3 * 3 + 1 = 10

       Case r = 10  ->  SAFE
            worst case : P1 = 3 , P2 = 3 , P3 = 3 , used = 9
            1 unit spare -> give it to P1 -> P1 has 4 , finishes ,
            releases 4 -> P2 finishes -> P3 finishes.

       Case r = 9   ->  DEADLOCK POSSIBLE
            P1 = 3 , P2 = 3 , P3 = 3 , used = 9 , spare = 0
            each needs 1 more , none can get it -> all wait forever.
    ```

    The general form when needs differ
    ```
       If process Pi may need at most  Ni  units (needs not equal), the
       condition becomes

            r  >=  SUM( Ni - 1 ) + 1  =  SUM(Ni) - P + 1

       which is the same statement, written for unequal maximum needs.
       The equivalent inequality often quoted is

            SUM(Ni)  <  r + P
    ```
    - Both forms say the same thing: `deadlock is impossible as long as the total demand is small enough that at least one process can always be given everything it needs`.

    - Note this is a `prevention` condition checked at design time from the totals — not the `Banker's algorithm`, which tests the actual allocation state at run time before granting each request.

14. **Name and define characteristics properties of the Deadlock situation in a computer system.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

    Answer: The `characteristic properties` of a deadlock are the four `Coffman conditions`. All four must hold `simultaneously` for a deadlock to exist.

    1. Mutual exclusion
    ```
       At least one resource is held in a NON-SHAREABLE mode - only one
       process may use it at a time.

       Example : a printer , a tape drive , a write lock on a record.
       A read-only file is shareable and can never cause a deadlock.
    ```

    2. Hold and wait
    ```
       A process HOLDS at least one resource while WAITING for additional
       resources that are held by other processes.

       Example : P1 holds the printer and waits for the scanner.
    ```

    3. No preemption
    ```
       A resource cannot be FORCIBLY TAKEN from its holder. It is released
       only VOLUNTARILY, after the holder finishes with it.

       Example : a printer cannot be seized mid-page. The CPU CAN be
       preempted, which is why the CPU is never a cause of deadlock.
    ```

    4. Circular wait
    ```
       A CLOSED CHAIN of waiting processes exists :

            P0 -> P1 -> P2 -> ... -> Pn -> P0

       Simplest case :
            P1 holds A , wants B
            P2 holds B , wants A

            P1 ---> P2
             ^        |
             +--------+
    ```

    Example in which all four are present
    ```
       t1  P1 requests the printer (A) -> granted
       t2  P2 requests the scanner (B) -> granted
       t3  P1 requests B              -> WAITS
       t4  P2 requests A              -> WAITS

       MUTUAL EXCLUSION : each device serves one process       HOLDS
       HOLD AND WAIT    : P1 holds A while waiting for B       HOLDS
       NO PREEMPTION    : neither device can be seized         HOLDS
       CIRCULAR WAIT    : P1 -> P2 -> P1                       HOLDS

       DEADLOCK.
    ```

    How each property is used to prevent deadlock

    | Property | Removable? | Method and cost |
    |---|---|---|
    | Mutual exclusion | Rarely | Spooling, where the device allows |
    | Hold and wait | Yes | Request everything at once — poor utilisation |
    | No preemption | Partly | Seize and roll back — useless for a printer |
    | `Circular wait` | `Yes, cheaply` | Total ordering of resource types |

    - One qualification worth stating: these four properties are `necessary but not sufficient` when a resource type has `several instances`. A cycle may then still be a safe state, which is why the `Banker's algorithm` tests the state instead of just looking for a cycle.

15. **(b) What are the conditions for deadlock situations? Explain briefly.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*

    Answer: A deadlock needs `four` conditions to hold at the same time. They are the `Coffman conditions`.

    1. Mutual exclusion
    ```
       At least one resource must be NON-SHAREABLE - only one process may
       hold it at a time.

       Example : a printer , a tape drive , a write lock.
       A shareable read-only file can never cause a deadlock.
    ```

    2. Hold and wait
    ```
       A process must be HOLDING one or more resources while WAITING for
       others that are currently held by other processes.

       Example : P1 holds the printer and waits for the scanner.
    ```

    3. No preemption
    ```
       A resource cannot be TAKEN AWAY by force. Its holder must release
       it voluntarily.

       Example : a printer cannot be seized mid-page. The CPU can be
       preempted, so the CPU never causes deadlock.
    ```

    4. Circular wait
    ```
       A CLOSED CHAIN of waiting processes must exist :

            P0 -> P1 -> ... -> Pn -> P0

            P1 holds A , wants B
            P2 holds B , wants A

            P1 ---> P2
             ^        |
             +--------+
    ```

    Brief example
    ```
       t1  P1 gets the printer
       t2  P2 gets the scanner
       t3  P1 asks for the scanner -> WAITS
       t4  P2 asks for the printer -> WAITS

       All four conditions hold, so this is a deadlock.
    ```

    Breaking the conditions
    ```
       Remove ANY ONE and deadlock becomes impossible.

       Mutual exclusion -> spooling , where possible
       Hold and wait    -> request all resources at once
       No preemption    -> seize the resource and roll the victim back
       Circular wait    -> NUMBER the resource types and require requests
                           in INCREASING order.  A cycle then cannot form,
                           because going round it would need F(R) < F(R).
    ```
    - Circular wait is the one attacked in practice; the rule "always take lock A before lock B" in real kernel and database code is exactly this.

    - Important qualification: the four are `necessary but not sufficient` when a resource type has `multiple instances`. There a cycle may still be a safe state, so the `Banker's safety algorithm` must be run to decide.

16. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances). Snapshot at time T_0. The content of the matrix. Need is defined to be \text{Max} - \text{Allocation}. Check that \text{Request} \le \text{Available}. Executing safety algorithm shows that sequence \langle P_1, P_3, P_4, P_0, P_2 \rangle satisfies safety requirement.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 855 (ET: N/A)]*

    Answer: Given, the standard snapshot at time T0.
    ```
       Total resources :  A = 10 , B = 5 , C = 7

               Allocation        Max
                A  B  C        A  B  C
       P0       0  1  0        7  5  3
       P1       2  0  0        3  2  2
       P2       3  0  2        9  0  2
       P3       2  1  1        2  2  2
       P4       0  0  2        4  3  3
    ```

    Step 1 — Available
    ```
       Available = Total - sum of Allocation

       sum of Allocation :  A : 0+2+3+2+0 = 7
                            B : 1+0+0+1+0 = 2
                            C : 0+0+2+1+2 = 5

       Available = (10-7 , 5-2 , 7-5) = (3 , 3 , 2)
    ```

    Step 2 — Need matrix, Need = Max - Allocation
    ```
                  Need
                A  B  C
       P0       7  4  3          (7-0 , 5-1 , 3-0)
       P1       1  2  2          (3-2 , 2-0 , 2-0)
       P2       6  0  0          (9-3 , 0-0 , 2-2)
       P3       0  1  1          (2-2 , 2-1 , 2-1)
       P4       4  3  1          (4-0 , 3-0 , 3-2)
    ```

    Step 3 — Safety algorithm
    - Work = Available = (3,3,2), and every Finish[i] = false. Repeatedly pick a process whose `Need <= Work`, let it finish, and add its Allocation to Work.
    ```
       Work = (3,3,2)

       P0 : Need (7,4,3) <= (3,3,2) ?   7>3   NO
       P1 : Need (1,2,2) <= (3,3,2) ?   YES -> run P1
            Work = (3,3,2) + Allocation(2,0,0) = (5,3,2)

       P2 : Need (6,0,0) <= (5,3,2) ?   6>5   NO
       P3 : Need (0,1,1) <= (5,3,2) ?   YES -> run P3
            Work = (5,3,2) + (2,1,1) = (7,4,3)

       P4 : Need (4,3,1) <= (7,4,3) ?   YES -> run P4
            Work = (7,4,3) + (0,0,2) = (7,4,5)

       P0 : Need (7,4,3) <= (7,4,5) ?   YES -> run P0
            Work = (7,4,5) + (0,1,0) = (7,5,5)

       P2 : Need (6,0,0) <= (7,5,5) ?   YES -> run P2
            Work = (7,5,5) + (3,0,2) = (10,5,7)
    ```
    ```
       All five Finish[i] = true , and Work returns to (10,5,7) = Total.
    ```

    Safe sequence
    ```
            < P1 , P3 , P4 , P0 , P2 >
    ```
    - The system is in a `safe state`.

    Step 4 — the request test
    - When a running process makes a request, three checks are applied in order:
    ```
       1. Request <= Need     else ERROR - the process exceeded its
                              declared maximum
       2. Request <= Available else WAIT  - the resources are not free
       3. PRETEND to grant :
               Available   = Available - Request
               Allocation  = Allocation + Request
               Need        = Need - Request
          then run the SAFETY ALGORITHM on this trial state.

               SAFE   -> grant the request for real
               UNSAFE -> undo the trial and make the process WAIT
    ```
    - Example: `P1 requests (1,0,2)`. Check `(1,0,2) <= Need(1,2,2)` — yes. Check `(1,0,2) <= Available(3,3,2)` — yes. After the trial grant, `Available = (2,3,0)` and the safety algorithm finds the sequence `<P1, P3, P4, P0, P2>`, so the request is `granted`.

    Points to note
    - The Banker's algorithm is `deadlock avoidance`, not detection. It refuses a request that `could` lead to trouble, so resources may sit idle even when a request could safely be served.
    - An `unsafe` state is not a deadlocked state; it only means deadlock has become possible.
    - Its practical limitation: every process must declare its `maximum need in advance`, which ordinary programs cannot do. This is why real operating systems do not use it.

17. **(a) What is Artificial Intelligence (AI)? What are the necessary conditions for a deadlock in an operating system?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 890 (ET: N/A)]*

    Answer: (a) What Artificial Intelligence is
    - `Artificial Intelligence (AI)` is the branch of computer science that builds machines able to do tasks that normally need human intelligence — learning from data, reasoning, understanding language, recognising images and making decisions.
    ```
       Main branches :
         Machine Learning     - learn patterns from data instead of being
                                programmed with fixed rules
         Deep Learning        - multi-layer neural networks
         NLP                  - understand and generate human language
         Computer Vision      - understand images and video
         Expert Systems       - rule-based reasoning in a narrow domain
         Robotics             - perceive the world and act in it
    ```
    ```
       Types by capability :
         NARROW AI   - good at ONE task. All AI in use today : spam
                       filters , face unlock , recommendation systems ,
                       chatbots , medical image screening.
         GENERAL AI  - human-level ability across ANY task. Does not exist.
         SUPER AI    - beyond human ability. Theoretical.
    ```
    - Common uses: fraud detection in banking, credit scoring, OCR for cheque clearing, speech recognition, machine translation and self-driving vehicles.

    The necessary conditions for a deadlock
    ```
       1. MUTUAL EXCLUSION
            At least one resource is non-shareable - one holder at a time.
            (printer , tape drive , write lock)

       2. HOLD AND WAIT
            A process holds one or more resources while waiting for others
            held by other processes.

       3. NO PREEMPTION
            A resource cannot be seized; it is released only voluntarily
            by its holder.

       4. CIRCULAR WAIT
            A closed chain exists :  P0 -> P1 -> ... -> Pn -> P0 ,
            each waiting for a resource held by the next.
    ```
    - All four must hold `at the same time`; breaking any one makes deadlock impossible.
    ```
       Example :
            t1  P1 gets the printer
            t2  P2 gets the scanner
            t3  P1 asks for the scanner -> WAITS
            t4  P2 asks for the printer -> WAITS

            Cycle P1 -> P2 -> P1 , both devices single-instance
            -> DEADLOCK
    ```
    - Circular wait is the condition attacked in practice: number the resource types and require requests in `increasing order`, so a cycle can never form.

18. **What is Deadlock? Explain two situations where deadlock condition occurs.** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*

    Answer: What deadlock is
    - A `deadlock` is a state in which a set of processes are each `waiting for a resource held by another process in the same set`, so none can ever proceed.
    - It needs the four `Coffman conditions` together: `mutual exclusion`, `hold and wait`, `no preemption` and `circular wait`.

    Situation 1 — two processes and two devices
    ```
       A printer (A) and a scanner (B). Both are single-instance.

       t1  P1 requests A -> granted        P1 holds A
       t2  P2 requests B -> granted        P2 holds B
       t3  P1 requests B -> WAITS          B is held by P2
       t4  P2 requests A -> WAITS          A is held by P1

       Wait-for graph :   P1 ---> P2
                           ^        |
                           +--------+

       P1 will not release A until it gets B ; P2 will not release B until
       it gets A. Neither ever happens.
    ```
    - The cause is the `order of requests`. Had both processes asked for A first and then B, no cycle could have formed. This is why resource ordering prevents deadlock.

    Situation 2 — two database transactions holding row locks
    ```
       T1 : UPDATE accounts SET bal = bal - 500 WHERE id = 1;   -- locks row 1
            UPDATE accounts SET bal = bal + 500 WHERE id = 2;   -- wants row 2

       T2 : UPDATE accounts SET bal = bal - 300 WHERE id = 2;   -- locks row 2
            UPDATE accounts SET bal = bal + 300 WHERE id = 1;   -- wants row 1

            T1 holds row 1 , waits for row 2
            T2 holds row 2 , waits for row 1
            -> circular wait on ROW LOCKS
    ```
    - This is the commonest deadlock in real banking software. The DBMS handles it by `detection and recovery`: it builds a wait-for graph, finds the cycle, picks a `victim` and `rolls that transaction back` automatically, so the other can finish. That is possible only because a transaction is designed to be undoable.

    Two more situations worth mentioning
    ```
       MESSAGE PASSING
            P1 does receive(from P2) , then send(to P2)
            P2 does receive(from P1) , then send(to P1)
            Both block on receive - each waits for a message the other
            will never send. Here the "resource" is a MESSAGE.

       SELF-DEADLOCK ON A NON-REENTRANT LOCK
            lock(m);  ...  lock(m);
            The thread waits for a lock it already holds - a cycle of
            length one. A recursive mutex prevents it.
    ```

    How each situation is avoided
    ```
       Situation 1 : impose a TOTAL ORDER on devices - always request the
            printer before the scanner. A cycle then cannot form.
       Situation 2 : access rows in a FIXED ORDER (ascending primary key),
            or let the DBMS detect and roll back a victim.
    ```

19. **A, B two resources. Two processes (P1 and P2) share these resources. When a process request for a resources, if that resource is free then it will be allocated with that resources. If the resources are not free then the process will halt. Now the scenario is:** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 973 (ET: BUET)]*

    Answer: The question is `incomplete` — the scenario table showing the actual sequence of requests by P1 and P2 was not captured, so the exact answer cannot be produced. The method and the standard version of this problem are given below.

    The rule stated in the question
    ```
       Request a free resource   -> it is ALLOCATED
       Request a busy resource   -> the process HALTS (blocks) and keeps
                                    whatever it already holds
    ```
    - This rule is exactly `hold and wait` with `no preemption`, so with two single-instance resources a deadlock is possible.

    The standard scenario for this problem
    ```
       Two resources A and B , each with ONE instance.

       Time   P1                        P2
       ----   -----------------------   -----------------------
       t1     request A -> granted      -
       t2     -                         request B -> granted
       t3     request B -> HALTS        -
       t4     -                         request A -> HALTS

       State :  P1 holds A , waits for B
                P2 holds B , waits for A
    ```

    Resource allocation graph
    ```mermaid
    flowchart LR
        P1((P1)) -->|requests| B[Resource B]
        B -->|held by| P2((P2))
        P2 -->|requests| A[Resource A]
        A -->|held by| P1
    ```
    ```
            +--------+  request  +--------+
            |   P1   |---------->|   B    |
            +--------+           +--------+
                 ^                    |
                 | held               | held
            +--------+  request  +--------+
            |   A    |<----------|   P2   |
            +--------+           +--------+

       Wait-for graph :   P1 ---> P2 ---> P1     a CYCLE
    ```

    Checking the four conditions
    ```
       MUTUAL EXCLUSION : A and B have one instance each          HOLDS
       HOLD AND WAIT    : P1 holds A and waits for B              HOLDS
       NO PREEMPTION    : a halted process keeps its resource     HOLDS
       CIRCULAR WAIT    : P1 -> P2 -> P1                          HOLDS

       Both resources are single-instance, so the cycle IS a deadlock.
    ```
    - Verdict for this ordering: `deadlock`.

    An ordering of the same requests that does NOT deadlock
    ```
       Time   P1                        P2
       t1     request A -> granted      -
       t2     request B -> granted      -
       t3     use , then release A , B  -
       t4     -                         request A -> granted
       t5     -                         request B -> granted

       P1 never waits while holding, so no cycle forms.  NO DEADLOCK.
    ```
    - The general test to apply to whatever the actual table shows: draw the resource allocation graph at the final state; with single-instance resources, `a cycle means a deadlock and no cycle means none`.

    How to make this system deadlock-free
    ```
       RESOURCE ORDERING : fix F(A) = 1 , F(B) = 2 and require every
            process to request in increasing order. Both processes then
            take A before B, so the one that gets A first finishes first.
            A cycle cannot form.

       ALL-OR-NOTHING    : a process requests A and B together ; if both
            are not free it gets neither. Removes HOLD AND WAIT.

       TIMEOUT and ROLLBACK : a halted process releases what it holds
            after a timeout and retries. Removes NO PREEMPTION.
    ```

20. **What is Operating Systems Deadlock? কীভাবে Deadlock দূর করা যায়?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What an operating system deadlock is
    - A `deadlock` is a state in which a set of processes are each `waiting for a resource held by another process in the same set`, so none can ever proceed.
    ```
       P1 holds A and requests B
       P2 holds B and requests A     -> both wait forever
    ```
    - All four `Coffman conditions` must hold together: `mutual exclusion`, `hold and wait`, `no preemption` and `circular wait`.

    How deadlock is removed — the four approaches

    1. Prevention — make one condition impossible
    ```
       MUTUAL EXCLUSION : use SPOOLING where the device allows. Print jobs
            go to a disk queue and a daemon feeds the printer, so no
            process ever holds the printer itself.

       HOLD AND WAIT    : require a process to request ALL its resources
            at once, or to release everything before requesting more.
            Cost : poor utilisation , possible starvation.

       NO PREEMPTION    : if a request cannot be met, seize what the
            process holds and restart it later. Works for CPU and memory,
            not for a printer mid-page.

       CIRCULAR WAIT    : NUMBER the resource types and require requests
            in INCREASING order.

                 F(printer) = 1 , F(scanner) = 2 , F(disk) = 3

            A cycle then cannot form : following it round, the numbers
            would have to increase all the way back to the start, needing
            F(R) < F(R) - impossible.

            THIS IS THE PRACTICAL METHOD - "always lock A before B".
    ```

    2. Avoidance — the Banker's algorithm
    ```
       Each process declares its MAXIMUM need in advance.
            Need = Max - Allocation

       Before granting any request the system tests the resulting state :
            SAFE   (some order exists in which all processes can finish)
                         -> grant
            UNSAFE -> make the process wait, even though resources are free
    ```
    - Weakness: maximum needs must be known in advance, which ordinary programs cannot supply. Hence real operating systems do not use it.

    3. Detection and recovery
    ```
       DETECTION
            Single-instance resources : keep a WAIT-FOR GRAPH and look for
                 a CYCLE - DFS, O(V + E).
            Multi-instance resources  : run the SAFETY ALGORITHM
                 periodically.

       RECOVERY
            KILL processes  - all of them (simple, wasteful) or one at a
                 time until the cycle breaks.
            PREEMPT resources - choose a VICTIM (fewest resources held,
                 least CPU consumed, lowest priority), ROLL IT BACK to a
                 checkpoint, and avoid STARVATION by not picking the same
                 victim every time.
    ```
    - This is what a `DBMS` does: it detects a lock cycle and rolls a transaction back automatically.

    4. Ignore it — the "ostrich algorithm"
    ```
       Deadlock is rare, and prevention costs utilisation permanently.
       So Windows, Linux and UNIX simply ignore it and rely on the user
       to kill the hung process or reboot. A deliberate trade-off.
    ```

    Comparison

    | Method | Applied at | Overhead | Utilisation | Used in practice |
    |---|---|---|---|---|
    | Prevention | Design time | Low | `Poor` | Yes, as lock ordering |
    | Avoidance | Every request | High | Moderate | Rarely |
    | Detection | Periodically | Medium | Good | `Databases` |
    | Ignore | Never | None | Best | `Windows, Linux, UNIX` |

21. **(d) Define Deadlock. Write down the necessary conditions for deadlock.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026 (ET: N/A)]*

    Answer: Definition
    - A `deadlock` is a state in which a set of processes are each `waiting for a resource held by another process in the same set`, so no process in the set can ever proceed.
    ```
       P1 holds A and requests B
       P2 holds B and requests A     -> the wait is PERMANENT
    ```
    - The wait is permanent because none of them will release what it holds until it gets what it is waiting for. This is what separates deadlock from `starvation`, where a process could still run if the scheduler chose it.

    The necessary conditions
    ```
       1. MUTUAL EXCLUSION
            At least one resource is non-shareable - only one process may
            hold it at a time.  (printer , tape drive , write lock)

       2. HOLD AND WAIT
            A process holds at least one resource while waiting for more
            that are held by other processes.

       3. NO PREEMPTION
            A resource cannot be forcibly taken from its holder; it is
            released only voluntarily.

       4. CIRCULAR WAIT
            A closed chain  P0 -> P1 -> ... -> Pn -> P0  exists, each
            process waiting for a resource held by the next.
    ```
    - All four must hold `simultaneously`. Breaking `any one` makes deadlock impossible, which is why they are called necessary conditions.

    Example
    ```
       t1  P1 gets the printer (A)
       t2  P2 gets the scanner (B)
       t3  P1 asks for B -> WAITS
       t4  P2 asks for A -> WAITS

       Wait-for graph :  P1 ---> P2 ---> P1     a CYCLE  ->  DEADLOCK
    ```

    Breaking each condition

    | Condition | Removable? | Method |
    |---|---|---|
    | Mutual exclusion | Rarely | Spooling, where the device allows |
    | Hold and wait | Yes | Request all resources at once |
    | No preemption | Partly | Seize the resource and roll the victim back |
    | `Circular wait` | `Yes, cheaply` | Total ordering of resource types |

    - Resource ordering, the practical method: number the resource types and require every process to request in `increasing order`. Following a hypothetical cycle round would require `F(R) < F(R)`, so no cycle can form.
    - One qualification: for a resource type with `multiple instances` the four conditions are `necessary but not sufficient` — a cycle may still be a safe state, so the `Banker's safety algorithm` decides instead.

22. **Four condition of deadlock in Operating System. Suppose, n processes, \text{P}_1, \text{P}_2\dots \text{P}_n share m identical esource units which can be reserved and released one at a time. The maximum resources request of process \text{P}_i is \text{S}_i, where \text{S}_i>0. Which one is sufficient condition for ensuring that deadlock doesn't occur? (Full প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

    Answer: The four conditions for deadlock
    ```
       1. MUTUAL EXCLUSION - at least one resource is non-shareable, so
          only one process may hold it at a time.
       2. HOLD AND WAIT    - a process holds resources while waiting for
          more that are held by others.
       3. NO PREEMPTION    - a resource cannot be seized; it is released
          only voluntarily.
       4. CIRCULAR WAIT    - a closed chain P0 -> P1 -> ... -> Pn -> P0
          exists, each waiting for a resource held by the next.
    ```
    - All four must hold at once. Breaking any one makes deadlock impossible.

    The sufficient condition
    ```
       Given :  n processes P1 ... Pn
                m identical resource units, reserved and released one at
                a time
                Si = maximum request of process Pi , Si > 0

       The sufficient condition for NO deadlock is

                SUM( Si )  <  m + n
                    i=1..n
    ```
    - Equivalently `sum(Si) <= m + n - 1`.

    Why it works
    ```
       For a deadlock, EVERY process must be blocked while holding some
       units. A process holding all Si of its units can finish, so a
       BLOCKED process holds at most  (Si - 1)  units.

       The worst case therefore ties up

            SUM( Si - 1 )  =  SUM(Si) - n     units

       If even ONE unit is still free, some process can be given its last
       unit, finish, and release everything - which unblocks the next, and
       so on. So deadlock is impossible when

            SUM(Si) - n  <  m
            SUM(Si)      <  m + n
    ```

    Worked check
    ```
       n = 3 processes , m = 10 units , S1 = 4 , S2 = 4 , S3 = 4

            SUM(Si) = 12 ,  m + n = 13
            12 < 13   ->  TRUE  ->  NO DEADLOCK POSSIBLE

       Verify : worst case each holds Si-1 = 3 , total 9 , one unit
       spare -> give it to P1 -> P1 has 4 , finishes , releases 4 ->
       P2 finishes -> P3 finishes.

       Now try m = 9 :
            SUM(Si) = 12 ,  m + n = 12
            12 < 12   ->  FALSE  ->  deadlock POSSIBLE

       Verify : each holds 3 , total 9 , nothing spare , each needs one
       more -> all wait forever.  DEADLOCK.
    ```

    - The equal-need form of the same result is `m >= n*(S - 1) + 1` when every process needs the same maximum `S`. Both say one thing: `deadlock cannot occur as long as at least one process can always be given everything it still needs`.
    - Note this is a `sufficient` condition, not a necessary one. If it fails, deadlock is merely `possible` — not certain. It is also a design-time check on totals, unlike the `Banker's algorithm`, which tests the actual allocation state before granting each request.

23. **(b) What are the conditions for a deadlock situation?** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130 (ET: N/A)]*

    Answer: A deadlock requires `four` conditions to hold at the same time — the `Coffman conditions`.

    1. Mutual exclusion
    ```
       At least one resource must be NON-SHAREABLE - only one process may
       hold it at a time.

       Example : printer , tape drive , write lock on a record.
       A read-only file is shareable, so it can never cause a deadlock.
    ```

    2. Hold and wait
    ```
       A process must be HOLDING at least one resource while WAITING for
       others that are held by other processes.

       Example : P1 holds the printer and waits for the scanner.
    ```

    3. No preemption
    ```
       A resource cannot be FORCIBLY TAKEN from its holder; it is released
       only voluntarily.

       Example : a printer cannot be seized mid-page. The CPU CAN be
       preempted, which is why the CPU never causes deadlock.
    ```

    4. Circular wait
    ```
       A CLOSED CHAIN of waiting processes must exist :

            P0 -> P1 -> ... -> Pn -> P0

            P1 holds A , wants B
            P2 holds B , wants A

            P1 ---> P2
             ^        |
             +--------+
    ```

    Example
    ```
       t1  P1 gets the printer (A)
       t2  P2 gets the scanner (B)
       t3  P1 asks for B -> WAITS
       t4  P2 asks for A -> WAITS

       All four hold, both devices are single-instance -> DEADLOCK.
    ```

    Breaking the conditions
    ```
       Mutual exclusion -> spooling , where the device allows
       Hold and wait    -> request all resources at once
       No preemption    -> seize the resource and roll the victim back
       Circular wait    -> NUMBER the resource types and require requests
                           in INCREASING order ; a cycle then cannot form
    ```
    - Circular wait is the one attacked in real systems; the documented "lock order" in kernel and database code is exactly this rule.
    - Qualification: with `multiple instances` of a resource type the four are `necessary but not sufficient` — a cycle may still be safe, so the `Banker's safety algorithm` is used to decide.

## Virtual Memory & Page Replacement (Thrashing) (16)

1. Consider the following page reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1. Assuming a system with 3 page frames initially empty, calculate the number of page faults using the following page replacement algorithms: (i) FIFO (First-In, First-Out), (ii) LRU (Least Recently Used), and (iii) Optimal Page Replacement. [BSCCPL AME 21-08-2026 (BUET)]

   Answer: Given, reference string = 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1 with 3 frames, all initially empty.

   (i) FIFO — replace the page that entered earliest
   ```
    Ref  7  0  1  2  0  3  0  4  2  3  0  3  2  1  2  0  1  7  0  1
    F1   7  7  7  2  2  2  2  4  4  4  0  0  0  0  0  0  0  7  7  7
    F2   .  0  0  0  0  3  3  3  2  2  2  2  2  1  1  1  1  1  0  0
    F3   .  .  1  1  1  1  0  0  0  3  3  3  3  3  2  2  2  2  2  1
         F  F  F  F  H  F  F  F  F  F  F  H  H  F  F  H  H  F  F  F
   ```
   ```
      Faults = 15 , Hits = 5
      Hit ratio = 5 / 20 = 0.25
   ```

   (ii) LRU — replace the page unused for the longest time
   ```
    Ref  7  0  1  2  0  3  0  4  2  3  0  3  2  1  2  0  1  7  0  1
    F1   7  7  7  2  2  2  2  4  4  4  0  0  0  1  1  1  1  1  1  1
    F2   .  0  0  0  0  0  0  0  0  3  3  3  3  3  3  0  0  0  0  0
    F3   .  .  1  1  1  3  3  3  2  2  2  2  2  2  2  2  2  7  7  7
         F  F  F  F  H  F  H  F  F  F  F  H  H  F  H  F  H  F  H  H
   ```
   ```
      Faults = 12 , Hits = 8
      Hit ratio = 8 / 20 = 0.40
   ```

   (iii) Optimal — replace the page that will be used farthest in the future
   ```
    Ref  7  0  1  2  0  3  0  4  2  3  0  3  2  1  2  0  1  7  0  1
    F1   7  7  7  2  2  2  2  2  2  2  2  2  2  2  2  2  2  7  7  7
    F2   .  0  0  0  0  0  0  4  4  4  0  0  0  0  0  0  0  0  0  0
    F3   .  .  1  1  1  3  3  3  3  3  3  3  3  1  1  1  1  1  1  1
         F  F  F  F  H  F  H  F  H  H  F  H  H  F  H  H  H  F  H  H
   ```
   ```
      Faults = 9 , Hits = 11
      Hit ratio = 11 / 20 = 0.55
   ```

   Result
   ```
           FIFO     = 15 page faults
           LRU      = 12 page faults
           OPTIMAL  =  9 page faults
   ```
   - Optimal gives the fewest faults, but it needs knowledge of future references, so it cannot be implemented. It is used only as a `benchmark` to judge the others.
   - LRU beats FIFO because it uses `recency of use`, which approximates locality of reference. FIFO ignores usage and can throw out a heavily used page just because it is old.
   - FIFO can also suffer `Belady's anomaly`: adding more frames can `increase` faults. LRU and Optimal are stack algorithms and never show it.

2. **Explain the concept of thrashing in an operating system, describing how it occurs in a demand-paged virtual memory system and how it impacts CPU utilization and overall system performance.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1422 (ET: E-Zone)]*

   Answer: What thrashing is
   - `Thrashing` is the state where the system spends more time `swapping pages between memory and disk` than running the processes themselves. Useful work almost stops.

   How it happens in a demand-paged system
   ```
      1. The degree of multiprogramming is raised - more processes are
         kept in memory at the same time.
      2. Each process now gets FEWER FRAMES than its WORKING SET (the set
         of pages it is actively using).
      3. A process cannot keep its active pages resident, so almost every
         memory reference is a PAGE FAULT.
      4. The faulting process blocks on the paging disk. The CPU goes idle.
      5. The CPU scheduler sees LOW CPU UTILISATION and, believing the
         system is under-loaded, ADMITS MORE PROCESSES.
      6. The new processes steal frames from the existing ones, so faults
         rise again -> step 4.
   ```
   - This feedback loop is the heart of the problem: the scheduler's cure makes the disease worse. The system collapses into thrashing.

   Effect on CPU utilisation
   ```
      CPU
      util
       |         ____
       |       /     \
       |     /        \          <- thrashing begins
       |   /            \
       | /                \_____
       +-----------------------------> degree of multiprogramming
                    ^
               optimal point
   ```
   ```
      Before the peak : more processes -> better CPU utilisation
      After  the peak : more processes -> utilisation FALLS SHARPLY
   ```
   - Effect on the system: throughput drops, response time becomes very long, the disk light stays on continuously, and the CPU sits mostly idle. The machine appears frozen even though the CPU has nothing to do.

   Why it is really a locality problem
   - A program does not use its pages evenly. At any moment it works inside a `locality` — a small group of pages (a function's code, its local variables, an array being scanned). If the frames given to a process can hold its current locality, faults are rare. If they cannot, faults explode.

   How thrashing is handled
   ```
      WORKING SET MODEL (Denning)
           W(t, D) = the set of pages referenced in the last D references.
           Give each process enough frames to hold its working set.
           If  SUM of all working set sizes > total frames , SUSPEND one
           process and free its frames.

      PAGE FAULT FREQUENCY (PFF)
           Measure each process's fault rate and keep it inside a band :

               rate ABOVE the upper limit -> give the process MORE frames
               rate BELOW the lower limit -> take frames AWAY
               no frames left to give     -> SUSPEND a process

      LOCAL REPLACEMENT
           A faulting process may only replace ITS OWN pages, so it cannot
           steal frames from others and spread the thrashing.

      PRACTICAL FIXES
           Add more RAM ; use a better replacement policy ; reduce the
           degree of multiprogramming.
   ```

   - The key point for the examiner: `thrashing is not caused by a slow CPU or a slow disk, but by giving processes fewer frames than their working sets need`. The fix is to reduce the load or increase the frames, never to admit more processes.

3. **a) Write about notes on i) Virtual memory, and ii) Cache memory.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*

   Answer: (i) Virtual memory
   - `Virtual memory` is a technique that lets a process run even when it is `larger than the physical RAM`. Only the parts currently needed are kept in RAM; the rest stays on disk in the `swap space`.
   ```
      Each process sees one large, continuous VIRTUAL ADDRESS SPACE.
      The MMU translates every virtual address into a physical address
      using the PAGE TABLE.

           virtual address = [ page number | offset ]
                                    |
                             page table lookup
                                    |
           physical address = [ frame number | offset ]
   ```
   - It works by `demand paging`: a page is brought in only when it is referenced. If the page is not resident, the valid bit is 0, the MMU raises a `page fault`, the OS fetches the page from disk into a free frame (evicting a victim if none is free), updates the page table and restarts the instruction.
   - Benefits: programs bigger than RAM can run, more processes fit in memory, each process is isolated from the others, and there is no external fragmentation.
   - Cost: a page fault costs milliseconds against nanoseconds for a memory access, and too little RAM leads to `thrashing`.

   (ii) Cache memory
   - `Cache memory` is a small, very fast memory placed between the CPU and main memory. It holds the data and instructions used most recently, so the CPU does not have to wait for slow RAM.
   ```
      CPU  <->  L1  <->  L2  <->  L3  <->  RAM  <->  DISK
           fastest, smallest  ----->  slowest, largest

      L1 : ~32 KB   , ~1-4 cycles
      L2 : ~256 KB-1 MB
      L3 : ~8-32 MB , shared between cores
   ```
   - It works because of `locality of reference`: `temporal` (a recently used item is likely to be used again) and `spatial` (neighbouring addresses are likely to be used next, so a whole block is fetched).
   - Mapping is `direct`, `fully associative` or `set associative`. Write policy is `write-through` or `write-back`.
   ```
      Average access time = h * Tc + (1 - h) * Tm
           h  = hit ratio , Tc = cache time , Tm = memory time
   ```

   The essential difference
   | Point | Virtual memory | Cache memory |
   |---|---|---|
   | Purpose | Run programs `bigger than RAM` | Make memory access `faster` |
   | Levels involved | RAM and `disk` | CPU and `RAM` |
   | Managed by | `Operating system` (software) | `Hardware` |
   | Unit moved | Page, 4 KB or larger | Block or line, 32-128 bytes |
   | Miss cost | Milliseconds (`page fault`) | Nanoseconds (`cache miss`) |
   | Miss handled by | OS page fault handler | Cache controller |

4. **Consider a reference string 4,7,6,1,2,7,2 the number of frames in the memory is 3. Using page Replacement Algorithm (LRU), find the number of page fault.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)]*

   Answer: Given, reference string = 4, 7, 6, 1, 2, 7, 2 with 3 frames, all initially empty, LRU policy.

   LRU rule
   ```
      On a fault with all frames full, replace the page that has NOT been
      USED for the LONGEST TIME.
   ```

   Step-by-step trace
   ```
    Ref     4     7     6     1     2     7     2
    F1      4     4     4     1     1     1     1
    F2      .     7     7     7     2     2     2
    F3      .     .     6     6     6     7     7
          FAULT FAULT FAULT FAULT FAULT FAULT  HIT
   ```
   ```
    Ref 4 : frames empty                 -> FAULT , load 4      [4]
    Ref 7 : not present , free frame     -> FAULT , load 7      [4,7]
    Ref 6 : not present , free frame     -> FAULT , load 6      [4,7,6]
    Ref 1 : not present , frames FULL
            last used : 4 -> t1 , 7 -> t2 , 6 -> t3
            oldest use = 4                -> FAULT , replace 4 with 1
                                                          [1,7,6]
    Ref 2 : not present , frames FULL
            last used : 7 -> t2 , 6 -> t3 , 1 -> t4
            oldest use = 7                -> FAULT , replace 7 with 2
                                                          [1,2,6]
    Ref 7 : not present , frames FULL
            last used : 6 -> t3 , 1 -> t4 , 2 -> t5
            oldest use = 6                -> FAULT , replace 6 with 7
                                                          [1,2,7]
    Ref 2 : PRESENT                       -> HIT
   ```

   Result
   ```
           Total references = 7
           Page faults      = 6
           Page hits        = 1

           Hit  ratio  = 1 / 7 = 0.143  (14.3 %)
           Miss ratio  = 6 / 7 = 0.857  (85.7 %)
   ```
   - The fault count is high because almost every page is referenced only once — there is little `locality of reference` for LRU to exploit. The first 3 faults are unavoidable `cold-start` faults, since the frames begin empty.

5. **Why virtual memory needed?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 477 (ET: N/A)]*

   Answer: What virtual memory is
   - `Virtual memory` lets a process run even when it is larger than the physical RAM. Only the pages currently in use stay in RAM; the rest sit on disk in the `swap space`.

   Why it is needed

   (a) Programs larger than RAM must still run
   ```
      A 4 GB program on a 2 GB machine :
           without virtual memory -> it cannot run at all
           with virtual memory    -> only the pages in use are resident,
                                     so it runs normally
   ```

   (b) More processes fit in memory, so the CPU stays busy
   ```
      Without VM : each process needs its FULL size in RAM, so few fit,
           and when they all block on I/O the CPU goes idle.
      With VM    : each process needs only its ACTIVE pages, so many more
           fit -> higher degree of multiprogramming -> better CPU
           utilisation and throughput.
   ```

   (c) The programmer is freed from memory limits
   - Before virtual memory the programmer had to split a program into `overlays` by hand and load them in turn. Virtual memory makes that automatic; the code is written against one large flat address space.

   (d) Protection and isolation between processes
   ```
      Every process has its OWN page table, so process A's virtual page 5
      and process B's virtual page 5 map to DIFFERENT frames.
      A stray pointer in A cannot touch B's memory - the MMU rejects any
      address not mapped in A's own page table.
   ```

   (e) No external fragmentation
   - Memory is handed out in fixed-size `frames`, so any free frame fits any page. There is no need to compact memory. Only a little `internal fragmentation` remains in the last page of a process.

   (f) Sharing and faster process creation
   ```
      One copy of a shared library (or the code of a program run twice)
      is kept in RAM and MAPPED into several page tables.
      COPY-ON-WRITE lets fork() share all pages read-only and copy a page
      only when one process writes to it - so process creation is cheap.
   ```

   How it works, in short
   ```
      Demand paging : a page is loaded only when referenced.

      reference -> valid bit = 1 ?  yes -> access memory
                                 no  -> PAGE FAULT
                                        -> find a free frame (replace a
                                           victim if none)
                                        -> read the page from disk
                                        -> update the page table
                                        -> restart the instruction
   ```

   The cost
   - A page fault costs `milliseconds` while a RAM access costs `nanoseconds`, so the fault rate must stay very low. If the frames given to processes fall below their `working sets`, the system starts `thrashing` — it spends all its time paging and almost none running.

6. **Consider page reference string 1, 3, 0, 3, 5, 6, 3 with 3 page frames. Find the number of page faults.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*

   Answer: Given, reference string = 1, 3, 0, 3, 5, 6, 3 with 3 frames, all initially empty. The policy is not stated, so `FIFO` is taken as the default and the other two are shown for comparison.

   FIFO — replace the page that came in earliest
   ```
    Ref     1     3     0     3     5     6     3
    F1      1     1     1     1     5     5     5
    F2      .     3     3     3     3     6     6
    F3      .     .     0     0     0     0     3
          FAULT FAULT FAULT  HIT  FAULT FAULT FAULT
   ```
   ```
    Ref 1 : free frame                  -> FAULT           [1]
    Ref 3 : free frame                  -> FAULT           [1,3]
    Ref 0 : free frame                  -> FAULT           [1,3,0]
    Ref 3 : present                     -> HIT
    Ref 5 : full , oldest in = 1        -> FAULT , 1 out   [5,3,0]
    Ref 6 : full , oldest in = 3        -> FAULT , 3 out   [5,6,0]
    Ref 3 : full , oldest in = 0        -> FAULT , 0 out   [5,6,3]
   ```
   ```
           Page faults = 6 ,  Hits = 1
           Hit ratio   = 1 / 7 = 0.143
   ```

   LRU — replace the page unused for the longest time
   ```
    Ref     1     3     0     3     5     6     3
    F1      1     1     1     1     5     5     5
    F2      .     3     3     3     3     3     3
    F3      .     .     0     0     0     6     6
          FAULT FAULT FAULT  HIT  FAULT FAULT  HIT
   ```
   ```
           Page faults = 5 ,  Hits = 2
   ```
   - LRU does better at reference 7: the hit on 3 at reference 4 made 3 recently used, so LRU kept it while FIFO threw it out.

   Optimal — replace the page needed farthest in the future
   ```
    Ref     1     3     0     3     5     6     3
    F1      1     1     1     1     5     6     6
    F2      .     3     3     3     3     3     3
    F3      .     .     0     0     0     0     0
          FAULT FAULT FAULT  HIT  FAULT FAULT  HIT
   ```
   ```
           Page faults = 5 ,  Hits = 2
   ```

   Result
   ```
           FIFO    = 6 page faults
           LRU     = 5 page faults
           OPTIMAL = 5 page faults
   ```
   - The first 3 faults in every case are unavoidable `cold-start` faults, because the frames start empty. FIFO loses one extra fault by evicting page 3, which was about to be used again — it looks only at `arrival time`, not at `usage`.

7. **Difference between physical memory and virtual memory, also describe the advantages and disadvantages of virtual memory.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 553 (ET: BIBM)]*

   Answer: Difference between physical memory and virtual memory

   | Point | Physical memory (RAM) | Virtual memory |
   |---|---|---|
   | What it is | The `actual hardware` — RAM chips on the board | A `technique` that uses RAM plus disk space |
   | Size | Fixed by the hardware installed | Limited by the `address space`, e.g. 4 GB on 32-bit |
   | Speed | Fast, nanoseconds | Slow when the disk is touched, milliseconds |
   | Location | RAM only | RAM + `swap space` on disk |
   | Addresses | `Physical addresses`, used by the memory bus | `Virtual addresses`, generated by the CPU |
   | Managed by | `Hardware` and the memory controller | `Operating system` and the MMU |
   | Cost | Expensive per GB | Cheap, uses existing disk |
   | Shared? | One physical RAM for the whole machine | Every process has `its own` virtual space |

   - How they connect: the CPU only ever issues `virtual addresses`. The `MMU` translates each one through the `page table` into a physical address. If the page is not in RAM the valid bit is 0, a `page fault` occurs, and the OS brings the page in from disk.
   ```
      virtual address = [ page number | offset ]
                               |
                        page table lookup
                               |
      physical address = [ frame number | offset ]
   ```

   Advantages of virtual memory
   - Programs `larger than RAM` can run — only the active pages need to be resident.
   - A `higher degree of multiprogramming`: each process needs only its working set in RAM, so more processes fit and the CPU stays busy.
   - `Protection and isolation` — each process has its own page table, so a stray pointer cannot reach another process's memory.
   - `No external fragmentation` — memory is given out in fixed-size frames, so any free frame fits any page. No compaction is needed.
   - `Sharing` — one copy of a shared library is mapped into many page tables. `Copy-on-write` makes `fork()` cheap.
   - The programmer no longer writes `overlays` by hand; one flat address space is assumed.

   Disadvantages of virtual memory
   - `Slow when it is actually used`: a page fault costs milliseconds against nanoseconds for a RAM access, so a high fault rate destroys performance.
   - `Thrashing` — if processes get fewer frames than their working sets, the system spends all its time paging and almost none running.
   - `Address translation overhead` on every reference; a `TLB` is needed to hide it, and a TLB miss costs extra memory accesses.
   - `Space cost` — page tables themselves occupy RAM, and swap space occupies disk.
   - `Internal fragmentation` in the last page of each process.
   - `Unpredictable timing`, which makes it unsuitable for hard `real-time` systems, where paging is usually disabled.

8. **(c) Define paging and trashing in the context of OS.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

   Answer: Paging
   - `Paging` is a memory management scheme that removes the need for a process to sit in one continuous block of RAM. Virtual memory is cut into fixed-size `pages` and physical memory into `frames` of the same size, and any page can go into any free frame.
   ```
      page size = frame size , typically 4 KB

      virtual address = [ page number p | offset d ]
                                 |
                         page table[p] = f
                                 |
      physical address = [ frame number f | offset d ]
   ```
   ```
      Process P (4 pages)              Physical memory (frames)
      +--------+                       +--------+ frame 0
      | page 0 |---------------------->| page 2 |
      +--------+                       +--------+ frame 1
      | page 1 |--------+              |  free  |
      +--------+        |              +--------+ frame 2
      | page 2 |---+    +------------->| page 1 |
      +--------+   |                   +--------+ frame 3
      | page 3 |-+ +------------------>| page 0 |
      +--------+ |                     +--------+ frame 4
                 +-------------------->| page 3 |
                                       +--------+
      The pages need NOT be next to each other in RAM.
   ```
   - What it gives: `no external fragmentation`, since any free frame fits any page; and it makes `virtual memory` possible, because unneeded pages can stay on disk.
   - What it costs: a little `internal fragmentation` in the last page, the RAM used by the `page table`, and one extra memory access per reference — which is why a `TLB` is added.

   Thrashing
   - `Thrashing` is the state where the system spends more time `swapping pages between RAM and disk` than executing processes. Useful work nearly stops.
   ```
      How it builds up :

      1. Too many processes are admitted.
      2. Each gets FEWER FRAMES than its WORKING SET.
      3. Nearly every reference is a PAGE FAULT.
      4. Processes block on the paging disk , so the CPU goes IDLE.
      5. The scheduler sees low CPU use and ADMITS MORE PROCESSES.
      6. Frames get thinner still -> back to step 3.
   ```
   ```
      CPU
      util
       |       ____
       |     /     \        <- thrashing starts here
       |   /         \
       | /             \____
       +---------------------> degree of multiprogramming
   ```
   - Symptoms: the disk runs continuously, response time becomes very long, throughput collapses and the CPU is mostly idle.
   - Cures: `working set model` — give each process enough frames for its active pages and suspend a process when the total exceeds the frames available; `page fault frequency` — add frames to a process whose fault rate is too high and take frames away when it is too low; `local replacement` so a faulting process can evict only its own pages; and in practice, more RAM or a lower degree of multiprogramming.

   - The relation between the two: paging is the `mechanism`, thrashing is what happens when that mechanism is `overloaded` — too many pages competing for too few frames.

9. **What is page fault in computing systems? What does it occur?** *[BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*

   Answer: What a page fault is
   - A `page fault` is the interrupt (a trap) raised by the hardware when a process refers to a page that is `not currently in physical memory`. It is not an error — in a demand-paged system it is the normal way pages get loaded.
   ```
      The page table entry carries a VALID / INVALID bit :

           valid bit = 1  ->  the page IS in a frame  -> access proceeds
           valid bit = 0  ->  the page is NOT resident -> PAGE FAULT
   ```

   When it occurs
   ```
      1. DEMAND PAGING - the first touch of a page. A new process starts
         with all pages invalid, so its first few references all fault.
         These are COLD-START faults and are unavoidable.
      2. The page was EVICTED earlier by the replacement algorithm and is
         referenced again.
      3. The page is in the SWAP FILE on disk, not in RAM.
      4. COPY-ON-WRITE - after fork(), a write to a shared page faults so
         the OS can make a private copy.
      5. MEMORY-MAPPED FILE - the first access to a mapped region.
      6. An INVALID reference - a wild pointer outside the address space.
         This one is a real error : the OS sends a segmentation fault and
         kills the process.
   ```

   How the OS handles it
   ```mermaid
   flowchart TD
       A[CPU references a page] --> B{Valid bit = 1?}
       B -->|Yes| C[Access memory - done]
       B -->|No| D[Trap to OS: page fault]
       D --> E{Free frame available?}
       E -->|No| F[Run page replacement, evict victim]
       E -->|Yes| G[Read page from disk into frame]
       F --> G
       G --> H[Update page table, valid bit = 1]
       H --> I[Restart the faulting instruction]
   ```
   ```
      Steps in order :
      1. The MMU traps to the kernel and saves the process state.
      2. The OS checks whether the reference is LEGAL. If not -> kill.
      3. It finds a free frame ; if there is none it runs the REPLACEMENT
         ALGORITHM (LRU, FIFO, clock) to pick a VICTIM. A DIRTY victim
         must be written back to disk first.
      4. It schedules a disk read for the required page and BLOCKS the
         process, so the CPU runs someone else meanwhile.
      5. When the read finishes it updates the page table and the TLB.
      6. It RESTARTS the faulting instruction - which now succeeds.
   ```

   Cost — why the fault rate must stay tiny
   ```
      Effective access time = (1 - p) * ma  +  p * (page fault time)

           p  = page fault rate
           ma = memory access time , say 100 ns
           page fault service time , say 8 ms = 8,000,000 ns

      If p = 0.001 :
           EAT = 0.999 * 100 + 0.001 * 8,000,000
               = 99.9 + 8000  =  8099.9 ns

      That is about 80 TIMES SLOWER than 100 ns.
      To keep the slowdown under 10 per cent, p must be below
      about 0.0000025 - roughly one fault in 400,000 accesses.
   ```
   - If the fault rate stays high because processes have fewer frames than their `working sets`, the system enters `thrashing` and throughput collapses.

   - Terminology worth keeping straight: a `page fault` means the page is not in RAM and is handled by the `operating system` in milliseconds. A `TLB miss` means only the translation is not cached; the page may still be in RAM, and the hardware handles it in nanoseconds.

10. **Write short note on Virtual Memory and Cache memory.** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

    Answer: Virtual memory
    - `Virtual memory` is a technique that lets a process run even when it is `larger than the installed RAM`. Only the pages currently in use are kept in RAM; the rest stay on disk in the `swap space`.
    ```
       The CPU issues only VIRTUAL addresses. The MMU translates each one
       through the PAGE TABLE :

            virtual address  = [ page number | offset ]
                                      |
                               page table lookup
                                      |
            physical address = [ frame number | offset ]
    ```
    - It runs on `demand paging`: a page is fetched only when referenced. If the valid bit is 0 the hardware raises a `page fault`; the OS finds a free frame (evicting a victim if none is free), reads the page from disk, updates the page table and restarts the instruction.
    - Advantages: programs bigger than RAM can run; more processes fit, so the CPU stays busy; each process is `isolated` by its own page table; there is `no external fragmentation`; and libraries can be shared, with `copy-on-write` making `fork()` cheap.
    - Cost: a page fault takes `milliseconds` against nanoseconds for a RAM access, and if processes get fewer frames than their `working sets` the system starts `thrashing` — all paging, no work.

    Cache memory
    - `Cache memory` is a small, very fast memory between the CPU and main memory. It holds recently and frequently used data and instructions so the CPU does not stall waiting for slow RAM.
    ```
       CPU <-> L1 <-> L2 <-> L3 <-> RAM <-> DISK
            fastest, smallest ------> slowest, largest

       L1 : ~32 KB  , 1-4 cycles , split into instruction and data
       L2 : ~256 KB - 1 MB , per core
       L3 : ~8-32 MB , shared between cores
    ```
    - It works because of `locality of reference` — `temporal` (what was just used will likely be used again) and `spatial` (nearby addresses come next, so a whole `block` is fetched, not one word).
    - Mapping is `direct`, `fully associative` or `set associative`. Writes use `write-through` (update both at once, simple) or `write-back` (update the cache and mark it dirty, faster).
    ```
       Average access time = h * Tc + (1 - h) * Tm

            h  = hit ratio , Tc = cache access time , Tm = memory time

       Example : h = 0.9 , Tc = 10 ns , Tm = 100 ns
            = 0.9 * 10 + 0.1 * 100 = 9 + 10 = 19 ns
    ```

    Difference in one view
    | Point | Virtual memory | Cache memory |
    |---|---|---|
    | Purpose | Run programs `bigger than RAM` | Make access `faster` |
    | Levels | RAM and `disk` | CPU and `RAM` |
    | Managed by | `Operating system` | `Hardware` |
    | Unit moved | Page, 4 KB or more | Block, 32-128 bytes |
    | Miss cost | Milliseconds (`page fault`) | Nanoseconds (`cache miss`) |

11. **(ii) Virtual Memory এর প্রয়োজনীয়তা কি ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 786 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What virtual memory is
    - `Virtual memory` lets a process run even when it is larger than the physical RAM. Only the pages in active use stay in RAM; the rest remain on disk in the `swap space`.

    Why it is needed

    (a) Address space limitation is removed
    ```
       A 4 GB program on a 2 GB machine :
            without virtual memory -> cannot be loaded , cannot run
            with virtual memory    -> only the ACTIVE pages are resident ,
                                      so it runs normally
    ```
    - Before virtual memory the programmer had to split a large program into `overlays` and load them by hand. Virtual memory does that automatically.

    (b) Higher degree of multiprogramming
    ```
       Without VM : each process needs its FULL size in RAM -> few
            processes fit -> when they block on I/O the CPU idles.
       With VM    : each process needs only its WORKING SET -> many more
            fit -> better CPU utilisation and throughput.
    ```

    (c) Protection and isolation
    ```
       Every process has its own PAGE TABLE, so process A's page 5 and
       process B's page 5 map to DIFFERENT frames. An address not mapped
       in A's page table is rejected by the MMU, so a stray pointer in A
       cannot touch B's memory.
    ```

    (d) No external fragmentation
    - RAM is handed out in fixed-size `frames`, so any free frame fits any page. Memory never has to be compacted; only a little `internal fragmentation` remains in the last page of a process.

    (e) Sharing and cheap process creation
    - One copy of a shared library is mapped into many page tables. `Copy-on-write` lets `fork()` share every page read-only and copy a page only when a process writes to it.

    How it works
    ```
       DEMAND PAGING - a page is loaded only when it is referenced.

            reference -> valid bit = 1 ? yes -> access memory
                                         no  -> PAGE FAULT
                                                -> get a free frame , or
                                                   evict a victim
                                                -> read the page from disk
                                                -> update the page table
                                                -> restart the instruction
    ```

    The cost
    ```
       Page fault  : MILLISECONDS
       RAM access  : NANOSECONDS

       So the fault rate must stay very low. If processes are given fewer
       frames than their working sets, the system THRASHES - it pages
       continuously and does almost no work.
    ```

12. **A system uses 3 page frames for storing process pages in main memory. It uses the Least Recently Used (LRU) page replacement policy. Assume that all the page frames are initially empty. What is the total number of page faults that will occur while processing the page reference string given below? 4, 7, 6, 1, 7, 6, 1, 2, 7, 2.** *[BPDB Assistant Engineer (CSE) 2021 compact it 817 (ET: BUET)]*

    Answer: Given, reference string = 4, 7, 6, 1, 7, 6, 1, 2, 7, 2 with 3 frames, all initially empty, LRU policy.

    LRU rule
    ```
       On a fault with all frames full, evict the page that has NOT been
       USED for the LONGEST TIME.
    ```

    Step-by-step trace
    ```
     Ref     4    7    6    1    7    6    1    2    7    2
     F1      4    4    4    1    1    1    1    1    1    1
     F2      .    7    7    7    7    7    7    2    2    2
     F3      .    .    6    6    6    6    6    6    7    7
           FLT  FLT  FLT  FLT  HIT  HIT  HIT  FLT  FLT  HIT
    ```
    ```
     Ref 4 : free frame                    -> FAULT  [4]
     Ref 7 : free frame                    -> FAULT  [4,7]
     Ref 6 : free frame                    -> FAULT  [4,7,6]
     Ref 1 : full ; last used 4@t1 7@t2 6@t3
             least recent = 4              -> FAULT , 4 out , 1 in
                                                      [1,7,6]
     Ref 7 : present                       -> HIT
     Ref 6 : present                       -> HIT
     Ref 1 : present                       -> HIT
     Ref 2 : full ; last used 7@t5 6@t6 1@t7
             least recent = 7              -> FAULT , 7 out , 2 in
                                                      [1,2,6]
     Ref 7 : full ; last used 6@t6 1@t7 2@t8
             least recent = 6              -> FAULT , 6 out , 7 in
                                                      [1,2,7]
     Ref 2 : present                       -> HIT
    ```

    Result
    ```
            Total references = 10
            Page faults      = 6
            Page hits        = 4

            Hit  ratio = 4 / 10 = 0.40  (40 %)
            Miss ratio = 6 / 10 = 0.60  (60 %)
    ```
    - 3 of the 6 faults are unavoidable `cold-start` faults, because the frames begin empty. Only 3 are genuine replacement faults.
    - Note reference 9: page 7 had just been evicted at reference 8 and is needed immediately afterwards. This is the weakness of a fixed-frame policy — the eviction decision uses only the `past`, while the request pattern depends on the `future`. Optimal replacement would have kept 7 and evicted 6 instead.

13. **Briefly explain the concept of ‘Thrashing’ in terms of OS.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 822 (ET: BUET)]*

    Answer: What thrashing is
    - `Thrashing` is the state in which the system spends more time `swapping pages between RAM and disk` than actually executing processes. Useful work almost stops.

    How it starts
    ```
       1. Too many processes are kept in memory at once.
       2. Each one gets FEWER FRAMES than its WORKING SET - the set of
          pages it is actively using.
       3. It cannot hold its active pages, so nearly every reference is a
          PAGE FAULT.
       4. The process blocks on the paging disk , so the CPU goes IDLE.
       5. The scheduler sees low CPU utilisation, thinks the system is
          under-loaded, and ADMITS MORE PROCESSES.
       6. The new processes steal frames from the old ones -> step 3.
    ```
    - The vicious circle is the point: the scheduler's attempted cure is what makes it worse.

    Effect on the system
    ```
       CPU
       util
        |       ____
        |     /     \        <- thrashing begins
        |   /         \
        | /             \____
        +---------------------> degree of multiprogramming
                  ^
            optimal point
    ```
    - Symptoms: the disk runs continuously, response time becomes very long, throughput collapses, and the CPU is mostly idle even though the machine seems frozen.

    Why it happens — locality
    - A program uses its pages unevenly. At any moment it works inside a small `locality` — one function's code, its local variables, an array being scanned. If the frames allotted can hold the current locality, faults are rare; if they cannot, faults explode.

    How it is controlled
    ```
       WORKING SET MODEL (Denning)
            W(t, D) = pages referenced in the last D references.
            Give each process enough frames to hold its working set.
            If SUM of working sets > total frames , SUSPEND a process.

       PAGE FAULT FREQUENCY (PFF)
            fault rate ABOVE the upper limit -> give MORE frames
            fault rate BELOW the lower limit -> take frames AWAY
            no frames left to give           -> SUSPEND a process

       LOCAL REPLACEMENT
            A faulting process may replace only ITS OWN pages, so it
            cannot steal frames and spread the problem.

       PRACTICAL : add RAM , use a better replacement policy , lower the
            degree of multiprogramming.
    ```

    - The key point: thrashing is not caused by a slow CPU or a slow disk. It is caused by giving processes `fewer frames than their working sets need`. The remedy is to reduce the load or increase the frames — never to admit more processes.

14. **(a) What do you mean by virtual memory?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

    Answer: What virtual memory is
    - `Virtual memory` is a technique that lets a process run even when it is `larger than the physical RAM`. Only the pages currently needed are kept in RAM; the rest stay on disk in the `swap space`. Each process therefore sees one large, continuous address space of its own, whatever the real memory size is.

    How it works
    ```
       The CPU issues only VIRTUAL addresses. The MMU translates each one
       through the PAGE TABLE :

            virtual address  = [ page number p | offset d ]
                                        |
                                page table[p] = f
                                        |
            physical address = [ frame number f | offset d ]

       The page table entry also holds :
            VALID bit  - is the page in RAM ?
            DIRTY bit  - has it been modified ?
            protection bits - read , write , execute
    ```
    ```
       DEMAND PAGING - fetch a page only when it is referenced :

            valid bit = 1  -> access memory , done
            valid bit = 0  -> PAGE FAULT
                              -> take a free frame , or evict a VICTIM
                                 chosen by LRU / FIFO / clock
                              -> write the victim back if it is DIRTY
                              -> read the wanted page from disk
                              -> set valid bit = 1 , update the TLB
                              -> RESTART the faulting instruction
    ```
    - A `TLB` (a small cache of recent translations) is used so most references need no page-table lookup at all.

    What it gives
    - Programs `bigger than RAM` can run.
    - A `higher degree of multiprogramming`, since each process needs only its working set resident — so the CPU stays busy.
    - `Protection` — each process has its own page table, so a stray pointer cannot reach another process's memory.
    - `No external fragmentation`, because any free frame fits any page.
    - `Sharing` of libraries, and cheap `fork()` through `copy-on-write`.

    The cost
    ```
       Page fault : MILLISECONDS      RAM access : NANOSECONDS

       Effective access time = (1 - p) * ma + p * (fault service time)

       With ma = 100 ns , fault = 8 ms , p = 0.001 :
            EAT = 0.999*100 + 0.001*8,000,000 = 8099.9 ns
            -> about 80 times slower than 100 ns
    ```
    - So the fault rate must be extremely small. If processes get fewer frames than their working sets, the system enters `thrashing` — it pages continuously and does almost no useful work.

15. **A system uses 8 page frames to store process pages in main memory. It uses the minimum page replacement policy. Assume that all page frames are initially blank. 64 separate pages were inserted and then the pages were inserted reverse order. How many pages will be miss?** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

    Answer: Given
    ```
       Frames                = 8 , all initially empty
       Policy                = MINIMUM page replacement (OPTIMAL / MIN) -
                               evict the page needed FARTHEST in the future
       64 distinct pages are referenced in order , then the SAME 64 pages
       are referenced in REVERSE order.

       Reference string : 1, 2, 3, ... , 64, 64, 63, 62, ... , 2, 1
       Total references : 64 + 64 = 128
    ```

    Phase 1 — the forward pass, references 1 to 64
    ```
       Every page is seen for the FIRST TIME, so every reference is a MISS.

            Misses in phase 1 = 64
    ```
    - What is left in the frames at the end matters. Optimal always evicts the page needed farthest ahead. During the forward pass, the pages needed soonest in the reverse pass are the `high-numbered` ones, so optimal keeps those and throws out the low-numbered ones.
    ```
       After reference 64, the 8 frames hold the LAST 8 pages loaded :

            { 57 , 58 , 59 , 60 , 61 , 62 , 63 , 64 }
    ```

    Phase 2 — the reverse pass, 64 down to 1
    ```
       64 -> HIT     63 -> HIT     62 -> HIT     61 -> HIT
       60 -> HIT     59 -> HIT     58 -> HIT     57 -> HIT
                                                 --> 8 HITS

       56 -> MISS , and from here on every page has already been evicted
            and will never be reused, so each one is a MISS :

            pages 56 , 55 , 54 , ... , 2 , 1   ->  56 MISSES
    ```
    ```
            Misses in phase 2 = 56
    ```

    Total
    ```
            Misses = 64 (forward)  +  56 (reverse)  =  120

            Hits   = 128 - 120 = 8

            Miss ratio = 120 / 128 = 0.9375   (93.75 %)
            Hit  ratio =   8 / 128 = 0.0625   ( 6.25 %)
    ```

    Answer: `120 page misses`.

    General formula for this pattern
    ```
       With F frames and N distinct pages referenced forward then reverse
       (N > F) :

            misses = N + (N - F)  =  2N - F

       Check : 2(64) - 8 = 128 - 8 = 120        matches
    ```
    - Why the result is so bad: only `8` of the 128 references hit. The reference pattern has no reuse within a window of 8 pages — page 1 is touched at reference 1 and again at reference 128, 127 references apart. No policy with 8 frames can help, and since MIN is provably `optimal`, FIFO and LRU cannot do better than 120 here either.

16. **(খ) Virtual Memory বলতে কী বোঝায়? এর কার্যপদ্ধতি সংক্ষেপে বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1093 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What virtual memory means
    - `Virtual memory` is a technique that lets a process run even when it is `larger than the installed RAM`. Only the pages currently in use are kept in RAM; the rest stay on disk in the `swap space`. Every process therefore sees one large, continuous address space of its own, regardless of the real memory size.

    Working procedure

    Step 1 — split memory into equal blocks
    ```
       Virtual memory of a process  ->  PAGES     (fixed size, e.g. 4 KB)
       Physical memory (RAM)        ->  FRAMES    (same size)

       Any page can go into any free frame - they need not be adjacent.
    ```

    Step 2 — address translation by the MMU
    ```
       virtual address  = [ page number p | offset d ]
                                    |
                            page table[p] = f
                                    |
       physical address = [ frame number f | offset d ]

       Each page table entry also holds :
            VALID bit      - is the page in RAM ?
            DIRTY bit      - was it modified ?
            protection bits - read / write / execute
    ```
    - A `TLB` caches the most recent translations, so most references need no page-table lookup.

    Step 3 — demand paging and the page fault
    ```mermaid
    flowchart TD
        A[CPU issues virtual address] --> B{Valid bit = 1?}
        B -->|Yes| C[Access the frame - done]
        B -->|No| D[Page fault - trap to OS]
        D --> E{Free frame?}
        E -->|No| F[Evict a victim, write back if dirty]
        E -->|Yes| G[Read the page from disk]
        F --> G
        G --> H[Update page table and TLB]
        H --> I[Restart the instruction]
    ```
    ```
       1. valid bit = 0  -> the hardware raises a PAGE FAULT.
       2. The OS checks that the reference is LEGAL ; if not , it kills
          the process with a segmentation fault.
       3. It finds a free frame ; if none , the REPLACEMENT ALGORITHM
          (LRU , FIFO , clock) picks a VICTIM. A DIRTY victim is written
          back to the swap space first.
       4. It reads the required page from disk , and BLOCKS the process
          meanwhile so the CPU can run another one.
       5. It updates the page table and the TLB.
       6. It RESTARTS the faulting instruction , which now succeeds.
    ```

    What it gives, and what it costs
    ```
       GIVES : programs bigger than RAM can run ; more processes fit , so
               CPU utilisation rises ; each process is ISOLATED by its own
               page table ; NO EXTERNAL FRAGMENTATION ; libraries can be
               shared , and fork() is cheap through COPY-ON-WRITE.

       COSTS : a page fault takes MILLISECONDS against NANOSECONDS for a
               RAM access ; page tables occupy RAM ; and if processes get
               fewer frames than their WORKING SETS the system THRASHES -
               it pages continuously and does almost no work.
    ```

## Memory Management & Paging (16)

1. **A system uses 16 bit logical address and a page size of 1 KB.**
   **(i) How many pages are in logical address space?**
   **(ii) How many bits are used for the page number and offset?** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*

   Answer: Given
   ```
      Logical address size = 16 bits
      Page size            = 1 KB = 1024 bytes = 2^10 bytes
   ```

   (i) Number of pages in the logical address space
   ```
      Logical address space = 2^16 bytes = 65536 bytes = 64 KB

      Number of pages = logical address space / page size
                      = 2^16 / 2^10
                      = 2^6
                      = 64 pages
   ```

   (ii) Bits for the page number and the offset
   ```
      Offset bits = log2(page size) = log2(2^10) = 10 bits

      Page number bits = total bits - offset bits
                       = 16 - 10
                       = 6 bits

      Check : 2^6 = 64 pages , which matches part (i).
   ```

   Address format
   ```
      16-bit logical address :

      +---------------------+--------------------------+
      |  page number  (6)   |     offset  (10)         |
      +---------------------+--------------------------+
           bits 15 - 10            bits 9 - 0

      Example : logical address 1500 (decimal)

           page number = 1500 / 1024 = 1
           offset      = 1500 % 1024 = 476
           -> byte 476 of page 1
   ```

   Answer
   ```
      (i)  Number of pages = 64
      (ii) Page number = 6 bits , Offset = 10 bits
   ```
   - Note that the page table for this process needs `64 entries`, one per page, and that the `physical` address size does not affect either answer — the offset is shared by both, while the frame number replaces the page number.

2. **Consider a logical address space of 512 pages, each of 2-KB page size, mapped onto a physical memory containing 128 frames.**
   **a. How many bits are required in the logical address?**
   **b. How many bits are required in the physical address?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

   Answer: Given
   ```
      Logical address space = 512 pages
      Page size             = 2 KB = 2048 bytes = 2^11 bytes
      Physical memory       = 128 frames
      Frame size = page size = 2 KB = 2^11 bytes
   ```

   a. Bits required in the logical address
   ```
      Page number bits = log2(number of pages)
                       = log2(512) = log2(2^9)
                       = 9 bits

      Offset bits      = log2(page size)
                       = log2(2048) = log2(2^11)
                       = 11 bits

      Logical address  = page number bits + offset bits
                       = 9 + 11
                       = 20 bits
   ```
   ```
      Cross-check : logical address space = 512 * 2 KB = 1024 KB = 1 MB
                    1 MB = 2^20 bytes  ->  20 bits      correct
   ```

   b. Bits required in the physical address
   ```
      Frame number bits = log2(number of frames)
                        = log2(128) = log2(2^7)
                        = 7 bits

      Offset bits       = 11 bits    (frame size = page size)

      Physical address  = frame number bits + offset bits
                        = 7 + 11
                        = 18 bits
   ```
   ```
      Cross-check : physical memory = 128 * 2 KB = 256 KB = 2^18 bytes
                    -> 18 bits      correct
   ```

   Address formats
   ```
      LOGICAL  (20 bits)
      +------------------+----------------------+
      | page number (9)  |     offset (11)      |
      +------------------+----------------------+

      PHYSICAL (18 bits)
      +---------------+----------------------+
      | frame no (7)  |     offset (11)      |
      +---------------+----------------------+

      Translation : the PAGE TABLE replaces the 9-bit page number with a
      7-bit frame number. The OFFSET is copied through UNCHANGED.
   ```

   Answer
   ```
      a. Logical address  = 20 bits
      b. Physical address = 18 bits
   ```
   - The logical space (1 MB) is larger than the physical memory (256 KB), which is exactly the case `virtual memory` is built for — only the pages in use are kept resident and the rest stay on disk.

3. **(a) Consider a computer system with the following specifications:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * Physical memory (RAM): 4\text{ GB}
 * Page size: 4\text{ KB}
 * Virtual address space: 32\text{ bits}
 * Page table entry size: 8\text{ bytes}
**Answer the following:**
 * **(i) How many pages are there in the virtual address space? Explain your answer.**
 * **(ii) What is the size of the page table? Explain your answer.**

   Answer: Given
   ```
      Physical memory (RAM)   = 4 GB
      Page size               = 4 KB = 2^12 bytes
      Virtual address space   = 32 bits
      Page table entry (PTE)  = 8 bytes
   ```

   (i) Number of pages in the virtual address space
   ```
      Virtual address space size = 2^32 bytes = 4 GB

      Number of pages = virtual address space / page size
                      = 2^32 / 2^12
                      = 2^20
                      = 1,048,576 pages   ( 1 M pages )
   ```
   - Why: a 32-bit address is split into a `page number` and an `offset`. The page size is `2^12`, so the low `12 bits` are the offset and the remaining `32 - 12 = 20 bits` are the page number. Twenty bits address `2^20` distinct pages.
   ```
      32-bit virtual address :

      +----------------------------+-------------------+
      |    page number  (20 bits)  |   offset (12)     |
      +----------------------------+-------------------+
   ```

   (ii) Size of the page table
   ```
      Page table size = number of pages * size of one entry
                      = 2^20 * 8 bytes
                      = 2^20 * 2^3
                      = 2^23 bytes
                      = 8 MB
   ```
   - Why: the page table needs `one entry per virtual page`, whether or not that page is resident. There are `2^20` pages and each entry is `8 bytes`, giving `8 MB` — `for every process`.
   ```
      The problem : 100 processes would need 800 MB of page tables in a
      4 GB machine, just to hold the tables. A single flat page table is
      therefore not practical.

      The fixes :
        MULTI-LEVEL PAGE TABLE - page the page table itself, so only the
             parts in use are resident.
        INVERTED PAGE TABLE    - one entry per FRAME, not per page ,
             so the size depends on RAM, not on the address space.
        LARGER PAGES           - 4 MB pages give 2^32 / 2^22 = 1024
             entries , a tiny table.
   ```

   Extra figures worth quoting
   ```
      Frames in physical memory = 4 GB / 4 KB = 2^32 / 2^12 = 2^20
                                = 1,048,576 frames

      Frame number bits = 20 , offset = 12
           -> physical address = 32 bits

      Here the virtual and physical spaces are the same size, so
      virtual memory buys ISOLATION and NO EXTERNAL FRAGMENTATION
      rather than extra capacity.
   ```

4. **Compare “Paging” and “Segmentation” memory management technique?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

   Answer: Comparison of paging and segmentation

   | Point | Paging | Segmentation |
   |---|---|---|
   | Division | Memory is split into `fixed-size` pages and frames | The process is split into `variable-size` segments |
   | Size decided by | The `hardware` — 4 KB, 8 KB and so on | The `programmer` / compiler, by logical unit |
   | Basis of division | `Physical` — a block of bytes with no meaning | `Logical` — code, data, stack, heap, a function |
   | Fragmentation | `Internal` only, in the last page | `External` — variable holes appear between segments |
   | User's view | `Invisible` to the programmer | `Visible` — it matches how the program is written |
   | Address form | `[ page number, offset ]`, one number split by bits | `[ segment number, offset ]`, two separate quantities |
   | Table used | `Page table` — page number to frame number | `Segment table` — base address and `limit` |
   | Offset check | Not needed; the offset cannot overflow a page | `Needed` — offset must be less than the limit |
   | Protection | Per page, so a page may mix code and data | `Natural` — a whole code segment is read-only |
   | Sharing | Possible but clumsy | `Easy` — share a whole library segment |
   | Compaction | Never needed | Sometimes needed, to close external holes |

   How the addresses are translated
   ```
      PAGING - the address is ONE number, split by BIT POSITION :

           +----------------+-----------+
           | page number p  | offset d  |
           +----------------+-----------+
                    |
             page table[p] = f
                    |
           physical = f * page size + d


      SEGMENTATION - the address is TWO quantities :

           +----------------+-----------+
           | segment no  s  | offset d  |
           +----------------+-----------+
                    |
           segment table[s] = ( base , limit )

           if d >= limit  ->  TRAP : addressing error
           else physical  =  base + d
   ```

   Why segmentation suffers external fragmentation
   ```
      Segments have different sizes, so freeing one leaves a HOLE :

      +--------+------+----------+-----+----------+
      | seg A  | FREE |  seg C   | FREE|  seg E   |
      |  40 K  | 20 K |   60 K   | 30 K|   50 K   |
      +--------+------+----------+-----+----------+

      50 K is free in total, but a 45 K segment will not fit in either
      hole. Paging never has this problem - ANY free frame fits ANY page.
   ```

   - What is used in practice: `paged segmentation`. Memory is seen as segments by the program, and each segment is then paged, so the design keeps segmentation's logical protection and sharing while paging removes the external fragmentation. The x86 architecture works this way.

5. **The __________ swaps process in and out of the memory.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

   Answer: The blank is filled by the `medium-term scheduler` (also called the `swapper`).
   ```
      The MEDIUM-TERM SCHEDULER swaps processes in and out of memory.
   ```

   The three schedulers
   ```
      LONG-TERM SCHEDULER   (job scheduler)
           Decides which jobs from the job pool are ADMITTED into memory.
           Controls the DEGREE OF MULTIPROGRAMMING.
           Runs rarely - seconds or minutes apart.

      MEDIUM-TERM SCHEDULER (swapper)
           SWAPS OUT a process from RAM to disk , and SWAPS IT IN later.
           Reduces the degree of multiprogramming when memory is tight.
           Runs occasionally.

      SHORT-TERM SCHEDULER  (CPU scheduler)
           Picks which READY process gets the CPU next.
           Runs very often - every few milliseconds.
   ```

   What swapping does
   ```
      RAM                              DISK (swap space / backing store)
      +-------------+                  +-------------------+
      |  process A  | ---- swap out -->|    process A      |
      +-------------+                  +-------------------+
      |  process B  | <--- swap in ----|    process C      |
      +-------------+                  +-------------------+
   ```
   - A swapped-out process moves to the `suspended` state, its memory is freed for others, and its whole image (or the pages it holds) is written to the `swap space`.

   Why it is done
   - To free RAM when memory is over-committed, and to lower the `degree of multiprogramming` when the system starts `thrashing`.
   - To move a low-priority or long-blocked process out so an urgent one can run.

   - Note the wording used in different books: some call the medium-term scheduler simply the `swapper`, and in a demand-paged system the same job is done page by page by the `pager`, which brings in individual pages instead of whole processes.

6. **Difference between Paging and Segmentation.** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

   Answer: Difference between paging and segmentation

   | Point | Paging | Segmentation |
   |---|---|---|
   | Division | Memory in `fixed-size` pages and frames | Process in `variable-size` segments |
   | Size decided by | `Hardware` — 4 KB, 8 KB and so on | `Programmer` / compiler, by logical unit |
   | Basis | `Physical` — a plain block of bytes | `Logical` — code, data, stack, heap |
   | Fragmentation | `Internal`, in the last page only | `External`, holes between segments |
   | Visible to user? | `No`, fully transparent | `Yes`, matches the program's structure |
   | Address | `[ page number, offset ]` — one number split by bits | `[ segment number, offset ]` — two quantities |
   | Table | `Page table` — page to frame | `Segment table` — base and `limit` |
   | Limit check | Not needed | `Needed` — offset must be below the limit |
   | Protection and sharing | Per page; a page may mix code and data | `Natural` — a whole code segment is read-only and shareable |

   Address translation compared
   ```
      PAGING - ONE number, split by BIT POSITION

           +---------------+-----------+
           | page number p | offset d  |
           +---------------+-----------+
                   |
            page table[p] = f
                   |
           physical = f * page size + d


      SEGMENTATION - TWO quantities, with a bounds check

           +---------------+-----------+
           | segment no s  | offset d  |
           +---------------+-----------+
                   |
           segment table[s] = ( base , limit )

           if d >= limit -> TRAP , addressing error
           else physical = base + d
   ```

   Why segmentation gives external fragmentation
   ```
      +--------+------+----------+------+----------+
      | seg A  | FREE |  seg C   | FREE |  seg E   |
      |  40 K  | 20 K |   60 K   | 30 K |   50 K   |
      +--------+------+----------+------+----------+

      50 K is free , but a 45 K segment fits in NEITHER hole.
      Paging cannot have this problem - any free frame fits any page.
   ```

   - In practice both are combined as `paged segmentation`: the program sees segments, and each segment is then paged. This keeps segmentation's logical protection and sharing while paging removes external fragmentation. The x86 architecture works this way.

7. **(ক) Swapping কী? Internal এবং External Fragmentation এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 414 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What swapping is
   - `Swapping` is moving a whole process out of RAM to the disk (the `swap space` or `backing store`) and bringing it back later. It frees memory for other processes when RAM is short.
   ```
      RAM                              DISK (swap space)
      +-------------+                  +----------------+
      |  process A  | ---- swap out -->|   process A    |
      +-------------+                  +----------------+
      |  process B  | <--- swap in ----|   process C    |
      +-------------+                  +----------------+
   ```
   - It is done by the `medium-term scheduler`, also called the `swapper`. A swapped-out process goes to the `suspended` state. It is used to lower the degree of multiprogramming when the system is short of memory or is `thrashing`.
   - The cost is high — the whole process image is written and read back — so modern systems swap `pages` instead of whole processes, which is `demand paging`.

   Difference between internal and external fragmentation

   | Point | Internal fragmentation | External fragmentation |
   |---|---|---|
   | What it is | Wasted space `inside` an allocated block | Free space `between` allocated blocks |
   | Cause | The block given is `larger` than requested | Free memory is split into `scattered small holes` |
   | Where it occurs | `Fixed-size` allocation — paging, fixed partitions | `Variable-size` allocation — segmentation, dynamic partitions |
   | Is the space usable? | No — it belongs to the process already | Yes in total, but `not as one piece` |
   | Cure | Use a smaller block size | `Compaction`, or use `paging` |
   | Present in paging? | `Yes`, in the last page | `No` — any free frame fits any page |

   Internal fragmentation
   ```
      Page size = 4 KB , process size = 10 KB

           page 0 : 4 KB  full
           page 1 : 4 KB  full
           page 2 : 2 KB used , 2 KB WASTED   <- internal fragmentation

      The 2 KB belongs to the process and cannot be given to anyone else.
      On average the waste is HALF A PAGE per process.
   ```

   External fragmentation
   ```
      +--------+------+----------+------+--------+
      | proc A | FREE |  proc C  | FREE | proc E |
      |  40 K  | 20 K |   60 K   | 30 K |  50 K  |
      +--------+------+----------+------+--------+

      Total free = 50 K , but a 45 K process fits in NEITHER hole,
      because the free memory is not CONTIGUOUS.
   ```
   - The cure for external fragmentation is `compaction` — sliding the processes together to make one big hole — but it is slow, and it only works if addresses are relocated at run time. This is exactly why `paging` was adopted: it removes external fragmentation completely, at the price of a little internal fragmentation.

8. **Find out total number of pages, when page size 4KB and address space 32 bit.** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 588 (ET: BUET)]*

   Answer: Given
   ```
      Page size    = 4 KB = 4096 bytes = 2^12 bytes
      Address space = 32 bits , so the space is 2^32 bytes = 4 GB
   ```

   Calculation
   ```
      Number of pages = address space size / page size

                      = 2^32 / 2^12

                      = 2^(32 - 12)

                      = 2^20

                      = 1,048,576 pages     ( 1 M pages )
   ```

   Bit-split view of the same result
   ```
      Page size 2^12 -> the OFFSET takes the low 12 bits.
      The remaining 32 - 12 = 20 bits are the PAGE NUMBER.
      20 bits address 2^20 = 1,048,576 pages.

      32-bit address :

      +-----------------------------+------------------+
      |    page number (20 bits)    |   offset (12)    |
      +-----------------------------+------------------+
   ```

   Answer
   ```
      Total number of pages = 2^20 = 1,048,576  ( about 1 million )
   ```
   - One consequence worth noting: the page table needs `one entry per page`, so with an 8-byte entry it would occupy `2^20 * 8 = 8 MB` for every process. That is why real systems use `multi-level` or `inverted` page tables instead of one flat table.

9. **(ক) Paging এবং Segmentation এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 609 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Difference between paging and segmentation

   | Point | Paging | Segmentation |
   |---|---|---|
   | Division | Memory in `fixed-size` pages and frames | Process in `variable-size` segments |
   | Size decided by | `Hardware` — 4 KB, 8 KB and so on | `Programmer` / compiler, by logical unit |
   | Basis | `Physical` — a plain block of bytes | `Logical` — code, data, stack, heap |
   | Fragmentation | `Internal`, in the last page | `External`, holes between segments |
   | Visible to user? | `No`, fully transparent | `Yes`, matches the program's structure |
   | Address | `[ page number, offset ]` — one number split by bits | `[ segment number, offset ]` — two quantities |
   | Table | `Page table` — page to frame | `Segment table` — base and `limit` |
   | Limit check | Not needed | `Needed` — offset must be below the limit |
   | Protection and sharing | Per page; a page may mix code and data | `Natural` — a whole code segment is read-only and shareable |
   | Compaction | Never needed | Sometimes needed, to close holes |

   Address translation
   ```
      PAGING - ONE number, split by BIT POSITION

           +---------------+-----------+
           | page number p | offset d  |
           +---------------+-----------+
                   |
            page table[p] = f
                   |
           physical = f * page size + d


      SEGMENTATION - TWO quantities, with a bounds check

           +---------------+-----------+
           | segment no s  | offset d  |
           +---------------+-----------+
                   |
           segment table[s] = ( base , limit )

           if d >= limit -> TRAP , addressing error
           else physical = base + d
   ```

   Why segmentation causes external fragmentation
   ```
      +--------+------+----------+------+--------+
      | seg A  | FREE |  seg C   | FREE | seg E  |
      |  40 K  | 20 K |   60 K   | 30 K |  50 K  |
      +--------+------+----------+------+--------+

      50 K is free , but a 45 K segment fits in NEITHER hole.
      With paging, ANY free frame fits ANY page, so this cannot happen.
   ```

   - What is actually used is `paged segmentation`: the program sees segments, and each segment is then paged. That keeps segmentation's logical protection and sharing while paging removes the external fragmentation. The x86 architecture works this way.

10. **(খ) Operating System-এর Memory hierarchy সচিত্র বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 611 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What the memory hierarchy is
    - The `memory hierarchy` arranges storage in levels. Going down the pyramid the memory gets `larger and cheaper but slower`; going up it gets `faster but smaller and costlier`. The aim is to give the CPU the speed of the top level at close to the cost of the bottom level.

    Diagram
    ```
                            /\
                           /  \        REGISTERS
                          /    \       ~1 KB , < 1 ns , inside CPU
                         /------\
                        /        \     CACHE  L1 / L2 / L3
                       /          \    32 KB - 32 MB , 1-20 ns , SRAM
                      /------------\
                     /              \  MAIN MEMORY (RAM)
                    /                \ 4 - 64 GB , ~100 ns , DRAM
                   /------------------\
                  /                    \  SECONDARY STORAGE
                 /                      \ SSD / HDD , 256 GB - 4 TB
                /                        \ 0.1 ms - 10 ms
               /--------------------------\
              /                            \ TERTIARY / BACKUP
             /                              \ tape , optical , cloud
            /________________________________\ TB - PB , seconds

       UPWARD  : faster , smaller , costlier per byte , volatile
       DOWNWARD: slower , larger , cheaper per byte , non-volatile
    ```

    Level by level
    ```
       REGISTERS   Inside the CPU. Hold the operands the ALU is working on
                   right now. Managed by the COMPILER.

       CACHE       SRAM between the CPU and RAM. Holds recently used data
                   and instructions. Managed by HARDWARE.
                   L1 per core (split into instruction and data),
                   L2 per core, L3 shared.

       MAIN MEMORY DRAM. Holds the running processes. Managed by the
                   OPERATING SYSTEM. Volatile.

       SECONDARY   SSD or hard disk. Holds files and the SWAP SPACE.
                   Non-volatile. Managed by the FILE SYSTEM.

       TERTIARY    Tape, optical or cloud. For archive and backup.
    ```

    Why the hierarchy works — locality of reference
    ```
       TEMPORAL locality : an item just used is likely to be used again
                           -> keep it in the fast level
       SPATIAL  locality : neighbouring addresses are used next
                           -> fetch a whole BLOCK, not one word

       So a small fast level, filled with the right data, satisfies MOST
       references. The slow levels are touched rarely.
    ```

    The two mechanisms that connect the levels
    ```
       CACHE  <-> RAM   : managed by HARDWARE , unit = BLOCK (32-128 B)
                          a miss costs NANOSECONDS

       RAM   <-> DISK   : managed by the OS , unit = PAGE (4 KB)
                          a miss is a PAGE FAULT , costing MILLISECONDS
    ```
    ```
       Average access time = h * T1 + (1 - h) * T2

            h = hit ratio at the faster level

       Example : h = 0.9 , cache 10 ns , RAM 100 ns
            = 0.9 * 10 + 0.1 * 100 = 19 ns
            -> close to cache speed at RAM cost
    ```

11. **(খ) Internal এবং External fragmentation এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) Difference between internal and external fragmentation

    | Point | Internal fragmentation | External fragmentation |
    |---|---|---|
    | What it is | Wasted space `inside` an allocated block | Free space `between` allocated blocks |
    | Cause | The block given is `bigger` than requested | Free memory is broken into `scattered small holes` |
    | Where it occurs | `Fixed-size` allocation — paging, fixed partitions | `Variable-size` allocation — segmentation, dynamic partitions |
    | Is the space usable? | No — it already belongs to the process | Yes in total, but `not as one piece` |
    | How it is measured | Block size − requested size | Total free memory − largest free hole |
    | Cure | Use a smaller block size | `Compaction`, or switch to `paging` |
    | Present in paging? | `Yes`, in the last page | `No` — any free frame fits any page |

    Internal fragmentation
    ```
       Page size = 4 KB , process size = 10 KB

            page 0 : 4 KB  fully used
            page 1 : 4 KB  fully used
            page 2 : 2 KB used , 2 KB WASTED   <- internal fragmentation

       That 2 KB is allocated to the process and cannot be given to
       anyone else. On average the waste is HALF A PAGE per process.
    ```

    External fragmentation
    ```
       +--------+------+----------+------+--------+
       | proc A | FREE |  proc C  | FREE | proc E |
       |  40 K  | 20 K |   60 K   | 30 K |  50 K  |
       +--------+------+----------+------+--------+

       Total free = 20 + 30 = 50 K
       Largest single hole = 30 K

       A 45 K process CANNOT be loaded, even though 50 K is free,
       because the free memory is not CONTIGUOUS.
    ```

    Compaction — the cure for external fragmentation
    ```
       BEFORE
       +--------+------+----------+------+--------+
       | proc A | FREE |  proc C  | FREE | proc E |
       +--------+------+----------+------+--------+

       AFTER  (processes slid together)
       +--------+----------+--------+----------------+
       | proc A |  proc C  | proc E |     FREE 50 K  |
       +--------+----------+--------+----------------+

       Now a 45 K process fits.
       Cost : all processes must be MOVED, which is slow, and it works
       only if addresses are relocated at RUN TIME (a relocation register).
    ```

    - The trade-off in one line: `paging removes external fragmentation completely but introduces a little internal fragmentation`, and since the loss is at most one page per process, that trade is almost always worth making. The 50 per cent rule for dynamic partitions makes the point — for every 2N blocks allocated, about N blocks' worth is lost to external fragmentation.

12. **(a) What is demand paging?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*

    Answer: What demand paging is
    - `Demand paging` is a way of implementing virtual memory in which a page is brought into RAM `only when it is actually referenced`, not when the process starts. It is `lazy loading` — nothing is fetched until it is needed.
    ```
       Without demand paging : load the WHOLE program into RAM, then run.
       With demand paging    : load NOTHING at first ; fetch each page
                               only when the process touches it.
    ```

    How it works
    ```
       Every page table entry carries a VALID / INVALID bit :

            valid = 1  ->  the page is in a frame  -> access proceeds
            valid = 0  ->  the page is on disk     -> PAGE FAULT
    ```
    ```mermaid
    flowchart TD
        A[Process references a page] --> B{Valid bit = 1?}
        B -->|Yes| C[Access the frame - done]
        B -->|No| D[Page fault - trap to OS]
        D --> E{Free frame available?}
        E -->|No| F[Replace a victim, write back if dirty]
        E -->|Yes| G[Read the page from disk]
        F --> G
        G --> H[Update page table, valid bit = 1]
        H --> I[Restart the instruction]
    ```
    ```
       The page fault is serviced in this order :
       1. Trap to the OS ; save the process state.
       2. Check that the reference is LEGAL ; if not, kill the process.
       3. Find a free frame , or run the REPLACEMENT ALGORITHM to pick a
          victim. Write the victim back if it is DIRTY.
       4. Schedule the disk read and BLOCK the process, so the CPU runs
          someone else meanwhile.
       5. Update the page table and the TLB.
       6. RESTART the faulting instruction.
    ```

    Advantages
    - A process `starts faster`, because only the first few pages are loaded.
    - `Less RAM per process`, so more processes fit — a higher degree of multiprogramming and better CPU utilisation.
    - Pages that are never used — error handlers, unused features — are `never loaded at all`.
    - Programs `larger than RAM` can run.

    The cost
    ```
       Effective access time = (1 - p) * ma + p * (page fault time)

            ma = 100 ns , fault service = 8 ms , p = fault rate

       p = 0.001 :
            EAT = 0.999*100 + 0.001*8,000,000 = 8099.9 ns
                -> about 80 times slower than plain RAM access
    ```
    - So `p` must be extremely small. If processes get fewer frames than their `working sets`, the fault rate stays high and the system `thrashes`.

    - Related term: `pure demand paging` starts a process with `no` pages resident at all, so the very first instruction causes a fault. Real systems soften this with `prepaging` — bringing in a few neighbouring pages at once, since `spatial locality` makes them likely to be needed.

13. **In the given example, let us assume the jobs and the memory requirements as the following: Job1=90k, Job2=20k, Job3=50k, Job4=200k. Let the free pace memory allocation blocks are: Block1=50k, Block2=100k, Block3=90k, Block4=200k, Block5=50k.** *[Janata Bank Assistant System Administrator 2021 compact it 939-940 (ET: N/A)]*

    Answer: The question gives the data but does not say which allocation strategy to apply, so all three standard strategies are worked out.
    ```
       Jobs (in order)   : J1 = 90 K , J2 = 20 K , J3 = 50 K , J4 = 200 K
       Free blocks       : B1 = 50 K , B2 = 100 K , B3 = 90 K ,
                           B4 = 200 K , B5 = 50 K
    ```

    (a) First Fit — take the first block big enough
    ```
       J1 = 90 K : B1=50 too small , B2=100 FITS       -> B2 , 10 K left
       J2 = 20 K : B1=50 FITS                          -> B1 , 30 K left
       J3 = 50 K : B1 has 30 , B2 has 10 , B3=90 FITS  -> B3 , 40 K left
       J4 = 200 K: B4=200 FITS                         -> B4 ,  0 K left

       Result
       +-------+---------+---------+-------------------+
       | Block |  Size   |   Job   |  Left over        |
       +-------+---------+---------+-------------------+
       |  B1   |   50 K  |   J2    |   30 K            |
       |  B2   |  100 K  |   J1    |   10 K            |
       |  B3   |   90 K  |   J3    |   40 K            |
       |  B4   |  200 K  |   J4    |    0 K            |
       |  B5   |   50 K  |    -    |   50 K unused     |
       +-------+---------+---------+-------------------+

       ALL 4 JOBS ALLOCATED.
       Internal fragmentation = 30 + 10 + 40 + 0 = 80 K
       Block B5 (50 K) stays completely free.
    ```

    (b) Best Fit — take the smallest block that is big enough
    ```
       J1 = 90 K : candidates B2=100 , B3=90 , B4=200 ; smallest = B3=90
                                                       -> B3 ,  0 K left
       J2 = 20 K : candidates B1=50 , B2=100 , B4=200 , B5=50 ;
                   smallest = B1=50 (first of the two 50 K)
                                                       -> B1 , 30 K left
       J3 = 50 K : candidates B2=100 , B4=200 , B5=50 ; smallest = B5=50
                                                       -> B5 ,  0 K left
       J4 = 200 K: candidates B4=200 ; smallest = B4   -> B4 ,  0 K left

       Result
       +-------+---------+---------+-------------------+
       | Block |  Size   |   Job   |  Left over        |
       +-------+---------+---------+-------------------+
       |  B1   |   50 K  |   J2    |   30 K            |
       |  B2   |  100 K  |    -    |  100 K unused     |
       |  B3   |   90 K  |   J1    |    0 K            |
       |  B4   |  200 K  |   J4    |    0 K            |
       |  B5   |   50 K  |   J3    |    0 K            |
       +-------+---------+---------+-------------------+

       ALL 4 JOBS ALLOCATED.
       Internal fragmentation = 30 K only - the BEST of the three.
       A whole 100 K block is left free for a future job.
    ```

    (c) Worst Fit — take the largest block available
    ```
       J1 = 90 K : largest = B4 = 200        -> B4 , 110 K left
       J2 = 20 K : largest = B4 rem 110      -> B4 ,  90 K left
       J3 = 50 K : largest = B2 = 100        -> B2 ,  50 K left
       J4 = 200 K: available now are
                   B1=50 , B2 rem 50 , B3=90 , B4 rem 90 , B5=50
                   the largest is only 90 K  -> J4 CANNOT BE ALLOCATED

       Result : only 3 of 4 jobs allocated.  J4 must WAIT.
    ```

    Comparison
    ```
       +------------+----------------+---------------------------+
       | Strategy   | Jobs placed    | Comment                   |
       +------------+----------------+---------------------------+
       | First Fit  | 4 of 4         | Fastest to compute        |
       | Best Fit   | 4 of 4         | Least waste , 30 K only   |
       | Worst Fit  | 3 of 4 , J4    | Worst - it broke up the   |
       |            | fails          | only 200 K block          |
       +------------+----------------+---------------------------+
    ```
    - The lesson this example teaches: `Worst Fit destroyed the one block large enough for the big job`. Best Fit did well here, though it is slower because the whole list must be scanned, and over time it tends to leave many tiny unusable holes. First Fit is the usual choice in practice — nearly as good and much faster.

14. **(ক) অপারেটিং সিস্টেম এর ক্ষেত্রে Swapping কী? কোন ক্ষেত্রে এটি ব্যবহৃত হয় লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094 (ET: N/A)]*

    Answer: (Answered in English, as required for IT topics.) What swapping is
    - `Swapping` is moving a whole process out of RAM to the disk and bringing it back later. The disk area used is called the `swap space` or `backing store`.
    ```
       RAM                              DISK (swap space)
       +-------------+                  +----------------+
       |  process A  | ---- swap out -->|   process A    |
       +-------------+                  +----------------+
       |  process B  | <--- swap in ----|   process C    |
       +-------------+                  +----------------+
    ```
    - `Swap out`: the process's memory image is written to disk and its frames are freed. The process moves to the `suspended` state.
    - `Swap in`: the image is read back into RAM (not necessarily to the same addresses, which is why run-time relocation is needed) and the process becomes `ready` again.
    - It is carried out by the `medium-term scheduler`, also called the `swapper`.

    ```mermaid
    stateDiagram-v2
        [*] --> Ready
        Ready --> Running: dispatch
        Running --> Ready: time slice over
        Running --> Blocked: I/O request
        Blocked --> Ready: I/O done
        Ready --> Suspended: swap out
        Suspended --> Ready: swap in
    ```

    Where swapping is used

    (a) When RAM is short
    - More processes have been admitted than memory can hold. Swapping one out frees its frames for the others.

    (b) To stop thrashing
    ```
       Too many processes -> each gets fewer frames than its WORKING SET
       -> page faults explode -> CPU idles.

       The cure is to SWAP OUT one or two processes, lowering the degree
       of multiprogramming so the rest get enough frames.
    ```

    (c) To favour a high-priority process
    - In `roll out, roll in`: a low-priority process is swapped out so an urgent one can be loaded and run at once, then the first is brought back.

    (d) When a process is blocked for a long time
    - A process waiting on slow I/O or user input is not going to run soon, so its frames are better used elsewhere.

    (e) In `hibernation`
    - The whole memory image of the system is written to disk so the machine can be powered off and resume from the same state.

    The cost, and what replaced it
    ```
       Swap time is dominated by TRANSFER TIME :

            a 100 MB process on a disk giving 50 MB per second
            = 2 seconds out + 2 seconds in = 4 SECONDS

       That is enormous. So classic whole-process swapping is rare today.
    ```
    - Modern systems swap `pages` rather than whole processes — `demand paging`. Only the individual pages that are not in use are written out, which is far cheaper. Linux still calls the disk area the `swap partition`, but what it actually does is page.

15. **(a) What do you mean by page table for memory management? Explain with example.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1129 (ET: N/A)]*

    Answer: What a page table is
    - A `page table` is the data structure the operating system keeps `for each process` to record which `frame` of physical memory holds each of its `pages`. It is the map the MMU uses to turn a virtual address into a physical one.
    ```
       One entry per virtual page. The entry holds :

            FRAME NUMBER    - where the page actually is in RAM
            VALID / INVALID - is the page resident ?
            DIRTY (modify)  - has it been written to ?
            REFERENCED      - has it been used recently ? (for LRU)
            PROTECTION      - read / write / execute permissions
    ```

    How it is used
    ```
       virtual address  = [ page number p | offset d ]
                                    |
                            page table[p] = f
                                    |
       physical address = [ frame number f | offset d ]

       The OFFSET is copied through UNCHANGED. Only the page number is
       translated. The PTBR (page table base register) in the CPU points
       to the current process's table, and it is reloaded on every
       context switch.
    ```

    Example
    ```
       Page size = 1 KB = 1024 bytes.  Process P has 4 pages.

       PAGE TABLE of P                      PHYSICAL MEMORY
       +------+-------+-------+             +---------+ frame 0
       | page | frame | valid |             | page 2  |
       +------+-------+-------+             +---------+ frame 1
       |  0   |   3   |   1   |             |  free   |
       |  1   |   6   |   1   |             +---------+ frame 2
       |  2   |   0   |   1   |             |  free   |
       |  3   |   -   |   0   | on disk     +---------+ frame 3
       +------+-------+-------+             | page 0  |
                                            +---------+ ...
                                            +---------+ frame 6
                                            | page 1  |
                                            +---------+

       Translate virtual address 1500 :
            page number = 1500 / 1024 = 1
            offset      = 1500 % 1024 = 476
            page table[1] = frame 6 , valid = 1
            physical address = 6 * 1024 + 476 = 6144 + 476 = 6620

       Translate virtual address 3200 :
            page number = 3200 / 1024 = 3
            offset      = 3200 % 1024 = 128
            page table[3] : valid = 0   ->  PAGE FAULT
            the OS loads page 3 from disk, fills in the frame number,
            sets valid = 1, and restarts the instruction.
    ```

    Two practical problems, and their fixes
    ```
       1. SPEED - the table is in RAM, so every reference would need TWO
          memory accesses (one for the table, one for the data).
          FIX : the TLB , a small associative cache of recent
          translations. With a 98 per cent hit ratio the extra cost is
          almost nil.

       2. SIZE - a 32-bit space with 4 KB pages has 2^20 pages ; at
          4 bytes per entry that is 4 MB PER PROCESS.
          FIX : MULTI-LEVEL page tables (page the page table itself, so
          only the parts in use are resident) , or an INVERTED page table
          (one entry per FRAME, so the size depends on RAM, not on the
          address space).
    ```

16. **Why page are sizes always powers of 2?** *[BCC-4TDC Assistant Programmer 2019 compact it 1161 (ET: BCC)]*

    Answer: Page sizes are always a power of 2 so that the hardware can split a virtual address into a `page number` and an `offset` by `simply cutting the bit string`, with no division or multiplication at all.

    The reason
    ```
       If page size = 2^k , then for any virtual address :

            page number = address / 2^k   =  address >> k   (right shift)
            offset      = address % 2^k   =  address & (2^k - 1)  (mask)

       A shift and a mask are FREE in hardware - they are just wires.
       No arithmetic circuit is involved.
    ```
    ```
       The address does not even need to be "split" - the SAME BITS ARE
       ALREADY the page number and the offset :

       32-bit address , page size 4 KB = 2^12

       +----------------------------+-------------------+
       |   page number (20 bits)    |   offset (12)     |
       +----------------------------+-------------------+
            bits 31 - 12                 bits 11 - 0

       Address 0x00003ABC :
            offset      = 0xABC   (low 12 bits)
            page number = 0x00003 (the rest)
       No calculation was performed.
    ```

    What would happen with a non-power-of-2 size
    ```
       Suppose page size = 1000 bytes.

            page number = address / 1000     <- an actual DIVISION
            offset      = address % 1000     <- an actual REMAINDER

       Integer division needs many clock cycles, and address translation
       happens on EVERY memory reference - several times per instruction.
       The CPU would be crippled.
    ```

    Other benefits that follow
    ```
       1. The physical address is built by CONCATENATION, not arithmetic :
               physical = ( frame number << 12 ) | offset
          Again just wires - no adder.

       2. NO WASTED ADDRESSES. With 12 offset bits, all 4096 combinations
          are legal. With a 1000-byte page, offsets 1000-4095 would be
          invalid and would need a bounds check.

       3. The TLB and page table can be indexed by taking BIT FIELDS
          directly out of the address.

       4. Every page starts on a natural boundary, so the low k bits of a
          frame's base address are always 0 - useful for ALIGNMENT.
    ```

    - The same argument explains why `cache block sizes`, `frame sizes`, `disk sector sizes` and `TLB entry counts` are also powers of 2. Common page sizes are `4 KB (2^12)`, `2 MB (2^21)` and `1 GB (2^30)` for huge pages — every one a power of two.

## Process Management & Process States (12)

1. **(b) What is process? Describe different states of a process.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

   Answer: What a process is
   - A `process` is a program in `execution`. A program is a passive file on disk; a process is the active thing the OS is running, with its own memory, registers and program counter.
   ```
      A process consists of :
           TEXT     - the program code
           DATA     - global and static variables
           HEAP     - memory allocated at run time (malloc / new)
           STACK    - function calls, parameters, local variables
           PROGRAM COUNTER and CPU registers
           PROCESS CONTROL BLOCK (PCB) - the OS's record of it
   ```
   - Two runs of the same program are `two different processes` — same code, separate memory and separate PCBs.

   The process states
   ```mermaid
   stateDiagram-v2
       [*] --> New
       New --> Ready: admitted
       Ready --> Running: dispatch
       Running --> Ready: interrupt / time slice over
       Running --> Waiting: I/O or event wait
       Waiting --> Ready: I/O or event done
       Running --> Terminated: exit
       Terminated --> [*]
   ```
   ```
      NEW        The process is being created. Its PCB is being set up
                 and it is not yet in memory.

      READY      It is in memory and ready to run, waiting only for the
                 CPU. It sits in the READY QUEUE. Many processes can be
                 ready at once.

      RUNNING    The CPU is executing its instructions. On a single-core
                 CPU only ONE process is running at a time.

      WAITING    It cannot continue until some event happens - an I/O
      (BLOCKED)  completion, user input, or a signal. It is NOT in the
                 ready queue and cannot be scheduled.

      TERMINATED It has finished or was killed. Its resources are freed
                 and its PCB is removed.
   ```

   The transitions, which are what carry the marks
   ```
      New -> Ready         ADMIT. The long-term scheduler lets it in.
      Ready -> Running     DISPATCH. The short-term scheduler picks it.
      Running -> Ready     TIMEOUT / PREEMPTION. Its time slice expired,
                           or a higher-priority process arrived. The
                           process is still able to run.
      Running -> Waiting   It ASKED for I/O or a resource, and must wait.
      Waiting -> Ready     The event finished. Note it goes to READY,
                           NOT straight to RUNNING - it must be
                           scheduled again.
      Running -> Terminated  exit() , or it was killed.
   ```
   - The distinction examiners look for: `Running -> Ready` is involuntary and the process could still run; `Running -> Waiting` is voluntary and the process cannot run until the event completes. There is `no Waiting -> Running` edge.

   - Two more states appear in systems that swap: `Suspended-Ready` and `Suspended-Blocked`, entered when the `medium-term scheduler` swaps a process out to disk to free memory.

2. **(c) Define context switch with proper example.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

   Answer: What a context switch is
   - A `context switch` is the act of saving the state of the process that is running and loading the saved state of another, so the CPU can switch from one process to the other.
   ```
      The "context" that is saved and restored :
           program counter (PC)
           all CPU registers , stack pointer , status flags
           memory management information - page table base register
           process state , priority , accounting data

      All of it is kept in the PROCESS CONTROL BLOCK (PCB).
   ```

   The steps
   ```mermaid
   sequenceDiagram
       participant P1 as Process P1
       participant OS as Kernel
       participant P2 as Process P2
       P1->>OS: interrupt or system call
       OS->>OS: save state of P1 into PCB1
       OS->>OS: select P2 (scheduler)
       OS->>OS: load state of P2 from PCB2
       OS->>P2: resume P2
   ```
   ```
      1. An INTERRUPT or SYSTEM CALL stops P1.
      2. The OS SAVES P1's registers and PC into PCB1.
      3. P1's state changes to READY or WAITING ; it joins a queue.
      4. The scheduler PICKS P2.
      5. The OS LOADS P2's registers and PC from PCB2.
      6. The page table base register is switched to P2's table, and
         the TLB is flushed or tagged.
      7. Control jumps to P2's saved PC ; P2 resumes exactly where it
         had stopped.
   ```

   Example
   ```
      P1 is a text editor , P2 is a music player. Time slice = 10 ms.

      t = 0 ms   P1 RUNNING. PC = 0x4021 , R1 = 55
      t = 10 ms  Timer interrupt.
                 SAVE : PCB1 <- PC 0x4021 , R1 = 55 , flags
                 P1 -> READY
                 LOAD : from PCB2 -> PC 0x8110 , R1 = 92
                 P2 -> RUNNING
      t = 20 ms  Timer interrupt again.
                 SAVE PCB2 , LOAD PCB1 -> P1 resumes at 0x4021 with
                 R1 = 55 , exactly as if nothing had happened.

      The user sees both the editor and the music running "together",
      though the CPU only ever ran one at a time.
   ```

   When it happens
   ```
      - the TIME SLICE expires (timer interrupt)
      - a process makes an I/O request and BLOCKS
      - a HIGHER-PRIORITY process becomes ready (preemption)
      - an interrupt from a device arrives
      - the process exits
   ```

   The cost
   ```
      A context switch is PURE OVERHEAD - no user work is done during it.

           typical cost : 1 - 100 microseconds
           plus an INDIRECT cost : the new process finds the CACHE and
           the TLB filled with the OLD process's data, so it runs slowly
           until they warm up again. This is often the bigger cost.

      That is why the time slice must not be too small : with a 1 ms
      slice and a 100 us switch, 10 per cent of the CPU is lost to
      switching alone.
   ```
   - A `thread` switch inside the same process is much cheaper, because the address space, the page table and the open files are shared — only the registers and the stack pointer change, and the TLB need not be flushed.

3. **(খ) Process কী? বিভিন্ন ধরনের Process state এর কাজ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 414 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What a process is
   - A `process` is a program in `execution`. The program is a passive file lying on disk; the process is the active thing the OS is actually running, with its own memory, registers and program counter.
   ```
      A process is made of :
           TEXT   - the program code
           DATA   - global and static variables
           HEAP   - memory allocated at run time
           STACK  - function calls , parameters , local variables
           program counter and CPU registers
           PROCESS CONTROL BLOCK (PCB) - the OS's record of it
   ```

   The states and what each one does
   ```mermaid
   stateDiagram-v2
       [*] --> New
       New --> Ready: admitted
       Ready --> Running: dispatch
       Running --> Ready: time slice over
       Running --> Waiting: I/O request
       Waiting --> Ready: I/O complete
       Running --> Terminated: exit
       Terminated --> [*]
   ```
   ```
      NEW
           The process is being created. The OS builds its PCB, assigns
           a PID and allocates memory. It is not yet running.
           Work done here : admission control - the LONG-TERM SCHEDULER
           decides whether memory is available to let it in.

      READY
           The process is in memory and can run ; it lacks only the CPU.
           It waits in the READY QUEUE.
           Work done here : the SHORT-TERM SCHEDULER chooses among all
           ready processes using FCFS , SJF , Round Robin or priority.

      RUNNING
           The CPU is executing its instructions. On one core, only ONE
           process is running at any instant.
           Work done here : the actual computation , plus system calls
           the process issues.

      WAITING (BLOCKED)
           The process cannot proceed until an event occurs - I/O
           completion, user input, a semaphore, a signal. It is NOT in
           the ready queue and cannot be scheduled.
           Work done here : the device or event is serviced ; when the
           interrupt arrives the process is moved back to READY.

      TERMINATED
           Execution has finished, or the process was killed. Its memory
           and open files are released and its PCB is removed.
           Work done here : the exit status is passed to the parent.
   ```

   The transitions
   ```
      New -> Ready         ADMIT      long-term scheduler
      Ready -> Running     DISPATCH   short-term scheduler
      Running -> Ready     TIMEOUT    preemption ; the process COULD
                                      still run
      Running -> Waiting   BLOCK      it asked for I/O ; VOLUNTARY
      Waiting -> Ready     WAKE UP    the event finished - note it goes
                                      to READY, not to RUNNING
      Running -> Terminated  EXIT
   ```
   - The point examiners look for: there is `no Waiting -> Running edge`. A woken process must queue up and be scheduled again like everyone else.
   - In systems that swap, two more states exist — `Suspended-Ready` and `Suspended-Blocked` — entered when the `medium-term scheduler` moves a process out to disk to free memory.

4. **Explain the process state.** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

   Answer: A `process state` says what a process is doing at this moment. The OS keeps the state in the process's `PCB` and moves it from queue to queue as the state changes.

   The five states
   ```mermaid
   stateDiagram-v2
       [*] --> New
       New --> Ready: admitted
       Ready --> Running: dispatch
       Running --> Ready: time slice over
       Running --> Waiting: I/O request
       Waiting --> Ready: I/O complete
       Running --> Terminated: exit
       Terminated --> [*]
   ```
   ```
      NEW        Being created. The PCB is set up and memory assigned.
                 Not yet in the ready queue.

      READY      In memory and able to run ; waiting only for the CPU.
                 Sits in the READY QUEUE. Many processes can be ready.

      RUNNING    The CPU is executing its instructions. Only ONE per
                 core at any instant.

      WAITING    Cannot proceed until an event occurs - I/O completion,
      (BLOCKED)  user input, a semaphore. NOT in the ready queue, so it
                 cannot be scheduled.

      TERMINATED Finished or killed. Resources freed, PCB removed.
   ```

   The transitions
   ```
      New -> Ready         ADMIT     the long-term scheduler lets it in
      Ready -> Running     DISPATCH  the short-term scheduler picks it
      Running -> Ready     TIMEOUT   its slice expired, or a higher
                                     priority process arrived.
                                     INVOLUNTARY - it could still run.
      Running -> Waiting   BLOCK     it REQUESTED I/O.
                                     VOLUNTARY - it cannot run now.
      Waiting -> Ready     WAKE UP   the event completed.
                                     It goes to READY, NOT to RUNNING.
      Running -> Terminated  EXIT
   ```

   Two points that are commonly asked
   ```
      1. There is NO  Waiting -> Running  edge.
         A woken process must join the ready queue and be scheduled
         again like every other ready process.

      2. There is NO  Ready -> Waiting  edge.
         Only a RUNNING process can ask for I/O, so only a running
         process can block.
   ```

   The difference between Ready and Waiting
   | Point | Ready | Waiting |
   |---|---|---|
   | Why it is not running | The CPU is busy | It is waiting for an `event` |
   | Could it run now? | `Yes`, if given the CPU | `No`, the CPU would not help |
   | Which queue | Ready queue | `Device` / event queue |
   | What frees it | The `scheduler` | An `interrupt` from the device |

   The suspended states
   ```
      When memory is short, the MEDIUM-TERM SCHEDULER swaps a process
      out to disk. Two more states then appear :

           SUSPENDED-READY    swapped out , but able to run
           SUSPENDED-BLOCKED  swapped out , and still waiting for an event

      Ready  ->  Suspended-Ready      swap out
      Suspended-Ready -> Ready        swap in
   ```
   - Why the state is tracked at all: the OS keeps one queue per state, so scheduling is just picking from the right queue. It never has to search through every process to find one that can run.

5. **(ক) Process কী? একটি Process এর বিভিন্ন ধাপগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What a process is
   - A `process` is a program in `execution`. The program is a passive file on disk; the process is the active running instance, with its own memory, registers and program counter.
   ```
      The parts of a process in memory :

      +----------------+  high address
      |     STACK      |  function calls , locals , parameters
      |       |        |  (grows DOWN)
      |       v        |
      +----------------+
      |     free       |
      +----------------+
      |       ^        |
      |       |        |  (grows UP)
      |     HEAP       |  malloc / new
      +----------------+
      |     DATA       |  global and static variables
      +----------------+
      |     TEXT       |  the program code
      +----------------+  low address
   ```
   - Two runs of the same program are `two separate processes`: the same code, but separate memory and separate `PCB`s.

   The stages a process goes through
   ```mermaid
   stateDiagram-v2
       [*] --> New
       New --> Ready: admitted
       Ready --> Running: dispatch
       Running --> Ready: time slice over
       Running --> Waiting: I/O request
       Waiting --> Ready: I/O complete
       Running --> Terminated: exit
       Terminated --> [*]
   ```
   ```
      1. NEW
         The process is created. The OS allots a PID, builds the PCB
         and assigns memory. The LONG-TERM SCHEDULER decides whether to
         admit it.

      2. READY
         It is in memory and can run - only the CPU is missing. It waits
         in the READY QUEUE, from which the SHORT-TERM SCHEDULER picks.

      3. RUNNING
         The CPU is executing its instructions. Only one process per
         core at a time.

      4. WAITING (BLOCKED)
         It asked for I/O or an event and cannot continue. It leaves the
         ready queue and joins a device queue.

      5. TERMINATED
         It has finished or been killed. Memory and open files are
         released, the exit status goes to the parent, and the PCB is
         removed.
   ```

   The transitions between the stages
   ```
      New -> Ready          ADMIT
      Ready -> Running      DISPATCH
      Running -> Ready      TIMEOUT , preemption - INVOLUNTARY , and the
                            process could still run
      Running -> Waiting    BLOCK - VOLUNTARY , it asked for I/O
      Waiting -> Ready      WAKE UP - it goes to READY, NOT to RUNNING
      Running -> Terminated EXIT
   ```
   - Note there is `no Waiting -> Running` transition and `no Ready -> Waiting` transition: only a running process can ask for I/O, and a woken process must be scheduled again before it runs.
   - Where swapping is used, two more stages exist — `Suspended-Ready` and `Suspended-Blocked` — reached when the `medium-term scheduler` moves a process out to disk to free memory.

6. **অথবা, (ক) Process Control Block (PCB) কী? এটি একটি Process সংক্রান্ত যে যে তথ্য রাখে সেগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What a PCB is
   - A `Process Control Block (PCB)` is the data structure the OS keeps for `every process`. It holds everything the OS needs to manage that process and, above all, everything needed to `stop it and restart it later exactly where it left off`. It is also called the `task control block`.
   - Every process has `exactly one` PCB. The OS keeps them all in a process table and links them into the ready and device queues.

   What it stores
   ```
      1. PROCESS IDENTIFICATION
           PID , parent PID (PPID) , user ID , group ID

      2. PROCESS STATE
           new / ready / running / waiting / terminated

      3. PROGRAM COUNTER
           the address of the NEXT instruction to execute

      4. CPU REGISTERS
           accumulator , index registers , stack pointer , general
           registers , condition flags - saved on a context switch

      5. CPU SCHEDULING INFORMATION
           priority , pointer to the scheduling queue , time slice used,
           scheduling parameters

      6. MEMORY MANAGEMENT INFORMATION
           base and limit registers , page table or segment table
           pointer , page table base register value

      7. ACCOUNTING INFORMATION
           CPU time used , real time elapsed , time limits , process
           numbers , resource usage

      8. I/O STATUS INFORMATION
           list of open files , allocated devices , pending I/O
           requests

      9. INTER-PROCESS COMMUNICATION
           pending signals , message queue pointers , semaphore state

      10. POINTER
           link to the next PCB in the ready or device queue
   ```

   Diagram
   ```
      +--------------------------------+
      |   pointer      |  process state|
      +--------------------------------+
      |          process ID            |
      +--------------------------------+
      |        program counter         |
      +--------------------------------+
      |         CPU registers          |
      +--------------------------------+
      |     memory limits / page table |
      +--------------------------------+
      |        list of open files      |
      +--------------------------------+
      |   accounting and priority      |
      +--------------------------------+
   ```

   Why it matters — the context switch
   ```
      When the OS switches from P1 to P2 :

           SAVE  P1's PC and registers  ->  PCB1
           LOAD  P2's PC and registers  <-  PCB2

      Without the PCB a stopped process could never be resumed. The PCB
      IS the process, as far as the operating system is concerned.
   ```
   - The PCB is kept in `kernel memory` only. A user process cannot read or write its own PCB — it can only ask through system calls such as `getpid()` or `nice()`. This is what makes process isolation and protection possible.

7. **Write down the name of four information stored in PCB (Process Control Block).** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

   Answer: Four pieces of information stored in the `Process Control Block`:
   ```
      1. PROCESS ID (PID) and process state
           The unique number identifying the process, and whether it is
           new , ready , running , waiting or terminated.

      2. PROGRAM COUNTER
           The address of the NEXT instruction to be executed. This is
           what lets a stopped process resume at exactly the right place.

      3. CPU REGISTERS
           Accumulator , index registers , stack pointer , general
           registers and condition flags - all saved on a context switch
           and restored when the process runs again.

      4. MEMORY MANAGEMENT INFORMATION
           Base and limit register values , and the pointer to the
           process's page table or segment table.
   ```

   Other fields, if more are asked for
   ```
      5. CPU SCHEDULING INFO  - priority , queue pointers , time slice
      6. ACCOUNTING INFO      - CPU time used , real time elapsed ,
                                time limits
      7. I/O STATUS INFO      - open files , allocated devices , pending
                                I/O requests
      8. IPC INFO             - pending signals , message queue pointers
      9. PARENT PID and the list of child processes
   ```

   Layout
   ```
      +--------------------------------+
      |  pointer       | process state |
      +--------------------------------+
      |         process ID (PID)       |
      +--------------------------------+
      |        program counter         |
      +--------------------------------+
      |         CPU registers          |
      +--------------------------------+
      |  memory limits / page table    |
      +--------------------------------+
      |       list of open files       |
      +--------------------------------+
   ```

   Why these four matter most
   ```
      On a CONTEXT SWITCH the OS must :
           SAVE  the PC and registers into the PCB of the outgoing
                 process
           LOAD  the PC and registers from the PCB of the incoming one
           SWITCH the page table pointer to the new process's table

      Without the PC and registers the process could not resume ;
      without the memory information it would read another process's
      memory. The PCB is kept in KERNEL memory, so a user process can
      never touch it directly.
   ```

8. **Operating System এর Process state diagram অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

   Answer: (Answered in English, as required for IT topics.) Process state diagram
   ```mermaid
   stateDiagram-v2
       [*] --> New
       New --> Ready: admitted
       Ready --> Running: dispatch (scheduler)
       Running --> Ready: interrupt / time slice over
       Running --> Waiting: I/O or event wait
       Waiting --> Ready: I/O or event complete
       Running --> Terminated: exit
       Terminated --> [*]
   ```
   ```
                            admitted
           +-------+  ------------------>  +---------+
           |  NEW  |                       |  READY  |<---------+
           +-------+                       +---------+          |
                                           |       ^            |
                                 dispatch  |       | interrupt  |
                                           v       |            |
                                       +-------------+          |
                                       |   RUNNING   |          |
                                       +-------------+          |
                                        |          |            |
                                 exit   |          | I/O request|
                                        v          v            |
                                +------------+  +---------+     |
                                | TERMINATED |  | WAITING |-----+
                                +------------+  +---------+
                                                    I/O complete
   ```

   The five states
   ```
      NEW        Being created ; the PCB is set up and memory assigned.
      READY      In memory , able to run , waiting only for the CPU.
                 It sits in the READY QUEUE.
      RUNNING    The CPU is executing its instructions. One per core.
      WAITING    Blocked on an event - I/O , user input , a semaphore.
                 Not in the ready queue , so it cannot be scheduled.
      TERMINATED Finished or killed ; resources freed , PCB removed.
   ```

   The six transitions
   ```
      New -> Ready          ADMIT      the long-term scheduler admits it
      Ready -> Running      DISPATCH   the short-term scheduler picks it
      Running -> Ready      TIMEOUT    time slice expired or preempted -
                                       INVOLUNTARY , it could still run
      Running -> Waiting    BLOCK      it REQUESTED I/O - VOLUNTARY
      Waiting -> Ready      WAKE UP    the event finished ; it goes to
                                       READY , not to RUNNING
      Running -> Terminated EXIT
   ```
   - Two edges that do `not` exist, and are often asked about: there is `no Waiting -> Running` (a woken process must be scheduled again) and `no Ready -> Waiting` (only a running process can issue an I/O request).

   With swapping — the seven-state diagram
   ```
      When memory is short, the MEDIUM-TERM SCHEDULER swaps a process
      out to disk :

           Ready   <---- swap in ----  SUSPENDED-READY
                   ---- swap out --->

           Waiting <---- swap in ----  SUSPENDED-BLOCKED
                   ---- swap out --->

      SUSPENDED-BLOCKED -> SUSPENDED-READY when its event completes
      while it is still on disk.
   ```

9. **(i) Operating System এর Process State Transition Diagram আঁকুন ও ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 786 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Process state transition diagram
   ```mermaid
   stateDiagram-v2
       [*] --> New
       New --> Ready: admitted
       Ready --> Running: dispatch
       Running --> Ready: interrupt / time slice over
       Running --> Waiting: I/O or event wait
       Waiting --> Ready: I/O or event complete
       Running --> Terminated: exit
       Terminated --> [*]
   ```
   ```
                            admitted
           +-------+  ------------------>  +---------+
           |  NEW  |                       |  READY  |<---------+
           +-------+                       +---------+          |
                                           |       ^            |
                                 dispatch  |       | interrupt  |
                                           v       |            |
                                       +-------------+          |
                                       |   RUNNING   |          |
                                       +-------------+          |
                                        |          |            |
                                 exit   |          | I/O request|
                                        v          v            |
                                +------------+  +---------+     |
                                | TERMINATED |  | WAITING |-----+
                                +------------+  +---------+
                                                   I/O complete
   ```

   The states
   ```
      NEW        The process is being created. The OS assigns a PID,
                 builds the PCB and allots memory.
      READY      In memory and able to run ; only the CPU is missing.
                 It waits in the READY QUEUE.
      RUNNING    The CPU is executing its instructions. Only one per
                 core at any instant.
      WAITING    Blocked until an event happens - I/O completion, user
                 input, a semaphore. Not schedulable.
      TERMINATED Finished or killed ; memory and files released, PCB
                 removed.
   ```

   Explanation of each transition
   ```
      1. New -> Ready       ADMIT
           The LONG-TERM SCHEDULER decides there is enough memory and
           admits the process. This controls the degree of
           multiprogramming.

      2. Ready -> Running   DISPATCH
           The SHORT-TERM SCHEDULER selects it by FCFS , SJF , Round
           Robin or priority, and the dispatcher loads its context.

      3. Running -> Ready   TIMEOUT / PREEMPTION
           The time slice expired, or a higher-priority process became
           ready. INVOLUNTARY - the process was perfectly able to
           continue, so it returns to the ready queue.

      4. Running -> Waiting  BLOCK
           The process itself asked for I/O or a resource. VOLUNTARY -
           it cannot continue, so keeping the CPU would waste it. It
           leaves the ready queue for a device queue.

      5. Waiting -> Ready    WAKE UP
           The device interrupt arrives and the event completes. Note
           carefully that it goes to READY , NOT to RUNNING - it must
           be scheduled again like everyone else.

      6. Running -> Terminated  EXIT
           exit() was called, or the process was killed. The exit status
           is passed to the parent and the PCB is freed.
   ```

   Two transitions that do not exist
   ```
      Waiting -> Running : NO. A woken process must queue and be
           scheduled again ; the CPU may be busy with someone else.

      Ready -> Waiting   : NO. Only a RUNNING process can execute an
           I/O instruction, so only a running process can block.
   ```

   With swapping
   ```
      Ready   <-- swap in / swap out -->  SUSPENDED-READY
      Waiting <-- swap in / swap out -->  SUSPENDED-BLOCKED

      Done by the MEDIUM-TERM SCHEDULER to free memory when RAM is
      short or the system is thrashing.
   ```

10. **Operating System এর ক্ষেত্রে নিম্নোক্ত Process State গুলো ব্যবহার করে State Diagram অংকন করুন। [New, ready, Wait, Run, Terminated]** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1040 (ET: DPI)]*

    Answer: (Answered in English, as required for IT topics.) State diagram using New, Ready, Wait, Run and Terminated
    ```mermaid
    stateDiagram-v2
        [*] --> New
        New --> Ready: admitted
        Ready --> Run: dispatch
        Run --> Ready: time slice over / preempted
        Run --> Wait: I/O request
        Wait --> Ready: I/O complete
        Run --> Terminated: exit
        Terminated --> [*]
    ```
    ```
                             admitted
            +-------+  ------------------>  +---------+
            |  NEW  |                       |  READY  |<---------+
            +-------+                       +---------+          |
                                            |       ^            |
                                  dispatch  |       | preempted  |
                                            v       |            |
                                        +-------------+          |
                                        |     RUN     |          |
                                        +-------------+          |
                                         |          |            |
                                  exit   |          | I/O request|
                                         v          v            |
                                 +------------+  +---------+     |
                                 | TERMINATED |  |  WAIT   |-----+
                                 +------------+  +---------+
                                                    I/O complete
    ```

    The states
    ```
       NEW        Being created. The OS assigns a PID, builds the PCB and
                  allots memory. Not yet runnable.

       READY      In memory and able to run ; only the CPU is missing.
                  It sits in the READY QUEUE.

       RUN        The CPU is executing its instructions. Only one process
                  per core at any instant.

       WAIT       Blocked on an event - I/O completion, user input, a
                  semaphore. It is NOT in the ready queue and cannot be
                  scheduled.

       TERMINATED Finished or killed. Memory and open files are released
                  and the PCB is removed.
    ```

    The transitions
    ```
       New -> Ready          ADMIT     the long-term scheduler admits it
       Ready -> Run          DISPATCH  the short-term scheduler picks it
       Run -> Ready          TIMEOUT   its time slice expired , or a
                                       higher-priority process arrived.
                                       INVOLUNTARY - it could still run.
       Run -> Wait           BLOCK     it REQUESTED I/O. VOLUNTARY - it
                                       cannot use the CPU now.
       Wait -> Ready         WAKE UP   the event completed. It goes to
                                       READY , NOT straight to RUN.
       Run -> Terminated     EXIT      exit() , or it was killed.
    ```

    The two edges that must not be drawn
    ```
       Wait  -> Run   : WRONG. A woken process joins the READY queue and
                        must be scheduled again ; the CPU may be busy.

       Ready -> Wait  : WRONG. Only a RUNNING process can execute an I/O
                        instruction, so only a running process can block.
    ```
    - The difference between Ready and Wait is what the diagram is really testing: a `Ready` process needs only the CPU, while a `Wait` process would not benefit from the CPU at all — it needs an `event`. That is why they sit in different queues, and why the scheduler looks only at the ready queue.

11. **(c) What are the difference between process and threads?** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130 (ET: N/A)]*

    Answer: Difference between a process and a thread

    | Point | Process | Thread |
    |---|---|---|
    | Definition | A program in `execution`, with its own memory | A `lightweight` unit of execution `inside` a process |
    | Memory | Has its `own` address space | `Shares` the process's code, data and heap |
    | What is private | Everything | Only the `stack`, registers and program counter |
    | Creation cost | `High` — a new address space and page table | `Low` — only a stack and a register set |
    | Context switch | `Slow` — the page table changes, the TLB is flushed | `Fast` — the address space is unchanged |
    | Communication | Needs `IPC` — pipes, shared memory, message queues | Direct, through `shared variables` |
    | Isolation | Strong — one crash does not touch the others | `Weak` — one bad thread can crash the whole process |
    | Synchronisation | Rarely needed between processes | `Essential` — mutex, semaphore, for shared data |
    | Dependence | Independent | Cannot exist without its parent process |

    Memory picture
    ```
       PROCESS A                    PROCESS B
       +-------------+              +-------------+
       |    STACK    |              |    STACK    |
       |    HEAP     |              |    HEAP     |
       |    DATA     |              |    DATA     |
       |    TEXT     |              |    TEXT     |
       +-------------+              +-------------+
       SEPARATE address spaces - A cannot touch B's memory.


       ONE PROCESS WITH THREE THREADS
       +--------------------------------------------+
       | stack T1 |  stack T2  |  stack T3          |  PRIVATE
       +--------------------------------------------+
       |            HEAP  (shared)                  |
       |            DATA  (shared)                  |  SHARED
       |            TEXT  (shared)                  |
       +--------------------------------------------+
       Each thread has its own PC and registers.
    ```

    What is shared and what is not
    ```
       SHARED among threads : code , global and static data , heap ,
                              open files , signals , the address space
       PRIVATE to a thread  : stack , registers , program counter ,
                              thread ID , errno
    ```

    Why threads are used
    - `Responsiveness` — a GUI stays alive while a background thread does the slow work.
    - `Cheap` — creating a thread and switching between threads costs far less than for a process.
    - `Easy sharing` — threads use the same variables directly, with no IPC layer.
    - `Parallelism` — different threads can run on different cores at the same time.

    The price
    - Because the heap and globals are shared, two threads writing the same variable create a `race condition`, so `mutexes` and `semaphores` are needed. Processes rarely have this problem, because their memory is separate.
    - One thread's segmentation fault kills the `entire process`, taking every other thread with it. A crashing process leaves its siblings untouched. This is exactly why Chrome puts each tab in a separate `process` rather than a thread.

12. **(b) What are the difference between process and thread?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1139 (ET: N/A)]*

    Answer: Difference between a process and a thread

    | Point | Process | Thread |
    |---|---|---|
    | What it is | A program in `execution`, with its own memory | A `lightweight` unit of execution `inside` a process |
    | Address space | `Own` address space and page table | `Shares` the process's address space |
    | Private data | Everything belongs to it | Only the `stack`, registers and program counter |
    | Creation cost | `High` — build an address space and a PCB | `Low` — just a stack and a register set |
    | Context switch | `Slow` — page table switch, TLB flush | `Fast` — no address-space change |
    | Communication | Through `IPC` — pipes, shared memory, sockets | Directly through `shared variables` |
    | Isolation | `Strong` — a crash affects only itself | `Weak` — a crash kills every thread in the process |
    | Synchronisation | Seldom needed | `Required` — mutex, semaphore |
    | Also called | Heavyweight process | Lightweight process (LWP) |

    Memory picture
    ```
       TWO PROCESSES                ONE PROCESS , THREE THREADS
       +----------+ +----------+    +-----------------------------+
       |  STACK   | |  STACK   |    | stk T1 | stk T2 | stk T3    |  private
       |  HEAP    | |  HEAP    |    +-----------------------------+
       |  DATA    | |  DATA    |    |        HEAP  (shared)       |
       |  TEXT    | |  TEXT    |    |        DATA  (shared)       |  shared
       +----------+ +----------+    |        TEXT  (shared)       |
        SEPARATE - no sharing       +-----------------------------+
    ```
    ```
       SHARED between threads : code , globals and statics , heap ,
                                open files , signal handlers
       PRIVATE to each thread : stack , registers , program counter ,
                                thread ID , errno
    ```

    Why threads exist
    - `Responsiveness` — a GUI keeps answering the user while a worker thread does the slow job.
    - `Low cost` — creating and switching threads is far cheaper than processes.
    - `Easy sharing` — no IPC layer is needed; the threads simply use the same variables.
    - `True parallelism` — different threads run on different cores at once.

    The trade-off
    ```
       Sharing memory is both the ADVANTAGE and the DANGER.

       Two threads doing  count = count + 1  at the same time can
       both read the old value, so one increment is LOST - a RACE
       CONDITION. A MUTEX or SEMAPHORE is needed.

       A segmentation fault in ONE thread kills the WHOLE process and
       every other thread in it. A crashing PROCESS leaves its siblings
       alive.
    ```
    - That last point is why a browser like Chrome puts every tab in a separate `process`, not a thread: one page crashing must not take the whole browser down. The cost is more memory and IPC — a deliberate trade of efficiency for isolation.

## Concurrency, Threads & Synchronization (11)

1. Multi-threaded processing and distributed computing have become essential. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

   Answer: The question is `incomplete` — only a statement is given, with no actual question following it. The topic it points to is answered below.

   Multi-threaded processing
   - `Multithreading` means running several `threads` inside one process. All threads share the process's code, data and heap; each has only its own `stack`, `registers` and `program counter`.
   ```
      ONE PROCESS , THREE THREADS
      +---------------------------------------+
      | stk T1 |  stk T2  |  stk T3           |  PRIVATE
      +---------------------------------------+
      |         HEAP , DATA , TEXT            |  SHARED
      +---------------------------------------+
   ```
   - Why it has become essential: `multicore CPUs`. A single-threaded program uses only one core, so on an 8-core machine it wastes 7 of them. Threads are the way a program gets `real parallelism`.
   - Other reasons: `responsiveness` — a GUI or a server keeps answering while a worker thread does the slow job; `low cost` — creating a thread and switching between threads is far cheaper than for a process; and `easy sharing` — threads use the same variables directly, with no IPC layer.
   - The price: shared memory brings `race conditions`, so `mutexes` and `semaphores` are needed; and a crash in one thread kills the whole process.

   Distributed computing
   - `Distributed computing` spreads work across `many machines` connected by a network, which appear to the user as one system.
   ```
           +---------+   +---------+   +---------+
           | Node 1  |   | Node 2  |   | Node 3  |
           +---------+   +---------+   +---------+
                |             |             |
                +------- network -----------+
                              |
                       +-------------+
                       |   Client    |
                       +-------------+
   ```
   - Why it has become essential: one machine cannot be made fast enough or large enough for modern workloads. Adding machines (`horizontal scaling`) is cheaper and has no ceiling, and multiple machines give `fault tolerance` — if one dies the others carry on.
   - Examples: `Hadoop` and `Spark` for large data sets, `Kubernetes` for containers, cloud services, and bank core systems replicated across data centres for disaster recovery.
   - The price: the `network` may fail or be slow, keeping data `consistent` across nodes is hard (the `CAP theorem` says you cannot have consistency, availability and partition tolerance all at once), and debugging is much harder than on one machine.

   How the two relate
   ```
      MULTITHREADING  : parallelism INSIDE one machine , shared memory
      DISTRIBUTED     : parallelism ACROSS many machines , message
                        passing over a network

      Real systems use BOTH : each node in a cluster runs a
      multi-threaded server process.
   ```

2. **What is Multithreading programming? Why Multithreading used in programming?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 296 (ET: BIBM)]*

   Answer: What multithreaded programming is
   - `Multithreading` is writing a program so that several `threads` run inside one process. Each thread is a separate path of execution, but they all share the process's memory.
   ```
      SHARED among threads : code (TEXT) , globals and statics (DATA) ,
                             HEAP , open files , signal handlers
      PRIVATE to a thread  : STACK , registers , program counter ,
                             thread ID
   ```
   ```
      ONE PROCESS , THREE THREADS
      +----------------------------------------+
      | stack T1 |  stack T2  |  stack T3      |  PRIVATE
      +----------------------------------------+
      |        HEAP    (shared)                |
      |        DATA    (shared)                |  SHARED
      |        TEXT    (shared)                |
      +----------------------------------------+
   ```
   - A single-threaded program does one thing at a time; a multithreaded one can download a file, update the screen and write a log at the same time.

   Why multithreading is used

   (a) Responsiveness
   ```
      A single-threaded GUI that starts a 10-second file save FREEZES -
      it cannot repaint or accept clicks until the save ends.

      With threads : the worker thread saves the file while the UI
      thread keeps answering the user.
   ```

   (b) Use of multiple cores — real parallelism
   ```
      On an 8-core CPU a single-threaded program uses ONE core and
      wastes seven. Eight threads can genuinely run at the same instant,
      one per core.
   ```

   (c) Cheaper than processes
   ```
      Creating a process : new address space , new page table , copy
           the parent - EXPENSIVE.
      Creating a thread  : just a stack and a register set - CHEAP,
           roughly 10 to 100 times faster.

      A context switch between threads of the same process needs NO
      page table change and NO TLB flush, so it is far quicker too.
   ```

   (d) Easy sharing of data
   - Threads share the heap and globals, so they exchange data by simply writing a variable. Processes need `IPC` — pipes, shared memory or sockets — which is slower and more code.

   (e) Better use of waiting time
   - While one thread blocks on disk or network I/O, another thread of the same process keeps the CPU busy. A web server usually gives one thread per request for exactly this reason.

   The cost, which should be mentioned
   ```
      RACE CONDITION - two threads doing  count = count + 1  can both
           read the old value, so one increment is LOST.
           -> MUTEX or SEMAPHORE is needed.

      DEADLOCK       - two threads each holding a lock the other wants.

      HARD TO DEBUG  - bugs depend on timing and may not repeat.

      NO ISOLATION   - a segmentation fault in one thread kills the
           WHOLE process and every thread in it.
   ```
   - That last point explains why a browser like Chrome puts each tab in a separate `process` rather than a thread: one crashing page must not take the whole browser down.

3. **What is Multithreading System?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1460 (ET: N/A)]*

   Answer: What a multithreading system is
   - A `multithreading system` is one in which a single process is divided into several `threads`, each running its own path of execution, while they all share the process's memory and resources. The OS can schedule those threads independently, so several can run at once on different cores.
   ```
      ONE PROCESS , THREE THREADS
      +----------------------------------------+
      | stack T1 |  stack T2  |  stack T3      |  PRIVATE
      +----------------------------------------+
      |         HEAP   (shared)                |
      |         DATA   (shared)                |  SHARED
      |         TEXT   (shared)                |
      +----------------------------------------+
      Each thread has its own PROGRAM COUNTER and REGISTERS.
   ```
   - A thread is called a `lightweight process` because it carries far less state than a process: no separate address space, no page table of its own.

   Multithreading models
   ```
      MANY-TO-ONE
           Many user threads mapped to ONE kernel thread.
           Cheap, but ONE blocking call blocks ALL of them, and it
           cannot use multiple cores.

      ONE-TO-ONE
           Each user thread has its OWN kernel thread.
           True parallelism and no blocking problem, but each thread
           costs kernel resources. Used by Linux and Windows.

      MANY-TO-MANY
           Many user threads multiplexed onto a smaller number of
           kernel threads. Combines the advantages, but is complex.
   ```

   Types of thread
   ```
      USER-LEVEL THREADS
           Managed by a library in user space. Fast to create and
           switch, but the kernel does not know they exist, so a
           blocking system call stops all of them.

      KERNEL-LEVEL THREADS
           Managed by the OS. Slower to create, but they can run on
           different cores and one blocking does not stop the rest.
   ```

   Benefits
   - `Responsiveness` — a GUI or a server keeps answering while a worker thread does the slow job.
   - `Resource sharing` — threads share code, data and files by default, with no IPC layer.
   - `Economy` — creating a thread and switching between threads is much cheaper than for a process, since the address space does not change and the TLB is not flushed.
   - `Scalability` — different threads run on different cores, giving real parallelism on a multicore CPU.

   Problems
   ```
      RACE CONDITION : shared data written by two threads at once.
                       Needs a MUTEX or SEMAPHORE.
      DEADLOCK       : each thread holds the lock the other wants.
      NO ISOLATION   : a crash in one thread kills the whole process.
      DEBUGGING      : bugs depend on timing and may not repeat.
   ```

4. **What is the output of the following code?** *[BAERA Assistant Engineer (CSE) 2023 compact it 574 (ET: BUET)]*
```c
#include <stdlib.h>
#include <sys/types.h>
#include <sys/wait.h>
#include <unistd.h>
int main(int argc, char *argv[]){
    int i;
    for(i=0;i<4;i++){
        int pid = fork();
        if(pid==0){
            printf("%d\n",i);
            exit(0);
        }
    }
    for(i=0;i<4;i++){
        wait(NULL);
    }
    return 0;
}
```

   Answer: Output
   ```
      0
      1
      2
      3

      Four lines - the numbers 0, 1, 2 and 3, each once.
      The ORDER is NOT guaranteed, because the four children are
      separate processes scheduled independently. On most systems it
      comes out in order, but 2 1 0 3 is equally legal.
   ```

   Why — the key point
   ```
      The child does  printf  and then  exit(0) , so a child NEVER
      returns to the loop. Only the PARENT keeps looping.

      Therefore exactly FOUR children are created, one per iteration :

           i = 0 : parent forks -> child C0 prints 0 , exits
           i = 1 : parent forks -> child C1 prints 1 , exits
           i = 2 : parent forks -> child C2 prints 2 , exits
           i = 3 : parent forks -> child C3 prints 3 , exits

      Total processes = 1 parent + 4 children = 5
   ```

   Process tree
   ```
                       PARENT
                    /   |   |   \
                  C0   C1  C2   C3
                (0)   (1) (2)   (3)

      A FLAT tree - every child is a direct child of the parent.
   ```

   How fork() behaves here
   ```
      fork() returns TWICE :
           in the CHILD  -> 0        so  if(pid==0)  is TRUE
           in the PARENT -> child's PID (> 0)   so the if is FALSE

      The child inherits a COPY of the parent's memory, so it has its
      own copy of  i  with the value at the moment of the fork. That is
      why C2 prints 2 and not something else.
   ```

   The second loop
   ```
      for(i=0;i<4;i++) wait(NULL);

      The parent waits for all 4 children before returning. This
      prevents ZOMBIE processes - a finished child stays as a zombie
      until its parent reaps it with wait(). It also guarantees the
      parent exits LAST.
   ```

   If the child did not call exit(0)
   ```
      Without exit(0) the child would CONTINUE THE LOOP and fork again.
      The count would then double at every iteration :

           total processes = 2^4 = 16
           printed lines   = 15

      That single exit(0) is what keeps the answer at 4 instead of 15.
   ```
   - One note on the code as written: `printf` is used but `<stdio.h>` is not included. Older compilers accept it with an implicit-declaration warning and the program still prints correctly; a strict C99 or later compiler will warn or refuse. The intended output is unaffected.

5. **অথবা, (ক) Thread এর সংজ্ঞা দিন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Definition
   - A `thread` is the smallest unit of execution that the CPU can schedule. It is a single path of execution `inside a process`. Several threads can exist in one process, and they all share the process's code, data and open files while each keeps its own stack and registers.
   - A thread is also called a `lightweight process (LWP)`, because it carries far less state than a full process — no separate address space and no page table of its own.

   What a thread owns and what it shares
   ```
      PRIVATE to each thread :
           STACK  (its own function calls and local variables)
           REGISTERS
           PROGRAM COUNTER
           thread ID , errno

      SHARED with the other threads of the same process :
           TEXT  - the code
           DATA  - globals and statics
           HEAP  - memory from malloc / new
           open files , signal handlers , the address space
   ```
   ```
      ONE PROCESS , THREE THREADS
      +----------------------------------------+
      | stack T1 |  stack T2  |  stack T3      |  PRIVATE
      +----------------------------------------+
      |         HEAP   (shared)                |
      |         DATA   (shared)                |  SHARED
      |         TEXT   (shared)                |
      +----------------------------------------+
   ```

   Types
   ```
      USER-LEVEL THREAD  - managed by a library in user space. Fast to
           create and switch, but the kernel cannot see it, so ONE
           blocking system call stops every thread.

      KERNEL-LEVEL THREAD - managed by the OS. Slower to create, but it
           can be scheduled on a different core and blocking affects
           only itself.
   ```

   Why threads are used
   - `Responsiveness` — a GUI keeps answering while a worker thread does the slow job.
   - `Economy` — creating a thread, and switching between threads of the same process, is much cheaper than for a process, because the address space does not change and the TLB is not flushed.
   - `Resource sharing` — threads share data directly, with no `IPC` layer.
   - `Parallelism` — different threads run on different cores at the same time.

   The danger
   ```
      Because the heap and globals are shared, two threads writing the
      same variable create a RACE CONDITION, so a MUTEX or SEMAPHORE is
      required. And a crash in ONE thread kills the WHOLE process.
   ```

6. **Write down the thread life cycle.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*

   Answer: What the thread life cycle is
   - The `thread life cycle` is the set of states a thread passes through from creation until it finishes. The thread scheduler moves it from one state to the next.

   The states
   ```mermaid
   stateDiagram-v2
       [*] --> New
       New --> Runnable: start()
       Runnable --> Running: scheduler picks it
       Running --> Runnable: yield() / time slice over
       Running --> Blocked: waiting for a lock
       Running --> Waiting: wait() / join()
       Blocked --> Runnable: lock acquired
       Waiting --> Runnable: notify() / timeout
       Running --> Terminated: run() ends
       Terminated --> [*]
   ```
   ```
      1. NEW (born)
           The thread object has been created but has not started. No
           CPU and no stack are assigned yet.
           In Java :  Thread t = new Thread(r);

      2. RUNNABLE (ready)
           start() has been called. The thread is ready and waiting in
           the READY QUEUE for the scheduler to pick it.

      3. RUNNING
           The scheduler gave it the CPU and run() is executing. Only
           one thread per core at a time.

      4. BLOCKED / WAITING (not runnable)
           The thread cannot proceed. Three common reasons :
               BLOCKED       - waiting for a MONITOR LOCK held by
                               another thread (a synchronized block)
               WAITING       - wait() or join() with no timeout ,
                               waiting indefinitely for another thread
               TIMED WAITING - sleep(ms) , wait(ms) , join(ms)
           It is NOT in the ready queue, so it cannot be scheduled.

      5. TERMINATED (dead)
           run() has returned, or an unhandled exception ended the
           thread. It cannot be restarted - calling start() again
           throws an error.
   ```

   The transitions
   ```
      New -> Runnable          start()
      Runnable -> Running      the scheduler dispatches it
      Running -> Runnable      yield() , or the time slice expired -
                               INVOLUNTARY , it could still run
      Running -> Blocked       it tried to enter a synchronized block
                               whose lock is held
      Running -> Waiting       wait() , join() , sleep()
      Blocked -> Runnable      the lock was released and acquired
      Waiting -> Runnable      notify() , notifyAll() , or the sleep
                               timeout expired
      Running -> Terminated    run() returned , or an exception escaped
   ```

   Points examiners look for
   ```
      1. There is NO  Blocked -> Running  edge. A woken thread goes to
         RUNNABLE and must be scheduled again.

      2. A TERMINATED thread CANNOT be restarted. To run the same work
         again, create a NEW thread object.

      3. RUNNABLE covers both "ready" and "running" in the Java enum -
         Java does not expose a separate RUNNING state, because
         whether a thread holds the CPU is decided by the OS.

      4. sleep() keeps any LOCK the thread holds ; wait() RELEASES the
         lock. This difference is asked very often.
   ```

7. **What is Multi-threading and multi-tasking? Difference between Multi-threading and Multi-tasking?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 854 (ET: N/A)]*

   Answer: What multithreading is
   - `Multithreading` means running several `threads` inside `one process`. The threads share the process's code, data and heap; each keeps only its own stack, registers and program counter.
   ```
      ONE PROCESS , THREE THREADS
      +----------------------------------------+
      | stack T1 |  stack T2  |  stack T3      |  PRIVATE
      +----------------------------------------+
      |        HEAP , DATA , TEXT              |  SHARED
      +----------------------------------------+
   ```
   - Example: a web browser where one thread renders the page, one downloads images and one runs JavaScript — all inside the same tab process.

   What multitasking is
   - `Multitasking` means the OS runs several `processes` at the same time on one CPU, switching between them so quickly that they appear to run together.
   ```
      PROCESS A     PROCESS B     PROCESS C
      +--------+    +--------+    +--------+
      | own    |    | own    |    | own    |
      | memory |    | memory |    | memory |
      +--------+    +--------+    +--------+
           \            |            /
            +---- CPU time-sliced ---+

      time -> | A | B | C | A | B | C | ...
   ```
   - Example: an editor, a music player and a browser all running while you work.
   ```
      Two forms :
        PREEMPTIVE   - the OS takes the CPU back after a time slice.
                       Windows, Linux, UNIX.
        COOPERATIVE  - a process keeps the CPU until it yields
                       voluntarily. One bad program freezes the machine.
   ```

   Difference between multithreading and multitasking

   | Point | Multithreading | Multitasking |
   |---|---|---|
   | Unit involved | `Threads` inside one process | Separate `processes` |
   | Memory | Threads `share` one address space | Each process has its `own` memory |
   | Switching cost | `Low` — no page table change, no TLB flush | `High` — full context switch |
   | Creation cost | `Cheap` — a stack and registers | `Expensive` — a whole address space |
   | Communication | Direct, through `shared variables` | Through `IPC` — pipes, sockets, shared memory |
   | Isolation | `Weak` — one crash kills the whole process | `Strong` — a crash affects only that process |
   | Synchronisation | `Needed` — mutex, semaphore | Rarely needed |
   | Granularity | Fine — inside one application | Coarse — between applications |

   - How they relate: they are `levels`, not alternatives. A modern OS multitasks between processes, and each of those processes may itself be multithreaded. Multitasking gives `isolation`; multithreading gives `speed and sharing`. Chrome uses both — a separate process per tab for safety, and many threads inside each tab for speed.

8. **(c) What is thread? Give some benefits of multi-threaded programming.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 889-890 (ET: N/A)]*

   Answer: What a thread is
   - A `thread` is the smallest unit of execution the CPU can schedule — a single path of execution `inside a process`. Several threads can live in one process, sharing its memory while each keeps its own stack and registers.
   ```
      PRIVATE to a thread : STACK , REGISTERS , PROGRAM COUNTER ,
                            thread ID
      SHARED with others  : TEXT (code) , DATA (globals) , HEAP ,
                            open files , signal handlers
   ```
   ```
      ONE PROCESS , THREE THREADS
      +----------------------------------------+
      | stack T1 |  stack T2  |  stack T3      |  PRIVATE
      +----------------------------------------+
      |        HEAP , DATA , TEXT              |  SHARED
      +----------------------------------------+
   ```
   - It is called a `lightweight process`, because it carries no separate address space and no page table of its own.

   Benefits of multithreaded programming

   (a) Responsiveness
   ```
      A single-threaded GUI that starts a 10-second save FREEZES - no
      repaint, no clicks accepted, until the save finishes.

      With threads : a worker thread saves while the UI thread keeps
      answering the user.
   ```

   (b) Resource sharing
   - Threads share code, data and the heap `by default`. Processes must set up `IPC` — shared memory or message passing — which is more code and slower.

   (c) Economy
   ```
      Creating a process : new address space , new page table , copy
           the parent's structures - EXPENSIVE.
      Creating a thread  : a stack and a register set - roughly 10 to
           100 times cheaper.

      Switching between threads of the SAME process needs NO page table
      change and NO TLB flush, so it is far faster than a process
      switch.
   ```

   (d) Scalability — use of multiple cores
   ```
      On an 8-core CPU a single-threaded program uses ONE core and
      wastes seven. Eight threads can genuinely execute at the same
      instant, one per core. This is REAL parallelism, not just
      interleaving.
   ```

   (e) Better use of blocking time
   - While one thread waits on disk or network I/O, another thread of the same process keeps the CPU busy. A web server gives one thread per request for exactly this reason.

   The cost, worth one line
   ```
      Sharing memory brings RACE CONDITIONS, so MUTEXES and SEMAPHORES
      are needed ; and a crash in ONE thread kills the WHOLE process.
   ```

9. **(d) Differentiate between thread and process.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

   Answer: Difference between a thread and a process

   | Point | Process | Thread |
   |---|---|---|
   | What it is | A program in `execution`, with its own memory | A path of execution `inside` a process |
   | Address space | `Own` address space and page table | `Shares` the process's address space |
   | Private data | Everything belongs to it | Only the `stack`, registers, program counter |
   | Creation cost | `High` — build an address space and a PCB | `Low` — a stack and a register set |
   | Context switch | `Slow` — page table switch, TLB flush | `Fast` — no address space change |
   | Communication | Through `IPC` — pipes, shared memory, sockets | Directly through `shared variables` |
   | Isolation | `Strong` — a crash affects only itself | `Weak` — a crash kills the whole process |
   | Synchronisation | Rarely needed | `Required` — mutex, semaphore |
   | Dependence | Independent | Cannot exist without its parent process |
   | Also called | Heavyweight process | Lightweight process (LWP) |

   Memory picture
   ```
      TWO PROCESSES                ONE PROCESS , THREE THREADS
      +----------+ +----------+    +-----------------------------+
      |  STACK   | |  STACK   |    | stk T1 | stk T2 | stk T3    | private
      |  HEAP    | |  HEAP    |    +-----------------------------+
      |  DATA    | |  DATA    |    |        HEAP  (shared)       |
      |  TEXT    | |  TEXT    |    |        DATA  (shared)       | shared
      +----------+ +----------+    |        TEXT  (shared)       |
       SEPARATE - no sharing       +-----------------------------+
   ```
   ```
      SHARED between threads : code , globals and statics , heap ,
                               open files , signal handlers
      PRIVATE to each thread : stack , registers , program counter ,
                               thread ID , errno
   ```

   Why the difference matters
   ```
      SPEED      : a thread switch skips the page table change and the
                   TLB flush, so it is far cheaper than a process switch.

      SAFETY     : two processes cannot corrupt each other's memory -
                   the MMU forbids it. Two threads CAN, because they
                   share the heap. Hence RACE CONDITIONS and the need
                   for locks.

      CRASH      : a segmentation fault in one thread kills EVERY thread
                   in the process. A crashing process leaves its
                   siblings alive.
   ```
   - That last point is the practical reason a browser like Chrome puts each tab in its own `process`, not a thread: one crashing page must not bring down the whole browser. The cost is more memory and IPC — isolation bought at the price of efficiency.

10. **What is multitasking and multithreading? What are the advantage threads over process?** *[Bangladesh Competition Commission Programmer 2019 compact it 1060 (ET: DU)]*

    Answer: What multitasking is
    - `Multitasking` is the OS running several `processes` at once on one CPU, switching between them so fast that they seem to run together.
    ```
       PROCESS A     PROCESS B     PROCESS C
       +--------+    +--------+    +--------+
       | own    |    | own    |    | own    |
       | memory |    | memory |    | memory |
       +--------+    +--------+    +--------+
            \            |            /
             +--- CPU time-sliced ----+

       time -> | A | B | C | A | B | C | ...
    ```
    - Two forms: `preemptive`, where the OS takes the CPU back when the time slice ends (Windows, Linux, UNIX), and `cooperative`, where a process keeps the CPU until it yields — so one badly written program can freeze the machine.

    What multithreading is
    - `Multithreading` is running several `threads` inside one process. They share the code, data and heap; each has only its own stack, registers and program counter.
    ```
       ONE PROCESS , THREE THREADS
       +----------------------------------------+
       | stack T1 |  stack T2  |  stack T3      |  PRIVATE
       +----------------------------------------+
       |        HEAP , DATA , TEXT              |  SHARED
       +----------------------------------------+
    ```

    Advantages of threads over processes

    (a) Cheaper to create
    ```
       A process : new address space , new page table , copy the
            parent's structures - EXPENSIVE.
       A thread  : a stack and a register set - roughly 10 to 100 times
            cheaper.
    ```

    (b) Cheaper to switch
    ```
       PROCESS switch : save registers , CHANGE the page table base
            register , FLUSH the TLB , and the cache is cold afterwards.
       THREAD  switch : save registers only. The address space, the page
            table and the TLB are UNCHANGED.
    ```

    (c) Easy data sharing
    - Threads share the heap and globals, so they exchange data by simply writing a variable. Processes need `IPC` — pipes, shared memory or sockets — which is slower and much more code.

    (d) Responsiveness
    - One thread can keep a GUI or a server answering while another does the slow work. A single-threaded program freezes for the whole duration of a long operation.

    (e) Better use of blocking time and of multiple cores
    - While one thread waits on I/O another keeps the CPU busy, and different threads can run on different cores at the same instant, giving real parallelism.

    (f) Less memory
    - Ten threads share one copy of the code and the heap. Ten processes need ten copies of everything.

    The trade-off
    ```
       What threads GAIN in speed and sharing, they LOSE in safety :

         RACE CONDITIONS - shared data needs MUTEXES and SEMAPHORES
         NO ISOLATION    - a crash in one thread kills the whole process
         HARD DEBUGGING  - bugs depend on timing and may not repeat
    ```
    - This is why a browser like Chrome uses `processes` for tabs and `threads` inside each tab: isolation where a crash would matter, speed where it would not.

11. **Define thread cancellation, target thread. Enumerate the different RAID level.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1106-1107 (ET: AUST)]*

    Answer: Thread cancellation
    - `Thread cancellation` is terminating a thread `before it has finished` its work. The thread being cancelled is called the `target thread`.
    ```
       Example : ten threads search a database in parallel. The moment
       one finds the record, the other nine are USELESS and are
       cancelled. The same happens when a user presses "Stop" on a
       page that is still loading.
    ```

    Target thread
    - The `target thread` is the thread that is to be cancelled — the one that receives the cancellation request. In POSIX it is named in `pthread_cancel(target)`.

    The two ways to cancel
    ```
       ASYNCHRONOUS CANCELLATION
            One thread terminates the target IMMEDIATELY.
            Problem : the target may be holding a LOCK, or half-way
            through updating shared data, or may have memory and files
            it never released. The system is left INCONSISTENT and
            resources LEAK.

       DEFERRED CANCELLATION  (the safe and usual method)
            The request is only MARKED. The target checks a flag at
            safe points called CANCELLATION POINTS, and terminates
            itself in an orderly way - releasing locks, freeing memory
            and closing files first.
            This is the DEFAULT in POSIX threads.
    ```
    ```
       Cancellation state in POSIX :
            PTHREAD_CANCEL_ENABLE  / PTHREAD_CANCEL_DISABLE
            PTHREAD_CANCEL_DEFERRED / PTHREAD_CANCEL_ASYNCHRONOUS

       A thread can DISABLE cancellation while in a critical section,
       and re-enable it afterwards. Cleanup handlers pushed with
       pthread_cleanup_push() are run in reverse order when the
       cancellation is finally acted upon.
    ```
    - Java takes the same view: `Thread.stop()` was deprecated because it was asynchronous and unsafe. The supported way is `interrupt()`, which sets a flag the thread checks itself — deferred cancellation by another name.

    RAID levels
    ```
       RAID 0  STRIPING , no redundancy
            Data split across N disks. Fastest read and write, full
            capacity, but ONE disk failure loses EVERYTHING.
            Minimum 2 disks. Usable = 100 %.

       RAID 1  MIRRORING
            Every disk has an exact copy. Survives one disk failure per
            mirror pair, fast reads, but half the capacity is lost.
            Minimum 2 disks. Usable = 50 %.

       RAID 2  Bit-level striping with HAMMING CODE error correction.
            Needs many disks and is OBSOLETE - modern drives detect
            their own errors.

       RAID 3  Byte-level striping with a DEDICATED PARITY disk.
            All disks must move together, so only one I/O at a time.
            Good for large sequential transfers, poor for small ones.

       RAID 4  BLOCK-level striping with a DEDICATED PARITY disk.
            Allows independent reads, but the single parity disk is a
            BOTTLENECK - every write touches it.

       RAID 5  Block-level striping with DISTRIBUTED PARITY.
            Parity spread over all disks, so no bottleneck. Survives
            ONE disk failure. Minimum 3 disks.
            Usable = (N - 1) / N.   THE MOST COMMON LEVEL.

       RAID 6  Block-level striping with DOUBLE distributed parity.
            Survives TWO simultaneous disk failures. Minimum 4 disks.
            Usable = (N - 2) / N. Slower writes than RAID 5.

       NESTED
       RAID 10 (1+0)  Mirror first, then stripe the mirrors.
            Fast and highly reliable ; 50 per cent usable.
            Used for DATABASES.
       RAID 01 (0+1)  Stripe first, then mirror. Less fault-tolerant
            than RAID 10 for the same disks.
    ```
    ```
       +-------+-----------+--------+----------------+-------------+
       | Level | Technique | Min    | Usable space   | Failures    |
       |       |           | disks  |                | survived    |
       +-------+-----------+--------+----------------+-------------+
       |   0   | striping  |   2    |    100 %       |     0       |
       |   1   | mirroring |   2    |     50 %       |     1       |
       |   5   | stripe +  |   3    |  (N-1)/N       |     1       |
       |       | parity    |        |                |             |
       |   6   | stripe +  |   4    |  (N-2)/N       |     2       |
       |       | 2 parity  |        |                |             |
       |  10   | mirror +  |   4    |     50 %       | 1 per mirror|
       |       | stripe    |        |                |             |
       +-------+-----------+--------+----------------+-------------+
    ```
    - The point to state plainly: `RAID is not a backup`. It protects against a `disk` failing, not against deletion, corruption, ransomware or fire. A separate backup is still required.

## File Systems & Disk Management (7)

1. **NTFS stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

   Answer: `NTFS` stands for `New Technology File System`.
   - It is the default file system of Windows NT and every Windows version after it — Windows 2000, XP, 7, 10 and 11. It replaced `FAT32`.
   ```
      Key features :
        large files and volumes - a file may exceed 4 GB , unlike FAT32
        JOURNALING - a log of pending changes, so the disk recovers
             quickly after a crash or power cut
        PERMISSIONS - per-file and per-folder access control (ACLs)
        ENCRYPTION - EFS , and compression on individual files
        DISK QUOTAS per user
        HARD LINKS , symbolic links and sparse files
   ```
   - Compared with `FAT32`: NTFS has no practical 4 GB file limit, supports permissions and journaling, and is more reliable; FAT32 is simpler and is still used on USB drives because almost every device can read it.
   - Related names worth knowing: `FAT32` (File Allocation Table), `exFAT` (Extended FAT, used on large SD cards), `ext4` (the usual Linux file system) and `APFS` (Apple File System).

2. **(খ) Unix file system এর প্রকারভেদ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 610 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) UNIX treats `everything as a file`, so file types cover far more than ordinary data. There are `seven` standard types, and the first character of `ls -l` shows which one it is.
   ```
      $ ls -l
      -rw-r--r--   1 user  staff   1024  report.txt        regular
      drwxr-xr-x   5 user  staff    160  documents         directory
      lrwxr-xr-x   1 user  staff     11  link -> file.txt  symbolic link
      crw-rw-rw-   1 root  wheel   3, 2  /dev/tty          character
      brw-r-----   1 root  disk    8, 0  /dev/sda          block
      prw-r--r--   1 user  staff      0  mypipe            FIFO
      srwxrwxrwx   1 user  staff      0  /tmp/socket       socket
   ```

   The seven types
   ```
      1. REGULAR FILE          -
           Ordinary data - text, source code, executables, images.
           UNIX imposes NO internal structure ; it is just a stream of
           bytes, and only the program using it knows the format.

      2. DIRECTORY             d
           A special file holding a list of ( file name -> inode
           number ) pairs. It does NOT hold the file contents.
           Every directory has "." for itself and ".." for its parent.

      3. SYMBOLIC LINK         l
           A small file holding the PATH of another file - a shortcut.
           It may cross file systems, and it breaks if the target is
           deleted. A HARD LINK, by contrast, is another directory
           entry pointing to the SAME INODE, so it cannot cross file
           systems and the data survives until the last link is gone.

      4. CHARACTER SPECIAL FILE   c
           A device accessed ONE CHARACTER AT A TIME, unbuffered -
           keyboard, terminal, serial port, /dev/null.

      5. BLOCK SPECIAL FILE       b
           A device accessed in FIXED-SIZE BLOCKS, buffered - hard
           disks, SSDs, USB drives, CD-ROM.

      6. FIFO / NAMED PIPE        p
           For inter-process communication between UNRELATED processes.
           One writes, another reads, first-in-first-out. Created with
           mkfifo. Unlike an ordinary pipe it has a NAME in the file
           system.

      7. SOCKET                   s
           For two-way communication between processes, on the same
           machine (a UNIX domain socket) or across a network.
   ```

   Why this design matters
   ```
      Because devices, pipes and sockets are all FILES, the SAME system
      calls work on all of them :

           open() , read() , write() , close()

      So a program can read from a file, a keyboard or a network
      connection with identical code. This uniformity is the single
      most important idea in the UNIX design.
   ```
   - The command to identify a type is `ls -l` (first character), `file <name>` (which inspects the content) or `stat <name>`.

3. **কোন ড্রাইভে ‘My Document’ রাখা হয় এবং NTFS কী?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) Which drive holds "My Documents"
   - `My Documents` (called `Documents` since Windows Vista) is kept on the drive where Windows itself is installed, which is normally the `C: drive`.
   ```
      Windows XP :  C:\Documents and Settings\<username>\My Documents
      Vista and later :  C:\Users\<username>\Documents
   ```
   - It is a `user profile folder`, so each user account gets its own copy. It can be `relocated` to another drive — right-click the folder, Properties, Location, Move — and many people move it to D: so a reinstall of Windows does not wipe their data.

   What NTFS is
   - `NTFS` stands for `New Technology File System`. It is the default file system of Windows NT and every later Windows version — 2000, XP, 7, 10 and 11. It replaced `FAT32`.
   ```
      Main features :

      JOURNALING     A log of pending changes is written before the
           change itself, so after a crash or power cut the disk
           recovers in seconds instead of needing a full scan.

      LARGE FILES    No 4 GB per-file limit, unlike FAT32. Volumes can
           run to hundreds of terabytes.

      SECURITY       Per-file and per-folder permissions through ACLs,
           so one user cannot read another's files.

      ENCRYPTION     EFS encrypts files transparently ; BitLocker
           encrypts the whole volume.

      COMPRESSION    Individual files or folders can be compressed.

      DISK QUOTAS    A limit on how much space each user may consume.

      OTHER          Hard links , symbolic links , sparse files ,
           shadow copies (previous versions) , and better handling of
           bad sectors.
   ```

   NTFS against FAT32

   | Point | NTFS | FAT32 |
   |---|---|---|
   | Maximum file size | Practically unlimited | `4 GB` |
   | Journaling | `Yes` | No |
   | Permissions | `Yes`, per file and folder | No |
   | Encryption, compression | `Yes` | No |
   | Compatibility | Windows; read-only on macOS | `Almost every device` |
   | Typical use | Windows system drives | USB drives, SD cards, cameras |

   - Which to choose: `NTFS` for a Windows hard disk or SSD, because of journaling and permissions; `FAT32` or `exFAT` for a pen drive that has to work on a TV, camera or car stereo, because those devices usually cannot read NTFS.

4. **A file system with 300 GB uses a file descriptor with 8 direct block address, 1 indirect block address and 1 doubly indirect block address. The size of each disk block is 128 Bytes and the size of each disk block address is 8 Bytes. The maximum possible file size in this file system.** *[BAUST Assistant Programmer 2021 compact it 917 (ET: N/A)]*

   Answer: Given
   ```
      Disk block size          = 128 bytes
      Disk block address size  = 8 bytes
      File descriptor (inode) holds :
           8 direct block addresses
           1 single indirect block address
           1 double indirect block address
   ```

   Step 1 — how many addresses fit in one block
   ```
      Addresses per block = block size / address size
                          = 128 / 8
                          = 16 addresses
   ```

   Step 2 — blocks reachable by each kind of pointer
   ```
      DIRECT           8 pointers , each -> 1 data block
                       = 8 blocks

      SINGLE INDIRECT  1 pointer -> 1 index block holding 16 addresses
                       = 16 blocks

      DOUBLE INDIRECT  1 pointer -> 1 index block of 16 addresses ,
                       each of those -> another index block of 16
                       = 16 * 16
                       = 256 blocks
   ```
   ```
      INODE
      +----------------+
      | direct  0..7   | -----> 8 data blocks
      +----------------+
      | single indirect| ----> [16 addr] ----> 16 data blocks
      +----------------+
      | double indirect| ----> [16 addr] --+--> [16 addr] -> 16 blocks
      +----------------+                   |    ...  (16 of these)
                                           +--> [16 addr] -> 16 blocks
                                                = 256 data blocks
   ```

   Step 3 — total data blocks
   ```
      Total = 8 + 16 + 256
            = 280 blocks
   ```

   Step 4 — maximum file size
   ```
      Maximum file size = total blocks * block size
                        = 280 * 128 bytes
                        = 35,840 bytes

                        = 35,840 / 1024 KB
                        = 35 KB
   ```

   Answer
   ```
      Maximum possible file size = 35,840 bytes = 35 KB
   ```
   - The 300 GB figure is a `distractor`. The limit here comes from the `inode structure`, not from the size of the disk — with only 280 addressable blocks, no file can exceed 35 KB however large the volume is.
   - Note also that the index blocks themselves consume disk space but hold no file data, so they are not counted in the file size.
   - If a `triple indirect` pointer were added it would contribute `16 * 16 * 16 = 4096` blocks, taking the maximum to `(8 + 16 + 256 + 4096) * 128 = 559,360 bytes ≈ 546 KB`. Real systems use 1 KB to 4 KB blocks, which is why their limits run into terabytes.

5. **(খ) Direct or Random Access File-প্রক্রিয়াকরণ চিত্রসহ বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1095 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What direct (random) access is
   - In `direct` or `random access`, any record can be read or written `immediately`, without reading the records before it. The file is treated as a numbered sequence of fixed-size records, and the OS jumps straight to the one asked for.

   Diagram
   ```
      DIRECT / RANDOM ACCESS
                   need record 4 - jump STRAIGHT to it
                               |
                               v
      +--------+--------+--------+--------+--------+
      | rec 0  | rec 1  | rec 2  | rec 3  | rec 4  |
      +--------+--------+--------+--------+--------+
           0       1        2        3        4     <- record number


      SEQUENTIAL ACCESS  (for contrast)
      +--------+--------+--------+--------+--------+
      | rec 0  |-> rec 1|-> rec 2|-> rec 3|-> rec 4|
      +--------+--------+--------+--------+--------+
      Records 0 to 3 MUST be read before record 4.
   ```

   How the address is worked out
   ```
      All records have the SAME LENGTH, so the position is arithmetic :

           byte offset = record number * record size

      Example : record size = 100 bytes , want record 4
           offset = 4 * 100 = 400
           -> seek to byte 400 and read 100 bytes

      The seek is O(1) - one calculation, one disk head movement,
      independent of how big the file is.
   ```

   The operations
   ```
      read (n)      read record n
      write (n)     write record n
      seek (n)      move the file pointer to record n
      position = n  then an ordinary read / write

      In C :   fseek(fp, n * sizeof(rec), SEEK_SET);
               fread(&r, sizeof(rec), 1, fp);
   ```

   ```mermaid
   flowchart LR
       A[Request record n] --> B[offset = n * record size]
       B --> C[Seek to that offset]
       C --> D[Read or write the record]
   ```

   Sequential against direct access

   | Point | Sequential | Direct / random |
   |---|---|---|
   | Order of access | One after another, in order | `Any record, any order` |
   | Time to reach record n | Proportional to `n` | `Constant` |
   | Record length | May vary | Must be `fixed` |
   | Storage needed | Tape or disk | `Disk` only — tape cannot seek |
   | Best for | Payroll, batch reports, logs | `Databases`, ATM, airline booking |

   - Where it is used and why: an ATM must fetch `one` account record out of millions in a fraction of a second, so sequential access is impossible. Database systems, indexed files (`ISAM`) and airline reservation systems all rely on direct access.
   - The requirement is that records be `fixed length`, so the offset can be computed. Variable-length records need an `index` that maps a key to a byte offset, which is exactly what a database index does.

6. **(a) An I/O system with a simple disk gets an average 50 I/O requests per second and average time for a disk to server an I/O request is 10ms. Calculate the utilization of I/O system.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1134-1136 (ET: N/A)]*

   Answer: Given
   ```
      Arrival rate         lambda = 50 I/O requests per second
      Average service time S      = 10 ms = 10 / 1000 = 0.01 second
   ```

   Formula
   ```
      Utilisation  U  =  arrival rate  *  average service time
                      =  lambda * S
   ```
   - The reasoning behind it: in one second `50` requests arrive, and each one keeps the disk busy for `0.01` second. So the total busy time in that second is `50 × 0.01`.

   Calculation
   ```
      U = 50 * 0.01

        = 0.5

        = 50 %
   ```

   Answer
   ```
      Utilisation of the I/O system = 0.5  =  50 %
   ```

   Cross-check by service capacity
   ```
      Service rate  mu = 1 / S = 1 / 0.01 = 100 requests per second

      U = lambda / mu = 50 / 100 = 0.5 = 50 %      same result
   ```
   - Meaning: the disk is busy `half` the time and idle the other half. It can serve `100` requests per second, so at 50 requests per second it has spare capacity.
   - Note the condition for stability: `U` must stay below `1`. If the arrival rate reached 100 per second, `U = 1` and the queue would grow without limit; response time rises very steeply as `U` approaches 1, which is why real systems are sized to run well below full utilisation.

7. **Explain inode data structures in Linux OS.** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1220-1221 (ET: N/A)]*

   Answer: What an inode is
   - An `inode` (index node) is the data structure Linux keeps for `every file`, holding all its `metadata` and the `pointers to its data blocks`. One inode per file, identified by a unique `inode number` within the file system.
   - The one thing an inode does `not` contain is the `file name`. The name lives in the `directory`, which is just a table of `(name → inode number)` pairs. This is what makes `hard links` possible — several names, one inode.

   What it stores
   ```
      FILE TYPE        regular , directory , symlink , block , char ,
                       FIFO , socket
      PERMISSIONS      rwx for owner , group , others
      OWNER            UID and GID
      SIZE             in bytes
      LINK COUNT       how many hard links point to this inode
      TIMESTAMPS       atime  - last access
                       mtime  - last modification of the CONTENT
                       ctime  - last change of the INODE itself
      BLOCK POINTERS   where the data actually is
   ```

   The block pointer structure — the heart of the design
   ```
      INODE
      +---------------------+
      | metadata            |
      +---------------------+
      | direct  0           | ------------> data block
      | direct  1           | ------------> data block
      |   ...  (12 of them) |
      | direct 11           | ------------> data block
      +---------------------+
      | single indirect     | --> [index blk] --> many data blocks
      +---------------------+
      | double indirect     | --> [index] --> [index] --> data blocks
      +---------------------+
      | triple indirect     | --> [index] -> [index] -> [index] -> data
      +---------------------+
   ```
   ```
      With a 4 KB block and a 4-byte address, one index block holds
      4096 / 4 = 1024 addresses :

           12 direct        =        12 blocks
           single indirect  =      1024 blocks
           double indirect  = 1024*1024 = 1,048,576 blocks
           triple indirect  = 1024^3   = 1,073,741,824 blocks

      So a small file needs NO index block at all - the first 12
      pointers cover 48 KB. Only a large file pays the cost of extra
      lookups, which is reasonable because it is large anyway.
   ```

   How a path is resolved
   ```mermaid
   flowchart LR
       A["/home/user/a.txt"] --> B[Read / directory]
       B --> C[Find inode of home]
       C --> D[Find inode of user]
       D --> E[Find inode of a.txt]
       E --> F[Follow block pointers to the data]
   ```

   Hard link against symbolic link
   ```
      HARD LINK      another NAME for the SAME inode. The link count
           goes up. Deleting one name leaves the data alive until the
           count reaches 0. Cannot cross file systems, cannot point to
           a directory.

      SYMBOLIC LINK  a SEPARATE inode whose data is the PATH of the
           target. Can cross file systems, and BREAKS if the target is
           deleted.
   ```

   Practical points
   ```
      ls -i file        show the inode number
      df -i             show inode usage per file system
      stat file         show all inode fields

      The number of inodes is FIXED when the file system is created.
      A disk can therefore run out of INODES while free space remains -
      the classic symptom of millions of tiny files, where "No space
      left on device" appears though df shows space available.
   ```

## CPU Scheduling (6)

1. A system has three processes with the following arrival times and CPU burst times:

| Process | Arrival Time (ms) | Burst Time (ms) |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 3 |
| P3 | 2 | 2 |

Using the First-Come, First-Served (FCFS) CPU scheduling algorithm calculate the average waiting time and the average turnaround time. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

   Answer: Given
   ```
      Process   Arrival Time (AT)   Burst Time (BT)
        P1            0                  5
        P2            1                  3
        P3            2                  2
   ```
   - `FCFS` is non-preemptive: the process that arrives first runs to completion. The order of arrival is P1, P2, P3.

   Gantt chart
   ```
      +-------------+---------+-------+
      |     P1      |   P2    |  P3   |
      +-------------+---------+-------+
      0             5         8       10
   ```

   Completion, turnaround and waiting times
   ```
      TAT = CT - AT          WT = TAT - BT

      P1 : CT = 5   TAT = 5 - 0 = 5    WT = 5 - 5 = 0
      P2 : CT = 8   TAT = 8 - 1 = 7    WT = 7 - 3 = 4
      P3 : CT = 10  TAT = 10 - 2 = 8   WT = 8 - 2 = 6
   ```
   ```
      +---------+----+----+----+-----+----+
      | Process | AT | BT | CT | TAT | WT |
      +---------+----+----+----+-----+----+
      |   P1    |  0 |  5 |  5 |   5 |  0 |
      |   P2    |  1 |  3 |  8 |   7 |  4 |
      |   P3    |  2 |  2 | 10 |   8 |  6 |
      +---------+----+----+----+-----+----+
   ```

   Averages
   ```
      Average waiting time    = (0 + 4 + 6) / 3
                              = 10 / 3
                              = 3.33 ms

      Average turnaround time = (5 + 7 + 8) / 3
                              = 20 / 3
                              = 6.67 ms
   ```

   Answer
   ```
      Average waiting time    = 3.33 ms
      Average turnaround time = 6.67 ms
   ```
   - Note the weakness this shows — the `convoy effect`. P1 has the longest burst and arrives first, so the two short processes must wait behind it. Running them shortest first (`SJF`) would give an average waiting time of `(0 + 3 + 5)/3 = 2.67 ms`, which is better. FCFS is simple and starvation-free, but it is poor for average waiting time.

2. (a) নিচের গুলোর Distributed-GPT control and computing এর কার্যকারিতা লিখুন:
   (b) Clock cycle কী? একটি প্রসেসরের clock speed 3.5 GHz বলতে কী বোঝায়?
   (c) নিচের সারণীটি দেখুুন:

| Process | Burst Time (milli second) | Priority |
|---|---|---|
| P_1 | 15 | 1 |
| P_2 | 2 | 1 |
| P_3 | 4 | 3 |
| P_4 | 2 | 4 |
| P_5 | 8 | 2 |

(a) অ্যালগরিদম প্রতিটি সংক্ষেপ ও সারণির উত্তর লেখুন।
(b) FCFS এবং SJF Scheduling algorithm গুলোর মধ্যে Gantt Chart এবং অপেক্ষাকৃত সুষম এবং গড়ের (average waiting time) ও টার্ন অ্যারাউন্ড (turnaround time) এর হিসাব নির্ণয় কর। *[Assistant Programmer - Department of Immigration & Passports 15.07.2026 compact it 1464 (ET: N/A)]*

   Answer: (a) The first part of the question is `incomplete` — "Distributed-GPT control and computing" has no list of items following it, so the items to describe were not captured. The standard topic it points to is `distributed control and computing`, covered briefly below.
   ```
      DISTRIBUTED COMPUTING - work is spread over MANY machines
      connected by a network, and they appear to the user as ONE system.

           +--------+   +--------+   +--------+
           | Node 1 |   | Node 2 |   | Node 3 |
           +--------+   +--------+   +--------+
                |            |            |
                +------- network ---------+

      WHY : one machine cannot be made fast or large enough. Adding
           machines is cheaper, has no ceiling, and gives FAULT
           TOLERANCE - if one node dies the rest carry on.
      COST: the network can fail, keeping data CONSISTENT across nodes
           is hard, and debugging is much harder.
      USES: Hadoop and Spark for large data, Kubernetes for containers,
           cloud services, bank core systems replicated across data
           centres.
   ```

   (b) Clock cycle, and what 3.5 GHz means
   - A `clock cycle` is one complete tick of the CPU's clock — one full swing from low to high and back. It is the smallest unit of time in which the processor does work; every instruction takes a whole number of cycles.
   ```
      CLK   __|‾‾|__|‾‾|__|‾‾|__|‾‾|__
            |<-->|
           one clock cycle
   ```
   ```
      Clock speed = how many cycles happen per second.

      3.5 GHz = 3.5 * 10^9 cycles per second
              = 3,500,000,000 cycles every second

      Cycle time = 1 / frequency
                 = 1 / (3.5 * 10^9)
                 = 0.2857 * 10^-9 second
                 = 0.2857 nanosecond  (about 286 picoseconds)
   ```
   - What it does `not` mean: 3.5 GHz is not 3.5 billion instructions per second. Some instructions need several cycles, and a pipelined superscalar CPU can finish more than one per cycle. The honest measure is
   ```
      CPU time = instruction count * CPI * cycle time

      So a 3.5 GHz CPU with CPI 2 is SLOWER than a 3.0 GHz CPU with
      CPI 1. Comparing clock speeds across different architectures is
      meaningless - this is the "megahertz myth".
   ```

   (c) Scheduling for the given table
   ```
      Process   BT   Priority        (all arrive at time 0 ;
        P1      15      1             priority 1 = HIGHEST)
        P2       2      1
        P3       4      3
        P4       2      4
        P5       8      2
   ```

   FCFS — order P1, P2, P3, P4, P5
   ```
      +----------------+----+------+----+--------+
      |       P1       | P2 |  P3  | P4 |   P5   |
      +----------------+----+------+----+--------+
      0                15   17     21   23       31

      Process  BT   CT   TAT   WT
        P1     15   15    15    0
        P2      2   17    17   15
        P3      4   21    21   17
        P4      2   23    23   21
        P5      8   31    31   23

      Average WT  = (0+15+17+21+23)/5 = 76/5  = 15.20 ms
      Average TAT = (15+17+21+23+31)/5 = 107/5 = 21.40 ms
   ```

   SJF — order P2, P4, P3, P5, P1 (shortest burst first)
   ```
      +----+----+------+--------+----------------+
      | P2 | P4 |  P3  |   P5   |       P1       |
      +----+----+------+--------+----------------+
      0    2    4      8        16               31

      Process  BT   CT   TAT   WT
        P1     15   31    31   16
        P2      2    2     2    0
        P3      4    8     8    4
        P4      2    4     4    2
        P5      8   16    16    8

      Average WT  = (16+0+4+2+8)/5 = 30/5 = 6.00 ms
      Average TAT = (31+2+8+4+16)/5 = 61/5 = 12.20 ms
   ```

   Comparison
   ```
      +--------+-------------+---------------+
      | Policy | Average WT  | Average TAT   |
      +--------+-------------+---------------+
      | FCFS   |  15.20 ms   |   21.40 ms    |
      | SJF    |   6.00 ms   |   12.20 ms    |
      +--------+-------------+---------------+
   ```
   - `SJF` is far better here, and this is not luck: SJF is `provably optimal` for average waiting time when all processes arrive together. FCFS suffers the `convoy effect` — the 15 ms P1 runs first and every short process queues behind it.
   - The catch with SJF is that the burst time must be known in advance, which it never is. Real schedulers estimate it by `exponential averaging` of past bursts. SJF can also `starve` a long process if short ones keep arriving; `ageing` fixes that by slowly raising a waiting process's priority.

3. **Consider the set of 3 processes whose arrival time and burst time are given below-**

| Process | AT | BT |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 4 |
| P3 | 2 | 2 |

**If the CPU scheduling policy is round robin with time quantum=2, finds out the completion time, turnaround time, waiting time, and response time** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1447 (ET: N/A)]*

   Answer: Given
   ```
      Process   AT   BT
        P1       0    5
        P2       1    4
        P3       2    2

      Round Robin , time quantum q = 2
   ```

   Ready queue trace
   ```
      t=0   P1 arrives , queue = [P1]
            P1 runs 0-2 , remaining 3
            at t=1 P2 arrived , at t=2 P3 arrived
            queue = [P2 , P3 , P1]

      t=2   P2 runs 2-4 , remaining 2 -> queue = [P3 , P1 , P2]
      t=4   P3 runs 4-6 , remaining 0 -> P3 DONE at 6
            queue = [P1 , P2]
      t=6   P1 runs 6-8 , remaining 1 -> queue = [P2 , P1]
      t=8   P2 runs 8-10, remaining 0 -> P2 DONE at 10
            queue = [P1]
      t=10  P1 runs 10-11 , remaining 0 -> P1 DONE at 11
   ```

   Gantt chart
   ```
      +------+------+------+------+------+---+
      |  P1  |  P2  |  P3  |  P1  |  P2  |P1 |
      +------+------+------+------+------+---+
      0      2      4      6      8     10   11
   ```

   Results
   ```
      TAT = CT - AT
      WT  = TAT - BT
      RT  = time of FIRST run - AT

      +---------+----+----+----+-----+----+----+
      | Process | AT | BT | CT | TAT | WT | RT |
      +---------+----+----+----+-----+----+----+
      |   P1    |  0 |  5 | 11 |  11 |  6 |  0 |
      |   P2    |  1 |  4 | 10 |   9 |  5 |  1 |
      |   P3    |  2 |  2 |  6 |   4 |  2 |  2 |
      +---------+----+----+----+-----+----+----+
   ```
   ```
      P1 : CT=11 , TAT = 11-0 = 11 , WT = 11-5 = 6 , RT = 0-0 = 0
      P2 : CT=10 , TAT = 10-1 =  9 , WT =  9-4 = 5 , RT = 2-1 = 1
      P3 : CT= 6 , TAT =  6-2 =  4 , WT =  4-2 = 2 , RT = 4-2 = 2
   ```

   Averages
   ```
      Average TAT = (11 + 9 + 4) / 3 = 24 / 3 = 8.00 ms
      Average WT  = ( 6 + 5 + 2) / 3 = 13 / 3 = 4.33 ms
      Average RT  = ( 0 + 1 + 2) / 3 =  3 / 3 = 1.00 ms
   ```
   - What Round Robin buys is a low `response time` — every process starts within one quantum of its turn, which is what an interactive user notices. The price is a higher average turnaround time than SJF, plus a `context switch` at every quantum boundary (5 switches here).
   - Choosing `q` matters: too large and RR degenerates into FCFS; too small and switching overhead dominates. The usual rule is that the quantum should exceed about 80 per cent of the CPU bursts.

4. **There are 3 tasks P1, P2, and P3. The arrival time and duration of each task is given below. Apply the round-robin scheduling algorithm with quantum size-20 to schedule the tasks in a single core machine. Calculate the turnaround time for each task. (All tasks have the same priority)** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

| Task | Arrival time (ms) | Duration (ms) |
|---|---|---|
| P1 | 0 | 40 |
| P2 | 5 | 40 |
| P3 | 10 | 20 |

   Answer: Given
   ```
      Task   Arrival time (ms)   Duration / BT (ms)
       P1           0                  40
       P2           5                  40
       P3          10                  20

      Round Robin , time quantum q = 20 , single core , equal priority
   ```

   Ready queue trace
   ```
      t=0    only P1 has arrived , queue = [P1]
             P1 runs 0-20 , remaining 20
             during this P2 arrived (t=5) and P3 arrived (t=10)
             queue = [P2 , P3 , P1]

      t=20   P2 runs 20-40 , remaining 20 -> queue = [P3 , P1 , P2]
      t=40   P3 runs 40-60 , remaining  0 -> P3 DONE at 60
             queue = [P1 , P2]
      t=60   P1 runs 60-80 , remaining  0 -> P1 DONE at 80
             queue = [P2]
      t=80   P2 runs 80-100, remaining  0 -> P2 DONE at 100
   ```

   Gantt chart
   ```
      +---------+---------+---------+---------+---------+
      |   P1    |   P2    |   P3    |   P1    |   P2    |
      +---------+---------+---------+---------+---------+
      0        20        40        60        80        100
   ```

   Turnaround time for each task
   ```
      TAT = Completion time - Arrival time

      P1 : CT = 80   TAT = 80 - 0  = 80 ms
      P2 : CT = 100  TAT = 100 - 5 = 95 ms
      P3 : CT = 60   TAT = 60 - 10 = 50 ms
   ```
   ```
      +------+----+----+-----+-----+-----+----+
      | Task | AT | BT | CT  | TAT | WT  | RT |
      +------+----+----+-----+-----+-----+----+
      |  P1  |  0 | 40 |  80 |  80 |  40 |  0 |
      |  P2  |  5 | 40 | 100 |  95 |  55 | 15 |
      |  P3  | 10 | 20 |  60 |  50 |  30 | 30 |
      +------+----+----+-----+-----+-----+----+

      WT = TAT - BT , RT = first run - AT
   ```

   Averages
   ```
      Average TAT = (80 + 95 + 50) / 3 = 225 / 3 = 75.00 ms
      Average WT  = (40 + 55 + 30) / 3 = 125 / 3 = 41.67 ms
      Average RT  = ( 0 + 15 + 30) / 3 =  45 / 3 = 15.00 ms
   ```
   - Note that the quantum of 20 exactly halves the 40 ms tasks, so each of them runs in two clean slices and there is no leftover fragment. The CPU is busy from 0 to 100 with `no idle time`, since P1 was already running when the others arrived.
   - With `q = 40` or more, RR would behave exactly like `FCFS` here — each task would finish in one slice. That is the general rule: a quantum larger than the longest burst turns Round Robin into FCFS.

5. **Calculate the average waiting time.** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

| Process | Burst Time |
|---|---|
| P1 | 21 |
| P2 | 3 |
| P3 | 6 |

   Answer: Given
   ```
      Process   Burst Time
        P1          21
        P2           3
        P3           6
   ```
   - No arrival times are given, so all three are taken to arrive at `time 0`. The scheduling policy is not stated, so `FCFS` is worked out as the default and `SJF` is shown for comparison.

   FCFS — order P1, P2, P3
   ```
      +----------------------+------+---------+
      |          P1          |  P2  |   P3    |
      +----------------------+------+---------+
      0                      21     24        30

      WT = start time - arrival time

      P1 : WT = 0
      P2 : WT = 21
      P3 : WT = 24
   ```
   ```
      +---------+----+----+-----+----+
      | Process | BT | CT | TAT | WT |
      +---------+----+----+-----+----+
      |   P1    | 21 | 21 |  21 |  0 |
      |   P2    |  3 | 24 |  24 | 21 |
      |   P3    |  6 | 30 |  30 | 24 |
      +---------+----+----+-----+----+
   ```
   ```
      Average waiting time = (0 + 21 + 24) / 3
                           = 45 / 3
                           = 15 ms

      Average turnaround   = (21 + 24 + 30) / 3 = 75 / 3 = 25 ms
   ```

   Answer
   ```
      Average waiting time = 15 ms
   ```

   SJF for comparison — order P2, P3, P1
   ```
      +------+---------+----------------------+
      |  P2  |   P3    |          P1          |
      +------+---------+----------------------+
      0      3         9                      30

      P2 : WT = 0    P3 : WT = 3    P1 : WT = 9

      Average waiting time = (0 + 3 + 9) / 3 = 12 / 3 = 4 ms
      Average turnaround   = (3 + 9 + 30) / 3 = 42 / 3 = 14 ms
   ```
   ```
      +--------+--------------+
      | Policy | Average WT   |
      +--------+--------------+
      | FCFS   |    15 ms     |
      | SJF    |     4 ms     |
      +--------+--------------+
   ```
   - The difference is the `convoy effect`: under FCFS the 21 ms P1 runs first and the two short processes queue behind it. `SJF` is provably `optimal` for average waiting time when all processes arrive together — no other order can beat 4 ms here.

6. **(খ) CPU Scheduling কী? যে যে কারণে CPU Scheduling করতে হয় সেগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*

   Answer: (Answered in English, as required for IT topics.) What CPU scheduling is
   - `CPU scheduling` is the OS deciding `which ready process gets the CPU next`. The part that chooses is the `short-term scheduler`, and the part that actually hands over control is the `dispatcher`.
   ```
      READY QUEUE
      +----+----+----+----+
      | P1 | P2 | P3 | P4 |  ---- scheduler chooses ---->  CPU
      +----+----+----+----+
   ```
   - It is needed because there is normally `one CPU and many ready processes`, so someone must decide the order.

   Why CPU scheduling is necessary

   (a) The CPU must not sit idle
   ```
      A process alternates between a CPU BURST and an I/O BURST :

           CPU burst | I/O burst | CPU burst | I/O burst | ...

      While P1 waits on the disk - MILLISECONDS, an eternity for the
      CPU - the CPU would be doing NOTHING. Scheduling gives it to
      another ready process, so the idle time is used.
   ```

   (b) To keep CPU utilisation and throughput high
   - `Utilisation` is the fraction of time the CPU is busy, and `throughput` is the number of processes finished per unit time. A good schedule raises both.

   (c) To keep response time low
   - On an interactive system the user must see something happen quickly. `Round Robin` gives every process a turn within one quantum, so nothing appears frozen.

   (d) To share the CPU fairly and prevent starvation
   - Without scheduling, one long process could hold the CPU forever. `Preemption` takes the CPU back when the time slice ends, and `ageing` slowly raises the priority of a long-waiting process so it is not starved.

   (e) To honour priorities
   - A real-time or system process must be able to run before an ordinary background job.

   (f) To minimise waiting and turnaround time
   ```
      Order matters enormously. With bursts 21, 3, 6 all arriving at 0 :

           FCFS  ->  average waiting time = 15 ms
           SJF   ->  average waiting time =  4 ms

      Same work, same CPU - only the ORDER changed.
   ```

   When scheduling decisions are made
   ```
      1. Running -> Waiting    (a process requests I/O)      non-preemptive
      2. Running -> Ready      (its time slice expired)      preemptive
      3. Waiting -> Ready      (I/O finished)                preemptive
      4. Running -> Terminated (it exits)                    non-preemptive

      If decisions are made ONLY at 1 and 4, the scheme is
      NON-PREEMPTIVE ; if at 2 and 3 as well, it is PREEMPTIVE.
   ```

   The criteria a scheduler is judged by
   ```
      MAXIMISE : CPU utilisation , throughput
      MINIMISE : turnaround time , waiting time , response time
      ENSURE   : fairness , and no starvation
   ```
   - These pull against each other, which is why no single algorithm wins. `FCFS` is simple but suffers the convoy effect; `SJF` is optimal for waiting time but needs the burst length in advance and can starve long jobs; `Round Robin` is best for response time but adds context-switch overhead; `priority` scheduling honours importance but needs `ageing` to avoid starvation. Real systems use `multilevel feedback queues`, which combine several of these.

## Windows & System Administration (5)

1. **How to check the IP address in the Windows Command Prompt?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

2. **Assume that an office has three departments and each department has 50 to 70 employees who are using computers with Windows operating systems. The office space is designed in such a way that an employee can use any computer within a department. Once an employee logs in from a computer, he/she will get access to his files from the server. Let you are planning for network and server setup for this company.**
   * **(a) What is Active Directory? Do you need an Active Directory for such an office? If yes, briefly explain its use under this circumstance.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 323 (ET: BIBM)]*

3. **Describe the booting process in windows system.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 565 (ET: N/A)]*

4. **১৯. বর্তমানে উইন্ডোজ অপারেটিং সিস্টেম এর কত তম ভার্সন বাজারজাত করা হয়েছে?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

5. **What is main difference between Domain and Workgroup?** *[Bangladesh Bank Assistant Programmer 2016 compact it 1265 (ET: N/A)]*

## Process Synchronization & Concurrency (4)

1. Two independent applications running concurrently attempt to update the same file located at a same file location. Both applications may read and modify the file at nearly the same time, creating a possibility of race conditions, lost updates, or inconsistent data. What type of consistency problem can occur in this situation, and which synchronization technique(s) should be used to ensure that only one application can safely update the file at a time? Explain the mechanism and justify the most appropriate solution. [BSCCPL AME 21-08-2026 (BUET)]

2. **What is Semaphore? How would you improve performance when using semaphores?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 504 (ET: N/A)]*

3. **(গ) Process Synchronization এর ক্ষেত্রে Race condition ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*

4. **(ক) Critical Section Problem কী? ইহা কীভাবে সমাধান করা যায়?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*
