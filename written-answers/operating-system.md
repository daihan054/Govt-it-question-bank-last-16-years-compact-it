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


   Answer: A CPU scheduling algorithm selects one process from the ready queue and allocates the CPU to it. The choice matters because the CPU is the scarcest resource in a multiprogramming system, and the scheduling policy determines throughput, response time and fairness.

   When scheduling decisions are taken:
   - When a process switches from the running state to the waiting state, for example on an input-output request.
   - When a process switches from the running state to the ready state, for example on a timer interrupt.
   - When a process switches from the waiting state to the ready state, for example on completion of input-output.
   - When a process terminates.
   Scheduling only in the first and fourth cases is non-preemptive; scheduling in all four is preemptive.

   The main criteria a scheduler tries to optimise:
   - CPU utilisation: keep the CPU as busy as possible; maximise.
   - Throughput: number of processes completed per unit time; maximise.
   - Turnaround time: total time from submission to completion; minimise.
   - Waiting time: time spent in the ready queue; minimise.
   - Response time: time from submission to the first response; minimise, and this is what matters most in an interactive system.
   - Fairness: no process should be starved.

   The principal algorithms:

   | Algorithm | Preemptive | Selection rule | Main advantage | Main drawback |
   |---|---|---|---|---|
   | FCFS | No | Order of arrival | Simple and fair in order | Convoy effect; a long job delays everything behind it |
   | SJF | No | Smallest burst time | Provably minimum average waiting time | Burst time must be known; long jobs starve |
   | SRTF | Yes | Smallest remaining time | Even lower average waiting time | High context-switch overhead; starvation |
   | Priority | Either | Highest priority | Important work first | Starvation of low-priority jobs; solved by ageing |
   | Round Robin | Yes | Cyclic, one time quantum each | Fair, good response time | Higher average turnaround; quantum must be tuned |
   | Multilevel Queue | Yes | Separate queue per class | Different policies for different classes | Rigid, processes cannot move between queues |
   | Multilevel Feedback Queue | Yes | Queues with promotion and demotion | Adapts to process behaviour | Complex to configure |

   Definitions used throughout:
   - Arrival Time (AT): when the process enters the ready queue.
   - Burst Time (BT): the CPU time the process needs.
   - Completion Time (CT): when the process finishes.
   - Turnaround Time (TAT) = CT - AT
   - Waiting Time (WT) = TAT - BT
   - Response Time = time of first CPU allocation - AT
   - Average = the sum over all processes divided by the number of processes

   Practical note: no single algorithm is best in every situation. A batch system favours SJF for throughput, an interactive system favours Round Robin for response time, and a real-time system uses priority or deadline-based scheduling. Modern general-purpose operating systems, such as Linux with its Completely Fair Scheduler, use a multilevel feedback approach that gives interactive processes a short effective quantum while letting compute-bound processes run longer.
2. **Five jobs A, B, C, D, and E arrive at a compute center at approximately the same time. Their estimated running times are 10, 6, 2, 4, and 8 minutes, respectively. Their (externally defined) priorities are 3, 5, 2, 1, and 4, respectively, with 5 being the highest priority. For each of the following scheduling algorithms, determine the mean process turnaround time. (Ignore process switching overhead.) (a) Round-robin (quantum = 2 minutes), (b) Priority scheduling, (c) First-come, first-served (run in order 10, 6, 2, 4, 8), (d) Shortest job first.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1421 (ET: E-Zone)]*


   Answer: Five jobs arrive at approximately the same time, so all arrival times are taken as 0.

   | Job | Burst Time | Priority (5 highest) |
   |---|---|---|
   | A | 10 | 3 |
   | B | 6 | 5 |
   | C | 2 | 2 |
   | D | 4 | 1 |
   | E | 8 | 4 |

   Since every arrival time is 0, turnaround time equals completion time.

   (a) Round Robin with a quantum of 2 minutes

   Gantt chart:
   ```
   | A | B | C | D | E | A | B | D | E | A | B | E | A | E | A |
   0   2   4   6   8  10  12  14  16  18  20  22  24  26  28  30
   ```
   The cycle repeats in the order A, B, C, D, E; C finishes in its first turn, D in its second, and so on.

   | Job | Completion Time | Turnaround Time |
   |---|---|---|
   | A | 30 | 30 |
   | B | 22 | 22 |
   | C | 6 | 6 |
   | D | 16 | 16 |
   | E | 28 | 28 |

   Mean turnaround time = (30 + 22 + 6 + 16 + 28) / 5 = 102 / 5 = 20.4 minutes

   (b) Priority scheduling (non-preemptive, 5 is the highest priority)

   Order of execution by descending priority: B (5), E (4), A (3), C (2), D (1).

   Gantt chart:
   ```
   |   B   |    E    |     A     | C |  D  |
   0       6        14          24  26    30
   ```

   | Job | Completion Time | Turnaround Time |
   |---|---|---|
   | B | 6 | 6 |
   | E | 14 | 14 |
   | A | 24 | 24 |
   | C | 26 | 26 |
   | D | 30 | 30 |

   Mean turnaround time = (24 + 6 + 26 + 30 + 14) / 5 = 100 / 5 = 20.0 minutes

   (c) First Come First Served, run in the order 10, 6, 2, 4, 8, that is A, B, C, D, E

   Gantt chart:
   ```
   |     A     |   B   | C |  D  |    E    |
   0          10      16  18    22        30
   ```

   | Job | Completion Time | Turnaround Time |
   |---|---|---|
   | A | 10 | 10 |
   | B | 16 | 16 |
   | C | 18 | 18 |
   | D | 22 | 22 |
   | E | 30 | 30 |

   Mean turnaround time = (10 + 16 + 18 + 22 + 30) / 5 = 96 / 5 = 19.2 minutes

   (d) Shortest Job First

   Order by increasing burst time: C (2), D (4), B (6), E (8), A (10).

   Gantt chart:
   ```
   | C |  D  |   B   |    E    |     A     |
   0   2     6      12        20          30
   ```

   | Job | Completion Time | Turnaround Time |
   |---|---|---|
   | C | 2 | 2 |
   | D | 6 | 6 |
   | B | 12 | 12 |
   | E | 20 | 20 |
   | A | 30 | 30 |

   Mean turnaround time = (30 + 12 + 2 + 6 + 20) / 5 = 70 / 5 = 14.0 minutes

   Summary and conclusion:

   | Algorithm | Mean turnaround time (minutes) |
   |---|---|
   | Round Robin (q = 2) | 20.4 |
   | Priority | 20.0 |
   | First Come First Served | 19.2 |
   | Shortest Job First | 14.0 |

   Shortest Job First gives the lowest mean turnaround time, 14.0 minutes, and this is not a coincidence: when all processes are available at the same instant, SJF is provably optimal for average waiting and turnaround time. Round Robin gives the worst figure here because every job is repeatedly interrupted, but it would give the best response time, which is why it is preferred in interactive systems.
3. **Process CPU burst and Priority given. Calculate Average Waiting time using (i) Preemptive Priority (ii) Non Preemptive priority.** *[DPDC Assistant Engineer (CSE) 17.10.2025 compact it 1453 (ET: N/A)]*


   Answer: Since the process table is not reproduced in the question paper, the standard example set below is used, and the complete method is shown so that any table can be solved the same way.

   | Process | Arrival Time | Burst Time | Priority (lower number = higher priority) |
   |---|---|---|---|
   | P1 | 0 | 5 | 2 |
   | P2 | 1 | 3 | 1 |
   | P3 | 2 | 8 | 4 |
   | P4 | 3 | 6 | 3 |

   Definitions used throughout:
   - Arrival Time (AT): when the process enters the ready queue.
   - Burst Time (BT): the CPU time the process needs.
   - Completion Time (CT): when the process finishes.
   - Turnaround Time (TAT) = CT - AT
   - Waiting Time (WT) = TAT - BT
   - Response Time = time of first CPU allocation - AT
   - Average = the sum over all processes divided by the number of processes

   (i) Preemptive priority scheduling

   The scheduler re-evaluates at every arrival. A newly arrived process with a higher priority immediately takes the CPU from the running process.

   Trace:
   - t = 0: only P1 is present, so P1 runs.
   - t = 1: P2 arrives with priority 1, which is higher than P1's priority 2, so P1 is preempted with 4 units remaining and P2 runs.
   - t = 2: P3 arrives with priority 4, lower, so P2 continues.
   - t = 3: P4 arrives with priority 3, lower, so P2 continues.
   - t = 4: P2 finishes. Among P1 (2), P4 (3) and P3 (4), P1 has the highest priority, so P1 runs to completion.
   - t = 8: P1 finishes. P4 has higher priority than P3, so P4 runs.
   - t = 14: P4 finishes, and P3 runs last.

   Gantt chart:
   ```
   | P1 |   P2  |    P1    |     P4     |       P3       |
   0    1       4          8           14               22
   ```

   | Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 8 | 8 | 3 |
   | P2 | 1 | 3 | 4 | 3 | 0 |
   | P3 | 2 | 8 | 22 | 20 | 12 |
   | P4 | 3 | 6 | 14 | 11 | 5 |

   Average Waiting Time = (3 + 0 + 12 + 5) / 4 = 20 / 4 = 5.00 ms
   Average Turnaround Time = (8 + 3 + 20 + 11) / 4 = 42 / 4 = 10.50 ms

   (ii) Non-preemptive priority scheduling

   Once a process starts it runs to completion; the priority is consulted only when the CPU becomes free.

   Trace:
   - t = 0: only P1 is present, so P1 runs to completion at t = 5.
   - t = 5: P2, P3 and P4 have all arrived. P2 has the highest priority (1), so P2 runs to t = 8.
   - t = 8: between P4 (3) and P3 (4), P4 wins and runs to t = 14.
   - t = 14: P3 runs to t = 22.

   Gantt chart:
   ```
   |    P1    |  P2  |     P4     |       P3       |
   0          5      8           14               22
   ```

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 5 | 5 | 0 |
   | P2 | 1 | 3 | 8 | 7 | 4 |
   | P3 | 2 | 8 | 22 | 20 | 12 |
   | P4 | 3 | 6 | 14 | 11 | 5 |

   Average Waiting Time = (0 + 4 + 12 + 5) / 4 = 21 / 4 = 5.25 ms
   Average Turnaround Time = (5 + 7 + 20 + 11) / 4 = 43 / 4 = 10.75 ms

   Comparison:

   | Metric | Preemptive | Non-preemptive |
   |---|---|---|
   | Average waiting time | 5.00 ms | 5.25 ms |
   | Average turnaround time | 10.50 ms | 10.75 ms |
   | Context switches | More | Fewer |
   | Response time for a high-priority arrival | Immediate | Must wait for the current process to finish |

   The preemptive version gives the better average because P2, which is short and of the highest priority, is served at once instead of waiting for P1 to finish. The cost is a greater number of context switches.

   Both versions suffer from starvation: a process of low priority may never run if higher-priority processes keep arriving. The standard remedy is ageing, in which the priority of a waiting process is gradually raised, so that every process eventually reaches the front.
4. **Calculate Average Waiting time using (i) FCFS (ii) SJF and (iii) RR (Quantum = 2) for the following:** *[BCC Assistant Programmer 18.10.2025 compact it 1443 (ET: BCC)]*


   Answer: Since the process table is not reproduced in the question paper, the standard example set below is used, and the complete method is shown so that any table can be solved the same way.

   | Process | Arrival Time | Burst Time | Priority (lower number = higher priority) |
   |---|---|---|---|
   | P1 | 0 | 5 | 2 |
   | P2 | 1 | 3 | 1 |
   | P3 | 2 | 8 | 4 |
   | P4 | 3 | 6 | 3 |

   Definitions used throughout:
   - Arrival Time (AT): when the process enters the ready queue.
   - Burst Time (BT): the CPU time the process needs.
   - Completion Time (CT): when the process finishes.
   - Turnaround Time (TAT) = CT - AT
   - Waiting Time (WT) = TAT - BT
   - Response Time = time of first CPU allocation - AT
   - Average = the sum over all processes divided by the number of processes

   (i) First Come First Served (FCFS)

   Processes run strictly in order of arrival.

   Gantt chart:
   ```
   |    P1    |  P2  |       P3       |      P4      |
   0          5      8               16             22
   ```

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 5 | 5 | 0 |
   | P2 | 1 | 3 | 8 | 7 | 4 |
   | P3 | 2 | 8 | 16 | 14 | 6 |
   | P4 | 3 | 6 | 22 | 19 | 13 |

   Average Waiting Time = (0 + 4 + 6 + 13) / 4 = 23 / 4 = 5.75 ms
   Average Turnaround Time = (5 + 7 + 14 + 19) / 4 = 45 / 4 = 11.25 ms

   (ii) Shortest Job First, non-preemptive

   When the CPU is free, the process with the smallest burst time among those that have arrived is chosen.

   Trace:
   - t = 0: only P1 has arrived, so it runs to t = 5.
   - t = 5: P2 (3), P3 (8) and P4 (6) have arrived; P2 is shortest, so it runs to t = 8.
   - t = 8: P4 (6) is shorter than P3 (8), so P4 runs to t = 14.
   - t = 14: P3 runs to t = 22.

   Gantt chart:
   ```
   |    P1    |  P2  |      P4      |       P3       |
   0          5      8             14               22
   ```

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 5 | 5 | 0 |
   | P2 | 1 | 3 | 8 | 7 | 4 |
   | P3 | 2 | 8 | 22 | 20 | 12 |
   | P4 | 3 | 6 | 14 | 11 | 5 |

   Average Waiting Time = (0 + 4 + 12 + 5) / 4 = 21 / 4 = 5.25 ms
   Average Turnaround Time = (5 + 7 + 20 + 11) / 4 = 43 / 4 = 10.75 ms

   (iii) Round Robin with quantum = 2

   Each process gets 2 ms in turn; if it is not finished it goes to the back of the ready queue. A process that arrives during a quantum joins the queue before the preempted process is re-added.

   Gantt chart:
   ```
   |P1|P2|P3|P1|P4|P2|P3|P1|P4|P3|P4|P3|
   0  2  4  6  8 10 11 13 14 16 18 20 22
   ```
   Reading it: P1 0-2, P2 2-4, P3 4-6, P1 6-8, P4 8-10, P2 10-11 (only 1 ms left), P3 11-13, P1 13-14 (1 ms left), P4 14-16, P3 16-18, P4 18-20, P3 20-22.

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 14 | 14 | 9 |
   | P2 | 1 | 3 | 11 | 10 | 7 |
   | P3 | 2 | 8 | 22 | 20 | 12 |
   | P4 | 3 | 6 | 20 | 17 | 11 |

   Average Waiting Time = (9 + 7 + 12 + 11) / 4 = 39 / 4 = 9.75 ms
   Average Turnaround Time = (14 + 10 + 20 + 17) / 4 = 61 / 4 = 15.25 ms

   Comparison:

   | Algorithm | Average Waiting Time | Average Turnaround Time |
   |---|---|---|
   | FCFS | 5.75 ms | 11.25 ms |
   | SJF (non-preemptive) | 5.25 ms | 10.75 ms |
   | Round Robin (q = 2) | 9.75 ms | 15.25 ms |

   Conclusion: SJF gives the lowest average waiting time, which is its known theoretical property. Round Robin gives the worst averages here because every process is interrupted repeatedly, but it gives by far the best response time, since every process receives the CPU within one cycle of the queue. That is why interactive systems use Round Robin despite its poorer averages.
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


   Answer: Given, all processes arrive at time 0, and a lower priority number means higher priority.

   | Process | Burst Time | Priority |
   |---|---|---|
   | P1 | 10 | 3 |
   | P2 | 1 | 1 |
   | P3 | 2 | 3 |
   | P4 | 1 | 4 |
   | P5 | 5 | 2 |

   Since every arrival time is 0, Turnaround Time = Completion Time and Waiting Time = TAT - BT.

   (i) Gantt charts

   FCFS, in the order P1, P2, P3, P4, P5:
   ```
   |      P1      |P2| P3 |P4|   P5   |
   0             10 11   13 14        19
   ```

   Non-preemptive priority, order P2 (1), P5 (2), P1 (3), P3 (3), P4 (4). P1 and P3 have the same priority, so FCFS breaks the tie:
   ```
   |P2|   P5   |      P1      | P3 |P4|
   0  1        6             16   18 19
   ```

   SJF, order by burst time P2 (1), P4 (1), P3 (2), P5 (5), P1 (10):
   ```
   |P2|P4| P3 |   P5   |      P1      |
   0  1  2    4        9             19
   ```

   Round Robin with quantum = 1:
   ```
   |P1|P2|P3|P4|P5|P1|P3|P5|P1|P5|P1|P5|P1|P5|P1|P1|P1|P1|P1|
   0  1  2  3  4  5  6  7  8  9 10 11 12 13 14 15 16 17 18 19
   ```
   P2 finishes at 2, P4 at 4, P3 at 7, P5 at 14 and P1 at 19.

   (ii) Turnaround time of each process

   | Process | BT | FCFS | Priority | SJF | RR (q=1) |
   |---|---|---|---|---|---|
   | P1 | 10 | 10 | 16 | 19 | 19 |
   | P2 | 1 | 11 | 1 | 1 | 2 |
   | P3 | 2 | 13 | 18 | 4 | 7 |
   | P4 | 1 | 14 | 19 | 2 | 4 |
   | P5 | 5 | 19 | 6 | 9 | 14 |
   | Average | | 13.40 | 12.00 | 7.00 | 9.20 |

   (iii) Waiting time of each process

   | Process | BT | FCFS | Priority | SJF | RR (q=1) |
   |---|---|---|---|---|---|
   | P1 | 10 | 0 | 6 | 9 | 9 |
   | P2 | 1 | 10 | 0 | 0 | 1 |
   | P3 | 2 | 11 | 16 | 2 | 5 |
   | P4 | 1 | 13 | 18 | 1 | 3 |
   | P5 | 5 | 14 | 1 | 4 | 9 |
   | Average | | 9.60 | 8.20 | 3.20 | 5.40 |

   (iv) Which algorithm gives the minimum average waiting time

   | Algorithm | Average Waiting Time |
   |---|---|
   | FCFS | 9.60 ms |
   | Non-preemptive priority | 8.20 ms |
   | SJF | 3.20 ms |
   | Round Robin (q = 1) | 5.40 ms |

   Shortest Job First gives the minimum average waiting time, 3.20 ms.

   Reason: when every process is available at time 0, SJF is provably optimal for average waiting time. Placing a short job before a long one reduces the waiting time of the short job by more than it increases that of the long one, so sorting by burst time minimises the total. FCFS is worst here because the longest job, P1, happens to run first and delays everything behind it, which is the convoy effect.

   Practical limitation of SJF: the burst time of a process is not known in advance in a real system; it must be predicted, usually with an exponential average of past bursts. SJF also starves long processes if short ones keep arriving.
6. **a) Define CPU Scheduling. Draw Gantt charts and find average waiting time for: i) FCFS, ii) SJF (Non-preemptive), iii) Preemptive Priority.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1344 (ET: N/A)]*


   Answer: CPU scheduling is the activity by which the operating system decides which of the processes in the ready queue is to be given the CPU next. It is the basis of multiprogramming: while one process waits for input or output, the CPU is given to another, so that the processor is never idle when work is available.

   The scheduler aims to maximise CPU utilisation and throughput while minimising turnaround time, waiting time and response time, and it must also be fair, so that no process starves. Scheduling decisions arise when a process moves from running to waiting, from running to ready, from waiting to ready, or terminates. A scheduler that acts only in the first and last cases is non-preemptive; one that acts in all four is preemptive.

   The process table is not reproduced in the question paper, so the standard set below is used and the full method is shown.

   | Process | Arrival Time | Burst Time | Priority (lower number = higher) |
   |---|---|---|---|
   | P1 | 0 | 5 | 2 |
   | P2 | 1 | 3 | 1 |
   | P3 | 2 | 8 | 4 |
   | P4 | 3 | 6 | 3 |

   Definitions used:
   - Turnaround Time (TAT) = Completion Time - Arrival Time
   - Waiting Time (WT) = Turnaround Time - Burst Time
   - Average = sum over all processes divided by the number of processes

   i) FCFS: processes run strictly in order of arrival.
   ```
   |    P1    |  P2  |       P3       |      P4      |
   0          5      8               16             22
   ```

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 5 | 5 | 0 |
   | P2 | 1 | 3 | 8 | 7 | 4 |
   | P3 | 2 | 8 | 16 | 14 | 6 |
   | P4 | 3 | 6 | 22 | 19 | 13 |

   Average Waiting Time = (0 + 4 + 6 + 13) / 4 = 5.75 ms
   Average Turnaround Time = (5 + 7 + 14 + 19) / 4 = 11.25 ms

   ii) SJF (non-preemptive): among the processes that have arrived, the one with the smallest burst time is chosen.
   ```
   |    P1    |  P2  |      P4      |       P3       |
   0          5      8             14               22
   ```

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 5 | 5 | 0 |
   | P2 | 1 | 3 | 8 | 7 | 4 |
   | P3 | 2 | 8 | 22 | 20 | 12 |
   | P4 | 3 | 6 | 14 | 11 | 5 |

   Average Waiting Time = (0 + 4 + 12 + 5) / 4 = 5.25 ms
   Average Turnaround Time = (5 + 7 + 20 + 11) / 4 = 10.75 ms

   iii) Preemptive priority: a newly arrived process of higher priority takes the CPU immediately.

   Trace:
   - t = 0: P1 runs (only process present).
   - t = 1: P2 arrives with priority 1, higher than P1's 2, so P1 is preempted with 4 ms left.
   - t = 4: P2 finishes; among P1 (2), P4 (3), P3 (4) the highest is P1, which runs its remaining 4 ms.
   - t = 8: P1 finishes; P4 (3) beats P3 (4).
   - t = 14: P4 finishes; P3 runs last.
   ```
   | P1 |   P2  |    P1    |     P4     |       P3       |
   0    1       4          8           14               22
   ```

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 8 | 8 | 3 |
   | P2 | 1 | 3 | 4 | 3 | 0 |
   | P3 | 2 | 8 | 22 | 20 | 12 |
   | P4 | 3 | 6 | 14 | 11 | 5 |

   Average Waiting Time = (3 + 0 + 12 + 5) / 4 = 5.00 ms
   Average Turnaround Time = (8 + 3 + 20 + 11) / 4 = 10.50 ms

   Comparison:

   | Algorithm | Average Waiting Time | Average Turnaround Time |
   |---|---|---|
   | FCFS | 5.75 ms | 11.25 ms |
   | SJF (non-preemptive) | 5.25 ms | 10.75 ms |
   | Preemptive priority | 5.00 ms | 10.50 ms |

   Preemptive priority is best for this data because the short, high-priority process P2 is served immediately. FCFS is worst because the order of arrival happens to place longer jobs early, which is the convoy effect.
7. **Process burst time and priority given. Draw Gantt chart and find average waiting time for preemptive priority scheduling.** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1339 (ET: N/A)]*


   Answer: The process table is not reproduced in the question paper, so the standard set below is used and the full method of preemptive priority scheduling is shown.

   | Process | Arrival Time | Burst Time | Priority (lower number = higher) |
   |---|---|---|---|
   | P1 | 0 | 5 | 2 |
   | P2 | 1 | 3 | 1 |
   | P3 | 2 | 8 | 4 |
   | P4 | 3 | 6 | 3 |

   Definitions used:
   - Turnaround Time (TAT) = Completion Time - Arrival Time
   - Waiting Time (WT) = Turnaround Time - Burst Time
   - Average = sum over all processes divided by the number of processes

   Preemptive priority: a newly arrived process of higher priority takes the CPU immediately.

   Trace:
   - t = 0: P1 runs (only process present).
   - t = 1: P2 arrives with priority 1, higher than P1's 2, so P1 is preempted with 4 ms left.
   - t = 4: P2 finishes; among P1 (2), P4 (3), P3 (4) the highest is P1, which runs its remaining 4 ms.
   - t = 8: P1 finishes; P4 (3) beats P3 (4).
   - t = 14: P4 finishes; P3 runs last.
   ```
   | P1 |   P2  |    P1    |     P4     |       P3       |
   0    1       4          8           14               22
   ```

   | Process | AT | BT | CT | TAT | WT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 8 | 8 | 3 |
   | P2 | 1 | 3 | 4 | 3 | 0 |
   | P3 | 2 | 8 | 22 | 20 | 12 |
   | P4 | 3 | 6 | 14 | 11 | 5 |

   Average Waiting Time = (3 + 0 + 12 + 5) / 4 = 5.00 ms
   Average Turnaround Time = (8 + 3 + 20 + 11) / 4 = 10.50 ms

   Points to state about preemptive priority scheduling:
   - The ready queue is re-examined at every arrival, not only when the running process finishes. This is the difference from the non-preemptive version, which for the same data gives an average waiting time of 5.25 ms instead of 5.00 ms.
   - Its advantage is a very short response time for important work, which is essential in a real-time or interactive system.
   - Its cost is a larger number of context switches, each of which wastes CPU time.
   - Its principal defect is starvation, also called indefinite blocking: a low-priority process may never run if higher-priority processes keep arriving. In 1973 a low-priority job was found still waiting on the IBM 7094 at MIT when the machine was shut down after seven years.
   - The standard remedy is ageing: the priority of a waiting process is raised gradually, for example by one level every fifteen minutes, so that every process eventually reaches the highest priority and runs.
   - Another problem is priority inversion, in which a high-priority process is blocked waiting for a resource held by a low-priority process, which is itself preempted by a medium-priority process. The remedy is priority inheritance, in which the low-priority holder temporarily inherits the priority of the waiter.
8. **Shortest job scheduling (SJF) is a __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: Shortest Job First (SJF) scheduling is a non-preemptive scheduling algorithm in its basic form. It is also described as an optimal algorithm, because it gives the minimum possible average waiting time for a given set of processes.

   Complete characterisation:
   - It is non-preemptive in its classic form: once a process begins, it runs until it finishes.
   - Its preemptive variant is called Shortest Remaining Time First (SRTF), in which a newly arrived process with a shorter remaining time takes the CPU at once.
   - It is optimal for average waiting time. Placing a shorter job before a longer one reduces the short job's wait by more than it increases the long job's wait, so sorting by burst length minimises the total. No other algorithm can do better on the same data.
   - It is a batch scheduling algorithm rather than an interactive one.

   Selection rule: among the processes that have arrived, choose the one with the smallest CPU burst; break ties by arrival order.

   Advantages:
   - Minimum average waiting time and minimum average turnaround time.
   - Maximum throughput, since more processes finish per unit time.
   - Very effective in a batch environment where job lengths are known in advance.

   Disadvantages:
   - The burst time of a process is not known in advance in a real system. It must be estimated, usually by an exponential average of previous bursts:
     tau(n+1) = alpha x t(n) + (1 - alpha) x tau(n), where t(n) is the length of the last burst and alpha is typically 0.5.
   - Starvation: a long process may never run if short processes keep arriving. The remedy is ageing.
   - It is not suitable for interactive or time-sharing systems, where response time matters more than average waiting time.
   - It requires the whole set of processes to be examined at every scheduling decision.
9. **Round-robin scheduling (RR) is a __________.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: Round Robin (RR) scheduling is a preemptive scheduling algorithm, and it is the algorithm designed specifically for time-sharing and interactive systems.

   Complete characterisation:
   - It is preemptive: a process is forcibly removed from the CPU when its time quantum expires, whether or not it has finished.
   - It is essentially FCFS with preemption added, using a circular ready queue.
   - It is the standard algorithm for time-sharing systems, because it guarantees a bounded response time.

   How it works:
   - A small unit of time called a time quantum or time slice is defined, typically 10 to 100 milliseconds.
   - The ready queue is treated as a circular queue. The scheduler takes the first process, allocates the CPU for at most one quantum, and then either the process finishes, or it is preempted by the timer interrupt and placed at the tail of the queue.
   - With n processes and a quantum of q, no process waits more than (n - 1) x q time units, which is the guarantee that makes the system feel responsive.

   Effect of the quantum size:
   - If q is very large, Round Robin degenerates into FCFS, because most processes finish within a single quantum.
   - If q is very small, response is excellent but the overhead of context switching dominates and throughput collapses. This is called processor sharing in the limit.
   - The usual rule of thumb is that about 80 per cent of CPU bursts should be shorter than the quantum, and the quantum should be large compared with the context-switch time, typically ten to a hundred times larger.

   Advantages:
   - Fair: every process gets an equal share of the CPU.
   - No starvation: every process is guaranteed to run within one cycle of the queue.
   - Excellent and predictable response time, which is why interactive systems use it.
   - Simple to implement, requiring only a timer and a queue.

   Disadvantages:
   - Higher average turnaround time and waiting time than SJF, because every process is interrupted repeatedly.
   - Context-switch overhead grows as the quantum shrinks.
   - It treats all processes as equally important, so it does not by itself express priority.
   - Performance depends critically on choosing the quantum correctly.
10. **(a) FCFS and SJF Scheduling. (b) Find AWT and ATAT.** *[Sonali Bank PLC Assistant Database Administrator 23.02.2024 compact it 316 (ET: N/A)]*


    Answer: The process table is not reproduced in the question paper, so the standard set below is used and the full method is shown.

    | Process | Arrival Time | Burst Time | Priority (lower number = higher) |
    |---|---|---|---|
    | P1 | 0 | 5 | 2 |
    | P2 | 1 | 3 | 1 |
    | P3 | 2 | 8 | 4 |
    | P4 | 3 | 6 | 3 |

    Definitions used:
    - Turnaround Time (TAT) = Completion Time - Arrival Time
    - Waiting Time (WT) = Turnaround Time - Burst Time
    - Average = sum over all processes divided by the number of processes

    (a) FCFS and SJF scheduling

    FCFS: processes run strictly in order of arrival.
    ```
    |    P1    |  P2  |       P3       |      P4      |
    0          5      8               16             22
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 5 | 5 | 5 | 0 |
    | P2 | 1 | 3 | 8 | 7 | 4 |
    | P3 | 2 | 8 | 16 | 14 | 6 |
    | P4 | 3 | 6 | 22 | 19 | 13 |

    Average Waiting Time = (0 + 4 + 6 + 13) / 4 = 5.75 ms
    Average Turnaround Time = (5 + 7 + 14 + 19) / 4 = 11.25 ms

    SJF (non-preemptive): among the processes that have arrived, the one with the smallest burst time is chosen.
    ```
    |    P1    |  P2  |      P4      |       P3       |
    0          5      8             14               22
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 5 | 5 | 5 | 0 |
    | P2 | 1 | 3 | 8 | 7 | 4 |
    | P3 | 2 | 8 | 22 | 20 | 12 |
    | P4 | 3 | 6 | 14 | 11 | 5 |

    Average Waiting Time = (0 + 4 + 12 + 5) / 4 = 5.25 ms
    Average Turnaround Time = (5 + 7 + 20 + 11) / 4 = 10.75 ms

    (b) Average Waiting Time (AWT) and Average Turnaround Time (ATAT)

    | Algorithm | AWT | ATAT |
    |---|---|---|
    | FCFS | 5.75 ms | 11.25 ms |
    | SJF (non-preemptive) | 5.25 ms | 10.75 ms |

    Observations:
    - SJF gives a lower average waiting time than FCFS, which is its known theoretical property.
    - The difference arises entirely from the order in which P3 and P4 are run. FCFS runs P3 (burst 8) before P4 (burst 6) merely because P3 arrived first; SJF runs the shorter one first, which reduces the total waiting.
    - FCFS suffers from the convoy effect: a long process at the head of the queue delays every process behind it, however short.
    - SJF cannot be used directly in practice, because the burst time is not known before the process runs; it must be predicted from the history of previous bursts.
11. **Advantages of CPU Scheduling Algorithm.** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1460 (ET: N/A)]*


    Answer: The advantages of using a CPU scheduling algorithm, that is of scheduling processes deliberately rather than running them to completion one after another:

    - Maximum CPU utilisation: when the running process blocks for input or output, the CPU is given at once to another ready process, so the processor is never idle while work exists. Without scheduling, utilisation on an input-output-bound workload would fall to a few per cent.

    - Higher throughput: more processes are completed per unit of time, because the CPU and the input-output devices operate in parallel rather than in turn.

    - Lower average waiting time and turnaround time: by choosing the order of execution intelligently, for example by running short jobs first, the total time processes spend waiting is reduced. SJF is provably optimal in this respect.

    - Better response time: with a preemptive algorithm such as Round Robin, every process receives the CPU within a bounded time, so an interactive user sees the system react promptly. This is the single most important property in a desktop or a server serving users.

    - Fairness and prevention of starvation: a well-designed policy gives every process a share of the CPU. Round Robin guarantees this by construction, and ageing does the same for priority scheduling.

    - Support for multiprogramming and multitasking: scheduling is what makes it possible for many programs to appear to run at the same time on one processor.

    - Prioritisation of important work: a priority scheme lets system processes, real-time tasks and interactive work take precedence over background batch jobs.

    - Predictability for real-time systems: deadline-based algorithms such as Earliest Deadline First allow a system to guarantee that a task completes before its deadline, which is essential in control and safety systems.

    - Efficient resource use as a whole: keeping a good mix of CPU-bound and input-output-bound processes in memory keeps both the processor and the devices busy.

    - Reduced convoy effect: preemptive scheduling stops one long process from blocking many short ones behind it.

    - Better user experience and system stability: the machine remains responsive under load, and a single runaway process cannot monopolise the CPU.

    The cost, which should also be stated: scheduling itself consumes CPU time, and every preemption causes a context switch, which saves and restores registers and may flush the cache and the TLB. A good algorithm therefore balances the benefit of switching against its overhead.
12. **What type of RR Scheduling Algorithm: Preemtive/ Non-Preemtive?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1461 (ET: N/A)]*


    Answer: Round Robin (RR) is a preemptive scheduling algorithm.

    Reason: each process is given the CPU for at most one time quantum. When the quantum expires, a timer interrupt occurs and the operating system forcibly takes the CPU away from the process, saves its state, and places it at the tail of the ready queue, even if the process has not finished its work. Forcibly removing a running process from the CPU is precisely the definition of preemption.

    How it works:
    - A time quantum or time slice, typically 10 to 100 milliseconds, is fixed.
    - The ready queue is circular. The scheduler picks the process at the head, sets the timer for one quantum, and dispatches it.
    - Either the process finishes or blocks within the quantum, in which case the scheduler moves on, or the timer expires and the process is preempted and requeued at the tail.
    - With n processes and quantum q, no process waits more than (n - 1) x q, which is the guaranteed bound on response time.

    Classification of the common algorithms:

    | Algorithm | Preemptive or non-preemptive |
    |---|---|
    | FCFS | Non-preemptive |
    | SJF | Non-preemptive |
    | SRTF (Shortest Remaining Time First) | Preemptive |
    | Priority | Both versions exist |
    | Round Robin | Preemptive |
    | Multilevel Queue | Usually preemptive |
    | Multilevel Feedback Queue | Preemptive |

    Consequences of RR being preemptive:
    - No starvation, since every process is reached within one full cycle of the queue.
    - Excellent and bounded response time, which is why every time-sharing and interactive operating system is built on it.
    - Higher context-switch overhead than a non-preemptive algorithm, and the overhead grows as the quantum shrinks.
    - Higher average turnaround time than SJF, because each process is interrupted repeatedly.

    A boundary case worth mentioning: if the quantum is made very large, larger than the longest burst, no preemption ever actually occurs and Round Robin behaves exactly like FCFS. If the quantum is made very small, the algorithm approaches processor sharing, in which every process appears to run at 1/n of the speed, but the context-switch cost then dominates.
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


    Answer: দেওয়া আছে, সব process সময় 0 তে এসে পৌঁছেছে।

    | Process | Burst Time (ms) | Priority |
    |---|---|---|
    | P1 | 15 | 3 |
    | P2 | 2 | 1 |
    | P3 | 4 | 3 |
    | P4 | 2 | 4 |
    | P5 | 8 | 2 |

    যেহেতু সব arrival time শূন্য, তাই Turnaround Time = Completion Time এবং Waiting Time = TAT - BT।

    i) Gantt Chart

    FCFS (আগমনের ক্রমে P1, P2, P3, P4, P5):
    ```
    |        P1        |P2|  P3  |P4|     P5     |
    0                 15 17     21 23           31
    ```

    SJF (burst time অনুযায়ী ছোট থেকে বড়: P2=2, P4=2, P3=4, P5=8, P1=15; P2 ও P4 এর burst সমান হওয়ায় আগমনের ক্রম অনুসারে P2 আগে):
    ```
    |P2|P4|  P3  |     P5     |        P1        |
    0  2  4      8           16                 31
    ```

    ii) প্রতিটি process এর Turnaround Time

    FCFS এর ক্ষেত্রে:

    | Process | BT | CT | TAT = CT - AT | WT = TAT - BT |
    |---|---|---|---|---|
    | P1 | 15 | 15 | 15 | 0 |
    | P2 | 2 | 17 | 17 | 15 |
    | P3 | 4 | 21 | 21 | 17 |
    | P4 | 2 | 23 | 23 | 21 |
    | P5 | 8 | 31 | 31 | 23 |

    গড় Turnaround Time = (15 + 17 + 21 + 23 + 31) / 5 = 107 / 5 = 21.40 ms
    গড় Waiting Time = (0 + 15 + 17 + 21 + 23) / 5 = 76 / 5 = 15.20 ms

    SJF এর ক্ষেত্রে:

    | Process | BT | CT | TAT | WT |
    |---|---|---|---|---|
    | P1 | 15 | 31 | 31 | 16 |
    | P2 | 2 | 2 | 2 | 0 |
    | P3 | 4 | 8 | 8 | 4 |
    | P4 | 2 | 4 | 4 | 2 |
    | P5 | 8 | 16 | 16 | 8 |

    গড় Turnaround Time = (31 + 2 + 8 + 4 + 16) / 5 = 61 / 5 = 12.20 ms
    গড় Waiting Time = (16 + 0 + 4 + 2 + 8) / 5 = 30 / 5 = 6.00 ms

    তুলনা:

    | Algorithm | গড় Turnaround Time | গড় Waiting Time |
    |---|---|---|
    | FCFS | 21.40 ms | 15.20 ms |
    | SJF | 12.20 ms | 6.00 ms |

    পর্যবেক্ষণ: SJF এ গড় সময় প্রায় অর্ধেকে নেমে এসেছে। এর কারণ FCFS এ সবচেয়ে দীর্ঘ process P1 (15 ms) সবার আগে চলেছে, ফলে পেছনের সব ছোট process কে দীর্ঘ সময় অপেক্ষা করতে হয়েছে। একে বলা হয় convoy effect। SJF ছোট কাজগুলো আগে শেষ করে দেয় বলে মোট অপেক্ষার সময় কমে যায়।

    তাত্ত্বিক ভিত্তি: সব process একই সময়ে উপস্থিত থাকলে SJF গড় অপেক্ষমাণ সময়ের দিক থেকে প্রমাণিতভাবে সর্বোত্তম (optimal)। তবে বাস্তবে burst time আগে থেকে জানা যায় না, এবং দীর্ঘ process starvation এর শিকার হতে পারে।
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


    Answer: Given:

    | Process | Arrival Time | Burst Time |
    |---|---|---|
    | P1 | 0 | 8 |
    | P2 | 0 | 4 |
    | P3 | 0 | 5 |
    | P4 | 1 | 9 |
    | P5 | 1 | 7 |
    | P6 | 0 | 1 |

    Shortest Job First, non-preemptive. At every point where the CPU becomes free, the process with the smallest burst time among those that have already arrived is selected.

    Trace:
    - t = 0: P1 (8), P2 (4), P3 (5) and P6 (1) have arrived. P6 is shortest, so P6 runs from 0 to 1.
    - t = 1: P1 (8), P2 (4), P3 (5), P4 (9) and P5 (7) are all available. P2 is shortest, so P2 runs from 1 to 5.
    - t = 5: remaining are P1 (8), P3 (5), P4 (9), P5 (7). P3 is shortest, so P3 runs from 5 to 10.
    - t = 10: remaining are P1 (8), P4 (9), P5 (7). P5 is shortest, so P5 runs from 10 to 17.
    - t = 17: remaining are P1 (8) and P4 (9). P1 is shortest, so P1 runs from 17 to 25.
    - t = 25: P4 runs from 25 to 34.

    Gantt chart:
    ```
    |P6|  P2  |   P3   |     P5     |      P1      |       P4       |
    0  1      5       10           17             25               34
    ```

    | Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
    |---|---|---|---|---|---|
    | P1 | 0 | 8 | 25 | 25 | 17 |
    | P2 | 0 | 4 | 5 | 5 | 1 |
    | P3 | 0 | 5 | 10 | 10 | 5 |
    | P4 | 1 | 9 | 34 | 33 | 24 |
    | P5 | 1 | 7 | 17 | 16 | 9 |
    | P6 | 0 | 1 | 1 | 1 | 0 |

    Average Turnaround Time = (25 + 5 + 10 + 33 + 16 + 1) / 6
    = 90 / 6
    = 15.00 time units

    Final answer: the average turnaround time using SJF is 15 time units.

    Average waiting time, for completeness = (17 + 1 + 5 + 24 + 9 + 0) / 6 = 56 / 6 = 9.33 time units.

    Note on the preemptive variant: because every process except P4 and P5 arrives at time 0, and the two that arrive at t = 1 are both longer than the process running at that instant, preemptive SJF (Shortest Remaining Time First) produces exactly the same schedule and the same averages for this particular data. The two versions differ only when a newly arrived process has a shorter remaining time than the one currently running.
15. **Find average turnaround time and average waiting time using round robin and FCFS algorithm?**
| Process | Arrival Time | Execute Time |
|---|---|---|
| P0 | 0 | 5 |
| P1 | 1 | 3 |
| P2 | 2 | 8 |
| P3 | 3 | 6 |
*[Teletalk Assistant Manager (IT) 2023 compact it 467 (ET: N/A)]*


    Answer: Given:

    | Process | Arrival Time | Burst Time |
    |---|---|---|
    | P0 | 0 | 5 |
    | P1 | 1 | 3 |
    | P2 | 2 | 8 |
    | P3 | 3 | 6 |

    The time quantum for Round Robin is not stated in the question, so a quantum of 2 time units is assumed and the value is stated in the answer.

    Definitions used:
    - Turnaround Time (TAT) = Completion Time - Arrival Time
    - Waiting Time (WT) = Turnaround Time - Burst Time
    - Average = sum over all processes divided by the number of processes

    (a) FCFS

    Processes run strictly in order of arrival: P0, P1, P2, P3.

    Gantt chart:
    ```
    |    P0    |  P1  |       P2       |      P3      |
    0          5      8               16             22
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P0 | 0 | 5 | 5 | 5 | 0 |
    | P1 | 1 | 3 | 8 | 7 | 4 |
    | P2 | 2 | 8 | 16 | 14 | 6 |
    | P3 | 3 | 6 | 22 | 19 | 13 |

    Average Turnaround Time = (5 + 7 + 14 + 19) / 4 = 45 / 4 = 11.25 units
    Average Waiting Time = (0 + 4 + 6 + 13) / 4 = 23 / 4 = 5.75 units

    (b) Round Robin, quantum = 2

    Trace of the ready queue: P0 runs first; P1 arrives at t = 1 and P2 at t = 2, both joining the queue; a preempted process is added after any process that arrived during its quantum.

    Gantt chart:
    ```
    |P0|P1|P2|P0|P3|P1|P2|P0|P3|P2|P3|P2|
    0  2  4  6  8 10 11 13 14 16 18 20 22
    ```
    Reading it: P0 0-2, P1 2-4, P2 4-6, P0 6-8, P3 8-10, P1 10-11 (only 1 unit left), P2 11-13, P0 13-14 (1 unit left), P3 14-16, P2 16-18, P3 18-20, P2 20-22.

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P0 | 0 | 5 | 14 | 14 | 9 |
    | P1 | 1 | 3 | 11 | 10 | 7 |
    | P2 | 2 | 8 | 22 | 20 | 12 |
    | P3 | 3 | 6 | 20 | 17 | 11 |

    Average Turnaround Time = (14 + 10 + 20 + 17) / 4 = 61 / 4 = 15.25 units
    Average Waiting Time = (9 + 7 + 12 + 11) / 4 = 39 / 4 = 9.75 units

    Comparison:

    | Algorithm | Average Turnaround Time | Average Waiting Time |
    |---|---|---|
    | FCFS | 11.25 | 5.75 |
    | Round Robin (q = 2) | 15.25 | 9.75 |

    Interpretation: FCFS gives better averages here, because Round Robin interrupts every process repeatedly and each interruption pushes its completion later. Round Robin is nevertheless preferred in an interactive system, because it gives a far better response time: under FCFS, P3 waits 13 units before it runs at all, whereas under Round Robin it first receives the CPU at t = 8, after only 5 units. Averages measure throughput; response time measures how the system feels to a user.

    For reference, with a quantum of 3 the Round Robin figures improve to an average turnaround time of 14.00 and an average waiting time of 8.50, which illustrates that a larger quantum moves Round Robin closer to FCFS.
16. **Starvation in SJF, Starvation free scheduling algorithm name. (Question not clear)** *[RPGCL Assistant Manager (ICT) 2022 compact it 654 (ET: BUET)]*


    Answer:

    Starvation in SJF:

    Starvation, also called indefinite blocking, is the situation in which a process waits in the ready queue for an unbounded length of time and may never receive the CPU.

    Why it occurs in SJF: the algorithm always selects the process with the smallest burst time. If short processes keep arriving, a long process is passed over at every scheduling decision. In a busy system with a continuous stream of short jobs, a long job can wait indefinitely, even though it arrived first. The preemptive variant, Shortest Remaining Time First, makes this worse, because a long process can be preempted repeatedly as short processes arrive.

    Example: suppose P1 needs 100 ms and arrives at t = 0, and a process needing 5 ms arrives every 4 ms thereafter. P1 will never run, because at every decision point a shorter process is available.

    Remedy: ageing. The effective priority of a waiting process is improved gradually as it waits. In SJF this is implemented by subtracting a factor proportional to the waiting time from the effective burst estimate, so that a long-waiting process eventually becomes the best candidate. This is the same technique used to cure starvation in priority scheduling.

    Starvation-free scheduling algorithms:

    - Round Robin: this is the standard answer. Every process is served in turn from a circular queue, so with n processes and quantum q, no process waits longer than (n - 1) x q. Starvation is impossible by construction.

    - First Come First Served: also starvation-free, since a process at the head of the queue is always served next and the queue advances strictly in order. It suffers from the convoy effect but not from starvation.

    - Priority scheduling with ageing: not starvation-free by itself, but made so by raising the priority of waiting processes over time.

    - Multilevel Feedback Queue: made starvation-free by periodically promoting long-waiting processes back to a higher queue, a technique called priority boosting.

    - Fair-share and lottery scheduling: every process holds at least one lottery ticket, so it has a non-zero probability of being selected at every draw, and the probability of never being selected tends to zero.

    - Linux Completely Fair Scheduler: it always selects the process with the smallest accumulated virtual runtime, so a process that has been waiting accumulates no virtual runtime and is guaranteed to be selected before long.

    Summary table:

    | Algorithm | Starvation possible | Reason |
    |---|---|---|
    | FCFS | No | Strict queue order |
    | SJF and SRTF | Yes | Long jobs are always passed over |
    | Priority (without ageing) | Yes | Low-priority jobs are always passed over |
    | Priority (with ageing) | No | Waiting raises the priority |
    | Round Robin | No | Every process is reached within one cycle |
    | Multilevel Feedback Queue | No, with boosting | Long-waiting processes are promoted |

    Distinction worth stating: starvation is not the same as deadlock. In deadlock no process in the set can proceed at all; in starvation the system as a whole is making progress, but one particular process never gets its turn.
17. **Consider the processes P1, P2, P3, P4 given in the below table, arrives for execution in the same order, with Arrival Time 0, and given Burst Time, let's find the average waiting time using the FCFS scheduling algorithm.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 856 (ET: N/A)]*


    Answer: The processes arrive in the order P1, P2, P3, P4, all with arrival time 0. The burst times are not reproduced in the question paper, so the standard set below is used and the full method is shown.

    | Process | Arrival Time | Burst Time (ms) |
    |---|---|---|
    | P1 | 0 | 5 |
    | P2 | 0 | 3 |
    | P3 | 0 | 8 |
    | P4 | 0 | 6 |

    In FCFS the CPU is given to the processes strictly in the order in which they arrive, and once a process starts it runs to completion; the algorithm is non-preemptive.

    Gantt chart:
    ```
    |    P1    |  P2  |       P3       |      P4      |
    0          5      8               16             22
    ```

    Calculation. Since all arrival times are 0, the waiting time of a process is simply the sum of the burst times of all the processes before it.

    | Process | BT | CT | TAT = CT - AT | WT = TAT - BT |
    |---|---|---|---|---|
    | P1 | 5 | 5 | 5 | 0 |
    | P2 | 3 | 8 | 8 | 5 |
    | P3 | 8 | 16 | 16 | 8 |
    | P4 | 6 | 22 | 22 | 16 |

    Average Waiting Time = (0 + 5 + 8 + 16) / 4
    = 29 / 4
    = 7.25 ms

    Average Turnaround Time = (5 + 8 + 16 + 22) / 4 = 51 / 4 = 12.75 ms

    General method for FCFS with all arrivals at zero:
    - The waiting time of the first process is always 0.
    - The waiting time of each subsequent process is the completion time of the one before it.
    - WT(i) = BT(1) + BT(2) + ... + BT(i-1)

    Characteristics of FCFS worth stating:
    - It is non-preemptive and is implemented with a simple FIFO queue, so it is the easiest algorithm to write.
    - It is fair in the sense that no process is starved, since the queue always advances.
    - Its main defect is the convoy effect: if a long process happens to arrive first, every short process behind it waits, and the average waiting time becomes large. In the table above, reversing the order to P2, P1, P4, P3 would give an average waiting time of only 5.25 ms for exactly the same work.
    - The average waiting time under FCFS is therefore highly sensitive to the order of arrival, which makes it unsuitable for time-sharing systems.
18. **Job arrival time and execution time of Operating system tasks table is given, find out- (i) Average waiting time for FCFS (ii) Preemptive SJF (iii) Round Robin (Quantum time: 3) scheduling algorithm** *[Rupali Bank Limited Assistant Network Engineer (ANE) 2021 compact it 925 (ET: CTI)]*


    Answer: The table of arrival and execution times is not reproduced in the question paper, so the standard set below is used and the complete method is shown for all three algorithms.

    | Process | Arrival Time | Burst Time |
    |---|---|---|
    | P1 | 0 | 5 |
    | P2 | 1 | 3 |
    | P3 | 2 | 8 |
    | P4 | 3 | 6 |

    Definitions used:
    - Turnaround Time (TAT) = Completion Time - Arrival Time
    - Waiting Time (WT) = Turnaround Time - Burst Time
    - Average = sum over all processes divided by the number of processes

    (i) FCFS

    FCFS: processes run strictly in order of arrival.
    ```
    |    P1    |  P2  |       P3       |      P4      |
    0          5      8               16             22
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 5 | 5 | 5 | 0 |
    | P2 | 1 | 3 | 8 | 7 | 4 |
    | P3 | 2 | 8 | 16 | 14 | 6 |
    | P4 | 3 | 6 | 22 | 19 | 13 |

    Average Waiting Time = (0 + 4 + 6 + 13) / 4 = 5.75 ms
    Average Turnaround Time = (5 + 7 + 14 + 19) / 4 = 11.25 ms

    (ii) Preemptive SJF, that is Shortest Remaining Time First

    At every arrival the scheduler compares the remaining time of the running process with the burst time of the new arrival, and switches if the new one is shorter.

    Trace:
    - t = 0: only P1 present, P1 runs.
    - t = 1: P2 arrives with 3, while P1 has 4 remaining. 3 is less than 4, so P1 is preempted and P2 runs.
    - t = 2: P3 arrives with 8, while P2 has 2 remaining, so P2 continues.
    - t = 3: P4 arrives with 6, while P2 has 1 remaining, so P2 continues.
    - t = 4: P2 finishes. Remaining are P1 (4), P3 (8), P4 (6); P1 is shortest and runs to completion.
    - t = 8: P4 (6) is shorter than P3 (8), so P4 runs.
    - t = 14: P3 runs last.

    ```
    | P1 |   P2  |    P1    |     P4     |       P3       |
    0    1       4          8           14               22
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 5 | 8 | 8 | 3 |
    | P2 | 1 | 3 | 4 | 3 | 0 |
    | P3 | 2 | 8 | 22 | 20 | 12 |
    | P4 | 3 | 6 | 14 | 11 | 5 |

    Average Waiting Time = (3 + 0 + 12 + 5) / 4 = 20 / 4 = 5.00 units
    Average Turnaround Time = (8 + 3 + 20 + 11) / 4 = 42 / 4 = 10.50 units

    (iii) Round Robin, quantum = 3

    ```
    |  P1  |  P2  |  P3  |  P4  |P1|  P3  |  P4  |  P3  |
    0      3      6      9     12 14     17     20     22
    ```
    Reading it: P1 0-3, P2 3-6 (finishes), P3 6-9, P4 9-12, P1 12-14 (finishes, 2 units left), P3 14-17, P4 17-20 (finishes), P3 20-22 (finishes).

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 5 | 14 | 14 | 9 |
    | P2 | 1 | 3 | 6 | 5 | 2 |
    | P3 | 2 | 8 | 22 | 20 | 12 |
    | P4 | 3 | 6 | 20 | 17 | 11 |

    Average Waiting Time = (9 + 2 + 12 + 11) / 4 = 34 / 4 = 8.50 units
    Average Turnaround Time = (14 + 5 + 20 + 17) / 4 = 56 / 4 = 14.00 units

    Comparison:

    | Algorithm | Average Waiting Time | Average Turnaround Time |
    |---|---|---|
    | FCFS | 5.75 | 11.25 |
    | Preemptive SJF (SRTF) | 5.00 | 10.50 |
    | Round Robin (q = 3) | 8.50 | 14.00 |

    Preemptive SJF gives the lowest averages, which is expected: SRTF is optimal for average waiting time among all algorithms. Round Robin gives the worst averages but the best response time, since every process receives the CPU within one cycle of the queue.
19. **Calculate The Average Waiting Time of SJF scheduling algorithm.** *[Janata Bank Assistant System Administrator 2021 compact it 940 (ET: N/A)]*


    Answer: The process table is not reproduced in the question paper, so the standard set below is used and the complete method of SJF is shown.

    | Process | Arrival Time | Burst Time (ms) |
    |---|---|---|
    | P1 | 0 | 5 |
    | P2 | 1 | 3 |
    | P3 | 2 | 8 |
    | P4 | 3 | 6 |

    SJF (non-preemptive):
    ```
    |    P1    |  P2  |      P4      |       P3       |
    0          5      8             14               22
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 5 | 5 | 5 | 0 |
    | P2 | 1 | 3 | 8 | 7 | 4 |
    | P3 | 2 | 8 | 22 | 20 | 12 |
    | P4 | 3 | 6 | 14 | 11 | 5 |

    Average Waiting Time = (0 + 4 + 12 + 5) / 4 = 5.25 ms
    Average Turnaround Time = (5 + 7 + 20 + 11) / 4 = 10.75 ms

    Method to follow for any such table:
    - At each moment when the CPU becomes free, list the processes that have already arrived and are not yet finished.
    - Choose the one with the smallest burst time; break a tie by arrival order.
    - Run it to completion, since the basic SJF is non-preemptive, and record its completion time.
    - Compute TAT = CT - AT, then WT = TAT - BT, and finally take the averages.

    Important properties of SJF:
    - It gives the minimum possible average waiting time for a given set of processes; no other algorithm can do better on the same data.
    - The proof is intuitive: exchanging a long job with a shorter one that follows it reduces the short job's waiting time by more than it increases the long job's, so the total falls.
    - Its practical difficulty is that burst times are not known before a process runs. They are estimated from the history of previous bursts using an exponential average:
      tau(n+1) = alpha x t(n) + (1 - alpha) x tau(n), typically with alpha = 0.5.
    - It can starve long processes if short ones keep arriving; ageing is the remedy.
    - The preemptive form is called Shortest Remaining Time First, and for this same data it gives an average waiting time of 5.00 ms rather than 5.25 ms.
20. **(a) Define FCFS, SJF and RR algorithm (Quantum=20).** *[National University Assistant Programmer 2020 compact it 977-978 (ET: DU)]*


    Answer:

    First Come First Served (FCFS):
    - The process that requests the CPU first is allocated the CPU first.
    - It is implemented with a simple FIFO queue: an arriving process is placed at the tail, and the process at the head is dispatched.
    - It is non-preemptive: once a process starts, it keeps the CPU until it finishes or blocks for input or output.
    - Advantages: extremely simple to implement and understand; no starvation, since the queue always advances; low scheduling overhead.
    - Disadvantages: the convoy effect, in which one long process at the head delays every short process behind it; a high average waiting time; and a poor response time, which makes it unsuitable for interactive systems.

    Shortest Job First (SJF):
    - The process with the smallest next CPU burst is selected. Ties are broken by arrival order.
    - In its basic form it is non-preemptive. The preemptive form, Shortest Remaining Time First, gives the CPU to a newly arrived process if its burst is shorter than the remaining time of the running one.
    - Advantages: it gives the provably minimum average waiting time and turnaround time for a given set of processes, and therefore the maximum throughput.
    - Disadvantages: the burst time is not known in advance and must be estimated from past behaviour, usually by an exponential average; and long processes can starve if short ones keep arriving, which is cured by ageing.

    Round Robin (RR) with quantum = 20:
    - The ready queue is treated as a circular queue. Each process is given the CPU for at most one time quantum, here 20 time units.
    - If the process finishes or blocks within the quantum, the scheduler moves on. If the quantum expires first, a timer interrupt preempts the process and it is placed at the tail of the queue.
    - It is preemptive, and it is designed for time-sharing systems.
    - Guarantee: with n processes and a quantum q, no process waits more than (n - 1) x q time units before it next receives the CPU. With q = 20 and 5 processes, no process waits more than 80 units.
    - Advantages: fairness, absence of starvation, and a bounded and predictable response time.
    - Disadvantages: a higher average turnaround time than SJF, because each process is interrupted repeatedly, and context-switch overhead that grows as the quantum shrinks.
    - Effect of the quantum: a very large quantum makes Round Robin behave exactly like FCFS, because most processes finish within one slice; a very small quantum gives excellent responsiveness but wastes the CPU on context switches. The usual guidance is that about 80 per cent of bursts should be shorter than the quantum, and the quantum should be at least ten to a hundred times the context-switch time.

    Comparison:

    | Point | FCFS | SJF | Round Robin (q = 20) |
    |---|---|---|---|
    | Preemptive | No | No (SRTF is) | Yes |
    | Selection rule | Order of arrival | Smallest burst | Cyclic turn |
    | Average waiting time | High | Minimum possible | Moderate to high |
    | Response time | Poor | Poor for long jobs | Best, and bounded |
    | Starvation | No | Yes | No |
    | Overhead | Lowest | Low | Higher, one switch per quantum |
    | Suitable for | Batch systems | Batch systems | Time-sharing and interactive systems |
21. **(b) Turnaround time of FCFS and SJF** *[National University Assistant Programmer 2020 compact it 978 (ET: DU)]*


    Answer: The process table is not reproduced in the question paper, so the standard set below is used and the turnaround time is computed for both algorithms.

    | Process | Arrival Time | Burst Time (ms) |
    |---|---|---|
    | P1 | 0 | 5 |
    | P2 | 1 | 3 |
    | P3 | 2 | 8 |
    | P4 | 3 | 6 |

    Turnaround Time = Completion Time - Arrival Time. It measures the total time a process spends in the system, from submission to completion, and therefore includes both the time it spends running and the time it spends waiting.

    Turnaround time under FCFS:

    ```
    |    P1    |  P2  |       P3       |      P4      |
    0          5      8               16             22
    ```

    | Process | AT | BT | CT | TAT = CT - AT |
    |---|---|---|---|---|
    | P1 | 0 | 5 | 5 | 5 |
    | P2 | 1 | 3 | 8 | 7 |
    | P3 | 2 | 8 | 16 | 14 |
    | P4 | 3 | 6 | 22 | 19 |

    Average Turnaround Time = (5 + 7 + 14 + 19) / 4 = 45 / 4 = 11.25 ms

    Turnaround time under SJF (non-preemptive):

    ```
    |    P1    |  P2  |      P4      |       P3       |
    0          5      8             14               22
    ```

    | Process | AT | BT | CT | TAT |
    |---|---|---|---|---|
    | P1 | 0 | 5 | 5 | 5 |
    | P2 | 1 | 3 | 8 | 7 |
    | P3 | 2 | 8 | 22 | 20 |
    | P4 | 3 | 6 | 14 | 11 |

    Average Turnaround Time = (5 + 7 + 20 + 11) / 4 = 43 / 4 = 10.75 ms

    Comparison:

    | Algorithm | Average Turnaround Time |
    |---|---|
    | FCFS | 11.25 ms |
    | SJF | 10.75 ms |

    Observation: SJF gives the lower average, and the difference arises entirely from the order in which P3 and P4 are run. FCFS runs P3 first merely because it arrived first, even though P4 is shorter; SJF runs the shorter one first. Note also that the total elapsed time is 22 ms in both cases, because the same total work is done; only the distribution of waiting among the processes changes. This is the central point about scheduling: it cannot create CPU time, it can only decide who waits.

    Note that individual processes can be worse off under SJF. Here P3's turnaround time rises from 14 to 20 ms, while P4's falls from 19 to 11 ms. The average improves, but at the cost of the longer process, which is exactly why SJF can lead to starvation.
22. **Operating system (OS) scheduling is the key concept of multiprogramming. List and briefly define the major types of OS scheduling.** *[Sonali & Janata Bank Officer (IT) 2020 compact it 985-986 (ET: DU)]* *[Bangladesh Bank Recruitment Test 2020 (ET: N/A)]*


    Answer: Operating system scheduling is organised in three levels, distinguished by how often they run and by which transition of the process state they control.

    1. Long-term scheduler, also called the job scheduler or admission scheduler:
    - Function: it selects which jobs from the job pool on disk are to be brought into main memory and admitted into the ready queue as processes.
    - It therefore controls the degree of multiprogramming, that is the number of processes resident in memory at one time.
    - Frequency: it runs infrequently, perhaps once every several seconds or minutes, so it can afford to be slow and to use a sophisticated policy.
    - Its most important task is to maintain a good mix of CPU-bound and input-output-bound processes. If all resident processes are CPU-bound, the devices are idle; if all are input-output-bound, the CPU is idle.
    - State transition controlled: New to Ready.
    - It is largely absent from modern time-sharing systems such as Unix and Windows, where every submitted process is admitted immediately and the degree of multiprogramming is regulated instead by swapping and by memory pressure.

    2. Short-term scheduler, also called the CPU scheduler or the dispatcher's selector:
    - Function: it selects which of the processes already in the ready queue is to be given the CPU next.
    - Frequency: it runs very often, typically every 10 to 100 milliseconds, so it must be extremely fast. Any time it takes is time stolen from useful work.
    - Its policy is one of the scheduling algorithms: FCFS, SJF, SRTF, priority, Round Robin, or a multilevel feedback queue.
    - State transition controlled: Ready to Running.
    - The component that actually performs the switch, saving the state of the old process, loading the state of the new one and jumping to it, is called the dispatcher, and the time it takes is the dispatch latency.

    3. Medium-term scheduler, also called the swapper:
    - Function: it removes a process from main memory temporarily and stores it on disk, which is called swapping out, and later brings it back, which is called swapping in.
    - Purpose: to reduce the degree of multiprogramming when memory is under pressure, to improve the mix of processes, and to free memory when thrashing begins.
    - Frequency: intermediate, running when memory conditions require it.
    - State transitions controlled: Ready to Suspended-Ready, and Blocked to Suspended-Blocked, and back.
    - It is essential in a system with virtual memory, and it is what prevents a machine from collapsing into thrashing when too many processes are resident.

    Comparison:

    | Point | Long-term | Short-term | Medium-term |
    |---|---|---|---|
    | Other name | Job scheduler | CPU scheduler | Swapper |
    | Selects | Which job enters memory | Which ready process gets the CPU | Which process to swap out or in |
    | Frequency | Seconds to minutes | Milliseconds | Between the two |
    | Speed required | Can be slow | Must be very fast | Moderate |
    | Controls | Degree of multiprogramming | CPU allocation | Degree of multiprogramming under memory pressure |
    | State transition | New to Ready | Ready to Running | Ready or Blocked to Suspended and back |
    | Present in time-sharing systems | Usually absent | Always present | Present with virtual memory |

    How the three work together: the long-term scheduler decides how many processes compete, the short-term scheduler decides which of them runs now, and the medium-term scheduler adjusts the population when memory becomes scarce.
23. **(c) Explain the following Scheduling algorithm: (i) Round Robin (ii) FCFS (iii) Priority scheduling** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026 (ET: N/A)]*


    Answer:

    (i) Round Robin (RR)

    Principle: the ready queue is treated as a circular queue. Each process is given the CPU for at most one fixed time quantum, typically 10 to 100 milliseconds. If it finishes or blocks within the quantum, the scheduler moves to the next process; if the quantum expires first, a timer interrupt preempts it and it is placed at the tail of the queue.

    Characteristics:
    - Preemptive, and designed specifically for time-sharing and interactive systems.
    - Guarantee: with n processes and quantum q, no process waits more than (n - 1) x q before its next turn.
    - Choice of quantum is critical: a very large quantum makes it behave like FCFS, and a very small one wastes the CPU on context switches. The usual rule is that about 80 per cent of bursts should fit within one quantum.

    Advantages: fairness, no starvation, and a bounded and predictable response time.
    Disadvantages: higher average turnaround time than SJF, and context-switch overhead.

    Example with quantum = 2, for P1 = 5, P2 = 3, P3 = 8, P4 = 6 arriving at 0, 1, 2 and 3:
    ```
    |P1|P2|P3|P1|P4|P2|P3|P1|P4|P3|P4|P3|
    0  2  4  6  8 10 11 13 14 16 18 20 22
    ```
    Average waiting time = 9.75 units, average turnaround time = 15.25 units.

    (ii) First Come First Served (FCFS)

    Principle: the process that requests the CPU first is served first. It is implemented with a simple FIFO queue.

    Characteristics:
    - Non-preemptive: a process keeps the CPU until it finishes or blocks.
    - The simplest possible policy, with the lowest scheduling overhead.

    Advantages: trivial to implement; fair in the sense of strict order; no starvation.
    Disadvantages: the convoy effect, in which one long process delays all the short ones behind it; a high average waiting time; and a poor response time that makes it unusable in an interactive system.

    Example with the same data:
    ```
    |    P1    |  P2  |       P3       |      P4      |
    0          5      8               16             22
    ```
    Average waiting time = 5.75 units, average turnaround time = 11.25 units.

    (iii) Priority scheduling

    Principle: every process is assigned a priority number, and the CPU is allocated to the process with the highest priority. Equal priorities are resolved by FCFS.

    Characteristics:
    - It exists in both preemptive and non-preemptive forms. In the preemptive form a newly arrived higher-priority process takes the CPU immediately.
    - Priorities may be internal, computed by the system from measured quantities such as memory use and the ratio of CPU to input-output time, or external, assigned by the administrator on the basis of importance, department or fee paid.
    - Note that SJF is a special case of priority scheduling, in which the priority is the inverse of the predicted burst time.

    Advantages: important and urgent work is served first, which is essential for system processes and for real-time tasks.
    Disadvantages:
    - Starvation, also called indefinite blocking: a low-priority process may never run. The remedy is ageing, in which the priority of a waiting process is raised gradually.
    - Priority inversion: a high-priority process is blocked waiting for a resource held by a low-priority process, which is itself preempted by a medium-priority process. The remedy is priority inheritance, in which the holder temporarily inherits the priority of the waiter. This was the fault that caused repeated resets on the Mars Pathfinder in 1997.

    Example, preemptive, with priorities P1 = 2, P2 = 1, P3 = 4, P4 = 3, lower number meaning higher priority:
    ```
    | P1 |   P2  |    P1    |     P4     |       P3       |
    0    1       4          8           14               22
    ```
    Average waiting time = 5.00 units, average turnaround time = 10.50 units.

    Summary comparison:

    | Point | Round Robin | FCFS | Priority |
    |---|---|---|---|
    | Preemptive | Yes | No | Both forms exist |
    | Selection | Cyclic turn | Order of arrival | Highest priority |
    | Starvation | No | No | Yes, unless ageing is used |
    | Response time | Best, bounded | Poor | Good for high priority, poor for low |
    | Best suited to | Time-sharing | Batch | Real-time and mixed workloads |
24. **Calculate the average waiting time and total turn around time in: (i) Non Preemptive SJF (ii) Preemptive SJF** *[Sundharban Gas Assistant Programmer 2020 compact it 1047 (ET: N/A)]*


    Answer: The process table is not reproduced in the question paper, so the set below is used, chosen so that the preemptive and non-preemptive versions give different results, which is the point of the comparison.

    | Process | Arrival Time | Burst Time (ms) |
    |---|---|---|
    | P1 | 0 | 8 |
    | P2 | 1 | 4 |
    | P3 | 2 | 9 |
    | P4 | 3 | 5 |

    Definitions used:
    - Turnaround Time (TAT) = Completion Time - Arrival Time
    - Waiting Time (WT) = Turnaround Time - Burst Time
    - Average = sum over all processes divided by the number of processes

    (i) Non-preemptive SJF

    Once a process starts it runs to completion; the shortest job is chosen only when the CPU becomes free.

    Trace:
    - t = 0: only P1 has arrived, so it runs to completion at t = 8.
    - t = 8: P2 (4), P3 (9) and P4 (5) are all waiting. P2 is shortest and runs to t = 12.
    - t = 12: P4 (5) is shorter than P3 (9), so P4 runs to t = 17.
    - t = 17: P3 runs to t = 26.

    Gantt chart:
    ```
    |       P1       |  P2  |   P4   |        P3        |
    0                8     12       17                 26
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 8 | 8 | 8 | 0 |
    | P2 | 1 | 4 | 12 | 11 | 7 |
    | P3 | 2 | 9 | 26 | 24 | 15 |
    | P4 | 3 | 5 | 17 | 14 | 9 |

    Average Waiting Time = (0 + 7 + 15 + 9) / 4 = 31 / 4 = 7.75 ms
    Average Turnaround Time = (8 + 11 + 24 + 14) / 4 = 57 / 4 = 14.25 ms
    Total turnaround time = 57 ms

    (ii) Preemptive SJF, that is Shortest Remaining Time First

    At every arrival the remaining time of the running process is compared with the burst time of the newcomer, and the CPU is given to whichever is shorter.

    Trace:
    - t = 0: P1 runs; remaining 8.
    - t = 1: P2 arrives with 4, while P1 has 7 remaining. 4 is less than 7, so P1 is preempted and P2 runs.
    - t = 2: P3 arrives with 9, while P2 has 3 remaining, so P2 continues.
    - t = 3: P4 arrives with 5, while P2 has 2 remaining, so P2 continues.
    - t = 5: P2 finishes. Remaining are P1 (7), P3 (9), P4 (5); P4 is shortest and runs.
    - t = 10: P4 finishes. P1 (7) is shorter than P3 (9), so P1 runs its remaining 7.
    - t = 17: P1 finishes and P3 runs to t = 26.

    Gantt chart:
    ```
    |P1|   P2   |    P4    |       P1       |        P3        |
    0  1        5         10               17                 26
    ```

    | Process | AT | BT | CT | TAT | WT |
    |---|---|---|---|---|---|
    | P1 | 0 | 8 | 17 | 17 | 9 |
    | P2 | 1 | 4 | 5 | 4 | 0 |
    | P3 | 2 | 9 | 26 | 24 | 15 |
    | P4 | 3 | 5 | 10 | 7 | 2 |

    Average Waiting Time = (9 + 0 + 15 + 2) / 4 = 26 / 4 = 6.50 ms
    Average Turnaround Time = (17 + 4 + 24 + 7) / 4 = 52 / 4 = 13.00 ms
    Total turnaround time = 52 ms

    Comparison:

    | Metric | Non-preemptive SJF | Preemptive SJF (SRTF) |
    |---|---|---|
    | Average waiting time | 7.75 ms | 6.50 ms |
    | Average turnaround time | 14.25 ms | 13.00 ms |
    | Total turnaround time | 57 ms | 52 ms |
    | Context switches | Fewer | More |

    Explanation of the difference: in the non-preemptive version P2 and P4, both short, must wait for the long P1 to finish. In the preemptive version P1 is interrupted at t = 1, so the two short processes are dispatched early and their waiting times fall sharply. The long process P1 pays for this, its waiting time rising from 0 to 9 ms, but the total improves because two processes gain more than one loses.

    Note that the total elapsed time is 26 ms in both cases. Scheduling does not create CPU time; it only redistributes waiting. SRTF is optimal for average waiting time among all algorithms, but it needs knowledge of burst times, causes more context switches, and can starve long processes.

## Deadlock & Resource Allocation (22)

1. **What is Deadlock? Given a scenery and find out the process is face deadlock sitiation?** *[IFIC Bank Officer IT 2025 compact it 1448 (ET: IFIC)]*


   Answer: Deadlock is a situation in which a set of processes are permanently blocked, because each process in the set is holding a resource and is waiting for a resource that is held by another process in the same set. No process can proceed, none will release what it holds, and the set waits for ever unless the operating system intervenes.

   Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

   The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

   - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

   - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

   - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

   - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

   How each condition can be attacked, which is the method of deadlock prevention:
   - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
   - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
   - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
   - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.

   Worked scenario, showing how to decide whether a deadlock exists:

   Suppose there are two processes and two non-sharable resources.

   | Time | Process P1 | Process P2 |
   |---|---|---|
   | t1 | Requests and gets R1 | Requests and gets R2 |
   | t2 | Requests R2, which P2 holds, so P1 blocks | Requests R1, which P1 holds, so P2 blocks |

   Resource-allocation graph:
   ```
   R1 ---> P1 ---> R2 ---> P2 ---> R1
   ```
   Reading the edges: R1 is assigned to P1; P1 requests R2; R2 is assigned to P2; P2 requests R1.

   Checking the four conditions:
   - Mutual exclusion: yes, R1 and R2 can be held by only one process at a time.
   - Hold and wait: yes, P1 holds R1 and waits for R2, and P2 holds R2 and waits for R1.
   - No preemption: yes, neither resource can be taken away.
   - Circular wait: yes, the graph contains the cycle P1 -> R2 -> P2 -> R1 -> P1.

   All four hold, and since each resource type has a single instance, the cycle is sufficient. The system is therefore deadlocked, and neither process will ever proceed.

   How the deadlock could have been avoided: if both processes had been required to request the resources in the same order, say R1 before R2, the second process would simply have waited for R1 without holding R2, and the cycle could not form. This is the resource-ordering rule, and it is the technique actually used in real systems.
2. **The four conditions that are necessary for a resource deadlock to occur are mutual exclusion, hold and wait, no preemption and circular wait. Give an example to show that these conditions are not sufficient for a resource deadlock to occur.** *[DPDC Assistant Manager (ICT) 27.06.2025 compact it 1364 (ET: BUET)]*


   Answer: The four Coffman conditions, mutual exclusion, hold and wait, no preemption and circular wait, are necessary for a resource deadlock: if a deadlock exists, all four must hold. They are not sufficient: all four can hold and yet no deadlock occurs.

   The reason: the conditions describe a state in which a deadlock is possible, but whether it actually occurs depends on the number of instances of each resource. A cycle in the resource-allocation graph is sufficient only when every resource type has exactly one instance. When a resource type has several instances, a cycle may exist and still be broken by a process outside the cycle releasing an instance.

   Counter-example with multiple instances:

   Consider two resource types, R1 with two instances and R2 with two instances, and four processes.

   | Process | Holds | Requests |
   |---|---|---|
   | P1 | one instance of R1 | one instance of R2 |
   | P2 | one instance of R2 | one instance of R1 |
   | P3 | one instance of R2 | nothing further |
   | P4 | one instance of R1 | nothing further |

   Resource-allocation graph:
   ```
   R1 ---> P1 ---> R2 ---> P2 ---> R1
   R1 ---> P4
   R2 ---> P3
   ```

   Checking the four conditions:
   - Mutual exclusion: yes, each instance is held exclusively.
   - Hold and wait: yes, P1 holds R1 and waits for R2, and P2 holds R2 and waits for R1.
   - No preemption: yes.
   - Circular wait: yes, the cycle P1 -> R2 -> P2 -> R1 -> P1 exists in the graph.

   All four conditions hold. Yet there is no deadlock, because P3 and P4 are not waiting for anything. P3 will finish and release its instance of R2, which is then given to P1; P1 completes and releases its instance of R1, which is given to P2; P2 completes. The cycle is broken from outside, and every process eventually finishes.

   Simpler counter-example: a single resource type with two instances and two processes, each holding one instance and each requesting one more. A cycle exists in the graph, but if a third process holding nothing is about to release an instance, or if either of the two can be persuaded to release, no deadlock occurs.

   Conclusion in one sentence: the four conditions guarantee only that a deadlock could occur. A deadlock actually occurs when, in addition, no process outside the cycle can release the resources needed to break it. This is precisely why a detection algorithm must examine the whole allocation state, as Banker's algorithm does, rather than merely look for a cycle.
3. **(a) Define operating system. Why resource allocation graph used for deadlock detection?** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1446 (ET: N/A)]*


   Answer:

   Definition of an operating system:

   An operating system is the system software that acts as an intermediary between the user or the application programs and the computer hardware. It manages all the hardware and software resources of the machine and provides an environment in which programs can be executed conveniently and efficiently.

   Its principal functions:
   - Process management: creation, scheduling, synchronisation and termination of processes.
   - Memory management: allocation and deallocation of main memory, virtual memory, paging and segmentation.
   - File system management: creation, deletion, organisation and protection of files and directories.
   - Device management: control of input and output devices through device drivers, buffering and spooling.
   - Security and protection: user authentication, access control and isolation of processes from one another.
   - Resource allocation: deciding which process receives which resource and for how long.
   - User interface: a command-line interface, a graphical interface, or both.
   - Error detection and handling.

   Examples: Linux, Windows, macOS, Unix, Android and iOS.

   A resource-allocation graph is a directed graph used to describe the state of resource allocation in a system.

   Components:
   - Processes are drawn as circles: P1, P2, and so on.
   - Resource types are drawn as rectangles, with one dot inside for each instance of that type.
   - A request edge runs from a process to a resource type: Pi -> Rj means Pi has requested an instance of Rj and is waiting.
   - An assignment edge runs from a resource instance to a process: Rj -> Pi means one instance of Rj is allocated to Pi.

   Why it is used for deadlock detection:
   - It makes the circular wait condition, which is otherwise abstract, directly visible as a cycle in a picture.
   - The fundamental theorem is simple to apply:
     - If the graph contains no cycle, then no deadlock exists. This is always true.
     - If the graph contains a cycle and every resource type has exactly one instance, then a deadlock exists. The cycle is both necessary and sufficient.
     - If the graph contains a cycle and some resource type has several instances, then a deadlock may or may not exist. The cycle is necessary but not sufficient, and a further test is needed.
   - Cycle detection in a directed graph is a standard algorithm, running in O(n^2) time for n vertices, so the test is cheap enough to run periodically.
   - The graph can be reduced to a wait-for graph, obtained by removing the resource nodes and joining processes directly, which is what a detection algorithm actually searches when every resource type has a single instance.

   Example of a deadlock:
   ```
   P1 ---> R1 ---> P2
    ^                |
    |                v
   R2 <------------ (P2 holds R2)
   ```
   In words: P1 holds R2 and requests R1; P2 holds R1 and requests R2. The cycle P1 -> R1 -> P2 -> R2 -> P1 exists, each resource has one instance, and therefore the system is deadlocked.
4. **What is Deadlock? Write Conditions for Deadlock and also write Deadlock.** *[BUET Assistant Programmer 21.06.2025 compact it 1434 (ET: BUET)]*


   Answer: Deadlock is a situation in which a set of processes are permanently blocked, because each process in the set is holding a resource and is waiting for a resource that is held by another process in the same set. No process can proceed, none will release what it holds, and the set waits for ever unless the operating system intervenes.

   Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

   The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

   - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

   - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

   - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

   - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

   How each condition can be attacked, which is the method of deadlock prevention:
   - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
   - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
   - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
   - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.

   Four approaches to handling deadlock:

   1. Deadlock prevention: design the system so that at least one of the four necessary conditions can never hold. The circular wait condition is the one usually attacked, by numbering all resource types and requiring requests in ascending order. Prevention is conservative and reduces resource utilisation.

   2. Deadlock avoidance: allow all four conditions, but examine every resource request before granting it and refuse any request that could lead to an unsafe state. The system needs advance information about the maximum demand of every process. The standard algorithm is Banker's algorithm, with the resource-allocation graph algorithm used when there is a single instance of each resource type. Avoidance keeps the system in a safe state, in which a sequence exists that lets every process finish.

   3. Deadlock detection and recovery: allow deadlocks to occur, detect them by periodically searching the wait-for graph for a cycle, and then recover. Recovery is by process termination, either aborting all deadlocked processes or aborting them one at a time until the cycle breaks, or by resource preemption, in which a resource is taken from a victim and the victim is rolled back to a safe checkpoint. The victim is chosen to minimise cost, considering priority, elapsed run time, resources held and how many more it needs. Starvation must be avoided by not choosing the same victim every time.

   4. Ignore the problem: assume deadlocks are rare and let the system administrator restart the machine if one occurs. This is called the ostrich algorithm, and it is what Unix, Linux and Windows actually do for most resources, because the cost of prevention or avoidance is judged higher than the cost of an occasional restart.

   Comparison:

   | Approach | Resource utilisation | Overhead | Used in practice |
   |---|---|---|---|
   | Prevention | Low | Low at run time | Yes, through lock ordering |
   | Avoidance | Medium | High, checked on every request | Rarely; needs advance knowledge |
   | Detection and recovery | High | Periodic detection cost | In database systems |
   | Ignore | Highest | None | Most general-purpose operating systems |

   Note on database systems: they do use detection and recovery. A transaction that is chosen as the victim of a deadlock is rolled back and restarted automatically, which is possible because transactions are atomic by design.
5. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances).** *[Bangladesh Bank Assistant Director (ICT) 07.02.2025 compact it 1321 (ET: DU)]*
   * (a) Need matrix
   * (b) Safe state or Unsafe
   Snapshot at time T_0:
The content of the matrix. Need is defined to be Max – Allocation.


   Answer: Given: 5 processes P0 to P4, and 3 resource types A (10 instances), B (5 instances), C (7 instances).

   Snapshot at time T0 (the standard example):

   | Process | Allocation A B C | Max A B C |
   |---|---|---|
   | P0 | 0 1 0 | 7 5 3 |
   | P1 | 2 0 0 | 3 2 2 |
   | P2 | 3 0 2 | 9 0 2 |
   | P3 | 2 1 1 | 2 2 2 |
   | P4 | 0 0 2 | 4 3 3 |

   Step 1 - compute the Available vector.
   - Total instances: A = 10, B = 5, C = 7
   - Total allocated: A = 0+2+3+2+0 = 7, B = 1+0+0+1+0 = 2, C = 0+0+2+1+2 = 5
   - Available = Total - Allocated = (10-7, 5-2, 7-5) = (3, 3, 2)

   Step 2 - compute the Need matrix, where Need = Max - Allocation.

   | Process | Allocation | Max | Need = Max - Allocation |
   |---|---|---|---|
   | P0 | 0 1 0 | 7 5 3 | 7 4 3 |
   | P1 | 2 0 0 | 3 2 2 | 1 2 2 |
   | P2 | 3 0 2 | 9 0 2 | 6 0 0 |
   | P3 | 2 1 1 | 2 2 2 | 0 1 1 |
   | P4 | 0 0 2 | 4 3 3 | 4 3 1 |

   Step 3 - run the safety algorithm.

   Initialise Work = Available = (3, 3, 2) and Finish[i] = false for every process. Repeatedly find a process whose Need is less than or equal to Work, mark it finished, and add its Allocation back to Work.

   | Step | Process chosen | Need | Work before | Allocation released | Work after |
   |---|---|---|---|---|---|
   | 1 | P1 | 1 2 2 | 3 3 2 | 2 0 0 | 5 3 2 |
   | 2 | P3 | 0 1 1 | 5 3 2 | 2 1 1 | 7 4 3 |
   | 3 | P4 | 4 3 1 | 7 4 3 | 0 0 2 | 7 4 5 |
   | 4 | P0 | 7 4 3 | 7 4 5 | 0 1 0 | 7 5 5 |
   | 5 | P2 | 6 0 0 | 7 5 5 | 3 0 2 | 10 5 7 |

   Checking each step:
   - P0 first: Need (7,4,3) against Work (3,3,2). 7 > 3, so P0 cannot proceed. Try the next.
   - P1: Need (1,2,2) against Work (3,3,2). Every component fits, so P1 can finish. Work becomes (3,3,2) + (2,0,0) = (5,3,2).
   - P2: Need (6,0,0) against Work (5,3,2). 6 > 5, so not yet.
   - P3: Need (0,1,1) against Work (5,3,2). It fits, so P3 finishes. Work becomes (5,3,2) + (2,1,1) = (7,4,3).
   - P4: Need (4,3,1) against Work (7,4,3). It fits, so P4 finishes. Work becomes (7,4,3) + (0,0,2) = (7,4,5).
   - P0: Need (7,4,3) against Work (7,4,5). It fits, so P0 finishes. Work becomes (7,4,5) + (0,1,0) = (7,5,5).
   - P2: Need (6,0,0) against Work (7,5,5). It fits, so P2 finishes. Work becomes (7,5,5) + (3,0,2) = (10,5,7).

   All five processes reached Finish = true, and Work has returned to the total (10, 5, 7), which confirms that every resource has been returned.

   Conclusion: the system is in a safe state, and a safe sequence is

   < P1, P3, P4, P0, P2 >

   Other safe sequences also exist, for example < P1, P3, P4, P2, P0 >, and the existence of at least one is what matters.

   Answers to the two parts as asked:
   - (a) The Need matrix is: P0 (7,4,3), P1 (1,2,2), P2 (6,0,0), P3 (0,1,1), P4 (4,3,1).
   - (b) The system is in a safe state, and a safe sequence is < P1, P3, P4, P0, P2 >.

   Notes on the method:
   - Banker's algorithm is a deadlock avoidance technique. Every request is granted only if the resulting state would still be safe.
   - A safe state is one in which there exists at least one ordering of the processes such that each can obtain its remaining need from the currently available resources plus the resources released by those before it.
   - A safe state is never deadlocked. An unsafe state is not necessarily deadlocked, but it may become so, and the algorithm refuses to enter one.
   - The algorithm requires that each process declare its maximum demand in advance, which is its main practical limitation and the reason it is rarely used in general-purpose systems.
   - The safety algorithm runs in O(m x n^2) time for m resource types and n processes.

   Handling a request, which is the second half of the algorithm: if process Pi requests a vector Request(i), the system first checks that Request(i) is less than or equal to Need(i), then that Request(i) is less than or equal to Available. If both hold, it pretends to allocate, recomputes the state, and runs the safety algorithm. If the result is safe the allocation is confirmed; otherwise Pi must wait and the old state is restored.
6. **(a) Explain Circular wait deadlock.** *[Titas Gas Assistant Engineer (CSE) 24.05.2024 compact it 415 (ET: BUET)]*


   Answer: Circular wait is one of the four necessary conditions for deadlock, stated by Coffman.

   Definition: circular wait exists when a set of waiting processes P0, P1, ..., Pn is such that P0 is waiting for a resource held by P1, P1 is waiting for a resource held by P2, and so on, until Pn is waiting for a resource held by P0. The chain of waiting closes into a circle, so no process in the set can ever proceed.

   Formally, the wait-for graph contains a cycle.

   Simple example with two processes:
   ```
   P1 holds R1 and requests R2
   P2 holds R2 and requests R1
   ```
   Graph:
   ```
   R1 ---> P1 ---> R2 ---> P2 ---> R1
   ```
   P1 cannot continue without R2, which P2 will not release until it gets R1, which P1 will not release until it gets R2. Both wait for ever.

   Example with three processes:
   ```
   P1 holds R1, waits for R2
   P2 holds R2, waits for R3
   P3 holds R3, waits for R1
   ```
   The cycle P1 -> R2 -> P2 -> R3 -> P3 -> R1 -> P1 exists.

   Everyday analogy: four cars arrive simultaneously at a four-way crossing with no traffic signal, each entering the junction and each blocked by the car on its right. All four wait for ever unless one reverses.

   Relationship with the other conditions: circular wait cannot occur unless hold and wait also holds, because a process must be holding something while waiting for something else. In that sense circular wait implies hold and wait, but the reverse is not true.

   Important qualification: a cycle in the resource-allocation graph is sufficient for deadlock only when every resource type has exactly one instance. If a resource type has several instances, a cycle may exist without deadlock, because a process outside the cycle may release an instance and break it.

   How circular wait is prevented, which is the practical method used in real systems:
   - Impose a total ordering on all resource types, giving each a number, and require every process to request resources only in increasing order of that number.
   - Proof that this works: suppose a cycle existed. Then some process would have to request a resource numbered lower than one it already holds, which the rule forbids. Hence no cycle can form.
   - Example: number the mutexes in a kernel and always acquire them in ascending order. The Linux kernel enforces exactly this discipline, and the lockdep tool checks it automatically.

   Practical illustration in code:
   ```c
   /* Deadlock-prone: the two threads take the locks in opposite orders */
   Thread 1: lock(A); lock(B); ... unlock(B); unlock(A);
   Thread 2: lock(B); lock(A); ... unlock(A); unlock(B);

   /* Safe: both threads take the locks in the same order */
   Thread 1: lock(A); lock(B); ... unlock(B); unlock(A);
   Thread 2: lock(A); lock(B); ... unlock(B); unlock(A);
   ```
   The second version cannot deadlock, whatever the interleaving of the two threads.
7. **Give the necessary conditions for deadlock to occur. Is it possible to have deadlock involving only a single process? Explain your answer.** *[Combined 2 Bank (Sonali & Janata) Officer IT 04.10.2024 compact it 422 (ET: BIBM)]*


   Answer: The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

   - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

   - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

   - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

   - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

   How each condition can be attacked, which is the method of deadlock prevention:
   - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
   - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
   - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
   - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.

   Is it possible to have a deadlock involving only a single process?

   The answer depends on how strictly the definition is applied, and a good answer states both sides.

   Under the strict definition, no.
   - Circular wait requires a cycle P0 -> P1 -> ... -> Pn -> P0 with at least two distinct processes. A single process cannot wait for a resource held by another process, because there is no other process.
   - The formal definition of deadlock speaks of a set of processes in which each waits for an event that only another process in the set can cause. With one process there is no other process to cause the event.
   - Therefore, by the textbook definition, a single-process deadlock is impossible.

   In practice, however, a single process can block itself permanently, and the effect is indistinguishable from deadlock. This is called self-deadlock.

   Case 1, a non-recursive lock taken twice:
   ```c
   pthread_mutex_lock(&m);
   ...
   pthread_mutex_lock(&m);   /* blocks for ever: the thread waits for itself */
   ```
   The thread holds the mutex and waits for the same mutex. It will never release it, because it is blocked, so it waits for ever. Formally this is a cycle of length one in the wait-for graph. A recursive mutex avoids the problem by allowing the same thread to lock it repeatedly.

   Case 2, requesting a resource it already holds exclusively, for example opening a file for exclusive write while already holding an exclusive write lock on it.

   Case 3, a process waiting on a semaphore or a condition variable that only it could signal.

   Case 4, deadlock with a device: a process holds a tape drive and requests a second one when only one exists in the system. Strictly this is starvation with a single process rather than a cycle.

   Conclusion to give in an answer: under the classical four-condition definition, deadlock requires at least two processes, because circular wait cannot be satisfied by one. But a single thread can block itself permanently by acquiring a non-recursive lock twice, and operating system texts recognise this as self-deadlock. Real lock-checking tools such as lockdep in Linux report it as a deadlock, because the practical consequence is the same.
8. **Deadlock এর চারটি শর্ত লিখ।** *[BTCL - JAM ( Technical) 05.04.2024 compact it 381 (ET: BUET)]*


   Answer: Deadlock এর চারটি শর্ত (Coffman conditions), যেগুলো একসঙ্গে বিদ্যমান থাকলেই কেবল deadlock ঘটতে পারে:

   - পারস্পরিক বর্জন (Mutual Exclusion): অন্তত একটি রিসোর্স এমন হতে হবে যা একই সময়ে কেবল একটি প্রসেস ব্যবহার করতে পারে। যেমন প্রিন্টার বা রাইট লক। একটি রিড-অনলি ফাইল এই শর্ত পূরণ করে না, কারণ তা একসঙ্গে অনেকে পড়তে পারে।

   - ধরে রেখে অপেক্ষা (Hold and Wait): একটি প্রসেস অন্তত একটি রিসোর্স ধরে রেখে অন্য একটি রিসোর্সের জন্য অপেক্ষা করছে, যা অন্য প্রসেসের দখলে আছে।

   - অপ্রত্যাহারযোগ্যতা (No Preemption): কোনো প্রসেসের দখলে থাকা রিসোর্স জোর করে কেড়ে নেওয়া যায় না। প্রসেসটি কাজ শেষ করে স্বেচ্ছায় ছেড়ে দিলে তবেই তা মুক্ত হয়।

   - চক্রাকার অপেক্ষা (Circular Wait): অপেক্ষমাণ প্রসেসগুলোর এমন একটি সেট থাকতে হবে যেখানে P0 অপেক্ষা করছে P1 এর দখলে থাকা রিসোর্সের জন্য, P1 অপেক্ষা করছে P2 এর জন্য, এবং শেষে Pn অপেক্ষা করছে P0 এর দখলে থাকা রিসোর্সের জন্য। অর্থাৎ wait-for গ্রাফে একটি চক্র (cycle) তৈরি হয়।

   গুরুত্বপূর্ণ বিষয়: এই চারটি শর্ত deadlock এর জন্য প্রয়োজনীয় (necessary), কিন্তু সবসময় যথেষ্ট (sufficient) নয়। কোনো রিসোর্স টাইপের একাধিক ইনস্ট্যান্স থাকলে চক্র থাকা সত্ত্বেও deadlock নাও হতে পারে, কারণ চক্রের বাইরের কোনো প্রসেস রিসোর্স ছেড়ে দিয়ে চক্রটি ভেঙে দিতে পারে। প্রতিটি রিসোর্স টাইপের একটিমাত্র ইনস্ট্যান্স থাকলে অবশ্য চক্র থাকা মানেই deadlock।

   প্রতিরোধের কৌশল (Deadlock Prevention): চারটি শর্তের যেকোনো একটি ভেঙে দিলেই deadlock অসম্ভব হয়ে যায়।
   - Mutual exclusion ভাঙা: সম্ভব হলে রিসোর্স ভাগাভাগিযোগ্য করা, যেমন প্রিন্টারের জন্য স্পুলিং ব্যবহার।
   - Hold and wait ভাঙা: প্রসেস শুরুর আগেই সব রিসোর্স একসঙ্গে চাইতে বাধ্য করা, অথবা নতুন কিছু চাওয়ার আগে হাতের সব ছেড়ে দিতে বলা।
   - No preemption ভাঙা: অপেক্ষমাণ প্রসেসের রিসোর্স কেড়ে নেওয়ার অনুমতি দেওয়া, যা কেবল সেই রিসোর্সের ক্ষেত্রেই সম্ভব যার অবস্থা সংরক্ষণ ও পুনরুদ্ধার করা যায়।
   - Circular wait ভাঙা: সব রিসোর্সকে ক্রমিক নম্বর দিয়ে সাজিয়ে প্রতিটি প্রসেসকে কেবল ঊর্ধ্বক্রমে রিসোর্স চাইতে বাধ্য করা। বাস্তবে এই পদ্ধতিটিই সবচেয়ে বেশি ব্যবহৃত হয়।
9. **What is deadlock? Draw its diagram.** *[BKSP Assistant Programmer 13.07.2024 compact it 1457 (ET: N/A)]*


   Answer: Deadlock is a situation in which a set of processes are permanently blocked, because each process in the set is holding a resource and is waiting for a resource that is held by another process in the same set. No process can proceed, none will release what it holds, and the set waits for ever unless the operating system intervenes.

   Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

   Resource-allocation graph showing a deadlock:

   ```mermaid
   flowchart LR
     P1((P1)) -- requests --> R2[R2]
     R2 -- assigned to --> P2((P2))
     P2 -- requests --> R1[R1]
     R1 -- assigned to --> P1
   ```

   In the notation of the textbook diagram:
   ```
        +---------+                 +---------+
        |   R1    |---assigned----->|   P1    |
        +---------+                 +---------+
             ^                            |
             |                            | requests
          requests                        v
        +---------+                 +---------+
        |   P2    |<---assigned-----|   R2    |
        +---------+                 +---------+
   ```

   Reading it: R1 is allocated to P1, and P1 has requested R2; R2 is allocated to P2, and P2 has requested R1. The edges form the cycle P1 -> R2 -> P2 -> R1 -> P1. Since each resource type has a single instance, the cycle proves that the system is deadlocked.

   The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

   - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

   - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

   - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

   - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

   How each condition can be attacked, which is the method of deadlock prevention:
   - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
   - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
   - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
   - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
10. **(ক) Deadlock কী? Deadlock Handling করার বিভিন্ন উপায়সমূহ আলোচনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 413 (ET: N/A)]*


    Answer: Deadlock হলো এমন একটি অবস্থা, যেখানে কতগুলো প্রসেসের একটি সেট স্থায়ীভাবে অবরুদ্ধ হয়ে পড়ে, কারণ সেটের প্রতিটি প্রসেস একটি রিসোর্স দখল করে রেখেছে এবং একই সেটের অন্য কোনো প্রসেসের দখলে থাকা রিসোর্সের জন্য অপেক্ষা করছে। ফলে কেউই এগোতে পারে না এবং কেউই নিজের দখলের রিসোর্স ছাড়ে না।

    উদাহরণ: এক লেনের সেতুর দুই প্রান্ত থেকে দুটি গাড়ি উঠে পড়ল। প্রত্যেকে সেতুর অর্ধেক দখল করে আছে এবং অন্যজনের পিছিয়ে যাওয়ার অপেক্ষায় আছে। কেউই নড়তে পারবে না।

    চারটি প্রয়োজনীয় শর্ত: Mutual Exclusion, Hold and Wait, No Preemption এবং Circular Wait। এই চারটি একসঙ্গে না থাকলে deadlock ঘটতে পারে না।

    Deadlock Handling এর চারটি পদ্ধতি:

    ১. Deadlock Prevention (প্রতিরোধ):
    সিস্টেমকে এমনভাবে গড়ে তোলা হয় যাতে চারটি শর্তের অন্তত একটি কখনোই সত্য না হয়।
    - Mutual exclusion ভাঙা: সম্ভব হলে রিসোর্স ভাগাভাগিযোগ্য করা, যেমন প্রিন্টারের ক্ষেত্রে স্পুলিং ব্যবহার। তবে প্রকৃত অভাগাযোগ্য রিসোর্সে এটি ভাঙা যায় না।
    - Hold and wait ভাঙা: প্রসেসকে শুরুর আগেই সব রিসোর্স একসঙ্গে চাইতে বাধ্য করা, অথবা নতুন কিছু চাওয়ার আগে হাতের সব ছেড়ে দিতে বলা। অসুবিধা: রিসোর্স ব্যবহার কমে যায় এবং starvation হতে পারে।
    - No preemption ভাঙা: অপেক্ষমাণ প্রসেসের হাত থেকে রিসোর্স কেড়ে নেওয়ার ব্যবস্থা রাখা। এটি কেবল সেই রিসোর্সে সম্ভব যার অবস্থা সংরক্ষণ ও পুনরুদ্ধার করা যায়, যেমন সিপিইউ রেজিস্টার বা মেমোরি; অর্ধেক ছাপা প্রিন্টারে সম্ভব নয়।
    - Circular wait ভাঙা: সব রিসোর্স টাইপকে ক্রমিক নম্বর দিয়ে প্রতিটি প্রসেসকে কেবল ঊর্ধ্বক্রমে রিসোর্স চাইতে বাধ্য করা। বাস্তবে এটিই সবচেয়ে ব্যবহারযোগ্য পদ্ধতি; লিনাক্স কার্নেলে lock ordering নিয়ম এভাবেই কাজ করে।

    ২. Deadlock Avoidance (পরিহার):
    চারটি শর্তই থাকতে দেওয়া হয়, কিন্তু প্রতিটি রিসোর্স অনুরোধ অনুমোদনের আগে পরীক্ষা করে দেখা হয় যে অনুমোদন দিলে সিস্টেম অনিরাপদ (unsafe) অবস্থায় চলে যাবে কিনা। গেলে অনুরোধটি স্থগিত রাখা হয়।
    - প্রধান অ্যালগরিদম: Banker's Algorithm, যা একাধিক ইনস্ট্যান্সের রিসোর্সে কাজ করে।
    - প্রতিটি রিসোর্স টাইপের একটিমাত্র ইনস্ট্যান্স থাকলে Resource-Allocation Graph অ্যালগরিদম ব্যবহার করা যায়।
    - শর্ত: প্রতিটি প্রসেসকে আগেই তার সর্বোচ্চ চাহিদা ঘোষণা করতে হয়, যা বাস্তবে বড় সীমাবদ্ধতা।
    - Safe state মানে এমন একটি ক্রম বিদ্যমান, যাতে প্রতিটি প্রসেস তার প্রয়োজন মিটিয়ে শেষ করতে পারে। Safe state এ কখনো deadlock হয় না।

    ৩. Deadlock Detection and Recovery (শনাক্তকরণ ও পুনরুদ্ধার):
    Deadlock ঘটতে দেওয়া হয়, তারপর তা শনাক্ত করে সারানো হয়।
    - শনাক্তকরণ: wait-for গ্রাফে চক্র খোঁজা হয়। একাধিক ইনস্ট্যান্সের ক্ষেত্রে Banker's algorithm এর মতো একটি detection algorithm চালানো হয়।
    - পুনরুদ্ধারের উপায় দুটি:
      - প্রসেস বাতিল করা: সব deadlocked প্রসেস একসঙ্গে বাতিল করা, অথবা একটি একটি করে বাতিল করে প্রতিবার পরীক্ষা করা যে চক্রটি ভাঙল কিনা।
      - রিসোর্স কেড়ে নেওয়া: একটি প্রসেসকে victim নির্বাচন করে তার রিসোর্স নিয়ে নেওয়া এবং প্রসেসটিকে নিরাপদ চেকপয়েন্টে rollback করা।
    - Victim নির্বাচনে বিবেচ্য: প্রসেসের অগ্রাধিকার, ইতোমধ্যে চলা সময়, দখলে থাকা রিসোর্স ও আরও কত লাগবে। একই প্রসেস বারবার victim হলে starvation হবে, তাই তা এড়াতে হবে।

    ৪. Ignore the Problem (উপেক্ষা করা):
    Deadlock বিরল ধরে নিয়ে কোনো ব্যবস্থাই না নেওয়া, এবং ঘটলে ব্যবহারকারী বা প্রশাসক সিস্টেম রিস্টার্ট করবেন। একে বলা হয় "ostrich algorithm"। ইউনিক্স, লিনাক্স ও উইন্ডোজসহ প্রায় সব সাধারণ অপারেটিং সিস্টেম বাস্তবে এই পথই নেয়, কারণ প্রতিরোধ বা পরিহারের খরচ মাঝেমধ্যে রিস্টার্ট করার খরচের চেয়ে বেশি।

    তুলনামূলক সারণি:

    | পদ্ধতি | রিসোর্স ব্যবহার | ওভারহেড | বাস্তব ব্যবহার |
    |---|---|---|---|
    | Prevention | কম | কম | হ্যাঁ, lock ordering আকারে |
    | Avoidance | মাঝারি | বেশি, প্রতিটি অনুরোধে পরীক্ষা | কদাচিৎ; আগাম তথ্য দরকার |
    | Detection & Recovery | বেশি | পর্যায়ক্রমিক পরীক্ষার খরচ | ডেটাবেজ ব্যবস্থায় ব্যবহৃত |
    | Ignore | সর্বোচ্চ | নেই | অধিকাংশ সাধারণ অপারেটিং সিস্টেমে |

    উল্লেখযোগ্য: ডেটাবেজ ব্যবস্থাপনা সিস্টেম detection and recovery ব্যবহার করে। Deadlock শনাক্ত হলে একটি ট্রানজেকশনকে victim করে rollback ও restart করা হয়, যা সম্ভব কারণ ট্রানজেকশন নকশাগতভাবেই পরমাণুসদৃশ (atomic)।
11. **What are the four necessary condition of deadlock in an operating system?** *[Milk Vita Assistant Manager (CSE/MIS) 2023 compact it 472 (ET: N/A)]*


    Answer: The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

    - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

    - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

    - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

    - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

    How each condition can be attacked, which is the method of deadlock prevention:
    - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
    - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
    - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
    - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
12. **(a) What is deadlock in operating system (OS)? What are the four necessary and sufficient conditions behind deadlock?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*


    Answer: Deadlock is a situation in which a set of processes are permanently blocked, because each process in the set is holding a resource and is waiting for a resource that is held by another process in the same set. No process can proceed, none will release what it holds, and the set waits for ever unless the operating system intervenes.

    Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

    The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

    - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

    - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

    - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

    - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

    How each condition can be attacked, which is the method of deadlock prevention:
    - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
    - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
    - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
    - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.

    An important correction to the wording of the question: these four conditions are necessary but they are not sufficient. If a deadlock exists, all four must hold; but all four can hold and no deadlock occur.

    Why they are not sufficient: a cycle in the resource-allocation graph is sufficient only when every resource type has exactly one instance. If a resource type has several instances, a cycle can exist while a process outside the cycle still holds an instance that it is about to release, and that release breaks the cycle. In such a case all four conditions hold, yet every process eventually finishes.

    Example: R1 and R2 each have two instances. P1 holds an instance of R1 and waits for R2; P2 holds an instance of R2 and waits for R1; P3 holds the second instance of R2 and is waiting for nothing; P4 holds the second instance of R1 and is waiting for nothing. All four conditions hold and the graph contains a cycle, but P3 and P4 will finish and release their instances, so no deadlock occurs.

    The correct statement is therefore: circular wait, together with the other three conditions, is necessary for deadlock; it is sufficient only in a system where every resource type has a single instance.
13. **(b) A system has P processes each needing a maximum of m resources and a total of r resources available. Which conditions must hold to make the system deadlock free?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 492 (ET: N/A)]*


    Answer: Given: P processes, each needing a maximum of m resources, and a total of r resources available, all of the same type.

    The condition for the system to be deadlock free is:

    r >= P x (m - 1) + 1

    Equivalently, r > P x (m - 1).

    Derivation of the condition:

    - Consider the worst possible situation. Deadlock is most likely when every process has been given as many resources as it can hold without being able to finish, that is (m - 1) resources each. At that point every process needs exactly one more resource to complete.

    - The number of resources held in this worst case is P x (m - 1).

    - If even one resource remains free after this allocation, it can be given to any one process, which then reaches its maximum of m, completes its work and releases all m of its resources. Those m resources are then available for the remaining processes, and the same argument repeats until every process has finished.

    - Therefore the system is guaranteed to be deadlock free if
      r >= P x (m - 1) + 1

    - Conversely, if r = P x (m - 1), the resources can be divided so that every process holds (m - 1) and none can obtain the one further resource it needs. Every process waits for ever, and the system is deadlocked.

    Worked examples:

    Example 1: P = 3 processes, each needing a maximum of m = 4 resources.
    - Required r >= 3 x (4 - 1) + 1 = 3 x 3 + 1 = 10
    - With r = 10 the system is safe. With r = 9, the nine resources could be split three each; every process would then hold 3 and need 1 more, and none could get it, so a deadlock is possible.

    Example 2: P = 5, m = 2.
    - Required r >= 5 x (2 - 1) + 1 = 6
    - With 6 resources the system is deadlock free.

    Example 3: P = 2, m = 3.
    - Required r >= 2 x (3 - 1) + 1 = 5

    The equivalent form often quoted: writing the maximum need of process i as Si, the general condition is

    sum of all Si < r + P

    that is, the total of the maximum needs must be less than the number of resources plus the number of processes. When every Si equals m this reduces to P x m < r + P, that is r > P x (m - 1), which is the same result.

    Assumptions behind the condition:
    - All the resources are of one type and are interchangeable.
    - Resources are requested and released one at a time.
    - A process releases all its resources when it finishes.
    - Each process needs at most m resources at any moment.
14. **Name and define characteristics properties of the Deadlock situation in a computer system.** *[BPSC (Ministry of Agriculture) Assistant Programmer 15.02.2022 compact it 677 (ET: N/A)]*


    Answer: The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

    - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

    - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

    - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

    - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

    How each condition can be attacked, which is the method of deadlock prevention:
    - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
    - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
    - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
    - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
15. **(b) What are the conditions for deadlock situations? Explain briefly.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*


    Answer: The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

    - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

    - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

    - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

    - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

    How each condition can be attacked, which is the method of deadlock prevention:
    - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
    - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
    - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
    - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
16. **Banker's Algorithm: 5 processes P_0 through P_4; 3 resource types A (10 instances), B (5 instances), and C (7 instances). Snapshot at time T_0. The content of the matrix. Need is defined to be \text{Max} - \text{Allocation}. Check that \text{Request} \le \text{Available}. Executing safety algorithm shows that sequence \langle P_1, P_3, P_4, P_0, P_2 \rangle satisfies safety requirement.** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 855 (ET: N/A)]*


    Answer: Given: 5 processes P0 to P4, and 3 resource types A (10 instances), B (5 instances), C (7 instances).

    Snapshot at time T0 (the standard example):

    | Process | Allocation A B C | Max A B C |
    |---|---|---|
    | P0 | 0 1 0 | 7 5 3 |
    | P1 | 2 0 0 | 3 2 2 |
    | P2 | 3 0 2 | 9 0 2 |
    | P3 | 2 1 1 | 2 2 2 |
    | P4 | 0 0 2 | 4 3 3 |

    Step 1 - Available vector.
    - Total: A = 10, B = 5, C = 7
    - Allocated: A = 0+2+3+2+0 = 7, B = 1+0+0+1+0 = 2, C = 0+0+2+1+2 = 5
    - Available = (10-7, 5-2, 7-5) = (3, 3, 2)

    Step 2 - Need matrix, where Need = Max - Allocation.

    | Process | Need A B C |
    |---|---|
    | P0 | 7 4 3 |
    | P1 | 1 2 2 |
    | P2 | 6 0 0 |
    | P3 | 0 1 1 |
    | P4 | 4 3 1 |

    Step 3 - Verify the given safe sequence < P1, P3, P4, P0, P2 >.

    Start with Work = Available = (3, 3, 2).

    | Step | Process | Need | Need <= Work? | Work before | Allocation released | Work after |
    |---|---|---|---|---|---|---|
    | 1 | P1 | 1 2 2 | (1,2,2) <= (3,3,2), yes | 3 3 2 | 2 0 0 | 5 3 2 |
    | 2 | P3 | 0 1 1 | (0,1,1) <= (5,3,2), yes | 5 3 2 | 2 1 1 | 7 4 3 |
    | 3 | P4 | 4 3 1 | (4,3,1) <= (7,4,3), yes | 7 4 3 | 0 0 2 | 7 4 5 |
    | 4 | P0 | 7 4 3 | (7,4,3) <= (7,4,5), yes | 7 4 5 | 0 1 0 | 7 5 5 |
    | 5 | P2 | 6 0 0 | (6,0,0) <= (7,5,5), yes | 7 5 5 | 3 0 2 | 10 5 7 |

    Every process passes the test in turn, and the final Work equals the total resource vector (10, 5, 7), which confirms that all resources have been returned. The sequence < P1, P3, P4, P0, P2 > therefore satisfies the safety requirement, and the system is in a safe state.

    Checking that Request <= Available, which is the second part of the algorithm:

    Suppose P1 now requests (1, 0, 2).
    - Test 1: is Request <= Need(P1)? (1,0,2) <= (1,2,2), yes.
    - Test 2: is Request <= Available? (1,0,2) <= (3,3,2), yes.
    - Pretend to allocate:
      - Available becomes (3,3,2) - (1,0,2) = (2,3,0)
      - Allocation(P1) becomes (2,0,0) + (1,0,2) = (3,0,2)
      - Need(P1) becomes (1,2,2) - (1,0,2) = (0,2,0)
    - Run the safety algorithm on the new state: the sequence < P1, P3, P4, P0, P2 > still works, so the new state is safe and the request is granted.

    Now suppose instead that P4 requests (3, 3, 0).
    - Request <= Need(P4)? (3,3,0) <= (4,3,1), yes.
    - Request <= Available? (3,3,0) <= (3,3,2), yes.
    - But after granting, Available becomes (0,0,2), and no process has a Need that fits within (0,0,2). No safe sequence exists, so the state would be unsafe and the request must be refused; P4 waits.

    Key points about Banker's algorithm:
    - It is a deadlock avoidance algorithm: it never lets the system enter an unsafe state.
    - A safe state is never deadlocked. An unsafe state is not necessarily deadlocked, but it might become so, so the algorithm refuses to enter one. It is therefore conservative.
    - It requires each process to declare its maximum demand in advance, which is its chief practical limitation.
    - The safety check runs in O(m x n^2) time for m resource types and n processes, which is why it is too expensive for a general-purpose operating system to run on every request.
17. **(a) What is Artificial Intelligence (AI)? What are the necessary conditions for a deadlock in an operating system?** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 890 (ET: N/A)]*


    Answer:

    Artificial Intelligence:

    Artificial Intelligence (AI) is the branch of computer science concerned with building machines and software that can perform tasks which normally require human intelligence, such as learning from experience, reasoning, understanding language, recognising patterns, solving problems and making decisions.

    Main branches:
    - Machine Learning: systems that improve their performance from data rather than from explicit programming. Its forms are supervised, unsupervised and reinforcement learning.
    - Deep Learning: machine learning using multi-layer neural networks, which has produced the recent advances in vision and language.
    - Natural Language Processing: understanding and generating human language, used in translation, chatbots and speech recognition.
    - Computer Vision: interpreting images and video, used in face recognition, medical imaging and autonomous vehicles.
    - Robotics: machines that sense and act in the physical world.
    - Expert Systems: rule-based systems that capture the knowledge of a specialist in a narrow field.

    Types by capability: narrow AI, which is what exists today and is limited to one task; general AI, which would match human ability across tasks and does not yet exist; and super AI, a hypothetical level beyond human capability.

    Applications: medical diagnosis, fraud detection in banking, credit scoring, recommendation systems, weather forecasting, agricultural yield prediction, machine translation and autonomous vehicles.

    Concerns: bias in training data, loss of jobs in routine occupations, privacy, the difficulty of explaining a model's decision, and the question of accountability when a system causes harm.

    The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

    - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

    - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

    - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

    - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

    How each condition can be attacked, which is the method of deadlock prevention:
    - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
    - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
    - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
    - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
18. **What is Deadlock? Explain two situations where deadlock condition occurs.** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*


    Answer: Deadlock is a situation in which a set of processes are permanently blocked, because each process in the set is holding a resource and is waiting for a resource that is held by another process in the same set. No process can proceed, none will release what it holds, and the set waits for ever unless the operating system intervenes.

    Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

    Two situations in which a deadlock condition occurs:

    Situation 1 - Two processes competing for two resources in opposite order:

    A file server holds two locks, one on a customer record and one on an account record. A transfer of money requires both.

    | Time | Transaction T1 (transfer from A to B) | Transaction T2 (transfer from B to A) |
    |---|---|---|
    | t1 | Locks account A | Locks account B |
    | t2 | Requests a lock on account B, which T2 holds, so T1 blocks | Requests a lock on account A, which T1 holds, so T2 blocks |

    Neither transaction can proceed and neither will release its lock. The wait-for graph contains the cycle T1 -> T2 -> T1. This is the classic deadlock of database systems, and it is exactly why database engines contain a deadlock detector that aborts one transaction and restarts it.

    Resource-allocation graph:
    ```
    A ---> T1 ---> B ---> T2 ---> A
    ```

    Situation 2 - Multiple processes and a chain of resources (the dining philosophers problem):

    Five philosophers sit around a table with one fork between each pair, so there are five forks. Each philosopher needs both the fork on the left and the fork on the right in order to eat.

    If every philosopher simultaneously picks up the fork on the left and then waits for the fork on the right, each holds one fork and waits for a fork held by the neighbour. The circular wait closes around the table and all five starve.

    ```
    Philosopher 1 holds Fork 1, waits for Fork 2
    Philosopher 2 holds Fork 2, waits for Fork 3
    Philosopher 3 holds Fork 3, waits for Fork 4
    Philosopher 4 holds Fork 4, waits for Fork 5
    Philosopher 5 holds Fork 5, waits for Fork 1
    ```

    Solutions to this second situation, which illustrate the general remedies:
    - Allow at most four philosophers to sit at the table at once, which breaks hold and wait.
    - Require a philosopher to pick up both forks only if both are free, which breaks hold and wait.
    - Make one philosopher, say the fifth, pick up the right fork first while the others pick up the left first. This breaks the symmetry and therefore the circular wait, and it is an instance of the resource-ordering rule.

    Two further practical situations worth mentioning:
    - Spooling: two print jobs each fill half the spool area and each waits for more space that the other holds.
    - Memory allocation: two processes each hold half the free memory and each requests more than the remaining amount.
19. **A, B two resources. Two processes (P1 and P2) share these resources. When a process request for a resources, if that resource is free then it will be allocated with that resources. If the resources are not free then the process will halt. Now the scenario is:** *[DPDC ( Technical part) JAM (ICT) 2020 compact it 973 (ET: BUET)]*


    Answer: Given: two resources A and B, and two processes P1 and P2 that share them. A process that requests a free resource is granted it; a process that requests a resource already held by another halts, that is it blocks until the resource becomes free.

    The specific interleaving of requests is not reproduced in the question paper, so the two cases are analysed: the one that deadlocks and the one that does not.

    Case 1 - the deadlocking interleaving, when the two processes request the resources in opposite order:

    ```
    P1:  request A;  request B;  use both;  release A;  release B
    P2:  request B;  request A;  use both;  release B;  release A
    ```

    | Time | P1 | P2 | State |
    |---|---|---|---|
    | t1 | requests A, granted | | P1 holds A |
    | t2 | | requests B, granted | P2 holds B |
    | t3 | requests B, held by P2, so P1 halts | | P1 blocked, still holding A |
    | t4 | | requests A, held by P1, so P2 halts | P2 blocked, still holding B |

    Resource-allocation graph:
    ```
    A ---> P1 ---> B ---> P2 ---> A
    ```

    Checking the four conditions:
    - Mutual exclusion: yes, A and B are exclusive.
    - Hold and wait: yes, P1 holds A and waits for B; P2 holds B and waits for A.
    - No preemption: yes, neither can be forced to release.
    - Circular wait: yes, the graph contains a cycle, and each resource has one instance.

    All four hold and each resource type has a single instance, so the system is deadlocked. Neither process will ever proceed.

    Case 2 - the safe interleaving, when both processes request the resources in the same order:

    ```
    P1:  request A;  request B;  use both;  release B;  release A
    P2:  request A;  request B;  use both;  release B;  release A
    ```

    | Time | P1 | P2 | State |
    |---|---|---|---|
    | t1 | requests A, granted | | P1 holds A |
    | t2 | | requests A, held by P1, so P2 halts | P2 blocked, holding nothing |
    | t3 | requests B, granted | | P1 holds A and B |
    | t4 | uses both, then releases B and A | | Both free |
    | t5 | | resumes, gets A, then B | P2 proceeds normally |

    No deadlock occurs, because P2 blocks while holding nothing at all. Hold and wait never arises for P2, and therefore no cycle can form.

    Conclusion and the general rule: the outcome depends entirely on the order in which the resources are requested. Imposing a global ordering on resources, here always A before B, and requiring every process to obey it, makes circular wait impossible. This is the standard method of deadlock prevention, and in real code it appears as the rule that all locks must be acquired in a fixed order.

    Illustration in code:
    ```c
    /* Deadlock-prone */
    Thread 1: lock(A); lock(B); ... unlock(B); unlock(A);
    Thread 2: lock(B); lock(A); ... unlock(A); unlock(B);

    /* Safe: the same order in both threads */
    Thread 1: lock(A); lock(B); ... unlock(B); unlock(A);
    Thread 2: lock(A); lock(B); ... unlock(B); unlock(A);
    ```
20. **What is Operating Systems Deadlock? কীভাবে Deadlock দূর করা যায়?** *[BPSC Assistant Maintenance Engineer (CSE) 2020 compact it 1019 (ET: N/A)]*


    Answer: Deadlock is a situation in which a set of processes are permanently blocked, because each process in the set is holding a resource and is waiting for a resource that is held by another process in the same set. No process can proceed, none will release what it holds, and the set waits for ever unless the operating system intervenes.

    Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

    Deadlock এর চারটি প্রয়োজনীয় শর্ত: Mutual Exclusion, Hold and Wait, No Preemption এবং Circular Wait। এই চারটি একসঙ্গে বিদ্যমান থাকলেই কেবল deadlock ঘটতে পারে।

    কীভাবে Deadlock দূর করা যায়:

    ক. প্রতিরোধ (Prevention) — চারটি শর্তের অন্তত একটি ভেঙে দেওয়া:
    - Mutual exclusion ভাঙা: সম্ভব হলে রিসোর্স ভাগাভাগিযোগ্য করা। যেমন প্রিন্টারে সরাসরি না লিখে স্পুল ডিরেক্টরিতে লেখা, যা একসঙ্গে অনেকে করতে পারে। তবে প্রকৃত অভাগাযোগ্য রিসোর্সে এটি সম্ভব নয়।
    - Hold and wait ভাঙা: প্রসেস শুরুর আগেই প্রয়োজনীয় সব রিসোর্স একসঙ্গে বরাদ্দ নেওয়া, অথবা নতুন কিছু চাওয়ার আগে হাতের সব ছেড়ে দেওয়া। অসুবিধা: রিসোর্স দীর্ঘ সময় অব্যবহৃত পড়ে থাকে এবং starvation হতে পারে।
    - No preemption ভাঙা: কোনো প্রসেস অপেক্ষমাণ হলে তার রিসোর্স কেড়ে নিয়ে অন্যকে দেওয়া এবং পরে তাকে পুনরায় শুরু করা। এটি কেবল সেসব রিসোর্সে সম্ভব যাদের অবস্থা সংরক্ষণ ও পুনরুদ্ধার করা যায়।
    - Circular wait ভাঙা: প্রতিটি রিসোর্স টাইপকে একটি ক্রমিক নম্বর দেওয়া এবং প্রতিটি প্রসেসকে কেবল ঊর্ধ্বক্রমে রিসোর্স চাইতে বাধ্য করা। প্রমাণ: চক্র তৈরি হতে হলে কোনো প্রসেসকে নিজের দখলে থাকা রিসোর্সের চেয়ে ছোট নম্বরের রিসোর্স চাইতে হবে, যা নিয়মে নিষিদ্ধ। বাস্তবে এটিই সবচেয়ে বহুল ব্যবহৃত পদ্ধতি।

    খ. পরিহার (Avoidance) — Banker's Algorithm:
    - প্রতিটি রিসোর্স অনুরোধ অনুমোদনের আগে পরীক্ষা করা হয় যে অনুমোদনের পর সিস্টেম নিরাপদ (safe) অবস্থায় থাকবে কিনা।
    - Safe state মানে এমন একটি ক্রম বিদ্যমান, যাতে প্রতিটি প্রসেস তার সর্বোচ্চ প্রয়োজন মিটিয়ে কাজ শেষ করতে পারবে।
    - প্রতিটি প্রসেসকে আগেই সর্বোচ্চ চাহিদা ঘোষণা করতে হয়, যা বাস্তবে বড় সীমাবদ্ধতা।

    গ. শনাক্তকরণ ও পুনরুদ্ধার (Detection and Recovery):
    - Wait-for গ্রাফে পর্যায়ক্রমে চক্র খুঁজে deadlock শনাক্ত করা হয়।
    - পুনরুদ্ধার দুইভাবে: (১) প্রসেস বাতিল করা — সব deadlocked প্রসেস একসঙ্গে, অথবা একটি একটি করে যতক্ষণ না চক্র ভাঙে; (২) রিসোর্স কেড়ে নেওয়া — একটি victim প্রসেস বেছে তার রিসোর্স নিয়ে তাকে নিরাপদ চেকপয়েন্টে ফিরিয়ে নেওয়া।
    - Victim নির্বাচনে অগ্রাধিকার, চলার সময়, দখলে থাকা রিসোর্স ও অবশিষ্ট প্রয়োজন বিবেচনা করতে হয়, এবং একই প্রসেস বারবার victim হলে starvation এড়াতে হয়।

    ঘ. উপেক্ষা করা (Ostrich Algorithm):
    - Deadlock বিরল ধরে নিয়ে কোনো ব্যবস্থা না নেওয়া। ঘটলে ব্যবহারকারী প্রসেস বন্ধ করে দেবেন বা সিস্টেম রিস্টার্ট হবে।
    - ইউনিক্স, লিনাক্স ও উইন্ডোজ বাস্তবে এই পথই নেয়, কারণ প্রতিরোধ বা পরিহারের খরচ বেশি।

    ব্যবহারিক পরামর্শ: প্রোগ্রাম লেখার সময় সবচেয়ে কার্যকর নিয়ম হলো সব লক একই ক্রমে নেওয়া, লক ধরে রেখে অন্য কোনো লক না চাওয়া, এবং টাইমআউটসহ লক নেওয়া যাতে অনির্দিষ্টকাল অপেক্ষা না করতে হয়।
21. **(d) Define Deadlock. Write down the necessary conditions for deadlock.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1026 (ET: N/A)]*


    Answer: Deadlock is a situation in which a set of processes are permanently blocked, because each process in the set is holding a resource and is waiting for a resource that is held by another process in the same set. No process can proceed, none will release what it holds, and the set waits for ever unless the operating system intervenes.

        Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

    The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

        - Mutual exclusion: at least one resource must be non-sharable, that is usable by only one process at a time. A printer or a write lock is an example; a read-only file is not.

        - Hold and wait: a process is holding at least one resource and is waiting to acquire additional resources that are currently held by other processes.

        - No preemption: a resource cannot be forcibly taken away from the process holding it. It can only be released voluntarily, when the process has finished with it.

        - Circular wait: there exists a set of waiting processes P0, P1, ..., Pn such that P0 is waiting for a resource held by P1, P1 for one held by P2, and so on, with Pn waiting for a resource held by P0. The wait-for graph therefore contains a cycle.

        How each condition can be attacked, which is the method of deadlock prevention:
        - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
        - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
        - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
        - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
22. **Four condition of deadlock in Operating System. Suppose, n processes, \text{P}_1, \text{P}_2\dots \text{P}_n share m identical esource units which can be reserved and released one at a time. The maximum resources request of process \text{P}_i is \text{S}_i, where \text{S}_i>0. Which one is sufficient condition for ensuring that deadlock doesn't occur? (Full প্রশ্ন সংগ্রহ করা সম্ভব হয়নি)** *[Microcredit Regulatory Authority Assistant Maintenance Engineer 2020 compact it 1036 (ET: BUET)]*


    Answer:

    Four conditions of deadlock: Mutual Exclusion, Hold and Wait, No Preemption and Circular Wait. All four must hold simultaneously for a deadlock to be possible.

    - Mutual exclusion: at least one resource is non-sharable, usable by only one process at a time.
    - Hold and wait: a process holds at least one resource while waiting for another that is held by a different process.
    - No preemption: a resource cannot be forcibly taken from a process; it must be released voluntarily.
    - Circular wait: a closed chain of processes exists, each waiting for a resource held by the next.

    The sufficient condition for the numerical part:

    Given n processes P1, P2, ..., Pn sharing m identical resource units, which can be reserved and released one at a time, and where the maximum requirement of process Pi is Si with Si > 0, the sufficient condition for ensuring that deadlock does not occur is:

    S1 + S2 + ... + Sn < m + n

    that is, the sum of the maximum requirements must be strictly less than the number of resources plus the number of processes.

    Derivation:

    - Consider the worst case, in which every process has been given as many units as it can hold without being able to finish, that is (Si - 1) units each. Every process then needs exactly one more unit to complete.
    - The number of units held in this worst case is the sum over all i of (Si - 1), which equals (S1 + S2 + ... + Sn) - n.
    - If at least one unit is still free after this allocation, it can be given to any one process, which then reaches its maximum, finishes and releases all its units. Those units allow the next process to finish, and so on until all are done.
    - Deadlock is therefore impossible if
      m > (S1 + S2 + ... + Sn) - n
    - Rearranging:
      S1 + S2 + ... + Sn < m + n

    Worked examples:

    Example 1: n = 3 processes with maximum needs S1 = 3, S2 = 4, S3 = 5, and m = 10 resources.
    - Sum of Si = 3 + 4 + 5 = 12
    - m + n = 10 + 3 = 13
    - 12 < 13, so the condition holds and the system is deadlock free.

    Example 2: the same processes but m = 8.
    - Sum of Si = 12, and m + n = 8 + 3 = 11
    - 12 is not less than 11, so the condition fails and deadlock is possible. Indeed, allocating 2, 3 and 3 units uses all 8, and each process still needs one more.

    Special case in which every process has the same maximum need m0:
    - The condition n x m0 < m + n reduces to m > n x (m0 - 1), that is m >= n x (m0 - 1) + 1.

    Note on the direction of the implication: the condition is sufficient but not necessary. A system that violates it is not certain to deadlock; it merely might. A system that satisfies it can never deadlock, whatever the order of requests.

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
