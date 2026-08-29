<!-- TOC START -->
**Table of Contents** — 12 subtopics · 168 questions

| # | Subtopic | Questions |
|---|---|---|
| 1 | [Linux / Unix Commands & Administration](#linux--unix-commands--administration-42) | 42 |
| 2 | [CPU Scheduling Algorithms](#cpu-scheduling-algorithms-24) | 24 |
| 3 | [Deadlock & Resource Allocation](#deadlock--resource-allocation-22) | 22 |
| 4 | [OS Concepts & System Software](#os-concepts--system-software-15) | 15 |
| 5 | [Virtual Memory & Page Replacement (Thrashing)](#virtual-memory--page-replacement-thrashing-15) | 15 |
| 6 | [Memory Management & Paging](#memory-management--paging-13) | 13 |
| 7 | [Process Management & Process States](#process-management--process-states-10) | 10 |
| 8 | [Concurrency, Threads & Synchronization](#concurrency-threads--synchronization-9) | 9 |
| 9 | [CPU Scheduling](#cpu-scheduling-6) | 6 |
| 10 | [Windows & System Administration](#windows--system-administration-4) | 4 |
| 11 | [Process Synchronization & Concurrency](#process-synchronization--concurrency-4) | 4 |
| 12 | [File Systems & Disk Management](#file-systems--disk-management-4) | 4 |

<!-- TOC END -->

---

## Linux / Unix Commands & Administration (42)

1. **Write Linux command:** *[Islami Bank PLC Senior Officer (Network/System) 14.03.2025 compact it 1331 (ET: BUET)]*
   (a) Give a file Read Write and Execute permission.
   (b) IP address show.
   (c) Delete all files in a folder.
   (d) Show partition.


   Answer:

   (a) Give a file read, write and execute permission:
   ```bash
   chmod 777 filename          # read, write, execute for owner, group and others
   chmod u+rwx filename        # only for the owner
   chmod a+rwx filename        # symbolic form of 777
   ```
   The three digits stand for owner, group and others, and each is the sum of read (4), write (2) and execute (1). So 7 = 4 + 2 + 1 = rwx.

   (b) Show the IP address:
   ```bash
   ip addr show                # modern standard command
   ip a                        # short form
   hostname -I                 # only the IP addresses
   ifconfig                    # older command, from the net-tools package
   curl ifconfig.me            # the public IP as seen from the internet
   ```

   (c) Delete all files in a folder:
   ```bash
   rm -r foldername/*          # delete the contents but keep the folder
   rm -rf foldername/*         # force, no prompt for each file
   rm foldername/*             # deletes only files, not sub-directories
   find foldername -type f -delete   # deletes only regular files, safest form
   ```
   Warning: rm -rf is irreversible and there is no recycle bin on the command line. Always check the current directory with pwd first.

   (d) Show partitions:
   ```bash
   lsblk                       # tree view of block devices and partitions
   fdisk -l                    # detailed partition table, needs root
   df -h                       # mounted file systems with sizes, human readable
   parted -l                   # partition information including the table type
   cat /proc/partitions        # the kernel's own list
   ```
2. **Write a Linux command to count the total number of characters and words from the first 10 lines of a file named "wasacustomers.txt".** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*


   Answer: The task is to take the first 10 lines of the file and then count the characters and the words in them.

   ```bash
   head -n 10 wasacustomers.txt | wc -c -w
   ```

   Explanation:
   - head -n 10 wasacustomers.txt prints the first 10 lines of the file.
   - The pipe symbol | sends that output as the input of the next command instead of to the screen.
   - wc means word count. The option -c counts characters (bytes) and -w counts words.

   Sample output:
   ```
     87  512
   ```
   The first figure is the word count and the second is the character count. The wc command always prints the counts in the fixed order lines, words, characters, whatever order the options are given in.

   Separate commands if the two counts are wanted individually:
   ```bash
   head -n 10 wasacustomers.txt | wc -w      # words only
   head -n 10 wasacustomers.txt | wc -c      # characters only
   head -n 10 wasacustomers.txt | wc -m      # characters, multibyte aware
   ```

   Variants:
   ```bash
   head wasacustomers.txt | wc -cw           # head defaults to 10 lines
   sed -n '1,10p' wasacustomers.txt | wc -cw # the same using sed
   awk 'NR<=10' wasacustomers.txt | wc -cw   # the same using awk
   ```

   Note on -c and -m: -c counts bytes and -m counts characters. For plain ASCII text they are identical, but for Bengali or any UTF-8 text one character occupies several bytes, so -m gives the number the question usually intends.
3. **Linux command:** *[DESCO Sub-Assistant Engineer 20.06.2025 compact it 1361 (ET: BUET)], [GTCL Assistant Engineer (CSE) 2022 compact it 685 (ET: BUET)], [PGCB Sub-Assistant Engineer (CSE) 2020 compact it 1046 (ET: BUET)]*


   Answer: The most frequently required Linux commands are grouped below.

   File and directory operations:
   ```bash
   ls -l              # long listing with permissions, owner, size and date
   ls -la             # including hidden files, whose names begin with a dot
   ls -lh             # sizes in human readable form
   pwd                # print the working directory
   cd /path           # change directory
   cd ..              # go one level up
   cd ~               # go to the home directory
   mkdir dirname      # create a directory
   mkdir -p a/b/c     # create a nested path in one step
   rmdir dirname      # remove an empty directory
   rm file            # delete a file
   rm -r dirname      # delete a directory and everything inside it
   cp source dest     # copy a file
   cp -r src dest     # copy a directory recursively
   mv old new         # move or rename
   touch file         # create an empty file, or update its timestamp
   ln -s target link  # create a symbolic link
   ```

   Viewing file contents:
   ```bash
   cat file           # print the whole file
   less file          # scroll through a file page by page
   head -n 20 file    # first 20 lines
   tail -n 20 file    # last 20 lines
   tail -f file       # follow a growing file, used for logs
   wc -l file         # count lines
   grep "text" file   # search for a pattern
   grep -r "text" .   # search recursively in the current directory
   ```

   Permissions and ownership:
   ```bash
   chmod 755 file     # rwx for owner, rx for group and others
   chmod +x script.sh # make a script executable
   chown user file    # change the owner
   chown user:group file
   chgrp group file   # change the group
   umask              # show the default permission mask
   ```

   Process management:
   ```bash
   ps aux             # list all running processes
   top                # live view of processes and resource use
   htop               # a friendlier version of top
   kill PID           # terminate a process politely
   kill -9 PID        # force termination
   killall name       # kill by process name
   jobs               # background jobs of the current shell
   bg / fg            # move a job to the background or the foreground
   ```

   System information:
   ```bash
   uname -a           # kernel and system information
   df -h              # disk space of mounted file systems
   du -sh dirname     # size of a directory
   free -h            # RAM and swap usage
   uptime             # how long the system has been running
   whoami             # current user
   date               # date and time
   lsblk              # block devices and partitions
   ```

   Networking:
   ```bash
   ip addr show       # network interfaces and IP addresses
   ping host          # test connectivity
   traceroute host    # show the route packets take
   netstat -tulnp     # listening ports (older)
   ss -tulnp          # listening ports (modern)
   wget URL           # download a file
   curl URL           # transfer data to or from a URL
   ssh user@host      # remote login
   scp file user@host:/path   # secure copy
   ```

   User management:
   ```bash
   sudo command       # run a command as the superuser
   useradd username   # create a user
   passwd username    # set or change a password
   userdel username   # delete a user
   groupadd groupname
   usermod -aG group user     # add a user to a group
   who                # who is logged in
   ```

   Package management:
   ```bash
   apt update && apt upgrade      # Debian and Ubuntu
   apt install package
   yum install package            # older Red Hat and CentOS
   dnf install package            # modern Fedora and RHEL
   ```

   Archiving:
   ```bash
   tar -cvf archive.tar dir/      # create an archive
   tar -xvf archive.tar           # extract
   tar -czvf archive.tar.gz dir/  # create and compress with gzip
   zip -r archive.zip dir/
   unzip archive.zip
   ```
4. **Write Linux command:** *[BCIC Assistant Programmer 14.02.2025 compact it 1324 (ET: BUET)]*
   * **(a) Displays real-time system statistics, including CPU usage, memory usage, running processes, and system load.**
   * **(b) Searches for a specified pattern in a file or output.**
   * **(c) Shows disk usage for all mounted file systems.**
   * **(d) Displays information about system memory (RAM and swap).** *[BCIC Assistant Programmer 14.02.2025 compact it 1325 (ET: BUET)]*


   Answer:

   (a) Displays real-time system statistics, including CPU usage, memory usage, running processes and system load:
   ```bash
   top
   ```
   It refreshes every few seconds and shows the load average, the number of tasks, CPU and memory usage, and the processes ranked by CPU consumption. Press q to quit, k to kill a process and M to sort by memory.
   ```bash
   htop        # an easier, colour version, if installed
   ```

   (b) Searches for a specified pattern in a file or output:
   ```bash
   grep "pattern" filename
   ```
   Useful options:
   ```bash
   grep -i "pattern" file       # ignore case
   grep -r "pattern" /path      # search recursively
   grep -n "pattern" file       # show line numbers
   grep -v "pattern" file       # show lines that do NOT match
   grep -c "pattern" file       # count matching lines
   ps aux | grep httpd          # search the output of another command
   ```

   (c) Shows disk usage for all mounted file systems:
   ```bash
   df -h
   ```
   The option -h means human readable, so sizes appear as 20G rather than as blocks. Related forms:
   ```bash
   df -h /home                  # only one file system
   df -i                        # inode usage rather than blocks
   du -sh /var/log              # size of a particular directory
   ```

   (d) Displays information about system memory (RAM and swap):
   ```bash
   free -h
   ```
   It shows total, used, free, shared, buffer/cache and available memory, for both RAM and swap. Related forms:
   ```bash
   free -m                      # in megabytes
   cat /proc/meminfo            # the kernel's detailed memory report
   vmstat                       # virtual memory statistics
   ```

   Summary table:

   | Requirement | Command |
   |---|---|
   | Real-time system statistics | top |
   | Search for a pattern | grep |
   | Disk usage of file systems | df -h |
   | Memory information | free -h |
5. **ফাইল Rename করার Linux কমান্ড কি?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: Linux এ ফাইল Rename করার কমান্ড হলো mv (move)।

   ```bash
   mv oldname.txt newname.txt
   ```

   ব্যাখ্যা: Linux এ আলাদা কোনো rename কমান্ড নেই। mv কমান্ডটি ফাইল সরানো ও নাম পরিবর্তন — দুটি কাজই করে। একই ডিরেক্টরির ভেতরে নতুন নাম দিলে সেটি নাম পরিবর্তন হয়, আর ভিন্ন পথ দিলে ফাইলটি সরে যায়।

   বিভিন্ন ব্যবহার:
   ```bash
   mv report.txt final_report.txt        # ফাইলের নাম পরিবর্তন
   mv olddir newdir                      # ডিরেক্টরির নাম পরিবর্তন
   mv file.txt /home/user/documents/     # ফাইল সরানো
   mv file.txt /home/user/doc/new.txt    # সরানো ও নাম পরিবর্তন একসঙ্গে
   mv -i old.txt new.txt                 # নতুন নামের ফাইল আগে থেকে থাকলে জিজ্ঞাসা করবে
   mv -n old.txt new.txt                 # আগের ফাইল থাকলে কিছুই করবে না
   mv -v old.txt new.txt                 # কী করা হলো তা দেখাবে
   ```

   একসঙ্গে অনেক ফাইলের নাম বদলাতে rename কমান্ড ব্যবহার করা যায় (কিছু ডিস্ট্রিবিউশনে আলাদা করে ইনস্টল করতে হয়):
   ```bash
   rename 's/\.txt$/\.bak/' *.txt        # সব .txt কে .bak করা
   ```

   অথবা লুপ ব্যবহার করে:
   ```bash
   for f in *.txt; do mv "$f" "${f%.txt}.bak"; done
   ```

   সতর্কতা: mv ডিফল্টভাবে কোনো সতর্কবার্তা ছাড়াই বিদ্যমান ফাইলের ওপর লিখে দেয়। তাই গুরুত্বপূর্ণ ফাইলের ক্ষেত্রে -i অপশন ব্যবহার করা উচিত।
6. **Which file is need by init to get the default run level?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1452 (ET: N/A)]*


   Answer: The file needed by init to determine the default run level is /etc/inittab.

   In that file the line has the form:
   ```
   id:3:initdefault:
   ```
   Here the number 3 is the default run level.

   The seven run levels in SysV init:

   | Run level | Meaning |
   |---|---|
   | 0 | Halt, that is shut down the system |
   | 1 | Single user mode, used for maintenance |
   | 2 | Multi-user mode without networking (varies by distribution) |
   | 3 | Full multi-user mode with networking, text console only |
   | 4 | Unused, available for a custom configuration |
   | 5 | Full multi-user mode with a graphical login |
   | 6 | Reboot |

   Related commands:
   ```bash
   runlevel                # show the previous and the current run level
   who -r                  # the same information
   init 3                  # change to run level 3
   telinit 5               # change to run level 5
   ```

   Important note on modern systems: most current distributions, including RHEL 7 and later, CentOS 7 and later, Ubuntu 15.04 and later and Debian 8 and later, have replaced SysV init with systemd. There is no /etc/inittab, and run levels have been replaced by targets:

   | Old run level | systemd target |
   |---|---|
   | 0 | poweroff.target |
   | 1 | rescue.target |
   | 3 | multi-user.target |
   | 5 | graphical.target |
   | 6 | reboot.target |

   The default is now read from the symbolic link /etc/systemd/system/default.target, and the commands are:
   ```bash
   systemctl get-default              # show the default target
   systemctl set-default multi-user.target
   systemctl isolate graphical.target # switch immediately
   ```

   So the answer is /etc/inittab for a SysV init system, and /etc/systemd/system/default.target for a systemd system.
7. **Show last 10 lines of log file which is continuously updating in Linux command?** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 417 (ET: BUET)]*


   Answer: The command is tail with the follow option.

   ```bash
   tail -f /var/log/syslog
   ```

   Explanation:
   - tail prints the last part of a file, and by default it prints the last 10 lines, which is exactly what the question asks for.
   - The option -f means follow: instead of ending, the command stays running and prints each new line as it is appended to the file. This is the standard way to watch a log while a service is running.
   - Press Ctrl+C to stop.

   Variants:
   ```bash
   tail -n 10 -f /var/log/syslog     # explicit about the 10 lines
   tail -20f /var/log/syslog         # start with the last 20 lines, then follow
   tail -F /var/log/syslog           # keep following even if the file is rotated
   tail -f file1 file2               # follow several files, with headers
   ```

   The difference between -f and -F is important in practice. Log files are rotated, that is renamed and replaced by a new empty file, by logrotate. With -f the command keeps watching the old, now renamed, file and appears to freeze. With -F it reopens the new file and continues, so -F is the safer choice for long-running monitoring.

   Combining with grep to watch only the interesting lines:
   ```bash
   tail -f /var/log/syslog | grep -i "error"
   tail -f /var/log/nginx/access.log | grep "404"
   ```

   On a systemd system the journal is watched with:
   ```bash
   journalctl -f                     # follow all logs
   journalctl -u nginx -f            # follow the log of one service
   journalctl -n 10 -f               # start with the last 10 lines
   ```

   Related command: less +F filename gives the same following behaviour but allows scrolling back with Ctrl+C, which tail cannot do.
8. **Linux Command in ownership and group permission.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 567 (ET: N/A)]*


   Answer: Ownership and permissions in Linux are handled by three commands: chown for the owner, chgrp for the group and chmod for the permission bits.

   Understanding the listing:
   ```bash
   $ ls -l report.txt
   -rw-r--r-- 1 rahim staff 2048 Aug 30 10:15 report.txt
   ```
   Reading the first field: the first character is the file type (- for a regular file, d for a directory, l for a link). The next nine characters are three groups of three: rw- for the owner, r-- for the group and r-- for others. Then come the owner name (rahim) and the group name (staff).

   Changing ownership with chown:
   ```bash
   chown rahim file.txt              # change the owner
   chown rahim:staff file.txt        # change the owner and the group together
   chown :staff file.txt             # change only the group
   chown -R rahim:staff /var/www     # recursively for a whole directory tree
   chown --reference=a.txt b.txt     # copy the ownership of one file to another
   ```
   Only the superuser may give a file away to another user, so chown normally requires sudo.

   Changing the group with chgrp:
   ```bash
   chgrp staff file.txt
   chgrp -R developers /project
   ```

   Changing permissions with chmod, numeric form:
   ```bash
   chmod 755 script.sh      # rwx for owner, r-x for group and others
   chmod 644 file.txt       # rw- for owner, r-- for group and others
   chmod 600 secret.key     # rw- for owner only
   chmod 777 file           # everything for everyone: avoid
   chmod -R 755 /var/www    # recursively
   ```
   The digits are the sum of read = 4, write = 2 and execute = 1, given for owner, group and others in that order.

   Changing permissions with chmod, symbolic form:
   ```bash
   chmod u+x script.sh      # add execute for the user (owner)
   chmod g-w file.txt       # remove write from the group
   chmod o-rwx file.txt     # remove everything from others
   chmod a+r file.txt       # add read for all
   chmod u=rw,g=r,o= file   # set exactly, clearing what is not listed
   ```
   The letters are u for user, g for group, o for others and a for all; the operators are + to add, - to remove and = to set exactly.

   Permission meanings on a directory, which differ from a file:
   - r allows the names inside to be listed.
   - w allows files to be created, renamed or deleted inside it.
   - x allows the directory to be entered and a named file inside it to be reached. Without x, r is almost useless.

   Special permission bits:
   ```bash
   chmod u+s program        # setuid: run with the owner's privileges
   chmod g+s directory      # setgid: new files inherit the directory's group
   chmod +t /tmp            # sticky bit: only the owner may delete their own files
   ```

   Default permissions:
   ```bash
   umask                    # show the mask, commonly 022
   umask 027                # set a stricter default
   ```
   New files are created with 666 minus the mask, and new directories with 777 minus the mask.

   Viewing the current state:
   ```bash
   ls -l file               # permissions, owner and group
   stat file                # full details including the numeric mode
   id username              # the user's UID, GID and group memberships
   groups username          # the groups a user belongs to
   ```

   Practical example, setting up a shared web directory:
   ```bash
   sudo chown -R www-data:developers /var/www/site
   sudo chmod -R 775 /var/www/site
   sudo chmod g+s /var/www/site      # new files keep the group
   ```
9. **UNIX command with example: File move, Change Directory and search from a specific line.** *[NPCBL Executive Trainee (Software) 26.05.2023 compact it 500 (ET: IBA)]*


   Answer:

   File move, using mv:
   ```bash
   mv report.txt /home/rahim/documents/          # move a file into a directory
   mv report.txt final_report.txt                # rename within the same directory
   mv *.txt /backup/                             # move all text files
   mv -i source.txt /tmp/                        # ask before overwriting
   mv olddir newdir                              # move or rename a directory
   ```
   Example with output:
   ```bash
   $ ls
   report.txt  data.csv
   $ mv report.txt /home/rahim/documents/
   $ ls
   data.csv
   $ ls /home/rahim/documents/
   report.txt
   ```
   Note that mv performs both moving and renaming; Unix has no separate rename command.

   Change directory, using cd:
   ```bash
   cd /var/log                # absolute path, starting from the root
   cd documents               # relative path, from the current directory
   cd ..                      # up one level
   cd ../..                   # up two levels
   cd ~                       # the home directory
   cd                         # also the home directory
   cd -                       # back to the previous directory
   cd /                       # the root directory
   ```
   Example with output:
   ```bash
   $ pwd
   /home/rahim
   $ cd /var/log
   $ pwd
   /var/log
   $ cd -
   /home/rahim
   ```
   cd is a shell built-in rather than a separate program, because it must change the state of the shell itself.

   Search from a specific line:

   To search for a pattern starting at a particular line, sed or awk is combined with grep.
   ```bash
   sed -n '10,$p' file.txt | grep "error"     # search from line 10 to the end
   awk 'NR>=10' file.txt | grep "error"       # the same using awk
   awk 'NR>=10 && /error/' file.txt           # awk alone, with the pattern built in
   tail -n +10 file.txt | grep "error"        # start at line 10 and search
   ```
   To search within a range of lines:
   ```bash
   sed -n '10,20p' file.txt | grep "error"    # only lines 10 to 20
   awk 'NR>=10 && NR<=20 && /error/' file.txt
   ```
   To find the line number at which a pattern first occurs:
   ```bash
   grep -n "error" file.txt                   # every match with its line number
   grep -n -m1 "error" file.txt               # only the first match
   ```
   Example with output:
   ```bash
   $ cat -n log.txt
        1  system started
        2  loading modules
        ...
       12  error: disk full
       15  error: timeout
   $ awk 'NR>=10' log.txt | grep -n "error"
   3:error: disk full
   6:error: timeout
   ```
   Note that the line numbers shown by grep -n after a pipe are relative to the piped input, not to the original file. To keep the original numbers, use grep -n on the file and filter:
   ```bash
   grep -n "error" log.txt | awk -F: '$1 >= 10'
   ```
10. **Write appropriate linux command:**
| Questions |
|---|
| Show hidden files and directories |
| Delete a directory and its file |
| Prints last five lines of a text file |
| Download a file from an URL |
*[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 474 (ET: N/A)]*


    Answer:

    | Requirement | Command |
    |---|---|
    | Show hidden files and directories | ls -a  (or ls -la for details) |
    | Delete a directory and its files | rm -r dirname  (or rm -rf dirname to force) |
    | Print the last five lines of a text file | tail -n 5 filename |
    | Download a file from a URL | wget URL  (or curl -O URL) |

    Details of each:

    Show hidden files and directories:
    ```bash
    ls -a              # all entries, including those beginning with a dot
    ls -la             # the same, in long form with permissions and sizes
    ls -A              # all except the . and .. entries
    ls -d .*           # only the hidden entries
    ```
    In Linux a file is hidden simply by beginning its name with a dot, for example .bashrc or .ssh. There is no hidden attribute as in Windows.

    Delete a directory and its files:
    ```bash
    rm -r dirname      # recursive delete, prompting for protected files
    rm -rf dirname     # recursive and forced, no prompts at all
    rm -ri dirname     # recursive but asking about every item
    rmdir dirname      # works only if the directory is already empty
    ```
    Warning: there is no recycle bin on the command line. rm -rf / would attempt to delete the entire system, so the current directory should always be verified with pwd first.

    Print the last five lines of a text file:
    ```bash
    tail -n 5 filename
    tail -5 filename           # older short form
    tail -n 5 -f filename      # print them and then keep following the file
    ```

    Download a file from a URL:
    ```bash
    wget https://example.com/file.zip            # save with the original name
    wget -O myfile.zip https://example.com/f.zip # save under a chosen name
    wget -c https://example.com/big.iso          # resume an interrupted download
    curl -O https://example.com/file.zip         # curl, keeping the remote name
    curl -o myfile.zip https://example.com/f.zip # curl, with a chosen name
    ```
    Difference between the two: wget is designed for downloading and can recurse through a whole site, while curl is a general transfer tool that supports many protocols and is better suited to scripting and to APIs.
11. **Write Linux command to find out the following question:** *[BTCL Assistant Manager (Technical) 2023 compact it 592 (ET: BUET)]*
   (a) To show current file directory.
   (b) To show 11^{\text{th}} to 15^{\text{th}} line from file name myfile.
   (c) To show permission for read, write and execution file name myfile.


    Answer:

    (a) To show the current file directory:
    ```bash
    pwd
    ```
    It prints the absolute path of the working directory, for example /home/rahim/documents. To list what is in it:
    ```bash
    ls          # names only
    ls -l       # long listing with permissions, owner, size and date
    ls -la      # including hidden files
    ```

    (b) To show the 11th to the 15th line of a file named myfile:
    ```bash
    sed -n '11,15p' myfile
    ```
    The option -n suppresses the automatic printing of every line, and the command 11,15p prints only lines 11 to 15.

    Alternative forms:
    ```bash
    head -n 15 myfile | tail -n 5        # take the first 15, then the last 5 of those
    awk 'NR>=11 && NR<=15' myfile        # using awk with the record number
    tail -n +11 myfile | head -n 5       # start at line 11, take 5 lines
    ```

    (c) To show the read, write and execute permissions of a file named myfile:
    ```bash
    ls -l myfile
    ```
    Sample output:
    ```
    -rwxr-xr-- 1 rahim staff 1024 Aug 30 11:20 myfile
    ```
    Reading it: the first character is the file type; the next three (rwx) are the owner's permissions; the next three (r-x) are the group's; and the last three (r--) are for others. So the owner may read, write and execute, the group may read and execute, and others may only read. In numeric form this is 754.

    Other ways to see the permissions:
    ```bash
    stat myfile                    # full details including the numeric mode
    stat -c "%a %n" myfile         # just the numeric permission and the name
    getfacl myfile                 # including any access control list entries
    namei -l /path/to/myfile       # permissions of every directory along the path
    ```
12. **Write down the names of the three users who can access a file on directory on Linux.** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 447 (ET: BUET)]*


    Answer: In Linux the permissions of a file or directory are defined for three classes of user.

    - Owner (user), abbreviated u: the user who created the file, or to whom it has been given by chown. The owner's permissions are the first three characters of the permission string.
    - Group, abbreviated g: the group that owns the file. Every user who is a member of that group receives these permissions. They are the middle three characters.
    - Others (world), abbreviated o: everybody else on the system, that is any user who is neither the owner nor a member of the owning group. They are the last three characters.

    Reading a listing:
    ```bash
    $ ls -l report.txt
    -rwxr-xr-- 1 rahim staff 2048 Aug 30 10:15 report.txt
     ^ ^^^ ^^^ ^^^   ^^^^^ ^^^^^
     |  |   |   |      |     |
     |  |   |   |      |     +-- owning group
     |  |   |   |      +-------- owner
     |  |   |   +--------------- others: r-- (read only)
     |  |   +------------------- group: r-x (read and execute)
     |  +----------------------- owner: rwx (read, write, execute)
     +-------------------------- file type: - regular file, d directory, l link
    ```

    The three permission bits:
    - r (read, value 4): view the contents of a file, or list the names in a directory.
    - w (write, value 2): modify a file, or create, rename and delete entries in a directory.
    - x (execute, value 1): run a file as a program, or enter a directory and reach a named file inside it.

    Setting them:
    ```bash
    chmod u+w file       # add write for the owner
    chmod g-x file       # remove execute from the group
    chmod o=r file       # set others to read only
    chmod a+r file       # add read for all three classes
    chmod 754 file       # owner rwx (7), group r-x (5), others r-- (4)
    ```

    Determining which class applies: when a user accesses a file, the kernel checks in strict order. If the user is the owner, the owner bits are used and no others are considered. Otherwise, if the user belongs to the owning group, the group bits are used. Otherwise the others bits are used. Because the first matching class wins, an owner with fewer permissions than others actually has less access, which surprises many beginners.

    The root user is the exception: root bypasses these checks entirely and may read or write any file.

    Beyond the three classes: when finer control is needed, access control lists give permissions to named individual users and groups.
    ```bash
    setfacl -m u:karim:rw file    # give karim read and write
    getfacl file                  # display the full ACL
    ```
13. **You need to find the total number of linux of the .c and .h file in the current directory formulas the linux commands to display this......... (Approximate)** *[BPDB Assistant Engineer (CSE) 24.02.2023 compact it 448 (ET: BUET)]*


    Answer: The task is to count the total number of lines in all the .c and .h files in the current directory.

    ```bash
    wc -l *.c *.h
    ```
    This prints the line count of each file and a total line at the end.

    Sample output:
    ```
       120 main.c
        85 utils.c
        45 main.h
        30 utils.h
       280 total
    ```

    To print only the total:
    ```bash
    cat *.c *.h | wc -l
    ```

    Including sub-directories as well:
    ```bash
    find . -name "*.c" -o -name "*.h" | xargs wc -l
    ```
    Explanation: find searches recursively, -name matches the pattern, -o means logical OR, and xargs passes the resulting list of file names to wc as arguments.

    A safer version, which copes with spaces in file names:
    ```bash
    find . \( -name "*.c" -o -name "*.h" \) -print0 | xargs -0 wc -l
    ```

    Only the grand total:
    ```bash
    find . \( -name "*.c" -o -name "*.h" \) -exec cat {} + | wc -l
    ```

    Excluding blank lines, which is often what is really wanted:
    ```bash
    cat *.c *.h | grep -v "^\s*$" | wc -l
    ```

    Excluding blank lines and single-line comments:
    ```bash
    cat *.c *.h | grep -v "^\s*$" | grep -v "^\s*//" | wc -l
    ```

    Counting other things about the same files:
    ```bash
    wc -w *.c *.h        # words
    wc -c *.c *.h        # bytes
    ls *.c *.h | wc -l   # how many such files exist
    ```

    Point to note about the two approaches: wc -l *.c *.h prints one line per file plus a total, while cat *.c *.h | wc -l prints a single number, because wc then reads one continuous stream and does not know where one file ends and the next begins.
14. **Find the possible path to know how data on the internet treavels from your mechine to the site www.bicic.gov.bd. Write down the necessary command to accomplish this.** *[BICIC Assistant Programmer 2022 compact it 633 (ET: BUET)]*


    Answer: The command that shows the route packets take from the local machine to a destination is traceroute.

    ```bash
    traceroute www.bicic.gov.bd
    ```

    How it works: traceroute sends packets with the IP time-to-live field set to 1, then 2, then 3, and so on. Each router along the path decrements the TTL, and the router at which it reaches zero returns an ICMP "time exceeded" message. The source address of that message identifies that hop. By increasing the TTL step by step, the whole path is discovered.

    Sample output:
    ```
    traceroute to www.bicic.gov.bd (203.112.xxx.xxx), 30 hops max, 60 byte packets
     1  192.168.1.1        1.234 ms   1.102 ms   1.045 ms
     2  10.10.1.1          8.567 ms   8.234 ms   8.109 ms
     3  103.xx.xx.xx      12.345 ms  12.100 ms  11.987 ms
     4  * * *
     5  203.112.xxx.xxx   25.678 ms  25.234 ms  25.100 ms
    ```
    Each line is one hop. The three timings are three separate probes, which shows whether the delay is consistent. A row of asterisks means that the router did not reply, usually because it is configured to ignore ICMP, and it does not necessarily indicate a fault.

    Useful options:
    ```bash
    traceroute -n www.bicic.gov.bd    # numeric only, skip DNS lookup, so it is faster
    traceroute -I www.bicic.gov.bd    # use ICMP echo instead of UDP
    traceroute -T -p 443 www.bicic.gov.bd  # use TCP to port 443, gets through firewalls
    traceroute -m 20 www.bicic.gov.bd # limit to 20 hops
    ```

    Equivalent and related commands:
    ```bash
    tracepath www.bicic.gov.bd        # similar, needs no root privileges
    mtr www.bicic.gov.bd              # traceroute and ping combined, updated live
    ping www.bicic.gov.bd             # only tests reachability, not the path
    ```
    On Windows the command is tracert www.bicic.gov.bd.

    If traceroute is not installed:
    ```bash
    sudo apt install traceroute       # Debian and Ubuntu
    sudo yum install traceroute       # CentOS and RHEL
    ```

    Practical value: traceroute shows where a connection slows down or breaks. If the delay jumps sharply at one hop, the congestion is at or after that router; if the trace stops entirely at a particular hop, the fault lies there rather than at the destination server.
15. **You want to run some specific commands at some price schedules time. Which command will have to be used for this.** *[BICIC Assistant Programmer 2022 compact it 633 (ET: BUET)]*


    Answer: To run specific commands at scheduled times, the cron system is used, and the command that manages it is crontab.

    ```bash
    crontab -e        # edit the current user's schedule
    crontab -l        # list the scheduled jobs
    crontab -r        # remove all jobs of the current user
    crontab -u user -e   # edit another user's schedule, needs root
    ```

    Format of a crontab line: five time fields followed by the command.
    ```
    * * * * * command_to_run
    | | | | |
    | | | | +--- day of week   (0 - 7, where both 0 and 7 mean Sunday)
    | | | +----- month         (1 - 12)
    | | +------- day of month  (1 - 31)
    | +--------- hour          (0 - 23)
    +----------- minute        (0 - 59)
    ```

    Examples:
    ```bash
    0 2 * * *      /home/user/backup.sh        # every day at 2:00 am
    */15 * * * *   /usr/bin/check_service.sh   # every 15 minutes
    0 9 * * 1-5    /home/user/report.sh        # 9 am, Monday to Friday
    0 0 1 * *      /home/user/monthly.sh       # midnight on the first of each month
    30 3 * * 0     /home/user/weekly.sh        # 3:30 am every Sunday
    @reboot        /home/user/startup.sh       # once, when the system boots
    @daily         /home/user/daily.sh         # shorthand for 0 0 * * *
    ```

    Redirecting output, which is important because cron mails any output to the user:
    ```bash
    0 2 * * * /home/user/backup.sh >> /var/log/backup.log 2>&1
    0 3 * * * /home/user/task.sh > /dev/null 2>&1     # discard all output
    ```

    For a job that is to run only once at a future time, the at command is used instead:
    ```bash
    at 14:30                      # then type the commands and press Ctrl+D
    echo "sh /home/user/task.sh" | at 10:00 tomorrow
    at now + 2 hours
    atq                           # list pending at jobs
    atrm 3                        # remove job number 3
    ```

    Difference between the two:
    - cron is for recurring jobs that repeat on a schedule.
    - at is for a single job that runs once at a specified time.
    - anacron is for jobs on machines that are not always powered on; it runs a missed job when the machine next starts.

    On systemd systems the modern equivalent is a timer unit:
    ```bash
    systemctl list-timers
    ```
    which offers better logging, dependency handling and randomised delays than cron.

    System-wide cron files, for reference: /etc/crontab, /etc/cron.d/ and the directories /etc/cron.hourly/, /etc/cron.daily/, /etc/cron.weekly/ and /etc/cron.monthly/.
16. **Linux Command লিখ:** *[BTCL Junior Assistant Manager 2022 compact it 640 (ET: BUET)]*
   a) একটি ফোল্ডারের সকল ফাইল দেখানোর কমান্ড।
   b) নতুন ডিরেক্টরি তৈরির কমান্ড।
   c) ফাইল এ্যাকসেস পারমিশন দেখানোর কমান্ড।


    Answer:

    (a) একটি ফোল্ডারের সকল ফাইল দেখানোর কমান্ড:
    ```bash
    ls                    # সাধারণ তালিকা
    ls -l                 # বিস্তারিত তালিকা: অনুমতি, মালিক, আকার, তারিখ
    ls -a                 # লুকানো ফাইলসহ (যেগুলোর নাম বিন্দু দিয়ে শুরু)
    ls -la                # লুকানো ফাইলসহ বিস্তারিত তালিকা
    ls -lh                # আকার মানুষের পাঠযোগ্য রূপে (K, M, G)
    ls -lt                # সময় অনুযায়ী সাজানো, নতুনটি আগে
    ls /path/to/folder    # নির্দিষ্ট ফোল্ডারের তালিকা
    ls -R                 # সাব-ডিরেক্টরিসহ পুনরাবৃত্ত তালিকা
    ```

    (b) নতুন ডিরেক্টরি তৈরির কমান্ড:
    ```bash
    mkdir dirname                 # একটি ডিরেক্টরি তৈরি
    mkdir dir1 dir2 dir3          # একসঙ্গে একাধিক
    mkdir -p project/src/main     # নেস্টেড পথ একবারে তৈরি
    mkdir -m 755 dirname          # তৈরির সময়েই অনুমতি নির্ধারণ
    mkdir -v dirname              # কী তৈরি হলো তা দেখাবে
    ```
    -p অপশনটি বিশেষভাবে গুরুত্বপূর্ণ: এটি মধ্যবর্তী ডিরেক্টরিগুলোও তৈরি করে এবং ডিরেক্টরি আগে থেকে থাকলে ত্রুটি দেখায় না।

    (c) ফাইল অ্যাকসেস পারমিশন দেখানোর কমান্ড:
    ```bash
    ls -l filename                # অনুমতি, মালিক ও গ্রুপ দেখায়
    stat filename                 # সংখ্যাসূচক মোডসহ বিস্তারিত তথ্য
    stat -c "%a %n" filename      # কেবল সংখ্যাসূচক অনুমতি ও নাম
    getfacl filename              # ACL সহ পূর্ণ অনুমতি
    namei -l /path/to/file        # পথের প্রতিটি ডিরেক্টরির অনুমতি
    ```

    উদাহরণ ও ব্যাখ্যা:
    ```bash
    $ ls -l report.txt
    -rwxr-xr-- 1 rahim staff 2048 Aug 30 10:15 report.txt
    ```
    - প্রথম অক্ষর ফাইলের ধরন: - সাধারণ ফাইল, d ডিরেক্টরি, l লিংক।
    - পরের তিনটি (rwx) মালিকের অনুমতি।
    - তার পরের তিনটি (r-x) গ্রুপের অনুমতি।
    - শেষ তিনটি (r--) অন্য সবার অনুমতি।
    - সংখ্যায় প্রকাশ করলে এটি 754 (r=4, w=2, x=1)।

    অনুমতি পরিবর্তনের কমান্ড:
    ```bash
    chmod 755 filename
    chmod u+x filename
    chown user:group filename
    ```
17. **UNIX command (directory listing with hidden files).** *[Sonali & Janata Bank Ltd. Assistant Database Administrator 2022 compact it 662 (ET: N/A)]*


    Answer: The command to list a directory including hidden files is:

    ```bash
    ls -a
    ```

    Forms and options:
    ```bash
    ls -a          # all entries, including . and .. and every dot file
    ls -A          # almost all: hidden files but not the . and .. entries
    ls -la         # all entries in long form, with permissions and sizes
    ls -lah        # the same, with sizes in human readable form
    ls -a /path    # a specific directory
    ls -d .*       # only the hidden entries
    ```

    Sample output:
    ```
    $ ls -la
    total 48
    drwxr-xr-x  5 rahim staff  4096 Aug 30 11:00 .
    drwxr-xr-x 12 root  root   4096 Aug 20 09:15 ..
    -rw-------  1 rahim staff  1024 Aug 29 18:30 .bash_history
    -rw-r--r--  1 rahim staff   220 Aug 20 09:15 .bashrc
    drwx------  2 rahim staff  4096 Aug 25 14:20 .ssh
    -rw-r--r--  1 rahim staff  2048 Aug 30 10:15 report.txt
    drwxr-xr-x  3 rahim staff  4096 Aug 28 16:45 documents
    ```

    Explanation:
    - In Unix and Linux a file is hidden simply because its name begins with a dot. There is no separate hidden attribute as there is in Windows. Making a file hidden is therefore only a matter of renaming it: mv file .file
    - The entry . is the current directory itself, and .. is the parent directory. The option -A suppresses these two, which is usually what is wanted.
    - Hidden files are used for configuration, for example .bashrc, .profile, .gitignore, .ssh and .config.

    Meaning of the long listing fields, in order: file type and permissions, number of hard links, owner, group, size in bytes, date and time of last modification, and the name.

    Related commands:
    ```bash
    ls -lS         # sort by size, largest first
    ls -lt         # sort by modification time, newest first
    ls -ltr        # oldest first
    ls -R          # recursive, including sub-directories
    ls -i          # show the inode number
    tree -a        # a tree view including hidden files, if tree is installed
    ```
18. **Difference between below 3 linux command: cd, cd usr/desk/home, cd/user/desk/home** *[EGCB Assistant Engineer (CSE) 2022 compact it 717 (ET: BUET)]*


    Answer: The three forms differ in where they take the user, and one of them contains a syntax error that is worth pointing out.

    | Command | Type of path | Where it goes |
    |---|---|---|
    | cd | No argument | The user's home directory, for example /home/rahim |
    | cd usr/desk/home | Relative path | Into usr/desk/home starting from the current directory |
    | cd /user/desk/home | Absolute path | To /user/desk/home starting from the root directory |

    1. cd with no argument:
    ```bash
    $ pwd
    /var/log
    $ cd
    $ pwd
    /home/rahim
    ```
    It is equivalent to cd ~ and to cd $HOME. It always returns the user to the home directory, whatever the current directory was.

    2. cd usr/desk/home, a relative path:
    ```bash
    $ pwd
    /home/rahim
    $ cd usr/desk/home
    $ pwd
    /home/rahim/usr/desk/home
    ```
    Because the path does not begin with a slash, it is interpreted relative to the current directory. The same command therefore leads to a different place depending on where it is issued, and it fails if usr does not exist inside the current directory.

    3. cd /user/desk/home, an absolute path:
    ```bash
    $ pwd
    /var/log
    $ cd /user/desk/home
    $ pwd
    /user/desk/home
    ```
    Because the path begins with a slash, it starts from the root of the file system. It leads to exactly the same place no matter where it is issued.

    Note on the printed form: the third command is written in the question as cd/user/desk/home with no space after cd. That is a syntax error; the shell would look for a program called cd/user/desk/home and report "command not found". A space is required between a command and its argument.

    The essential distinction: a path beginning with / is absolute and is measured from the root; a path not beginning with / is relative and is measured from the current directory. This is the single most important idea in navigating a Unix file system.

    Other useful forms:
    ```bash
    cd ..        # one level up
    cd ../..     # two levels up
    cd -         # back to the previous directory
    cd ~/docs    # relative to the home directory
    cd /         # the root directory
    ```
19. **Linux Command: Write down the linux command: All hidden flies, remove a file, permission of a file, search for a string.** *[Water Supply and Sewerage Authority (WASA); Assistant Programmer 25.11.2022 compact it 763 (ET: N/A)], [MGMCL Assistant Manager (ICT) 20.05.2022 compact it 651 (ET: BUET)]*


    Answer:

    All hidden files:
    ```bash
    ls -a              # every entry, including . and ..
    ls -A              # hidden files but not . and ..
    ls -la             # long listing including hidden files
    ls -d .*           # only the hidden entries
    find . -name ".*"  # hidden files recursively
    ```
    In Linux a file is hidden simply because its name begins with a dot.

    Remove a file:
    ```bash
    rm filename                # delete one file
    rm file1 file2 file3       # delete several
    rm -i filename             # ask for confirmation first
    rm -f filename             # force, no prompt even if write-protected
    rm *.txt                   # delete all text files
    rm -r dirname              # delete a directory and its contents
    rm -rf dirname             # force recursive delete
    ```
    There is no recycle bin, so a deleted file is gone. The habit of running pwd before rm -rf is worth acquiring.

    Permission of a file:
    ```bash
    ls -l filename             # show the permissions
    stat filename              # detailed, with the numeric mode
    stat -c "%a %n" filename   # just the numeric mode and the name

    chmod 755 filename         # set: rwx for owner, rx for group and others
    chmod u+x filename         # add execute for the owner
    chmod g-w filename         # remove write from the group
    chmod a+r filename         # add read for all
    chmod -R 755 dirname       # recursively for a directory tree
    chown user:group filename  # change owner and group
    ```

    Search for a string:
    ```bash
    grep "string" filename          # search in one file
    grep -i "string" filename       # ignore case
    grep -n "string" filename       # show line numbers
    grep -r "string" /path          # search recursively through a directory
    grep -c "string" filename       # count matching lines
    grep -v "string" filename       # show lines that do not match
    grep -w "string" filename       # match the whole word only
    grep -l "string" *.txt          # list only the file names that match
    grep -A 3 -B 3 "string" file    # show 3 lines of context each side
    grep -E "error|warning" file    # extended regular expression, either word
    ```
    To search in the output of another command:
    ```bash
    ps aux | grep nginx
    dmesg | grep -i usb
    ```
    To search for a file by name rather than for text inside files:
    ```bash
    find /path -name "filename"
    locate filename                 # faster, uses a prebuilt database
    ```
20. **(b) Write Linux commands to: (i) Make a directory named PSC (ii) Copy a directory with all its Contents into a directory name/home/admin.** *[BPSC Sub-Assistant Engineer (Ministry of Agriculture) 2021 compact it 799 (ET: N/A)]*


    Answer:

    (i) Make a directory named PSC:
    ```bash
    mkdir PSC
    ```
    Related forms:
    ```bash
    mkdir -p /home/admin/PSC        # create the whole path if it does not exist
    mkdir -m 755 PSC                # create it with specific permissions
    mkdir -v PSC                    # report what was created
    ```

    (ii) Copy a directory with all its contents into the directory /home/admin:
    ```bash
    cp -r PSC /home/admin/
    ```
    The option -r means recursive, so the directory and everything inside it, including sub-directories, is copied. Without -r the command refuses to copy a directory.

    Better forms in practice:
    ```bash
    cp -a PSC /home/admin/          # archive mode: preserves permissions, ownership,
                                    # timestamps and symbolic links
    cp -rv PSC /home/admin/         # verbose, lists each file as it is copied
    cp -ri PSC /home/admin/         # ask before overwriting anything
    cp -ru PSC /home/admin/         # copy only files that are newer, useful for syncing
    ```

    Using rsync, which is preferred for large directories:
    ```bash
    rsync -av PSC /home/admin/      # archive and verbose
    rsync -av --progress PSC /home/admin/   # with a progress display
    ```
    rsync copies only what has changed, can resume after an interruption, and can work over the network, which makes it the standard tool for backups.

    A point about the trailing slash, which causes a common mistake:
    - cp -r PSC /home/admin/ creates /home/admin/PSC with the contents inside it.
    - cp -r PSC/ /home/admin/ does the same for cp.
    - In rsync, however, rsync -av PSC/ /home/admin/ copies the contents of PSC directly into /home/admin, without creating a PSC directory, while rsync -av PSC /home/admin/ creates /home/admin/PSC. The trailing slash matters in rsync but not in cp.

    Verifying the result:
    ```bash
    ls -l /home/admin/PSC
    du -sh /home/admin/PSC          # compare the size with the original
    diff -r PSC /home/admin/PSC     # confirm the copy is identical
    ```
21. **In Linux, History is a very useful command to show you all of the last commands that have been recently used. Grep is a Linux command-line tool used to search for a string of characters in a specified file. Write grep and history command to find previous commands in Linux.** *[BCC Assistant Programmer 12.02.2021 compact it 813 (ET: BUET)]*


    Answer: The history command lists the commands recently used, and grep filters that list. Combining them with a pipe is the standard way to find a command that was used earlier.

    The history command:
    ```bash
    history                 # show the whole history, numbered
    history 20              # show only the last 20 commands
    history -c              # clear the history of the current session
    !123                    # re-run command number 123
    !!                      # re-run the previous command
    !grep                   # re-run the most recent command beginning with grep
    ```
    The history is kept in memory during the session and is written to ~/.bash_history on exit. Its size is controlled by the variables HISTSIZE and HISTFILESIZE.

    Combining history with grep, which is what the question asks for:
    ```bash
    history | grep "ssh"              # every past command containing ssh
    history | grep -i "docker"        # ignoring case
    history | grep "apt install"      # find what was installed
    history | grep "^ *[0-9]* *git"   # commands that begin with git
    history | grep "mysql" | tail -5  # the five most recent matches
    ```

    Sample output:
    ```
    $ history | grep "ssh"
      112  ssh rahim@192.168.1.50
      145  ssh-keygen -t rsa -b 4096
      201  ssh-copy-id rahim@server.local
      256  history | grep "ssh"
    ```
    The number at the start is the history index, so the command can be re-run simply by typing !112.

    Note that the grep command itself appears in the output, because by the time grep runs, the history command has already recorded it.

    Searching interactively, which is often quicker than using history at all:
    - Press Ctrl+R and start typing. Bash performs a reverse incremental search through the history. Press Ctrl+R again to step back through further matches, Enter to run the command, or the right arrow key to edit it first.

    Useful related settings, placed in ~/.bashrc:
    ```bash
    export HISTSIZE=10000              # commands kept in memory
    export HISTFILESIZE=20000          # commands kept in the file
    export HISTTIMEFORMAT="%F %T "     # record and show the date and time
    export HISTCONTROL=ignoredups      # do not store consecutive duplicates
    ```
    With HISTTIMEFORMAT set, the output becomes:
    ```
      112  2026-08-28 14:32:05 ssh rahim@192.168.1.50
    ```

    A useful one-liner to find the ten commands used most often:
    ```bash
    history | awk '{print $2}' | sort | uniq -c | sort -rn | head -10
    ```

    A security note worth stating: the history file records everything typed, including passwords given on the command line. That is one reason why a password should never be passed as a command argument.
22. **Write down a shell script program that would add the line “This is my file” at the top of each file having the extention ‘txt’ in the current directory. Note that all the other contents of the .txt file(s) would remain unchanged and start from the second line.** *[BPDB Assistant Engineer (CSE) 2021 compact it 818 (ET: BUET)]*


    Answer: The script must insert the line "This is my file" as the first line of every .txt file in the current directory, leaving all existing content unchanged and pushed down by one line.

    Method 1, using sed in place, which is the shortest correct solution:

    ```bash
    #!/bin/bash
    # add_header.sh - insert a header line at the top of every .txt file

    for file in *.txt
    do
        # guard against the case where no .txt file exists,
        # in which case the pattern remains the literal string *.txt
        if [ -f "$file" ]; then
            sed -i '1i This is my file' "$file"
            echo "Header added to: $file"
        fi
    done

    echo "Done."
    ```

    Explanation:
    - for file in *.txt loops over every file whose name ends in .txt.
    - [ -f "$file" ] checks that it really is a regular file, which also prevents the loop from running once with the literal text *.txt when the directory contains no such file.
    - sed -i edits the file in place rather than printing to the screen.
    - 1i means insert before line 1. The existing line 1 becomes line 2, so nothing is lost or overwritten.
    - The variable is quoted as "$file" so that names containing spaces are handled correctly.

    Method 2, without sed, using a temporary file. This shows the logic explicitly and works on any Unix system:

    ```bash
    #!/bin/bash

    for file in *.txt
    do
        if [ -f "$file" ]; then
            temp=$(mktemp)                       # create a safe temporary file
            echo "This is my file" > "$temp"     # write the new first line
            cat "$file" >> "$temp"               # append the original content
            mv "$temp" "$file"                   # replace the original
            echo "Header added to: $file"
        fi
    done
    ```

    Method 3, a compact one-line form:
    ```bash
    for f in *.txt; do sed -i '1i This is my file' "$f"; done
    ```

    Method 4, taking a backup at the same time, which is the safest for real use:
    ```bash
    #!/bin/bash
    for file in *.txt
    do
        [ -f "$file" ] || continue
        sed -i.bak '1i This is my file' "$file"    # keeps file.txt.bak
        echo "Processed $file (backup saved as $file.bak)"
    done
    ```

    Running the script:
    ```bash
    chmod +x add_header.sh      # make it executable
    ./add_header.sh             # run it
    ```

    Demonstration:
    ```bash
    $ cat note.txt
    First original line
    Second original line

    $ ./add_header.sh
    Header added to: note.txt
    Done.

    $ cat note.txt
    This is my file
    First original line
    Second original line
    ```

    A caution on portability: sed -i without an argument works on GNU sed, which is what Linux uses. On macOS and BSD, sed -i requires an argument, so the portable form is sed -i '' '1i\
    This is my file' "$file". For an exam answer on Linux, the GNU form given above is correct.
23. **Write the following UNIX command with example: (a) ls (b) grep (c) ssh** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 820 (ET: BUET)]*


    Answer:

    (a) ls, list directory contents:

    It displays the names of the files and directories in a directory.

    ```bash
    ls                    # names only, in columns
    ls -l                 # long listing: permissions, links, owner, group, size, date
    ls -a                 # including hidden files, whose names begin with a dot
    ls -la                # long listing including hidden files
    ls -lh                # sizes in human readable form, such as 4.0K or 2.3M
    ls -lt                # sorted by modification time, newest first
    ls -lS                # sorted by size, largest first
    ls -R                 # recursive, including sub-directories
    ls /var/log           # list a specific directory
    ls *.txt              # list only the text files
    ```

    Example:
    ```bash
    $ ls -lh
    total 24K
    drwxr-xr-x 2 rahim staff 4.0K Aug 30 10:00 documents
    -rw-r--r-- 1 rahim staff 2.0K Aug 30 10:15 report.txt
    -rwxr-xr-x 1 rahim staff 1.2K Aug 29 16:45 backup.sh
    ```

    (b) grep, global regular expression print:

    It searches for a pattern in a file or in the output of another command and prints the lines that match.

    ```bash
    grep "pattern" file           # basic search
    grep -i "pattern" file        # case insensitive
    grep -n "pattern" file        # show line numbers
    grep -r "pattern" /path       # search recursively through a directory
    grep -v "pattern" file        # invert: show lines that do NOT match
    grep -c "pattern" file        # count the matching lines
    grep -w "word" file           # match whole words only
    grep -l "pattern" *.txt       # print only the names of matching files
    grep -A 2 -B 2 "pattern" file # show two lines of context on each side
    grep -E "error|fail" file     # extended regex: either word
    ```

    Example:
    ```bash
    $ grep -in "error" /var/log/syslog
    45:Aug 30 09:12:33 server kernel: ERROR: device not found
    128:Aug 30 10:45:02 server app: Error connecting to database

    $ ps aux | grep nginx
    root      1234  0.0  0.1  12345  6789 ?  Ss  09:00  0:00 nginx: master process
    ```

    (c) ssh, secure shell:

    It opens an encrypted login session on a remote machine, and it is the standard way to administer a server over a network.

    ```bash
    ssh username@hostname             # log in to a remote machine
    ssh rahim@192.168.1.50            # by IP address
    ssh -p 2222 rahim@server.com      # a non-standard port
    ssh -i ~/.ssh/mykey.pem user@host # authenticate with a private key file
    ssh user@host "df -h"             # run one command and return
    ssh -X user@host                  # forward the graphical display
    ssh -L 8080:localhost:80 user@host  # local port forwarding (tunnel)
    ```

    Example:
    ```bash
    $ ssh rahim@192.168.1.50
    rahim@192.168.1.50's password:
    Welcome to Ubuntu 22.04.3 LTS
    Last login: Fri Aug 29 18:20:11 2026 from 192.168.1.10
    rahim@server:~$
    ```

    Setting up key-based login, which is both more convenient and more secure than a password:
    ```bash
    ssh-keygen -t rsa -b 4096              # generate a key pair
    ssh-copy-id rahim@192.168.1.50         # install the public key on the server
    ssh rahim@192.168.1.50                 # now logs in without a password
    ```

    Related commands in the same family:
    ```bash
    scp file.txt user@host:/path/          # copy a file to a remote machine
    scp user@host:/path/file.txt .         # copy a file from a remote machine
    sftp user@host                         # interactive secure file transfer
    rsync -avz -e ssh dir/ user@host:/dir/ # efficient synchronisation over ssh
    ```

    Why ssh replaced telnet: telnet sends everything, including the password, in plain text, so anyone on the network can read it. ssh encrypts the entire session and also verifies the identity of the server through its host key.
24. **(a) Check if the website of ‘TGTDCL’. (b) How to create folder in sub-directory?** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 823 (ET: BUET)]*


    Answer:

    (a) Check whether the website of TGTDCL is reachable:

    ```bash
    ping www.tgtdcl.gov.bd            # test basic connectivity
    ping -c 4 www.tgtdcl.gov.bd       # send only 4 packets and stop
    ```
    A reply means the host is reachable at the network level.

    Other checks, each answering a different question:
    ```bash
    curl -I https://www.tgtdcl.gov.bd       # fetch only the HTTP headers
    curl -Is https://www.tgtdcl.gov.bd | head -1   # just the status line
    wget --spider https://www.tgtdcl.gov.bd # check existence without downloading
    nslookup www.tgtdcl.gov.bd              # resolve the domain to an IP address
    dig www.tgtdcl.gov.bd                   # detailed DNS query
    host www.tgtdcl.gov.bd                  # simple DNS lookup
    traceroute www.tgtdcl.gov.bd            # show the route packets take
    telnet www.tgtdcl.gov.bd 80             # test whether port 80 is open
    nc -zv www.tgtdcl.gov.bd 443            # test port 443 with netcat
    ```

    Sample output:
    ```bash
    $ ping -c 4 www.tgtdcl.gov.bd
    PING www.tgtdcl.gov.bd (203.112.xxx.xxx) 56(84) bytes of data.
    64 bytes from 203.112.xxx.xxx: icmp_seq=1 ttl=54 time=12.3 ms
    64 bytes from 203.112.xxx.xxx: icmp_seq=2 ttl=54 time=11.9 ms
    --- www.tgtdcl.gov.bd ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3005ms
    ```

    A useful point for an answer: ping failing does not prove the website is down. Many servers and firewalls block ICMP while still serving web traffic normally. The reliable test for a website is therefore curl -I, which checks the HTTP service itself, and a status line of HTTP/1.1 200 OK confirms the site is working.

    (b) How to create a folder in a sub-directory:

    ```bash
    mkdir parent/child                    # create child inside an existing parent
    mkdir -p parent/child/grandchild      # create the whole path at once
    ```
    The option -p means "parents": it creates every missing directory in the path and does not complain if a directory already exists. Without it, mkdir fails if the parent does not exist.

    Examples:
    ```bash
    mkdir -p /home/admin/projects/2026/reports
    mkdir -p documents/{invoices,receipts,contracts}   # several at once, brace expansion
    mkdir -p project/{src,bin,docs,tests}
    ```

    Verifying:
    ```bash
    ls -R project          # recursive listing
    tree project           # tree view, if tree is installed
    ```
    Output of tree:
    ```
    project
    ├── bin
    ├── docs
    ├── src
    └── tests
    ```

    Setting permissions at the same time:
    ```bash
    mkdir -p -m 755 parent/child
    ```
25. **Write a Linux command to revoke permission from no user but owner from a file “jdcl.txt”.** *[JGTDSL Assistant Engineer (CSE) 08.10.2021 compact it 859 (ET: N/A)]*


    Answer: The requirement is that the owner keeps full access while the group and all other users have no access at all.

    ```bash
    chmod 700 jdcl.txt
    ```

    Explanation of 700:
    - 7 for the owner = 4 (read) + 2 (write) + 1 (execute) = rwx
    - 0 for the group = no permission at all
    - 0 for others = no permission at all
    The resulting permission string is -rwx------.

    If the file is a document rather than a program, execute is unnecessary and 600 is the more correct choice:
    ```bash
    chmod 600 jdcl.txt        # -rw------- : read and write for the owner only
    ```

    Symbolic forms that achieve the same result:
    ```bash
    chmod go-rwx jdcl.txt     # remove all permissions from group and others
    chmod g=,o= jdcl.txt      # set group and others to nothing
    chmod u=rwx,go= jdcl.txt  # set the owner explicitly and clear the rest
    chmod og-rwx jdcl.txt     # same as the first form
    ```

    Verifying:
    ```bash
    $ chmod 700 jdcl.txt
    $ ls -l jdcl.txt
    -rwx------ 1 rahim staff 2048 Aug 30 11:30 jdcl.txt
    ```
    The seven dashes after rwx confirm that neither the group nor others have any access.

    A practical point worth adding: the permissions on the file are not the whole story. To open a file, a user must also have execute permission on every directory along its path. If /home/rahim is world-readable and world-executable, another user cannot read jdcl.txt itself but can see that it exists. To hide it completely, the containing directory should also be restricted:
    ```bash
    chmod 700 /home/rahim/private
    ```

    Note also that the root user is unaffected by any of this and can read the file regardless. Genuine secrecy from the administrator requires encryption, for example with gpg.
26. **Linux এর ক্ষেত্রে User Creation এর কমান্ড লিখ?** *[PGCB Sub-Assistant Engineer (CSE) 30.09.2021 compact it 866 (ET: BUET)]*


    Answer: Linux এ নতুন ব্যবহারকারী তৈরির প্রধান কমান্ড দুটি: useradd এবং adduser।

    useradd (নিম্নস্তরের কমান্ড, সব ডিস্ট্রিবিউশনে আছে):
    ```bash
    sudo useradd rahim                          # ব্যবহারকারী তৈরি
    sudo useradd -m rahim                       # হোম ডিরেক্টরিসহ তৈরি
    sudo useradd -m -s /bin/bash rahim          # শেল নির্ধারণ করে
    sudo useradd -m -G sudo,developers rahim    # অতিরিক্ত গ্রুপে যুক্ত করে
    sudo useradd -m -c "Rahim Uddin" rahim      # পূর্ণ নাম যুক্ত করে
    sudo useradd -e 2026-12-31 rahim            # মেয়াদ শেষের তারিখ নির্ধারণ
    sudo useradd -r sysuser                     # সিস্টেম অ্যাকাউন্ট
    ```
    গুরুত্বপূর্ণ: useradd দিয়ে তৈরির পর অবশ্যই পাসওয়ার্ড নির্ধারণ করতে হয়, নইলে অ্যাকাউন্টটি লক থাকে।
    ```bash
    sudo passwd rahim
    ```

    adduser (Debian ও Ubuntu তে ব্যবহৃত সহজ, ইন্টারেক্টিভ কমান্ড):
    ```bash
    sudo adduser rahim
    ```
    এটি স্বয়ংক্রিয়ভাবে হোম ডিরেক্টরি তৈরি করে, ডিফল্ট শেল নির্ধারণ করে, পাসওয়ার্ড চায় এবং পূর্ণ নাম ও অন্যান্য তথ্য জিজ্ঞাসা করে। নতুনদের জন্য এটিই সুপারিশযোগ্য।

    সংশ্লিষ্ট কমান্ডসমূহ:
    ```bash
    sudo passwd rahim                  # পাসওয়ার্ড নির্ধারণ বা পরিবর্তন
    sudo usermod -aG sudo rahim        # sudo গ্রুপে যুক্ত করা (-a না দিলে আগের গ্রুপ মুছে যাবে)
    sudo usermod -s /bin/zsh rahim     # শেল পরিবর্তন
    sudo usermod -L rahim              # অ্যাকাউন্ট লক করা
    sudo usermod -U rahim              # আনলক করা
    sudo userdel rahim                 # ব্যবহারকারী মুছে ফেলা
    sudo userdel -r rahim              # হোম ডিরেক্টরিসহ মুছে ফেলা
    sudo groupadd developers           # নতুন গ্রুপ তৈরি
    id rahim                           # UID, GID ও গ্রুপ দেখা
    groups rahim                       # গ্রুপের তালিকা
    su - rahim                         # ওই ব্যবহারকারী হিসেবে লগইন
    ```

    সংশ্লিষ্ট ফাইলসমূহ:
    - /etc/passwd — ব্যবহারকারীর নাম, UID, GID, হোম ডিরেক্টরি ও শেল
    - /etc/shadow — এনক্রিপ্ট করা পাসওয়ার্ড ও মেয়াদ সংক্রান্ত তথ্য
    - /etc/group — গ্রুপের তালিকা
    - /etc/skel/ — নতুন হোম ডিরেক্টরিতে যে ফাইলগুলো অনুলিপি হয়

    /etc/passwd এর একটি লাইনের গঠন:
    ```
    rahim:x:1001:1001:Rahim Uddin:/home/rahim:/bin/bash
      |   |   |    |       |            |          |
      |   |   |    |       |            |          +-- লগইন শেল
      |   |   |    |       |            +------------- হোম ডিরেক্টরি
      |   |   |    |       +-------------------------- পূর্ণ নাম
      |   |   |    +---------------------------------- গ্রুপ আইডি
      |   |   +--------------------------------------- ব্যবহারকারী আইডি
      |   +------------------------------------------- পাসওয়ার্ড (x মানে shadow ফাইলে)
      +----------------------------------------------- ব্যবহারকারীর নাম
    ```

    useradd ও adduser এর পার্থক্য: useradd একটি নিম্নস্তরের বাইনারি এবং সব লিনাক্সে পাওয়া যায়, কিন্তু কিছুই স্বয়ংক্রিয়ভাবে করে না। adduser একটি পার্ল স্ক্রিপ্ট, কেবল ডেবিয়ানভিত্তিক সিস্টেমে থাকে এবং সব কাজ ইন্টারেক্টিভভাবে সম্পন্ন করে।
27. **Write Linux command for following question: a) Create a file apscl.txt in current location. b) Given permission to all read write and execute to the file apscl.txt c) Read first 7 lines from apscl.txt file d) Delete the file apscl.txt** *[APSCL Assistant Engineer (ICT/MIS) 12.11.2021 compact it 867-868 (ET: BUET)]*


    Answer:

    (a) Create a file apscl.txt in the current location:
    ```bash
    touch apscl.txt
    ```
    Alternatives:
    ```bash
    > apscl.txt                  # create an empty file by redirection
    cat > apscl.txt              # create and type content, ending with Ctrl+D
    echo "some text" > apscl.txt # create with one line of content
    nano apscl.txt               # create and edit in the nano editor
    vi apscl.txt                 # create and edit in vi
    ```
    touch also updates the timestamp of a file that already exists, without changing its content.

    (b) Give read, write and execute permission to all for the file apscl.txt:
    ```bash
    chmod 777 apscl.txt
    ```
    Explanation: each digit is the sum of read (4), write (2) and execute (1), given for owner, group and others. So 7 = 4 + 2 + 1 = rwx for every class, and the permission string becomes -rwxrwxrwx.

    Symbolic equivalents:
    ```bash
    chmod a+rwx apscl.txt        # add rwx for all
    chmod ugo+rwx apscl.txt      # the same, spelled out
    ```
    Verification:
    ```bash
    $ ls -l apscl.txt
    -rwxrwxrwx 1 rahim staff 0 Aug 30 12:00 apscl.txt
    ```
    Security note worth stating: 777 means any user on the system may modify or delete the file, so it should never be used on a real server. For a data file 644 is normal, and for a script 755.

    (c) Read the first 7 lines of apscl.txt:
    ```bash
    head -n 7 apscl.txt
    ```
    Alternatives:
    ```bash
    head -7 apscl.txt            # older short form
    sed -n '1,7p' apscl.txt      # using sed
    awk 'NR<=7' apscl.txt        # using awk
    ```

    (d) Delete the file apscl.txt:
    ```bash
    rm apscl.txt
    ```
    Alternatives:
    ```bash
    rm -i apscl.txt              # ask for confirmation
    rm -f apscl.txt              # force, no prompt even if write-protected
    unlink apscl.txt             # removes a single file, cannot take options
    ```
    There is no recycle bin, so the deletion is immediate and permanent.

    The four commands in sequence:
    ```bash
    touch apscl.txt              # create
    chmod 777 apscl.txt          # permissions
    head -n 7 apscl.txt          # read the first 7 lines
    rm apscl.txt                 # delete
    ```
28. **How do you define bash?** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 875 (ET: BUET)]*


    Answer: Bash stands for Bourne Again SHell. It is a command-line interpreter, that is a program that reads commands typed by the user or read from a file, interprets them, and asks the kernel to carry them out. It is the default login shell on most Linux distributions.

    Its place in the system: the kernel manages the hardware, and the shell is the layer between the user and the kernel. The user types a command, the shell parses it, finds the corresponding program, creates a process for it, passes the arguments and returns the result.

    History: it was written by Brian Fox in 1989 for the GNU Project as a free replacement for the original Bourne shell (sh) written by Stephen Bourne in 1979. The name is a pun: it is the Bourne shell born again.

    Main features:
    - Command execution: it runs both built-in commands, such as cd and echo, and external programs found through the PATH variable.
    - Command history: previous commands are stored and can be recalled with the arrow keys, with Ctrl+R for a reverse search, or with the history command.
    - Tab completion: pressing Tab completes file names, directory names, command names and, with extensions, options.
    - Shell scripting: a sequence of commands can be saved in a file and executed as a program, with variables, conditions, loops, functions and arguments.
    - Input and output redirection: > to write to a file, >> to append, < to read from a file, and 2> for the error stream.
    - Pipes: | sends the output of one command as the input of the next, which is the central idea of the Unix philosophy.
    - Variables and environment: local variables, exported environment variables such as PATH, HOME and USER, and command substitution with $(...).
    - Job control: running a command in the background with &, and managing jobs with jobs, fg and bg.
    - Wildcards (globbing): *, ? and [...] to match many file names at once.
    - Aliases and functions, defined in ~/.bashrc for convenience.

    Configuration files:
    - /etc/profile, the system-wide settings for login shells
    - ~/.bash_profile or ~/.profile, run for a login shell
    - ~/.bashrc, run for every interactive shell, where aliases and prompts are normally defined
    - ~/.bash_history, the record of commands
    - ~/.bash_logout, run on exit

    A simple script showing the main constructs:
    ```bash
    #!/bin/bash
    # the first line, called the shebang, tells the system which interpreter to use

    NAME="Rahim"                       # a variable
    echo "Hello, $NAME"

    if [ -f "/etc/passwd" ]; then      # a condition
        echo "The password file exists"
    fi

    for i in 1 2 3; do                 # a loop
        echo "Iteration $i"
    done

    count=$(ls | wc -l)                # command substitution
    echo "There are $count entries here"
    ```

    Running it:
    ```bash
    chmod +x script.sh
    ./script.sh
    ```

    Other shells, for comparison: sh (the original Bourne shell), csh and tcsh (C-like syntax), ksh (the Korn shell), zsh (feature-rich, now the default on macOS) and fish (designed for friendliness). Bash remains the most widely used, and almost all system scripts on Linux are written for it. The current shell can be found with echo $SHELL, and the list of installed shells is in /etc/shells.
29. **Linux Command: Write a code for listing home directory files with all details and human readable size got to Home directory, list directory files with 10-15 are display only 10^{\text{th}} to 15^{\text{th}} lines of words of them. Write the instructions in a way that they execute together and shows the result.** *[BGDCL (Bakhrabad Gas) Assistant Engineer (CSE) 19.11.2021 compact it 878 (ET: BUET)]*


    Answer: The three actions are to go to the home directory, list its contents in long form with human-readable sizes, and show only lines 10 to 15 of that listing. They are joined into a single command line so that they execute together.

    ```bash
    cd ~ && ls -lh | sed -n '10,15p'
    ```

    Explanation:
    - cd ~ changes to the home directory. The tilde is shorthand for $HOME.
    - && runs the next command only if the previous one succeeded, which is the safe way to chain commands.
    - ls -lh gives a long listing (-l) with human-readable sizes (-h), so 2048 appears as 2.0K.
    - The pipe sends that listing to sed.
    - sed -n '10,15p' prints only lines 10 to 15; -n suppresses the automatic printing of every line.

    Including hidden files as well:
    ```bash
    cd ~ && ls -lah | sed -n '10,15p'
    ```

    Alternative ways to select lines 10 to 15:
    ```bash
    cd ~ && ls -lh | head -n 15 | tail -n 6      # take the first 15, then the last 6
    cd ~ && ls -lh | awk 'NR>=10 && NR<=15'      # using the record number in awk
    cd ~ && ls -lh | tail -n +10 | head -n 6     # start at line 10, take 6 lines
    ```
    Note that lines 10 to 15 inclusive is six lines, not five, so tail -n 6 and head -n 6 are correct.

    Other ways of joining commands, and how they differ:
    ```bash
    cmd1 ; cmd2      # run cmd2 whatever happened to cmd1
    cmd1 && cmd2     # run cmd2 only if cmd1 succeeded (exit status 0)
    cmd1 || cmd2     # run cmd2 only if cmd1 failed
    cmd1 | cmd2      # send the output of cmd1 as the input of cmd2
    ```
    Here && is correct, because listing a directory we failed to enter would be meaningless.

    Saving the result to a file at the same time:
    ```bash
    cd ~ && ls -lh | sed -n '10,15p' | tee output.txt
    ```
    tee prints to the screen and writes to the file simultaneously.

    Sample output:
    ```
    -rw-r--r--  1 rahim staff  2.0K Aug 30 10:15 notes.txt
    drwxr-xr-x  3 rahim staff  4.0K Aug 28 16:45 pictures
    -rwxr-xr-x  1 rahim staff  1.2K Aug 29 16:45 backup.sh
    -rw-r--r--  1 rahim staff  15K  Aug 27 11:30 report.pdf
    drwxr-xr-x  2 rahim staff  4.0K Aug 26 09:00 videos
    -rw-r--r--  1 rahim staff  512   Aug 25 14:20 todo.md
    ```
30. **(i) Linux command for showing all files including the hidden files inside the home directory.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*


    Answer: The command to show all files, including hidden files, inside the home directory:

    ```bash
    ls -a ~
    ```

    Forms and variations:
    ```bash
    ls -a ~              # all entries in the home directory
    ls -a $HOME          # the same, using the environment variable
    ls -a /home/username # the same, by absolute path
    cd ~ && ls -a        # change to the home directory first, then list
    ls -la ~             # long listing with permissions, owner, size and date
    ls -lah ~            # the same, with human readable sizes
    ls -A ~              # all hidden files but not the . and .. entries
    ls -d ~/.*           # only the hidden entries
    ```

    Sample output:
    ```
    $ ls -la ~
    total 64
    drwxr-xr-x 15 rahim staff  4096 Aug 30 12:00 .
    drwxr-xr-x  4 root  root   4096 Aug 20 09:00 ..
    -rw-------  1 rahim staff  3421 Aug 30 11:45 .bash_history
    -rw-r--r--  1 rahim staff   220 Aug 20 09:00 .bash_logout
    -rw-r--r--  1 rahim staff  3771 Aug 20 09:00 .bashrc
    drwx------  2 rahim staff  4096 Aug 25 14:20 .ssh
    -rw-r--r--  1 rahim staff   807 Aug 20 09:00 .profile
    drwxr-xr-x  2 rahim staff  4096 Aug 28 16:45 Documents
    drwxr-xr-x  2 rahim staff  4096 Aug 26 09:00 Downloads
    ```

    Explanation:
    - In Linux a file is hidden simply because its name begins with a dot. There is no hidden attribute as there is in Windows, so renaming a file to begin with a dot hides it and removing the dot reveals it.
    - The entry . is the directory itself and .. is its parent. The option -A excludes these two, which is usually more useful.
    - Hidden files in the home directory are almost all configuration files: .bashrc for shell settings, .profile for login settings, .ssh for keys and known hosts, .gitconfig for Git, and .config for a great many applications.
    - The tilde ~ is expanded by the shell to the path of the current user's home directory, and ~username expands to another user's home directory.

    Related commands:
    ```bash
    ls -a ~ | wc -l          # count the entries
    find ~ -maxdepth 1 -name ".*"   # hidden entries using find
    du -sh ~/.[!.]*          # the size of each hidden item
    tree -a -L 1 ~           # tree view of the top level, including hidden entries
    ```
31. **(ii) Linux command for showing page size, disk space in a human-readable format.** *[NESCO Assistant Manager (ICT) 2021 compact it 907 (ET: BUET)]*


    Answer: Two separate pieces of information are asked for, the page size and the disk space.

    Page size (the size of a memory page used by the kernel):
    ```bash
    getconf PAGESIZE           # prints the page size in bytes
    getconf PAGE_SIZE          # the same, alternative name
    ```
    Sample output:
    ```
    4096
    ```
    That is 4096 bytes, which is 4 KB, the standard page size on most x86-64 Linux systems.

    Other ways to obtain it:
    ```bash
    getconf -a | grep -i page       # all page-related configuration values
    cat /proc/meminfo | grep -i huge # huge page settings
    python3 -c "import os; print(os.sysconf('SC_PAGE_SIZE'))"
    ```
    The page is the unit in which the memory management unit maps virtual addresses to physical frames, so the page size determines the granularity of paging and the size of the page table.

    Disk space in human readable form:
    ```bash
    df -h
    ```
    The option -h means human readable, so sizes appear as 20G rather than as 20971520 blocks.

    Sample output:
    ```
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/sda1        50G   28G   20G  59% /
    /dev/sda2       100G   45G   50G  48% /home
    tmpfs           3.9G  1.2M  3.9G   1% /dev/shm
    ```

    Related forms:
    ```bash
    df -h /home            # only one file system
    df -Th                 # also show the file system type
    df -i                  # inode usage instead of block usage
    du -sh /var/log        # the size of one directory
    du -sh * | sort -rh    # the size of everything here, largest first
    du -h --max-depth=1 /  # size of each top-level directory
    lsblk                  # block devices and partitions in a tree
    free -h                # RAM and swap, also human readable
    ```

    The distinction between df and du, which is often asked: df reports what the file system says about free and used space, while du adds up the sizes of the files it can see. The two can disagree when a deleted file is still held open by a running process, because df counts the space as used while du no longer sees the file. Restarting the process, or rebooting, then releases the space.
32. **A home directory called SGFL exists on your computer. Write a Linux command to create a link called “SGFL-Link” in the home directory.** *[SGFL Assistant General Engineer 2021 compact it 937 (ET: BUET)]*


    Answer: A link is created with the ln command. The question describes a directory, and a hard link cannot be made to a directory, so a symbolic (soft) link must be used.

    ```bash
    ln -s ~/SGFL ~/SGFL-Link
    ```

    Explanation:
    - ln creates a link.
    - The option -s makes it symbolic, which is a small file containing the path of the target rather than a second name for the same inode.
    - The first argument is the target (the existing directory) and the second is the name of the link to be created.

    Verification:
    ```bash
    $ ls -l ~
    drwxr-xr-x 2 rahim staff 4096 Aug 30 12:00 SGFL
    lrwxrwxrwx 1 rahim staff   17 Aug 30 12:05 SGFL-Link -> /home/rahim/SGFL
    ```
    The l at the start of the permission string identifies it as a link, and the arrow shows what it points to.

    Using it:
    ```bash
    cd ~/SGFL-Link          # enters the real SGFL directory
    ls ~/SGFL-Link          # lists the contents of SGFL
    ```

    Other forms:
    ```bash
    ln -s /full/path/to/SGFL /home/rahim/SGFL-Link   # absolute paths, safer
    ln -sf target linkname                            # replace an existing link
    ln -sn target linkname                            # do not follow an existing link
    unlink ~/SGFL-Link                                # remove the link
    rm ~/SGFL-Link                                    # also removes the link only
    readlink ~/SGFL-Link                              # show where it points
    readlink -f ~/SGFL-Link                           # resolve it fully
    ```

    Difference between a symbolic link and a hard link:

    | Point | Symbolic (soft) link | Hard link |
    |---|---|---|
    | Command | ln -s target link | ln target link |
    | What it stores | The path of the target | A second directory entry for the same inode |
    | Inode | Its own, different from the target | The same as the target |
    | Directories | Allowed | Not allowed |
    | Across file systems | Allowed | Not allowed |
    | If the target is deleted | The link is left dangling and stops working | The data survives until the last hard link is removed |
    | Size | A few bytes, the length of the path | Not applicable; it is the same file |
    | Shown by ls -l | lrwxrwxrwx with an arrow | Indistinguishable from an ordinary file |

    Warning about deleting a link to a directory: use rm SGFL-Link or unlink SGFL-Link, never rm -r SGFL-Link/ with a trailing slash, because that would follow the link and delete the contents of the real directory.
33. **Write Shell command which make a folder name ‘A’ with read permission access only.** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*


    Answer: The requirement is a folder named A that has read access only, that is no write and no execute permission.

    ```bash
    mkdir A && chmod 444 A
    ```
    Or in two steps:
    ```bash
    mkdir A
    chmod 444 A
    ```
    Or setting the permission at creation:
    ```bash
    mkdir -m 444 A
    ```

    Explanation of 444: each digit is the sum of read (4), write (2) and execute (1). A value of 4 for each of owner, group and others gives r--r--r--, that is read only for everyone.

    Verification:
    ```bash
    $ ls -ld A
    dr--r--r-- 2 rahim staff 4096 Aug 30 12:10 A
    ```
    The option -d is important: without it, ls -l A would list the contents of A rather than A itself.

    An important practical point about directories: for a directory the three bits mean something different from what they mean for a file.
    - r allows the names inside to be listed.
    - w allows entries to be created, renamed or deleted inside it.
    - x allows the directory to be entered with cd and allows a named file inside it to be opened.

    Because execute has been removed, the directory cannot be entered at all:
    ```bash
    $ cd A
    bash: cd: A: Permission denied
    $ ls A
    ls: cannot access 'A/file.txt': Permission denied
    ```
    ls can print the names, because r is present, but it cannot read the details of the entries, because that requires x. This is exactly what "read permission access only" means, and stating it shows that the difference between file and directory permissions is understood.

    If the intention is that the contents should be readable but not modifiable, which is what is usually wanted in practice, execute must be kept:
    ```bash
    chmod 555 A          # r-xr-xr-x : may enter and read, may not create or delete
    ```

    Symbolic forms:
    ```bash
    chmod a=r A          # exactly read for all
    chmod a-wx A         # remove write and execute from all
    chmod u=r,g=r,o=r A  # spelled out
    ```

    Restoring normal permissions:
    ```bash
    chmod 755 A          # rwx for the owner, r-x for others
    ```
34. **Write Shell command which copy folder ‘A’ all information into folder ‘P’. Folder ‘A’ and folder ‘P’s parent folder is same.** *[Janata Bank Assistant System Administrator 2021 compact it 938-939 (ET: N/A)]*


    Answer: Folder A is to be copied, with all of its contents, into folder P, and both share the same parent directory.

    ```bash
    cp -r A P
    ```
    This creates P/A containing everything that was in A.

    Better forms in practice:
    ```bash
    cp -a A P            # archive mode: preserves permissions, ownership,
                         # timestamps and symbolic links
    cp -rv A P           # verbose: names each file as it is copied
    cp -ri A P           # ask before overwriting anything
    cp -ru A P           # copy only files that are newer, useful for updating
    ```

    If the contents of A are to be placed directly inside P, rather than inside P/A:
    ```bash
    cp -r A/. P/         # copies the contents, including hidden files
    cp -r A/* P/         # copies the contents but misses hidden files
    ```
    The form A/. is the correct one, because A/* is expanded by the shell and the shell does not include names beginning with a dot.

    Using rsync, which is preferred for large folders:
    ```bash
    rsync -av A P/            # creates P/A
    rsync -av A/ P/           # copies the contents of A directly into P
    rsync -av --progress A P/ # with a progress display
    ```
    In rsync the trailing slash on the source is significant, which is a common source of mistakes. rsync also copies only what has changed and can resume after an interruption.

    Full sequence with verification:
    ```bash
    $ ls
    A  P
    $ cp -r A P
    $ ls P
    A
    $ ls -R P
    P:
    A

    P/A:
    file1.txt  file2.txt  subdir
    ```

    Checking that the copy is complete:
    ```bash
    du -sh A P/A         # compare the sizes
    diff -r A P/A        # report any difference; silence means they are identical
    ```

    Why -r is essential: without it, cp refuses to copy a directory and prints "cp: -r not specified; omitting directory 'A'". The letter R may be used instead of r, and -a implies -r as well as preservation of attributes.
35. **৩. লিনাক্স এর প্রিন্ট কমান্ডটি লিখ?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*


    Answer: লিনাক্সে প্রিন্ট করার প্রধান কমান্ড lp এবং lpr।

    ```bash
    lp filename.txt                  # ডিফল্ট প্রিন্টারে প্রিন্ট করা
    lpr filename.txt                 # একই কাজ, BSD ধারার কমান্ড
    lp -d printer_name filename.txt  # নির্দিষ্ট প্রিন্টারে পাঠানো
    lp -n 3 filename.txt             # তিন কপি প্রিন্ট
    lp -o sides=two-sided-long-edge file.pdf   # দুই পাশে প্রিন্ট
    lp -o media=A4 file.pdf          # কাগজের আকার নির্ধারণ
    ```

    সংশ্লিষ্ট কমান্ডসমূহ:
    ```bash
    lpstat -p              # উপলব্ধ প্রিন্টারের তালিকা ও অবস্থা
    lpstat -d              # ডিফল্ট প্রিন্টার কোনটি
    lpstat -o              # প্রিন্ট কিউতে থাকা কাজের তালিকা
    lpq                    # প্রিন্ট কিউ দেখা
    cancel job_id          # একটি প্রিন্ট কাজ বাতিল করা
    lprm job_id            # একই কাজ
    cancel -a              # সব কাজ বাতিল
    lpadmin -d printer     # ডিফল্ট প্রিন্টার নির্ধারণ
    ```

    টার্মিনালে লেখা প্রদর্শনের কমান্ড (যদি প্রশ্নটি সেই অর্থে হয়):
    ```bash
    echo "Hello World"          # একটি লাইন প্রদর্শন
    printf "%s\n" "Hello"       # ফরম্যাট নিয়ন্ত্রণসহ প্রদর্শন
    cat filename                # ফাইলের সম্পূর্ণ বিষয়বস্তু প্রদর্শন
    less filename               # পৃষ্ঠা ধরে ধরে প্রদর্শন
    ```

    উল্লেখযোগ্য: লিনাক্সে প্রিন্টিং ব্যবস্থার নাম CUPS (Common Unix Printing System)। lp ও lpr কমান্ড দুটি এর সঙ্গেই কাজ করে। ওয়েব ব্রাউজারে http://localhost:631 ঠিকানায় গিয়ে গ্রাফিক্যাল ইন্টারফেসেও প্রিন্টার ব্যবস্থাপনা করা যায়।

    lp ও lpr এর পার্থক্য: lp এসেছে System V ধারা থেকে এবং lpr এসেছে BSD ধারা থেকে। আধুনিক লিনাক্সে দুটিই CUPS এর সঙ্গে কাজ করে, তবে অপশনের সিনট্যাক্স ভিন্ন। যেমন কপি সংখ্যা নির্ধারণে lp -n 3 এবং lpr -#3 লিখতে হয়।
36. **৬. ফোল্ডার রিমুভ করার জন্য নিচেরর কোনটি লিনাক্স কমান্ড হিসেবে ব্যবহৃত হয়?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*


    Answer: ফোল্ডার বা ডিরেক্টরি রিমুভ করার জন্য লিনাক্স কমান্ড rmdir এবং rm -r।

    rmdir — কেবল খালি ডিরেক্টরি মুছতে পারে:
    ```bash
    rmdir dirname                  # ডিরেক্টরিটি খালি হলে মুছে যাবে
    rmdir dir1 dir2 dir3           # একাধিক খালি ডিরেক্টরি
    rmdir -p a/b/c                 # c মুছে তারপর b, তারপর a, যদি খালি হয়
    rmdir --ignore-fail-on-non-empty dirname
    ```
    ডিরেক্টরিতে কিছু থাকলে ত্রুটি দেখাবে:
    ```
    rmdir: failed to remove 'dirname': Directory not empty
    ```

    rm -r — ডিরেক্টরি ও তার ভেতরের সবকিছু মুছে ফেলে:
    ```bash
    rm -r dirname                  # পুনরাবৃত্ত মুছে ফেলা
    rm -rf dirname                 # জোর করে, কোনো প্রশ্ন ছাড়াই
    rm -ri dirname                 # প্রতিটি জিনিস সম্পর্কে জিজ্ঞাসা করবে
    rm -rv dirname                 # কী কী মুছল তা দেখাবে
    ```

    অপশনগুলোর অর্থ:
    - -r বা -R: recursive, অর্থাৎ ডিরেক্টরির ভেতরে ঢুকে সবকিছু মুছবে।
    - -f: force, অর্থাৎ লিখতে বাধা থাকলেও মুছবে এবং কোনো সতর্কবার্তা দেবে না।
    - -i: interactive, প্রতিটি মুছে ফেলার আগে অনুমতি চাইবে।
    - -v: verbose, কী মুছল তা দেখাবে।

    গুরুত্বপূর্ণ সতর্কতা: লিনাক্সে কমান্ড লাইনে কোনো রিসাইকেল বিন নেই। rm -rf দিয়ে মোছা জিনিস ফিরে পাওয়া যায় না। বিশেষভাবে ভয়ংকর কমান্ড rm -rf / যা পুরো সিস্টেম মুছে ফেলার চেষ্টা করে। তাই মোছার আগে সবসময় pwd দিয়ে বর্তমান অবস্থান যাচাই করা উচিত এবং সম্ভব হলে প্রথমে ls দিয়ে দেখে নেওয়া উচিত কী মুছতে যাচ্ছি।

    নিরাপদ বিকল্প:
    ```bash
    ls dirname                     # আগে দেখে নেওয়া
    rm -ri dirname                 # প্রতিটির জন্য নিশ্চিত হওয়া
    mv dirname ~/.trash/           # মোছার বদলে সরিয়ে রাখা
    trash-put dirname              # trash-cli প্যাকেজ থাকলে রিসাইকেল বিনে পাঠানো
    ```

    তুলনা:

    | কমান্ড | খালি ডিরেক্টরি | অখালি ডিরেক্টরি | ঝুঁকি |
    |---|---|---|---|
    | rmdir | মুছবে | মুছবে না, ত্রুটি দেখাবে | কম |
    | rm -r | মুছবে | সবকিছুসহ মুছবে | বেশি |
    | rm -rf | মুছবে | প্রশ্ন ছাড়াই সব মুছবে | সবচেয়ে বেশি |
37. **৭. ফাইল কপি করার জন্য লিনাক্স কমান্ড কোনটি?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 941 (ET: N/A)]*


    Answer: ফাইল কপি করার লিনাক্স/ইউনিক্স কমান্ড cp (copy)।

    ```bash
    cp source.txt destination.txt          # ফাইল কপি করে নতুন নাম দেওয়া
    cp file.txt /home/user/documents/      # ফাইল অন্য ডিরেক্টরিতে কপি
    cp file1.txt file2.txt /backup/        # একাধিক ফাইল একসঙ্গে
    cp *.txt /backup/                      # সব টেক্সট ফাইল
    cp -r sourcedir destdir                # ডিরেক্টরি ও তার ভেতরের সবকিছু
    ```

    গুরুত্বপূর্ণ অপশনসমূহ:
    ```bash
    cp -r dir1 dir2       # recursive: ডিরেক্টরি কপি করতে অপরিহার্য
    cp -i file1 file2     # interactive: গন্তব্যে ফাইল থাকলে জিজ্ঞাসা করবে
    cp -f file1 file2     # force: বাধা থাকলেও কপি করবে
    cp -v file1 file2     # verbose: কী কপি হলো তা দেখাবে
    cp -u file1 file2     # update: উৎস নতুন হলেই কেবল কপি করবে
    cp -p file1 file2     # preserve: অনুমতি, মালিকানা ও সময় অক্ষুণ্ন রাখবে
    cp -a dir1 dir2       # archive: -r ও -p একসঙ্গে, ব্যাকআপের জন্য আদর্শ
    cp -n file1 file2     # গন্তব্যে ফাইল থাকলে কিছুই করবে না
    ```

    উদাহরণ:
    ```bash
    $ ls
    report.txt
    $ cp report.txt report_backup.txt
    $ ls
    report.txt  report_backup.txt
    ```

    সতর্কতা: cp ডিফল্টভাবে কোনো সতর্কবার্তা ছাড়াই গন্তব্যের বিদ্যমান ফাইলের ওপর লিখে দেয়। গুরুত্বপূর্ণ ফাইলের ক্ষেত্রে -i অপশন ব্যবহার করা উচিত। অনেক সিস্টেমে ~/.bashrc ফাইলে alias cp='cp -i' লিখে এটি স্থায়ীভাবে নিরাপদ করা হয়।

    বড় ফাইল বা ডিরেক্টরির জন্য rsync অধিক উপযোগী:
    ```bash
    rsync -av source/ destination/         # কেবল পরিবর্তিত অংশ কপি করে
    rsync -av --progress source/ dest/     # অগ্রগতি দেখায়
    rsync -avz src/ user@host:/dest/       # নেটওয়ার্কে কপি, সংকুচিত করে
    ```

    সংশ্লিষ্ট কমান্ড:
    - mv — সরানো ও নাম পরিবর্তন
    - rm — মুছে ফেলা
    - dd — ডিস্ক বা পার্টিশন বিট-বাই-বিট কপি
    - scp — নিরাপদভাবে দূরবর্তী মেশিনে কপি
38. **ফাইল কপি করার লিনাক্স/ইউনিক্স কমান্ড কি?** *[BPSC Ministry of Women and Children Affairs Computer Trainer 2021 compact it 944 (ET: N/A)]*


    Answer: ফাইল কপি করার লিনাক্স/ইউনিক্স কমান্ড cp (copy)।

    ```bash
    cp source.txt destination.txt          # ফাইল কপি করে নতুন নাম দেওয়া
    cp file.txt /home/user/documents/      # ফাইল অন্য ডিরেক্টরিতে কপি
    cp file1.txt file2.txt /backup/        # একাধিক ফাইল একসঙ্গে
    cp *.txt /backup/                      # সব টেক্সট ফাইল
    cp -r sourcedir destdir                # ডিরেক্টরি ও তার ভেতরের সবকিছু
    ```

    গুরুত্বপূর্ণ অপশনসমূহ:
    ```bash
    cp -r dir1 dir2       # recursive: ডিরেক্টরি কপি করতে অপরিহার্য
    cp -i file1 file2     # interactive: গন্তব্যে ফাইল থাকলে জিজ্ঞাসা করবে
    cp -f file1 file2     # force: বাধা থাকলেও কপি করবে
    cp -v file1 file2     # verbose: কী কপি হলো তা দেখাবে
    cp -u file1 file2     # update: উৎস নতুন হলেই কেবল কপি করবে
    cp -p file1 file2     # preserve: অনুমতি, মালিকানা ও সময় অক্ষুণ্ন রাখবে
    cp -a dir1 dir2       # archive: -r ও -p একসঙ্গে, ব্যাকআপের জন্য আদর্শ
    cp -n file1 file2     # গন্তব্যে ফাইল থাকলে কিছুই করবে না
    ```

    উদাহরণ:
    ```bash
    $ ls
    report.txt
    $ cp report.txt report_backup.txt
    $ ls
    report.txt  report_backup.txt
    ```

    সতর্কতা: cp ডিফল্টভাবে কোনো সতর্কবার্তা ছাড়াই গন্তব্যের বিদ্যমান ফাইলের ওপর লিখে দেয়। গুরুত্বপূর্ণ ফাইলের ক্ষেত্রে -i অপশন ব্যবহার করা উচিত। অনেক সিস্টেমে ~/.bashrc ফাইলে alias cp='cp -i' লিখে এটি স্থায়ীভাবে নিরাপদ করা হয়।

    বড় ফাইল বা ডিরেক্টরির জন্য rsync অধিক উপযোগী:
    ```bash
    rsync -av source/ destination/         # কেবল পরিবর্তিত অংশ কপি করে
    rsync -av --progress source/ dest/     # অগ্রগতি দেখায়
    rsync -avz src/ user@host:/dest/       # নেটওয়ার্কে কপি, সংকুচিত করে
    ```

    সংশ্লিষ্ট কমান্ড:
    - mv — সরানো ও নাম পরিবর্তন
    - rm — মুছে ফেলা
    - dd — ডিস্ক বা পার্টিশন বিট-বাই-বিট কপি
    - scp — নিরাপদভাবে দূরবর্তী মেশিনে কপি
39. **২. নেটওয়ার্ক কানেক্টিভিটি টেস্ট করার জন্য লিনাক্স কমান্ড লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 946 (ET: BUET)]*


    Answer: নেটওয়ার্ক কানেক্টিভিটি পরীক্ষা করার প্রধান কমান্ড ping।

    ```bash
    ping google.com              # ডোমেইন নামে পরীক্ষা
    ping 8.8.8.8                 # আইপি ঠিকানায় পরীক্ষা
    ping -c 4 google.com         # কেবল ৪টি প্যাকেট পাঠিয়ে থেমে যাবে
    ping -i 2 google.com         # ২ সেকেন্ড অন্তর প্যাকেট পাঠাবে
    ping -s 1000 google.com      # ১০০০ বাইটের প্যাকেট পাঠাবে
    ping6 ipv6.google.com        # IPv6 এর ক্ষেত্রে
    ```

    কার্যপ্রণালী: ping ICMP Echo Request প্যাকেট পাঠায় এবং গন্তব্য থেকে ICMP Echo Reply আসে কিনা দেখে। এর মাধ্যমে বোঝা যায় গন্তব্য সচল কিনা এবং কত সময়ে সাড়া দিচ্ছে।

    নমুনা আউটপুট:
    ```
    $ ping -c 4 google.com
    PING google.com (142.250.183.14) 56(84) bytes of data.
    64 bytes from 142.250.183.14: icmp_seq=1 ttl=115 time=18.2 ms
    64 bytes from 142.250.183.14: icmp_seq=2 ttl=115 time=17.9 ms
    64 bytes from 142.250.183.14: icmp_seq=3 ttl=115 time=18.5 ms
    64 bytes from 142.250.183.14: icmp_seq=4 ttl=115 time=18.1 ms

    --- google.com ping statistics ---
    4 packets transmitted, 4 received, 0% packet loss, time 3005ms
    rtt min/avg/max/mdev = 17.9/18.1/18.5/0.2 ms
    ```

    ফলাফলের ব্যাখ্যা:
    - 0% packet loss — সংযোগ ভালো
    - time — রাউন্ড ট্রিপ সময়; কম মানে দ্রুত সংযোগ
    - ttl — প্যাকেটটি আর কতগুলো রাউটার পার হতে পারবে
    - প্যাকেট লস থাকলে সংযোগ অস্থিতিশীল; সাড়া না এলে গন্তব্য অনুপলব্ধ বা ICMP বন্ধ

    অন্যান্য কানেক্টিভিটি পরীক্ষার কমান্ড:
    ```bash
    traceroute google.com        # প্যাকেট কোন কোন রাউটার হয়ে যাচ্ছে
    tracepath google.com         # একই কাজ, root অধিকার লাগে না
    mtr google.com               # ping ও traceroute একত্রে, লাইভ আপডেট
    nslookup google.com          # DNS সমাধান পরীক্ষা
    dig google.com               # বিস্তারিত DNS তথ্য
    host google.com              # সরল DNS অনুসন্ধান
    curl -I https://google.com   # HTTP সেবা সচল কিনা
    nc -zv google.com 443        # নির্দিষ্ট পোর্ট খোলা কিনা
    ss -tulnp                    # স্থানীয় মেশিনে খোলা পোর্টের তালিকা
    ip link show                 # নেটওয়ার্ক ইন্টারফেস সচল কিনা
    ip route                     # রাউটিং টেবিল ও ডিফল্ট গেটওয়ে
    ```

    সমস্যা নির্ণয়ের ধাপে ধাপে পদ্ধতি:
    ```bash
    ping 127.0.0.1               # ১. নিজের TCP/IP স্ট্যাক ঠিক আছে কিনা
    ping 192.168.1.1             # ২. গেটওয়ে বা রাউটার পর্যন্ত পৌঁছায় কিনা
    ping 8.8.8.8                 # ৩. ইন্টারনেটে পৌঁছায় কিনা
    ping google.com              # ৪. DNS কাজ করছে কিনা
    ```
    ৩ নম্বর কাজ করলেও ৪ নম্বর না করলে বুঝতে হবে সমস্যা DNS এ, ইন্টারনেট সংযোগে নয়।

    উল্লেখযোগ্য: অনেক সার্ভার নিরাপত্তার কারণে ICMP প্যাকেট বন্ধ রাখে, তাই ping এর উত্তর না আসা মানেই সার্ভার বন্ধ, তা নয়। সে ক্ষেত্রে curl বা nc দিয়ে নির্দিষ্ট পোর্ট পরীক্ষা করা উচিত।
40. **৩. IP Address বের করার জন্য লিনাক্স কমান্ড লিখ।** *[PGCL Sub Assistant Engineer (CSE) 2021 compact it 946 (ET: BUET)]*


    Answer: IP Address বের করার লিনাক্স কমান্ড:

    আধুনিক ও প্রধান কমান্ড:
    ```bash
    ip addr show           # সব ইন্টারফেসের বিস্তারিত তথ্য
    ip a                   # সংক্ষিপ্ত রূপ
    ip addr show eth0      # নির্দিষ্ট ইন্টারফেসের তথ্য
    ip -4 addr show        # কেবল IPv4 ঠিকানা
    ip -6 addr show        # কেবল IPv6 ঠিকানা
    ip -br addr show       # সংক্ষিপ্ত ও পরিচ্ছন্ন তালিকা
    ```

    নমুনা আউটপুট:
    ```
    $ ip -br addr show
    lo      UNKNOWN  127.0.0.1/8 ::1/128
    eth0    UP       192.168.1.105/24 fe80::a00:27ff:fe4e:66a1/64
    ```

    কেবল আইপি ঠিকানা পেতে:
    ```bash
    hostname -I            # সব আইপি ঠিকানা এক লাইনে
    hostname -i            # হোস্টনেমের সঙ্গে যুক্ত ঠিকানা
    ip route get 1.1.1.1 | awk '{print $7; exit}'   # কোন ঠিকানা দিয়ে বাইরে যাচ্ছে
    ```

    পুরোনো কমান্ড (net-tools প্যাকেজ, এখন অনেক ডিস্ট্রিবিউশনে ডিফল্টভাবে থাকে না):
    ```bash
    ifconfig               # সব ইন্টারফেস
    ifconfig eth0          # নির্দিষ্ট ইন্টারফেস
    ```

    পাবলিক আইপি (ইন্টারনেট থেকে যেভাবে দেখা যায়):
    ```bash
    curl ifconfig.me
    curl ipinfo.io/ip
    curl -s https://api.ipify.org
    wget -qO- ifconfig.me
    dig +short myip.opendns.com @resolver1.opendns.com
    ```

    সংশ্লিষ্ট নেটওয়ার্ক তথ্য:
    ```bash
    ip route               # রাউটিং টেবিল ও ডিফল্ট গেটওয়ে
    ip route show default  # কেবল ডিফল্ট গেটওয়ে
    ip link show           # ইন্টারফেসের অবস্থা ও MAC ঠিকানা
    ip neigh               # ARP টেবিল
    cat /etc/resolv.conf   # DNS সার্ভারের তালিকা
    nmcli device show      # NetworkManager এর মাধ্যমে বিস্তারিত তথ্য
    ```

    প্রাইভেট ও পাবলিক আইপির পার্থক্য: ip addr দেখায় স্থানীয় নেটওয়ার্কে বরাদ্দ করা প্রাইভেট আইপি (যেমন 192.168.x.x বা 10.x.x.x), আর curl ifconfig.me দেখায় NAT এর বাইরে ইন্টারনেট যে পাবলিক আইপি দেখে। বাসা বা অফিসের বহু যন্ত্র একই পাবলিক আইপি ভাগ করে ব্যবহার করে।
41. **Write down Linux command: i. Display current directory folder and file. ii. Create a folder name “DPDC”. iii. Remove a file like as “DPDC2”. iv. A file name is “myFile”; Rename the file name to “DPDC2.txt”. v. Give permission to a file so that anyone can read, write and executive that file.** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 975 (ET: BUET)]*


    Answer:

    (i) Display the current directory's folders and files:
    ```bash
    ls                    # names only
    ls -l                 # long listing with permissions, owner, size and date
    ls -la                # including hidden files
    ls -lh                # human readable sizes
    pwd                   # print the path of the current directory
    ```

    (ii) Create a folder named DPDC:
    ```bash
    mkdir DPDC
    mkdir -p DPDC         # does not complain if it already exists
    mkdir -m 755 DPDC     # create with specific permissions
    ```

    (iii) Remove a file named DPDC2:
    ```bash
    rm DPDC2              # delete the file
    rm -i DPDC2           # ask for confirmation
    rm -f DPDC2           # force, no prompt
    rm -r DPDC2           # if DPDC2 is a directory, delete it and its contents
    ```

    (iv) Rename a file named myFile to DPDC2.txt:
    ```bash
    mv myFile DPDC2.txt
    ```
    Linux has no separate rename command for a single file; mv performs both moving and renaming. Adding -i makes it ask before overwriting an existing DPDC2.txt.

    (v) Give permission to a file so that anyone can read, write and execute it:
    ```bash
    chmod 777 filename
    ```
    Each digit is the sum of read (4), write (2) and execute (1), given for owner, group and others, so 7 means rwx for each and the permission string becomes -rwxrwxrwx.

    Symbolic equivalent:
    ```bash
    chmod a+rwx filename
    chmod ugo+rwx filename
    ```

    All five in sequence:
    ```bash
    ls -la                  # (i)   list the current directory
    mkdir DPDC              # (ii)  create the folder
    rm DPDC2                # (iii) remove the file
    mv myFile DPDC2.txt     # (iv)  rename
    chmod 777 DPDC2.txt     # (v)   full permission for everyone
    ls -l DPDC2.txt         # verify
    ```

    Expected verification output:
    ```
    -rwxrwxrwx 1 rahim staff 1024 Aug 30 12:30 DPDC2.txt
    ```

    A security note worth adding: 777 gives every user on the system the right to modify or delete the file, so it should never be used on a production server. For an ordinary data file 644 is correct, and for a script 755.
42. **A bash shell script using for loop to give output of given pattern:** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1035 (ET: BUET)]*


    Answer: The pattern itself is not reproduced in the question paper, so the standard patterns asked in such questions are given below, each with a for loop.

    Pattern 1, a right-angled triangle of stars:
    ```
    *
    **
    ***
    ****
    *****
    ```

    ```bash
    #!/bin/bash
    n=5
    for (( i=1; i<=n; i++ ))
    do
        for (( j=1; j<=i; j++ ))
        do
            echo -n "*"
        done
        echo            # move to the next line
    done
    ```
    The option -n in echo suppresses the newline, so the stars are printed side by side; the bare echo at the end of the outer loop then starts a new line.

    Pattern 2, an inverted triangle:
    ```
    *****
    ****
    ***
    **
    *
    ```

    ```bash
    #!/bin/bash
    n=5
    for (( i=n; i>=1; i-- ))
    do
        for (( j=1; j<=i; j++ )); do echo -n "*"; done
        echo
    done
    ```

    Pattern 3, a pyramid:
    ```
        *
       ***
      *****
     *******
    *********
    ```

    ```bash
    #!/bin/bash
    n=5
    for (( i=1; i<=n; i++ ))
    do
        for (( s=n; s>i; s-- )); do echo -n " "; done      # leading spaces
        for (( j=1; j<=2*i-1; j++ )); do echo -n "*"; done # stars
        echo
    done
    ```

    Pattern 4, a number triangle:
    ```
    1
    12
    123
    1234
    12345
    ```

    ```bash
    #!/bin/bash
    n=5
    for (( i=1; i<=n; i++ ))
    do
        for (( j=1; j<=i; j++ )); do echo -n "$j"; done
        echo
    done
    ```

    Pattern 5, Floyd's triangle:
    ```
    1
    2 3
    4 5 6
    7 8 9 10
    ```

    ```bash
    #!/bin/bash
    n=4
    count=1
    for (( i=1; i<=n; i++ ))
    do
        for (( j=1; j<=i; j++ ))
        do
            echo -n "$count "
            ((count++))
        done
        echo
    done
    ```

    Pattern 6, a multiplication table, which is also frequently asked:
    ```bash
    #!/bin/bash
    for (( i=1; i<=5; i++ ))
    do
        for (( j=1; j<=5; j++ ))
        do
            printf "%4d" $((i*j))
        done
        echo
    done
    ```
    Output:
    ```
       1   2   3   4   5
       2   4   6   8  10
       3   6   9  12  15
       4   8  12  16  20
       5  10  15  20  25
    ```

    Running any of these:
    ```bash
    chmod +x pattern.sh
    ./pattern.sh
    ```

    Points to note about bash loops:
    - The C-style form for (( i=1; i<=n; i++ )) requires double parentheses; it is a bash extension and does not work in plain sh.
    - The list form is also available: for i in 1 2 3 4 5, or for i in {1..5}, or for i in $(seq 1 5).
    - Arithmetic is written inside $(( )) or (( )), because bash does not evaluate arithmetic in ordinary expressions.
    - echo -n prints without a newline; printf gives full control over width and alignment and is preferred for tables.

## CPU Scheduling Algorithms (24)

1. A CPU scheduling algorithm must choose a process from the ready queue to execute. *[Combined Bank Officer (IT) 09.05.2026 debug it (ET: N/A)]*

2. **Five jobs A, B, C, D, and E arrive at a compute center at approximately the same time. Their estimated running times are 10, 6, 2, 4, and 8 minutes, respectively. Their (externally defined) priorities are 3, 5, 2, 1, and 4, respectively, with 5 being the highest priority. For each of the following scheduling algorithms, determine the mean process turnaround time. (Ignore process switching overhead.) (a) Round-robin (quantum = 2 minutes), (b) Priority scheduling, (c) First-come, first-served (run in order 10, 6, 2, 4, 8), (d) Shortest job first.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1421 (ET: E-Zone)]*

3. **Process CPU burst and Priority given. Calculate Average Waiting time using (i) Preemptive Priority (ii) Non Preemptive priority.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*

4. **Calculate Average Waiting time using (i) FCFS (ii) SJF and (iii) RR (Quantum = 2) for the following:** *[BCC Assistant Programmer 18.10.2025 compact it 1443 (ET: BCC)]*

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

6. **a) Define CPU Scheduling. Draw Gantt charts and find average waiting time for: i) FCFS, ii) SJF (Non-preemptive), iii) Preemptive Priority.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1344 (ET: N/A)]*

7. **Process burst time and priority given. Draw Gantt chart and find average waiting time for preemptive priority scheduling.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*

8. **Shortest job scheduling (SJF) is a __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

9. **Round-robin scheduling (RR) is a __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

10. **(a) FCFS and SJF Scheduling. (b) Find AWT and ATAT.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*

11. **Advantages of CPU Scheduling Algorithm.** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1460 (ET: N/A)]*

12. **What type of RR Scheduling Algorithm: Preemtive/ Non-Preemtive?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*

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

15. **Find average turnaround time and average waiting time using round robin and FCFS algorithm?**
| Process | Arrival Time | Execute Time |
|---|---|---|
| P0 | 0 | 5 |
| P1 | 1 | 3 |
| P2 | 2 | 8 |
| P3 | 3 | 6 |
*[Teletalk Assistant Manager (IT) 2023 compact it 467 (ET: N/A)]*

16. **Starvation in SJF, Starvation free scheduling algorithm name. (Question not clear)** *[RPGCL Assistant Manager (ICT) 2022 compact it 654 (ET: BUET)]*

17. **Consider the processes P1, P2, P3, P4 given in the below table, arrives for execution in the same order, with Arrival Time 0, and given Burst Time, let's find the average waiting time using the FCFS scheduling algorithm.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*

18. **Job arrival time and execution time of Operating system tasks table is given, find out- (i) Average waiting time for FCFS (ii) Preemptive SJF (iii) Round Robin (Quantum time: 3) scheduling algorithm** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925 (ET: CTI)]*

19. **Calculate The Average Waiting Time of SJF scheduling algorithm.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*

20. **(a) Define FCFS, SJF and RR algorithm (Quantum=20).** *[National University Assistant Programmer 2020 compact it 977-978 (ET: DU)]*

21. **(b) Turnaround time of FCFS and SJF** *[National University Assistant Programmer 2020 compact it 978 (ET: DU)]*

22. **Operating system (OS) scheduling is the key concept of multiprogramming. List and briefly define the major types of OS scheduling.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985-986 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*

23. **(c) Explain the following Scheduling algorithm: (i) Round Robin (ii) FCFS (iii) Priority scheduling** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026 (ET: N/A)]*

24. **Calculate the average waiting time and total turn around time in: (i) Non Preemptive SJF (ii) Preemptive SJF** *[Sundharban Gas Assistant Programmer 2020 compact it 1047 (ET: N/A)]*

## Deadlock & Resource Allocation (22)

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

## OS Concepts & System Software (15)

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

## Virtual Memory & Page Replacement (Thrashing) (15)

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

## Memory Management & Paging (13)

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

## Process Management & Process States (10)

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

## Concurrency, Threads & Synchronization (9)

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

## Windows & System Administration (4)

1. **How to check the IP address in the Windows Command Prompt?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*

2. **Assume that an office has three departments and each department has 50 to 70 employees who are using computers with Windows operating systems. The office space is designed in such a way that an employee can use any computer within a department. Once an employee logs in from a computer, he/she will get access to his files from the server. Let you are planning for network and server setup for this company.**
   * **(a) What is Active Directory? Do you need an Active Directory for such an office? If yes, briefly explain its use under this circumstance.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 323 (ET: BIBM)]*

3. **Describe the booting process in windows system.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 565 (ET: N/A)]*

4. **১৯. বর্তমানে উইন্ডোজ অপারেটিং সিস্টেম এর কত তম ভার্সন বাজারজাত করা হয়েছে?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*

## Process Synchronization & Concurrency (4)

1. Two independent applications running concurrently attempt to update the same file located at a same file location. Both applications may read and modify the file at nearly the same time, creating a possibility of race conditions, lost updates, or inconsistent data. What type of consistency problem can occur in this situation, and which synchronization technique(s) should be used to ensure that only one application can safely update the file at a time? Explain the mechanism and justify the most appropriate solution. [BSCCPL AME 21-08-2026 (BUET)]

2. **What is Semaphore? How would you improve performance when using semaphores?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 504 (ET: N/A)]*

3. **(গ) Process Synchronization এর ক্ষেত্রে Race condition ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*

4. **(ক) Critical Section Problem কী? ইহা কীভাবে সমাধান করা যায়?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*

## File Systems & Disk Management (4)

1. **NTFS stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*

2. **(খ) Unix file system এর প্রকারভেদ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 610 (ET: N/A)]*

3. **কোন ড্রাইভে ‘My Document’ রাখা হয় এবং NTFS কী?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*

4. **A file system with 300 GB uses a file descriptor with 8 direct block address, 1 indirect block address and 1 doubly indirect block address. The size of each disk block is 128 Bytes and the size of each disk block address is 8 Bytes. The maximum possible file size in this file system.** *[BAUST Assistant Programmer 2021 compact it 917 (ET: N/A)]*
