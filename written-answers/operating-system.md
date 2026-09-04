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

2. **Define: Socket, Kernel, Process, Program, Multiprogramming, Context Switching; Explain Preemptive Priority Scheduling algorithm with illustration; Explain LRU and NRU Page Replacement algorithm.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 302 (ET: BIBM)]*

3. **Explain how can multiprogramming be achieved on a uniprocessor system?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 379 (ET: BUET)]*

4. **Write the difference between shell and kernel?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*

5. **DOS কী? অপারেটিং সিস্টেমের কাজ ও প্রকারভেদ ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*

6. **Write down the difference between Multitasking and Multiprocessing.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*

7. **(b) What is the difference between micro kernel and macro kernel in the context of OS?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

8. **অথবা, (ক) Blocking এবং Buffering OS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 610 (ET: N/A)]*

9. **(গ) Real Time System বলতে কী বোঝায় ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*

10. **Explain context switching in Operating System.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*

11. **Which Operating system is considered as an Open source?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*

12. **What is kernel? Write down the objectives of kernel.** *[SPCB Sub-Assistant Programmer 2022 compact it 740 (ET: N/A)]*

13. **IBM প্রতিষ্ঠান কর্তৃক কোন Operating System প্রস্তুত করা হয়?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*

14. **Explain: Kernel, Cache, Virtual Memory and RAID.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 872-873 (ET: N/A)]*

15. **(a) Briefly describe the function that measure the efficiency of an operating system.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1025 (ET: N/A)]*

16. **What is the difference between micro kernel and macro kernel? What are the sub components of I/O manager in Windows NT?** *[Bangladesh Bank Assistant Maintenance Engineer 2019 compact it 1052-1053 (ET: BUET)]*

17. **What is operating System? What are the main components of operating System?** *[Bangladesh Competition Commission Programmer 2019 compact it 1059 (ET: DU)]*

18. **(গ) Operating System-এর সংগঠন সহ কাজ উল্লেখ করুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1067-1068 (ET: N/A)]*

19. **(খ) Time shearing operating system and Real time operating system-এর মধ্যে পার্থক্য লিখুন।** *[16th NTRCA Lecturer (ICT) (CSE): 2019 compact it 1072 (ET: N/A)]*

20. **(ক) মাল্টি প্রোগ্রামিং অপারেটিং সিস্টেম কী? সচিত্র বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1092 (ET: N/A)]*

21. **Discuss the Operating System architecture and how it works?** *[BINA Assistant Programmer 2019 compact it 1155 (ET: IBA)]*

22. **Difference between Multiprocessing and Multitasking.** *[Palli Sanchay Bank Assistant Database Administrator 2018 compact it 1169 (ET: N/A)]*

23. **Difference between Multitasking and Multiprogramming.** *[NWPGCL Assistant Engineer (CSE) 2018 compact it 1213 (ET: N/A)]*

24. **Explain the functionalities of operating system.** *[ICT Ministry Assistant Programmer 2017 compact it 1239-1240 (ET: N/A)]*

## Deadlock & Resource Allocation (23)

1. **What is Deadlock? Given a scenery and find out the process is face deadlock sitiation?** *[IFIC Bank Officer IT 2025 compact it 1448 (ET: IFIC)]*

2. **The four conditions that are necessary for a resource deadlock to occur are mutual exclusion, hold and wait, no preemption and circular wait. Give an example to show that these conditions are not sufficient for a resource deadlock to occur.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*

3. **(a) Define operating system. Why resource allocation graph used for deadlock detection?** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*

4. **What is Deadlock? Write Conditions for Deadlock and also write Deadlock.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*

5. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances).** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1321 (ET: DU)]*
   * (a) Need matrix
   * (b) Safe state or Unsafe
   Snapshot at time T_0:
The content of the matrix. Need is defined to be Max – Allocation.

6. **(a) Explain Circular wait deadlock.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 415 (ET: BUET)]*

7. **Give the necessary conditions for deadlock to occur. Is it possible to have deadlock involving only a single process? Explain your answer.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 422 (ET: BIBM)]*

8. **Deadlock এর চারটি শর্ত লিখ।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*

9. **What is deadlock? Draw its diagram.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*

10. **(ক) Deadlock কী? Deadlock Handling করার বিভিন্ন উপায়সমূহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 413 (ET: N/A)]*

11. **What are the four necessary condition of deadlock in an operating system?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*

12. **(a) What is deadlock in operating system (OS)? What are the four necessary and sufficient conditions behind deadlock?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

13. **(b) A system has P processes each needing a maximum of m resources and a total of r resources available. Which conditions must hold to make the system deadlock free?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*

14. **Name and define characteristics properties of the Deadlock situation in a computer system.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*

15. **(b) What are the conditions for deadlock situations? Explain briefly.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*

16. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances). Snapshot at time T_0. The content of the matrix. Need is defined to be \text{Max} - \text{Allocation}. Check that \text{Request} \le \text{Available}. Executing safety algorithm shows that sequence \langle P_1, P_3, P_4, P_0, P_2 \rangle satisfies safety requirement.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 855 (ET: N/A)]*

17. **(a) What is Artificial Intelligence (AI)? What are the necessary conditions for a deadlock in an operating system?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 890 (ET: N/A)]*

18. **What is Deadlock? Explain two situations where deadlock condition occurs.** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*

19. **A, B two resources. Two processes (P1 and P2) share these resources. When a process request for a resources, if that resource is free then it will be allocated with that resources. If the resources are not free then the process will halt. Now the scenario is:** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 973 (ET: BUET)]*

20. **What is Operating Systems Deadlock? কীভাবে Deadlock দূর করা যায়?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*

21. **(d) Define Deadlock. Write down the necessary conditions for deadlock.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026 (ET: N/A)]*

22. **Four condition of deadlock in Operating System. Suppose, n processes, \text{P}_1, \text{P}_2\dots \text{P}_n share m identical esource units which can be reserved and released one at a time. The maximum resources request of process \text{P}_i is \text{S}_i, where \text{S}_i>0. Which one is sufficient condition for ensuring that deadlock doesn't occur? (Full প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*

23. **(b) What are the conditions for a deadlock situation?** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130 (ET: N/A)]*

## Virtual Memory & Page Replacement (Thrashing) (16)

1. Consider the following page reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1. Assuming a system with 3 page frames initially empty, calculate the number of page faults using the following page replacement algorithms: (i) FIFO (First-In, First-Out), (ii) LRU (Least Recently Used), and (iii) Optimal Page Replacement. [BSCCPL AME 21-08-2026 (BUET)]

2. **Explain the concept of thrashing in an operating system, describing how it occurs in a demand-paged virtual memory system and how it impacts CPU utilization and overall system performance.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1422 (ET: E-Zone)]*

3. **a) Write about notes on i) Virtual memory, and ii) Cache memory.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*

4. **Consider a reference string 4,7,6,1,2,7,2 the number of frames in the memory is 3. Using page Replacement Algorithm (LRU), find the number of page fault.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)]*

5. **Why virtual memory needed?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 477 (ET: N/A)]*

6. **Consider page reference string 1, 3, 0, 3, 5, 6, 3 with 3 page frames. Find the number of page faults.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*

7. **Difference between physical memory and virtual memory, also describe the advantages and disadvantages of virtual memory.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 553 (ET: BIBM)]*

8. **(c) Define paging and trashing in the context of OS.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*

9. **What is page fault in computing systems? What does it occur?** *[BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*

10. **Write short note on Virtual Memory and Cache memory.** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*

11. **(ii) Virtual Memory এর প্রয়োজনীয়তা কি ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 786 (ET: N/A)]*

12. **A system uses 3 page frames for storing process pages in main memory. It uses the Least Recently Used (LRU) page replacement policy. Assume that all the page frames are initially empty. What is the total number of page faults that will occur while processing the page reference string given below? 4, 7, 6, 1, 7, 6, 1, 2, 7, 2.** *[BPDB Assistant Engineer (CSE) 2021 compact it 817 (ET: BUET)]*

13. **Briefly explain the concept of ‘Thrashing’ in terms of OS.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 822 (ET: BUET)]*

14. **(a) What do you mean by virtual memory?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*

15. **A system uses 8 page frames to store process pages in main memory. It uses the minimum page replacement policy. Assume that all page frames are initially blank. 64 separate pages were inserted and then the pages were inserted reverse order. How many pages will be miss?** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*

16. **(খ) Virtual Memory বলতে কী বোঝায়? এর কার্যপদ্ধতি সংক্ষেপে বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1093 (ET: N/A)]*

## Memory Management & Paging (16)

1. **A system uses 16 bit logical address and a page size of 1 KB.**
   **(i) How many pages are in logical address space?**
   **(ii) How many bits are used for the page number and offset?** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*

2. **Consider a logical address space of 512 pages, each of 2-KB page size, mapped onto a physical memory containing 128 frames.**
   **a. How many bits are required in the logical address?**
   **b. How many bits are required in the physical address?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*

3. **(a) Consider a computer system with the following specifications:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * Physical memory (RAM): 4\text{ GB}
 * Page size: 4\text{ KB}
 * Virtual address space: 32\text{ bits}
 * Page table entry size: 8\text{ bytes}
**Answer the following:**
 * **(i) How many pages are there in the virtual address space? Explain your answer.**
 * **(ii) What is the size of the page table? Explain your answer.**

4. **Compare “Paging” and “Segmentation” memory management technique?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*

5. **The __________ swaps process in and out of the memory.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

6. **Difference between Paging and Segmentation.** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*

7. **(ক) Swapping কী? Internal এবং External Fragmentation এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 414 (ET: N/A)]*

8. **Find out total number of pages, when page size 4KB and address space 32 bit.** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 588 (ET: BUET)]*

9. **(ক) Paging এবং Segmentation এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 609 (ET: N/A)]*

10. **(খ) Operating System-এর Memory hierarchy সচিত্র বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 611 (ET: N/A)]*

11. **(খ) Internal এবং External fragmentation এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

12. **(a) What is demand paging?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*

13. **In the given example, let us assume the jobs and the memory requirements as the following: Job1=90k, Job2=20k, Job3=50k, Job4=200k. Let the free pace memory allocation blocks are: Block1=50k, Block2=100k, Block3=90k, Block4=200k, Block5=50k.** *[Janata Bank Assistant System Administrator 2021 compact it 939-940 (ET: N/A)]*

14. **(ক) অপারেটিং সিস্টেম এর ক্ষেত্রে Swapping কী? কোন ক্ষেত্রে এটি ব্যবহৃত হয় লিখুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1094 (ET: N/A)]*

15. **(a) What do you mean by page table for memory management? Explain with example.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1129 (ET: N/A)]*

16. **Why page are sizes always powers of 2?** *[BCC-4TDC Assistant Programmer 2019 compact it 1161 (ET: BCC)]*

## Process Management & Process States (12)

1. **(b) What is process? Describe different states of a process.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

2. **(c) Define context switch with proper example.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*

3. **(খ) Process কী? বিভিন্ন ধরনের Process state এর কাজ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 414 (ET: N/A)]*

4. **Explain the process state.** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*

5. **(ক) Process কী? একটি Process এর বিভিন্ন ধাপগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*

6. **অথবা, (ক) Process Control Block (PCB) কী? এটি একটি Process সংক্রান্ত যে যে তথ্য রাখে সেগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*

7. **Write down the name of four information stored in PCB (Process Control Block).** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*

8. **Operating System এর Process state diagram অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*

9. **(i) Operating System এর Process State Transition Diagram আঁকুন ও ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 786 (ET: N/A)]*

10. **Operating System এর ক্ষেত্রে নিম্নোক্ত Process State গুলো ব্যবহার করে State Diagram অংকন করুন। [New, ready, Wait, Run, Terminated]** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1040 (ET: DPI)]*

11. **(c) What are the difference between process and threads?** *[BPSC Assistant Programmer (CSE) 2019 compact it 1130 (ET: N/A)]*

12. **(b) What are the difference between process and thread?** *[BPSC Assistant Programmer (ICT) 2019 compact it 1139 (ET: N/A)]*

## Concurrency, Threads & Synchronization (11)

1. Multi-threaded processing and distributed computing have become essential. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*

2. **What is Multithreading programming? Why Multithreading used in programming?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 296 (ET: BIBM)]*

3. **What is Multithreading System?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1460 (ET: N/A)]*

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

5. **অথবা, (ক) Thread এর সংজ্ঞা দিন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*

6. **Write down the thread life cycle.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*

7. **What is Multi-threading and multi-tasking? Difference between Multi-threading and Multi-tasking?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 854 (ET: N/A)]*

8. **(c) What is thread? Give some benefits of multi-threaded programming.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 889-890 (ET: N/A)]*

9. **(d) Differentiate between thread and process.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*

10. **What is multitasking and multithreading? What are the advantage threads over process?** *[Bangladesh Competition Commission Programmer 2019 compact it 1060 (ET: DU)]*

11. **Define thread cancellation, target thread. Enumerate the different RAID level.** *[Sonali & Janata Bank Officer (IT/ICT) 2019 compact it 1106-1107 (ET: AUST)]*

## File Systems & Disk Management (7)

1. **NTFS stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

2. **(খ) Unix file system এর প্রকারভেদ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 610 (ET: N/A)]*

3. **কোন ড্রাইভে ‘My Document’ রাখা হয় এবং NTFS কী?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

4. **A file system with 300 GB uses a file descriptor with 8 direct block address, 1 indirect block address and 1 doubly indirect block address. The size of each disk block is 128 Bytes and the size of each disk block address is 8 Bytes. The maximum possible file size in this file system.** *[BAUST Assistant Programmer 2021 compact it 917 (ET: N/A)]*

5. **(খ) Direct or Random Access File-প্রক্রিয়াকরণ চিত্রসহ বর্ণনা করুন।** *[16th NTRCA Lecturer (ICT) (ICT): 2019 compact it 1095 (ET: N/A)]*

6. **(a) An I/O system with a simple disk gets an average 50 I/O requests per second and average time for a disk to server an I/O request is 10ms. Calculate the utilization of I/O system.** *[BPSC Assistant Programmer (CSE) 2019 compact it 1134-1136 (ET: N/A)]*

7. **Explain inode data structures in Linux OS.** *[Agrani Bank Ltd. Senior Officer (IT) 2017 compact it 1220-1221 (ET: N/A)]*

## CPU Scheduling (6)

1. A system has three processes with the following arrival times and CPU burst times:

| Process | Arrival Time (ms) | Burst Time (ms) |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 3 |
| P3 | 2 | 2 |

Using the First-Come, First-Served (FCFS) CPU scheduling algorithm calculate the average waiting time and the average turnaround time. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*

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

3. **Consider the set of 3 processes whose arrival time and burst time are given below-**

| Process | AT | BT |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 4 |
| P3 | 2 | 2 |

**If the CPU scheduling policy is round robin with time quantum=2, finds out the completion time, turnaround time, waiting time, and response time** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1447 (ET: N/A)]*

4. **There are 3 tasks P1, P2, and P3. The arrival time and duration of each task is given below. Apply the round-robin scheduling algorithm with quantum size-20 to schedule the tasks in a single core machine. Calculate the turnaround time for each task. (All tasks have the same priority)** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

| Task | Arrival time (ms) | Duration (ms) |
|---|---|---|
| P1 | 0 | 40 |
| P2 | 5 | 40 |
| P3 | 10 | 20 |

5. **Calculate the average waiting time.** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

| Process | Burst Time |
|---|---|
| P1 | 21 |
| P2 | 3 |
| P3 | 6 |

6. **(খ) CPU Scheduling কী? যে যে কারণে CPU Scheduling করতে হয় সেগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*

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
