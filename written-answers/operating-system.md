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
   Two types of scheduling:
   - Non-preemptive: a switch happens only when the process finishes, or when it moves from running to waiting on its own. Once a process gets the CPU, it keeps it until it finishes or blocks. That is cases one and four.
   - Preemptive: a switch can also happen when a process moves from running to ready, or from waiting to ready. The CPU can interrupt a running process. That is all four cases.

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
   | FCFS | No | Order of arrival, like a queue | Simple, and no starvation | Large average waiting time. Convoy effect: one long job delays everything behind it |
   | SJF | No | Smallest burst time first | Gives the minimum average waiting time | More complex than FCFS. Burst time must be known in advance. Long jobs can starve |
   | SRTF | Yes | Smallest remaining time first. It is the preemptive form of SJF | Even lower average waiting time, because short jobs get preference | Long processes can starve. High context switch overhead. More complex to build |
   | Priority | Either | Highest priority | Important work first | Starvation of low-priority jobs; solved by ageing |
   | Round Robin | Yes | In arrival order, each process gets a fixed time quantum, then goes to the back of the queue | Fair to everyone, and no starvation. Good response time | Waiting time is larger than in SJF or Priority. The quantum size must be tuned carefully |
   | Multilevel Queue | Yes | Separate queue per class | Different policies for different classes | Rigid, processes cannot move between queues |
   | Multilevel Feedback Queue | Yes | Queues with promotion and demotion | Adapts to process behaviour | Complex to configure |

   Definitions used throughout:
   - Arrival Time (AT): the time at which the process arrives in the ready queue.
   - Burst Time (BT): the time the process needs for CPU execution.
   - Completion Time (CT): the time at which the process finishes its execution.
   - Turnaround Time (TAT) = Completion Time − Arrival Time. It is the total time from arrival to finish.
   - Waiting Time (WT) = Turnaround Time − Burst Time. It is how long the process sat in the ready queue.
   - Response Time (RT): the time from submission until the first response is given. This matters most in an interactive system.
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
   - Arrival Time (AT): the time at which the process arrives in the ready queue.
   - Burst Time (BT): the time the process needs for CPU execution.
   - Completion Time (CT): the time at which the process finishes its execution.
   - Turnaround Time (TAT) = Completion Time − Arrival Time. It is the total time from arrival to finish.
   - Waiting Time (WT) = Turnaround Time − Burst Time. It is how long the process sat in the ready queue.
   - Response Time (RT): the time from submission until the first response is given. This matters most in an interactive system.
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
   - Arrival Time (AT): the time at which the process arrives in the ready queue.
   - Burst Time (BT): the time the process needs for CPU execution.
   - Completion Time (CT): the time at which the process finishes its execution.
   - Turnaround Time (TAT) = Completion Time − Arrival Time. It is the total time from arrival to finish.
   - Waiting Time (WT) = Turnaround Time − Burst Time. It is how long the process sat in the ready queue.
   - Response Time (RT): the time from submission until the first response is given. This matters most in an interactive system.
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


   Answer: Deadlock is a state in an operating system where two or more processes are stuck forever, because each one is waiting for a resource that another one is holding. No process can move ahead, none of them will let go of what it holds, and they wait for ever unless the operating system steps in.

   Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

   The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

   - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

   - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

   - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

   - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

   All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

   Four ways to handle deadlock:
   - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
   - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
   - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
   - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

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


   Answer: Deadlock is a state in an operating system where two or more processes are stuck forever, because each one is waiting for a resource that another one is holding. No process can move ahead, none of them will let go of what it holds, and they wait for ever unless the operating system steps in.

   Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

   The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

   - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

   - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

   - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

   - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

   All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

   Four ways to handle deadlock:
   - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
   - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
   - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
   - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

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

   - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

   - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

   - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

   - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

   All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

   Four ways to handle deadlock:
   - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
   - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
   - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
   - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

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


   Answer: Deadlock is a state in an operating system where two or more processes are stuck forever, because each one is waiting for a resource that another one is holding. No process can move ahead, none of them will let go of what it holds, and they wait for ever unless the operating system steps in.

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

   - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

   - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

   - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

   - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

   All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

   Four ways to handle deadlock:
   - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
   - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
   - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
   - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

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

     - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

     - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

     - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

     - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

     All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

    Four ways to handle deadlock:
    - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
    - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
    - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
    - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

    How each condition can be attacked, which is the method of deadlock prevention:
     - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
     - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
     - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
     - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
12. **(a) What is deadlock in operating system (OS)? What are the four necessary and sufficient conditions behind deadlock?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*


    Answer: Deadlock is a state in an operating system where two or more processes are stuck forever, because each one is waiting for a resource that another one is holding. No process can move ahead, none of them will let go of what it holds, and they wait for ever unless the operating system steps in.

     Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

     The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

     - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

     - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

     - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

     - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

     All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

    Four ways to handle deadlock:
    - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
    - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
    - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
    - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

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

     - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

     - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

     - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

     - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

     All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

    Four ways to handle deadlock:
    - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
    - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
    - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
    - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

    How each condition can be attacked, which is the method of deadlock prevention:
     - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
     - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
     - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
     - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
15. **(b) What are the conditions for deadlock situations? Explain briefly.** *[BPSC (Ministry of Home Affairs) Senior Computer Operator (CSE) 13.09.2022 compact it 688 (ET: N/A)]*


    Answer: The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

     - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

     - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

     - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

     - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

     All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

    Four ways to handle deadlock:
    - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
    - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
    - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
    - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

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

     - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

     - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

     - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

     - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

     All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

    Four ways to handle deadlock:
    - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
    - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
    - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
    - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

    How each condition can be attacked, which is the method of deadlock prevention:
     - Mutual exclusion: make resources sharable where possible, for example by spooling the printer. This condition cannot be removed for genuinely non-sharable resources.
     - Hold and wait: require a process to request all its resources at once before it begins, or to release everything it holds before requesting more. This causes low utilisation and possible starvation.
     - No preemption: allow the system to take resources back from a waiting process and restart it later. This works only for resources whose state can be saved and restored, such as CPU registers or memory, not for a printer half-way through a job.
     - Circular wait: impose a total ordering on all resource types and require every process to request resources only in increasing order. This is the practical method actually used in real systems, for example in the Linux kernel's lock ordering rules.
18. **What is Deadlock? Explain two situations where deadlock condition occurs.** *[Janata Bank Assistant System Administrator 2021 compact it 938 (ET: N/A)]*


    Answer: Deadlock is a state in an operating system where two or more processes are stuck forever, because each one is waiting for a resource that another one is holding. No process can move ahead, none of them will let go of what it holds, and they wait for ever unless the operating system steps in.

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


    Answer: Deadlock is a state in an operating system where two or more processes are stuck forever, because each one is waiting for a resource that another one is holding. No process can move ahead, none of them will let go of what it holds, and they wait for ever unless the operating system steps in.

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


    Answer: Deadlock is a state in an operating system where two or more processes are stuck forever, because each one is waiting for a resource that another one is holding. No process can move ahead, none of them will let go of what it holds, and they wait for ever unless the operating system steps in.

         Everyday analogy: two cars meet on a single-lane bridge from opposite ends. Each occupies half the bridge and each waits for the other to reverse. Neither can move, and neither will give way.

     The four necessary conditions, stated by Coffman in 1971. All four must hold simultaneously for a deadlock to be possible.

         - Mutual exclusion: only one process can use a resource at any one time, that is the resource is non-sharable. A printer or a write lock is an example. A read-only file is not.

         - Hold and wait: a process is holding at least one resource, and at the same time it is waiting to get other resources that are held by other processes.

         - No preemption: we cannot take a resource away from a process. The process must release it itself, when it has finished with it.

         - Circular wait: a set of processes wait for each other in a circle. P1 holds R1 and needs R2, which P2 holds. P2 holds R2 and needs R3, which P3 holds, and so on, until the last one waits for the first. So the wait-for graph contains a cycle.

         All four conditions must be true at the same time for a deadlock to happen. If we break any one of them, a deadlock cannot occur.

    Four ways to handle deadlock:
    - Prevention: remove one of the four necessary conditions, so a deadlock can never form.
    - Avoidance: check every request before granting it, and grant it only if the system stays in a safe state. The Banker's algorithm does this.
    - Detection and recovery: let deadlocks happen, find them with a wait-for graph, then recover by killing a process or taking a resource back.
    - Ignorance: pretend deadlocks never happen. Most general purpose systems, including UNIX and Windows, do this, because deadlocks are rare and the cost of handling them is high. This is called the ostrich algorithm.

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


   Answer:

   | Point | Firmware | Operating System |
   |---|---|---|
   | Definition | Permanent software programmed into the read-only memory of a hardware device, which controls that device directly | System software that manages all the hardware and software resources of a computer and provides services to applications |
   | Where it is stored | In ROM, EPROM, EEPROM or flash memory on the device itself | On secondary storage, and loaded into RAM at boot |
   | Size | Small, kilobytes to a few megabytes | Large, hundreds of megabytes to several gigabytes |
   | Scope | Controls one specific device | Controls the whole computer |
   | User interaction | Almost none; the user rarely sees it | Continuous, through a command line or a graphical interface |
   | Modification | Rarely, and only by flashing a new image; a failure can make the device unusable | Frequently, through updates, patches and new versions |
   | Loaded when | Runs immediately at power-on, before anything else | Loaded by the firmware after the power-on self test |
   | Dependence | Independent of the operating system, and specific to the hardware | Depends on the firmware to start, but is largely hardware independent above the driver layer |
   | Multitasking | No; it performs one fixed task | Yes; it runs many processes concurrently |
   | Examples | BIOS, UEFI, the controller code inside a hard disk, a router or a washing machine, and a mobile phone's baseband software | Windows, Linux, macOS, Android, iOS, Unix |

   Relationship between the two: the firmware runs first. It performs the power-on self test, initialises the hardware, and then finds and loads the boot loader of the operating system. From that point the operating system takes control and uses the firmware only occasionally, for example to read hardware information or to change boot settings. In this sense the firmware is the bridge that hands the machine over to the operating system.

   Middle position of device drivers: a driver is neither firmware nor part of the kernel's core. It is software supplied by the hardware maker that lets the operating system talk to a device, and it is loaded and updated by the operating system, unlike firmware which lives on the device.

   Practical note: updating the firmware, commonly called flashing the BIOS, is risky because an interruption during the update can leave the machine unable to start at all. Updating an operating system, by contrast, is routine and reversible.
2. **Define: Socket, Kernel, Process, Program, Multiprogramming, Context Switching; Explain Preemptive Priority Scheduling algorithm with illustration; Explain LRU and NRU Page Replacement algorithm.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Engineer (IT) 24.02.2024 compact it 302 (ET: BIBM)]*


   Answer:

   Definitions:

   - Socket: an endpoint of a two-way communication link between two programs, usually across a network. It is identified by an IP address and a port number, and it is the standard programming interface for TCP and UDP communication. Types: stream sockets (TCP, reliable and connection-oriented) and datagram sockets (UDP, unreliable and connectionless). Unix domain sockets provide the same interface for two processes on the same machine.

   - Kernel: the core of the operating system, loaded at boot and permanently resident in memory, which has complete control of the hardware. It manages processes, memory, devices and files, handles interrupts, and provides the system call interface through which applications request its services. It runs in kernel mode, in which all instructions are permitted.

   - Process: a program in execution. It is an active entity with its own address space, program counter, registers, stack and process control block. One program can give rise to many processes.

   - Program: a passive entity, a file of instructions stored on disk. It becomes a process only when it is loaded into memory and given a processor. The distinction is that of a recipe (program) and the act of cooking (process).

   - Multiprogramming: keeping several programs in main memory at the same time so that when one blocks for input or output, the CPU is given to another. Its purpose is to maximise CPU utilisation, and it is the ancestor of multitasking.

   - Context switching: the operation of saving the entire execution state of the running process into its process control block and restoring the state of another process, so that the CPU can be transferred from one to the other. It is pure overhead, costing one to a hundred microseconds directly, plus the indirect cost of cache and TLB pollution.

   Preemptive priority scheduling, with illustration:

   Every process is given a priority number. The CPU is always allocated to the highest-priority process among those ready, and a newly arrived process of higher priority immediately takes the CPU from the running one.

   Example, where a lower number means a higher priority:

   | Process | Arrival Time | Burst Time | Priority |
   |---|---|---|---|
   | P1 | 0 | 5 | 2 |
   | P2 | 1 | 3 | 1 |
   | P3 | 2 | 8 | 4 |
   | P4 | 3 | 6 | 3 |

   Trace:
   - t = 0: only P1 is present, so P1 runs.
   - t = 1: P2 arrives with priority 1, higher than P1's 2, so P1 is preempted with 4 ms remaining.
   - t = 4: P2 finishes; among P1 (2), P4 (3) and P3 (4), P1 is highest and runs its remaining 4 ms.
   - t = 8: P1 finishes; P4 beats P3 and runs.
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

   Its principal defect is starvation of low-priority processes, cured by ageing, in which the priority of a waiting process is raised gradually.

   LRU and NRU page replacement algorithms:

   LRU (Least Recently Used):
   - The page that has not been referenced for the longest time is chosen as the victim.
   - It rests on the assumption that a page used recently is likely to be used again soon, so the least recently used is the least likely to be needed.
   - Implementation: either a counter, in which the time of the last reference is stored with every page and the smallest is chosen, or a stack, in which every reference moves the page to the top and the victim is taken from the bottom. Both require hardware support, and a full software implementation is too slow.
   - LRU is a stack algorithm, so it does not suffer from Belady's anomaly.
   - Example with the string 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1 and three frames, LRU gives 12 page faults, against 15 for FIFO and 9 for Optimal.

   NRU (Not Recently Used):
   - A cheap approximation to LRU, using only two bits per page: the reference bit R, set by the hardware whenever the page is read or written, and the modify bit M, set whenever it is written.
   - A periodic timer interrupt clears all the R bits, so R indicates use in the current interval only.
   - Pages are then divided into four classes:
     - Class 0: not referenced, not modified
     - Class 1: not referenced, modified
     - Class 2: referenced, not modified
     - Class 3: referenced, modified
   - NRU evicts a page at random from the lowest non-empty class. A class 0 page is ideal, since it is neither in use nor dirty and can simply be discarded. A class 3 page is the worst, being both in use and requiring a write to disk.
   - Class 1 exists because the periodic clearing of R can leave a modified page marked as not referenced.
   - Advantages: very cheap, needing only two bits and a periodic interrupt, and easy to implement in hardware.
   - Disadvantage: coarse, since it distinguishes only four classes and chooses at random within a class, so it performs noticeably worse than true LRU.
   - It is the ancestor of the clock and second-chance algorithms, which are what real systems actually use.
3. **Explain how can multiprogramming be achieved on a uniprocessor system?** *[BGDCL Assistant Manager (CSE) 15.03.2024 compact it 379 (ET: BUET)]*


   Answer: Multiprogramming on a uniprocessor system is achieved by keeping several programs in main memory at the same time and switching the single CPU rapidly among them, so that the processor is never idle while any program has work to do.

   The observation that makes it possible: a typical program spends most of its life waiting rather than computing. A disk read takes several milliseconds, during which the CPU could execute millions of instructions. Without multiprogramming the CPU would simply stand idle for that whole period. CPU utilisation on a single-program batch system was often below 10 per cent.

   How it is achieved, step by step:

   1. Several jobs are loaded into main memory at once. The long-term scheduler chooses which jobs to admit, aiming for a good mix of CPU-bound and input-output-bound work, so that both the processor and the devices stay busy.

   2. Memory protection is provided, using base and limit registers in early systems or paging in modern ones, so that one program cannot read or overwrite another's memory. Without protection, multiprogramming would be unsafe.

   3. The CPU begins executing one job. When that job issues an input-output request, it cannot proceed, so the operating system moves it to the waiting state and hands the CPU to another job that is ready. This is the essential mechanism.

   4. The state of the outgoing job is saved in its process control block, and the state of the incoming job is restored from its own. This is the context switch, and it is what makes the interruption invisible to the program.

   5. Interrupts drive the whole system. When the input-output operation completes, the device raises an interrupt; the operating system moves the waiting job back to the ready queue and, at the next scheduling decision, may give it the CPU again.

   6. Direct Memory Access allows the device to transfer data to and from memory without the CPU, so the CPU is genuinely free during the transfer rather than merely waiting differently.

   7. A short-term scheduler chooses which ready job runs next, using an algorithm such as FCFS, SJF, priority or Round Robin.

   8. In time-sharing systems a timer interrupt is added, so that a job is preempted after its quantum expires even if it never requests input or output. This prevents a compute-bound job from monopolising the machine and gives every user a share.

   Illustration with two jobs:
   ```
   Time:      0    10   15   25   30   40
   Job A:     RUN  I/O ......... RUN
   Job B:          RUN  I/O ..........  RUN
   CPU busy:  A    B    idle?    A     B
   ```
   While A waits for its input-output between t = 10 and t = 25, the CPU runs B. Neither job runs faster than it would alone, but the machine as a whole completes far more work.

   Hardware support required:
   - An interrupt mechanism, so that the operating system regains control.
   - A timer, for preemption.
   - Memory protection hardware.
   - Dual mode operation, user mode and kernel mode, so that a program cannot execute privileged instructions or touch another's memory.
   - DMA, so that transfers do not consume the CPU.

   Benefits: high CPU utilisation, greater throughput, shorter average waiting time, and the ability to share one machine among many users.

   Costs and difficulties: memory must be large enough to hold several programs; the operating system becomes far more complex, needing scheduling, protection, and process management; context switches consume time; and concurrent access to shared resources introduces the problems of synchronisation and deadlock.

   Terms to distinguish clearly:
   - Multiprogramming: several programs in memory, one CPU, switching on input-output waits. The aim is CPU utilisation.
   - Multitasking (time-sharing): the same, with the addition of a timer so that switching also happens on a quantum. The aim is response time.
   - Multiprocessing: more than one physical CPU or core, allowing genuinely simultaneous execution.
   - Multithreading: several threads within one process.
   Multiprogramming, multitasking and multithreading are all achievable on a uniprocessor; only multiprocessing is not.
4. **Write the difference between shell and kernel?** *[Bangladesh Oil Gas Mineral Corporation (PetroBangla) Assistant Manager (CSE/IT) 31.06.2024 compact it 1454 (ET: BUET)]*


   Answer: | Point | Shell | Kernel |
   |---|---|---|
   | Definition | The command interpreter, the outer layer through which the user talks to the system | The core of the operating system, which controls the hardware |
   | Position | Outer layer, between the user and the kernel | Innermost layer, between the operating system and the hardware |
   | Function | Reads commands, interprets them, and asks the kernel to carry them out | Manages processes, memory, devices and files |
   | Mode of execution | Runs in user mode | Runs in kernel mode, with full privileges |
   | Interaction | With the user directly | With the hardware directly |
   | Number | Many can exist, and a user may choose or replace them | Only one, and it cannot be replaced while running |
   | Replaceable | Yes, easily: bash, zsh, fish | No; changing it requires rebooting into another kernel |
   | If it crashes | Only that session is lost | The whole system halts, a kernel panic or blue screen |
   | Loaded | When a user logs in or opens a terminal | At boot, and it stays resident until shutdown |
   | Examples | bash, sh, csh, ksh, zsh, fish, PowerShell, cmd.exe | Linux kernel, Windows NT kernel, XNU |

   How they work together: the user types ls -l. The shell parses the line, finds the program /bin/ls, creates a process with the fork() system call, loads the program with exec(), and waits. The program then issues system calls such as openat() and getdents() to the kernel, which reads the directory from the disk and returns the data. The shell displays the result and prints the prompt again.

   In short: the shell is the interface; the kernel is the engine. The shell asks, and the kernel does.
5. **DOS কী? অপারেটিং সিস্টেমের কাজ ও প্রকারভেদ ব্যাখ্যা করুন।** *[18th NTRCA Assistant Teacher (ICT) 12.07.2024 compact it 407 (ET: N/A)]*


   Answer: DOS কী:

   DOS এর পূর্ণরূপ Disk Operating System। এটি একটি একক ব্যবহারকারীর, একক কাজের (single-user, single-tasking) কমান্ড লাইন ভিত্তিক অপারেটিং সিস্টেম, যা ডিস্কে সংরক্ষিত ফাইল ব্যবস্থাপনার জন্য তৈরি হয়েছিল। এর সবচেয়ে পরিচিত সংস্করণ MS-DOS, যা মাইক্রোসফট ১৯৮১ সালে আইবিএম পিসির জন্য প্রকাশ করে।

   বৈশিষ্ট্য:
   - কোনো গ্রাফিক্যাল ইন্টারফেস নেই; সব কাজ কমান্ড টাইপ করে করতে হয়।
   - একই সময়ে একটিমাত্র প্রোগ্রাম চলতে পারে।
   - ১৬ বিট, এবং সরাসরি ৬৪০ কিলোবাইট পর্যন্ত প্রচলিত মেমোরি ব্যবহার করতে পারত।
   - ফাইল সিস্টেম FAT12 ও FAT16; ফাইলের নাম সর্বোচ্চ ৮ অক্ষর, এক্সটেনশন ৩ অক্ষর (8.3 ফরম্যাট)।
   - কোনো মেমোরি সুরক্ষা বা ব্যবহারকারী ব্যবস্থাপনা ছিল না।
   - প্রচলিত কমান্ড: DIR, CD, COPY, DEL, MD, RD, FORMAT, TYPE, REN।
   - অন্যান্য সংস্করণ: PC-DOS, DR-DOS এবং মুক্ত সংস্করণ FreeDOS।

   অপারেটিং সিস্টেমের কাজ:

   - প্রসেস ব্যবস্থাপনা: প্রসেস তৈরি, শিডিউলিং, সিঙ্ক্রোনাইজেশন, যোগাযোগ ও সমাপ্তি; deadlock সামলানো।
   - মেমোরি ব্যবস্থাপনা: মেমোরি বরাদ্দ ও মুক্তকরণ, কোন অংশ কে ব্যবহার করছে তার হিসাব রাখা, ভার্চুয়াল মেমোরি ও পেজিং পরিচালনা এবং প্রসেসগুলোর মধ্যে সুরক্ষা নিশ্চিত করা।
   - ফাইল ব্যবস্থাপনা: ফাইল ও ডিরেক্টরি তৈরি, মোছা, পড়া, লেখা, সংগঠিত রাখা এবং অনুমতি নিয়ন্ত্রণ।
   - যন্ত্র ব্যবস্থাপনা: ড্রাইভারের মাধ্যমে সব ইনপুট-আউটপুট যন্ত্র নিয়ন্ত্রণ, বাফারিং, ক্যাশিং ও স্পুলিং।
   - নিরাপত্তা ও সুরক্ষা: ব্যবহারকারী প্রমাণীকরণ, অ্যাক্সেস নিয়ন্ত্রণ, প্রসেসগুলোকে পরস্পর থেকে বিচ্ছিন্ন রাখা।
   - সম্পদ বরাদ্দ: কে কোন সম্পদ কতক্ষণ পাবে তা নির্ধারণ।
   - ব্যবহারকারী ইন্টারফেস: কমান্ড লাইন বা গ্রাফিক্যাল ইন্টারফেস প্রদান।
   - ত্রুটি শনাক্তকরণ ও সমাধান।
   - হিসাব রাখা: কোন ব্যবহারকারী কত সম্পদ ব্যবহার করেছে।
   - নেটওয়ার্ক ব্যবস্থাপনা ও যোগাযোগ।

   অপারেটিং সিস্টেমের প্রকারভেদ:

   - Batch Operating System: একই ধরনের কাজ একত্র করে ব্যাচ আকারে চালানো হয়, ব্যবহারকারীর সরাসরি হস্তক্ষেপ ছাড়াই। উদাহরণ: প্রাথমিক মেইনফ্রেম ব্যবস্থা।
   - Time-Sharing (Multitasking) OS: সিপিইউকে ছোট ছোট সময়ের ভাগে ভাগ করে বহু ব্যবহারকারীকে একসঙ্গে সেবা দেওয়া হয়। উদাহরণ: ইউনিক্স, লিনাক্স।
   - Multiprogramming OS: একাধিক প্রোগ্রাম মেমোরিতে রেখে সিপিইউকে সর্বদা ব্যস্ত রাখা।
   - Multiprocessing OS: একাধিক প্রসেসর বা কোর ব্যবহার করে প্রকৃত সমান্তরাল নির্বাহ।
   - Real-Time OS: নির্দিষ্ট সময়সীমার মধ্যে সাড়া দেওয়া নিশ্চিত করে। Hard real-time এ সময়সীমা লঙ্ঘন সম্পূর্ণ অগ্রহণযোগ্য (যেমন বিমান নিয়ন্ত্রণ, পেসমেকার), আর soft real-time এ সামান্য বিলম্ব সহনীয় (যেমন ভিডিও স্ট্রিমিং)। উদাহরণ: VxWorks, RTLinux, QNX।
   - Distributed OS: নেটওয়ার্কে যুক্ত বহু কম্পিউটারকে একটি একক ব্যবস্থার মতো দেখায় এবং সম্পদ ভাগাভাগি করে।
   - Network OS: নেটওয়ার্কের সেবা ও সম্পদ ব্যবস্থাপনা করে; প্রতিটি মেশিন স্বতন্ত্র থাকে। উদাহরণ: Windows Server, Novell NetWare।
   - Mobile OS: মোবাইল যন্ত্রের জন্য, কম বিদ্যুৎ ও স্পর্শ ইন্টারফেসের উপযোগী। উদাহরণ: Android, iOS।
   - Embedded OS: নির্দিষ্ট একটি যন্ত্রের একটি নির্দিষ্ট কাজের জন্য। উদাহরণ: ওয়াশিং মেশিন, রাউটার, স্মার্ট টিভির অভ্যন্তরীণ সফটওয়্যার।
   - Single-user single-tasking: MS-DOS। Single-user multitasking: Windows, macOS। Multi-user: ইউনিক্স, লিনাক্স।
6. **Write down the difference between Multitasking and Multiprocessing.** *[DESCO Sub-Assistant Engineer 20.05.2023 compact it 581 (ET: DESCO)]*


   Answer:

   | Point | Multitasking | Multiprocessing |
   |---|---|---|
   | Definition | The execution of more than one task apparently at the same time on a single processor, by switching the CPU rapidly among them | The use of two or more physical processors or cores in one system, so that tasks execute genuinely at the same instant |
   | Number of CPUs | One is sufficient | Two or more required |
   | Nature of the parallelism | Apparent, achieved by rapid switching (concurrency) | Real, achieved by simultaneous execution (parallelism) |
   | Mechanism | Context switching and time slicing | Distribution of processes or threads across processors |
   | Speed benefit | No true speed increase; only better utilisation | Genuine speed increase for parallelisable work |
   | Hardware cost | Low | High, since more processors are needed |
   | Reliability | A processor failure stops everything | Work can continue on the remaining processors |
   | Operating system support | A scheduler with preemption | A scheduler aware of several processors, plus cache coherence and load balancing |
   | Types | Preemptive and cooperative | Symmetric (SMP), in which all processors are equal, and asymmetric (AMP), in which one master assigns work to slaves |
   | Example | Editing a document while music plays and a file downloads, all on one core | A four-core processor compiling four source files at the same time, each on its own core |

   Relationship between them: the two are not alternatives; they combine. A modern machine has several cores (multiprocessing) and each core is time-shared among many processes (multitasking), so that a hundred processes can run on four cores.

   Related terms that should be distinguished in a full answer:
   - Multiprogramming: keeping several programs in memory so that the CPU switches to another whenever one blocks for input or output. Its aim is CPU utilisation, and it is the ancestor of multitasking.
   - Multitasking (time-sharing): multiprogramming with the addition of a timer, so that switching also occurs when a quantum expires. Its aim is response time.
   - Multithreading: several threads of execution within a single process, sharing its address space.
   - Concurrency versus parallelism: concurrency means several tasks make progress in overlapping periods; parallelism means they literally execute at the same instant. Multitasking gives concurrency; multiprocessing gives parallelism.

   Note on Amdahl's law, which limits the benefit of multiprocessing: if a fraction p of a program can be parallelised, the maximum speedup with any number of processors is 1/(1 - p). A program that is 90 per cent parallel can never be more than ten times faster, however many cores are added. This is why adding processors gives diminishing returns.
7. **(b) What is the difference between micro kernel and macro kernel in the context of OS?** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*


   Answer:

   | Point | Microkernel | Monolithic (macro) kernel |
   |---|---|---|
   | Design | Only the minimum runs in kernel mode: scheduling, basic memory management and inter-process communication | All operating system services run in one large kernel address space |
   | Services in kernel space | Very few | Memory management, file system, device drivers, networking, everything |
   | Services in user space | File system, device drivers, networking, protocol stacks, all as separate servers | Almost none |
   | Size | Small, tens to a few hundred kilobytes | Large, tens of megabytes |
   | Communication between services | By message passing, which crosses the user-kernel boundary | By ordinary function calls within the same address space |
   | Speed | Slower, because every service request costs several context switches and message copies | Faster, since a call is a direct function call |
   | Reliability | High; a driver that crashes takes down only its own user-space server, which can be restarted | Low; a fault in any driver can crash the whole system |
   | Security | Better, since each service is isolated and has only the privileges it needs | Weaker, since all code runs with full privileges |
   | Extensibility | Easy; a new service is simply a new user-space program | Harder; a change means rebuilding or at least reloading part of the kernel |
   | Maintainability | Good, because the components are clearly separated | Harder, because everything is interconnected |
   | Portability | Better, since only the small kernel is hardware dependent | Poorer |
   | Examples | Minix, QNX, L4, Mach, Symbian, and the kernel of Fuchsia | Linux, Unix, BSD, MS-DOS, and the classic AIX and Solaris |

   The essential trade-off: a microkernel buys reliability, security and modularity at the cost of performance, because moving a service out of the kernel means that every use of it becomes a message rather than a function call. A monolithic kernel buys performance at the cost of fault isolation.

   The hybrid kernel, which is what most systems actually use today:
   - Some services are kept in the kernel for speed, while others run outside for reliability.
   - Windows NT and its successors use a hybrid design, as does macOS with XNU, which combines the Mach microkernel with a BSD monolithic component.

   The special position of Linux: Linux is technically monolithic, but it is modular. Device drivers and file systems can be compiled as loadable kernel modules and inserted or removed at run time with insmod and rmmod. This gives much of the flexibility of a microkernel while keeping the speed of direct function calls, and it is why Linux has succeeded on hardware ranging from watches to supercomputers.

   Historical note: the argument between the two designs was the subject of the well-known 1992 debate between Andrew Tanenbaum, the author of Minix, who argued that monolithic kernels were obsolete, and Linus Torvalds, who argued that the performance cost of message passing was not worth paying. Both positions have proved partly right: microkernel ideas dominate in safety-critical and embedded systems such as QNX in cars, while monolithic and hybrid kernels dominate in general-purpose computing.
8. **অথবা, (ক) Blocking এবং Buffering OS এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 610 (ET: N/A)]*


   Answer: Blocking এবং Buffering — অপারেটিং সিস্টেমে দুটি সম্পূর্ণ ভিন্ন ধারণা, যদিও দুটিই ইনপুট-আউটপুট ব্যবস্থাপনার সঙ্গে সম্পর্কিত।

   Blocking (অবরোধ):

   Blocking হলো এমন একটি অবস্থা, যেখানে কোনো প্রসেস তার অনুরোধ করা কাজ (সাধারণত ইনপুট-আউটপুট) শেষ না হওয়া পর্যন্ত থেমে থাকে এবং সিপিইউ ছেড়ে দেয়। প্রসেসটি running অবস্থা থেকে waiting অবস্থায় চলে যায় এবং কাজ শেষ হলে আবার ready অবস্থায় ফিরে আসে।

   - Blocking I/O: read() বা write() কল করার পর প্রসেসটি অপেক্ষা করে যতক্ষণ না কাজ সম্পূর্ণ হয়। কোড লেখা সহজ, কিন্তু প্রসেসটি ওই সময় কিছুই করতে পারে না।
   - Non-blocking I/O: কল করার সঙ্গে সঙ্গে ফিরে আসে; তথ্য প্রস্তুত না থাকলে ত্রুটি বা শূন্য ফেরত দেয়। প্রসেসটি অন্য কাজ চালিয়ে যেতে পারে, কিন্তু বারবার পরীক্ষা করতে হয়।
   - Asynchronous I/O: কাজটি শুরু করে দিয়ে প্রসেস চলতে থাকে, এবং শেষ হলে সংকেত বা কলব্যাকের মাধ্যমে জানানো হয়।

   উদাহরণ: একটি প্রসেস ডিস্ক থেকে ফাইল পড়তে চাইলে blocking read() এ প্রসেসটি ৫ মিলিসেকেন্ড অপেক্ষা করে; ওই সময়ে অপারেটিং সিস্টেম সিপিইউ অন্য প্রসেসকে দিয়ে দেয়।

   Buffering (বাফারিং):

   Buffering হলো মেমোরির একটি অস্থায়ী সংরক্ষণ অঞ্চল (buffer) ব্যবহার করে তথ্য জমিয়ে রাখা, যখন দুটি যন্ত্র বা প্রক্রিয়ার গতি ভিন্ন হয় বা তথ্য স্থানান্তরের একক ভিন্ন হয়।

   Buffering কেন প্রয়োজন:
   - গতির অসামঞ্জস্য দূর করা: সিপিইউ ন্যানোসেকেন্ডে কাজ করে, প্রিন্টার সেকেন্ডে। বাফার না থাকলে সিপিইউকে প্রিন্টারের গতিতে নেমে আসতে হতো।
   - তথ্য স্থানান্তরের একক মেলানো: নেটওয়ার্ক থেকে প্যাকেট আসে টুকরো টুকরো, কিন্তু অ্যাপ্লিকেশন চায় সম্পূর্ণ বার্তা।
   - কপি সেমান্টিকস রক্ষা: write() কল করার পর প্রোগ্রাম বাফারের তথ্য বদলে ফেললেও ডিস্কে যাতে মূল তথ্যই লেখা হয়।
   - সিস্টেম কল সংখ্যা কমানো: এক এক অক্ষর না লিখে ৪ কিলোবাইট জমিয়ে একবারে লেখা অনেক দ্রুত।

   Buffering এর প্রকারভেদ:
   - Single buffering: একটি বাফার। একটিতে তথ্য ভরার সময় প্রক্রিয়াকরণ থেমে থাকে।
   - Double buffering: দুটি বাফার। একটিতে তথ্য ভরা হয় আর অন্যটি প্রক্রিয়াকরণ করা হয়, তারপর ভূমিকা বদল হয়। এতে অপেক্ষা প্রায় দূর হয়। ভিডিও প্রদর্শনে এটি ব্যবহৃত হয়, যাকে বলে double buffering, যা পর্দায় ঝিলিক (flicker) দূর করে।
   - Circular buffering: একাধিক বাফার বৃত্তাকারে সাজানো; উৎপাদক ও ভোক্তার গতির পার্থক্য বেশি হলে ব্যবহৃত হয়।

   পার্থক্য:

   | বিষয় | Blocking | Buffering |
   |---|---|---|
   | প্রকৃতি | প্রসেসের একটি অবস্থা বা আচরণ | মেমোরির একটি কৌশল |
   | উদ্দেশ্য | কাজ শেষ হওয়া পর্যন্ত অপেক্ষা করা | গতির পার্থক্য সামলানো ও কর্মদক্ষতা বাড়ানো |
   | কী ঘটে | প্রসেস থেমে যায়, সিপিইউ ছেড়ে দেয় | তথ্য অস্থায়ীভাবে মেমোরিতে জমা হয় |
   | সম্পদ | সিপিইউ সময় | প্রধান মেমোরি |
   | প্রভাব | ওই প্রসেসের অগ্রগতি থেমে থাকে | সামগ্রিক থ্রুপুট বাড়ে |
   | সম্পর্ক | বাফারিং থাকলে অনেক সময় blocking এড়ানো যায় | বাফার পূর্ণ বা খালি হলে blocking ঘটতে পারে |

   দুইয়ের সম্পর্ক: বাফারিং প্রায়ই blocking কমায়। যেমন একটি প্রোগ্রাম ফাইলে এক অক্ষর লিখলে সেটি বাফারে জমা হয় এবং প্রোগ্রাম সঙ্গে সঙ্গে ফিরে আসে, ডিস্কের অপেক্ষা করতে হয় না। কিন্তু বাফার পূর্ণ হয়ে গেলে প্রোগ্রামকে অবশ্যই অপেক্ষা করতে হবে, অর্থাৎ তখন blocking ঘটবে। উৎপাদক-ভোক্তা সমস্যার মূল কথাই এটি।

   সংশ্লিষ্ট ধারণা:
   - Caching: বাফারের মতোই মেমোরিতে তথ্য রাখা, তবে উদ্দেশ্য ভিন্ন — বারবার ব্যবহৃত তথ্য দ্রুত পাওয়া, গতির পার্থক্য মেলানো নয়।
   - Spooling: ধীরগতির যন্ত্রের (যেমন প্রিন্টার) জন্য তথ্য ডিস্কে জমিয়ে রাখা, যাতে একাধিক প্রসেস একসঙ্গে যন্ত্রটি ব্যবহার করতে পারে।
9. **(গ) Real Time System বলতে কী বোঝায় ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 625 (ET: N/A)]*


   Answer: Real Time System (রিয়েল-টাইম সিস্টেম) বলতে এমন একটি কম্পিউটার ব্যবস্থাকে বোঝায়, যেখানে ফলাফলের সঠিকতা কেবল যৌক্তিক শুদ্ধতার ওপর নয়, বরং ফলাফলটি কখন পাওয়া গেল তার ওপরও নির্ভর করে। অর্থাৎ সঠিক উত্তর দেরিতে পাওয়া মানে ভুল উত্তর।

   মূল বৈশিষ্ট্য:
   - প্রতিটি কাজের একটি নির্দিষ্ট সময়সীমা (deadline) থাকে, যার মধ্যে তা শেষ করতেই হবে।
   - সাড়া দেওয়ার সময় নির্ধারিত ও পূর্বানুমেয় (deterministic) হতে হবে; গড় গতি নয়, সবচেয়ে খারাপ ক্ষেত্রের গতি গুরুত্বপূর্ণ।
   - সাধারণত একটি নির্দিষ্ট কাজের জন্য নিবেদিত, সাধারণ উদ্দেশ্যের নয়।
   - অগ্রাধিকারভিত্তিক preemptive শিডিউলিং ব্যবহার করা হয়।
   - প্রায়ই ভার্চুয়াল মেমোরি ও পেজিং বন্ধ রাখা হয়, কারণ page fault এর সময় অনিশ্চিত।

   প্রকারভেদ:

   - Hard Real-Time System: সময়সীমা লঙ্ঘন সম্পূর্ণ অগ্রহণযোগ্য এবং তা বিপর্যয় ডেকে আনতে পারে। এখানে ফলাফলের নিশ্চয়তা গাণিতিকভাবে প্রমাণ করতে হয়।
     উদাহরণ: বিমানের ফ্লাই-বাই-ওয়্যার নিয়ন্ত্রণ, গাড়ির এয়ারব্যাগ, পেসমেকার, পারমাণবিক চুল্লির নিয়ন্ত্রণ ব্যবস্থা, ক্ষেপণাস্ত্র নির্দেশনা।

   - Soft Real-Time System: সময়সীমা লঙ্ঘিত হলে মান কমে যায়, কিন্তু বিপর্যয় ঘটে না। মাঝেমধ্যে দেরি সহনীয়।
     উদাহরণ: ভিডিও স্ট্রিমিং, অনলাইন গেম, ভিডিও কনফারেন্স, মাল্টিমিডিয়া প্লেব্যাক। একটি ফ্রেম দেরিতে এলে ছবি একটু আটকে যায়, কিন্তু কেউ মারা যায় না।

   - Firm Real-Time System: সময়সীমার পরে ফলাফলের কোনো মূল্য থাকে না, কিন্তু ক্ষতিও হয় না। যেমন একটি উৎপাদন লাইনে ছবি বিশ্লেষণ; ছবিটি দেরিতে বিশ্লেষিত হলে সেটি ফেলে দেওয়া হয়।

   রিয়েল-টাইম অপারেটিং সিস্টেমের বৈশিষ্ট্য:
   - অতি দ্রুত ও পূর্বানুমেয় context switch।
   - অগ্রাধিকারভিত্তিক preemptive শিডিউলিং, প্রায়শই Rate Monotonic Scheduling বা Earliest Deadline First অ্যালগরিদম।
   - Priority inversion প্রতিরোধে priority inheritance protocol।
   - ইন্টারাপ্টের সাড়া দেওয়ার সময়ের একটি নির্দিষ্ট ঊর্ধ্বসীমা।
   - ছোট আকার ও কম ওভারহেড, যা এমবেডেড যন্ত্রে চালানোর উপযোগী।

   উদাহরণ RTOS: VxWorks, QNX, RTLinux, FreeRTOS, RT-Thread এবং μC/OS।

   সাধারণ অপারেটিং সিস্টেমের সঙ্গে পার্থক্য:

   | বিষয় | সাধারণ OS (Linux, Windows) | Real-Time OS |
   |---|---|---|
   | প্রধান লক্ষ্য | গড় থ্রুপুট ও ন্যায্যতা বাড়ানো | প্রতিটি কাজের সময়সীমা রক্ষা |
   | পূর্বানুমেয়তা | কম | অত্যন্ত বেশি |
   | শিডিউলিং | ন্যায্যতাভিত্তিক | কঠোর অগ্রাধিকারভিত্তিক |
   | ভার্চুয়াল মেমোরি | ব্যবহৃত হয় | প্রায়ই বন্ধ রাখা হয় |
   | সবচেয়ে খারাপ ক্ষেত্রের গতি | অনির্ধারিত | নির্ধারিত ও নিশ্চিত |

   গুরুত্বপূর্ণ ভুল ধারণা: রিয়েল-টাইম মানে "খুব দ্রুত" নয়, বরং "সময়মতো ও নিশ্চিতভাবে"। একটি ধীর কিন্তু পূর্বানুমেয় ব্যবস্থা রিয়েল-টাইম হতে পারে, আর একটি অত্যন্ত দ্রুত কিন্তু মাঝেমধ্যে অনির্দিষ্ট বিলম্বযুক্ত ব্যবস্থা রিয়েল-টাইম নয়।
10. **Explain context switching in Operating System.** *[MGMCL Assistant Manager (ICT) 20.05.2022 compact it 649 (ET: BUET)]*


    Answer: A context switch is the operation by which the CPU is transferred from one process to another. The state of the currently running process is saved into its Process Control Block so that it can be resumed later, and the saved state of the incoming process is restored from its own PCB.

    What constitutes the context that is saved and restored:
    - The program counter, so that execution resumes at the right instruction
    - All CPU registers, including general-purpose registers, the stack pointer and the flag register
    - Memory management information: page table pointers or base and limit registers
    - The process state and scheduling information
    - Open file and input-output status

    Steps:
    1. An interrupt or a system call causes entry into kernel mode.
    2. The context of the running process P1 is saved into PCB1.
    3. The scheduler selects the next process P2 from the ready queue.
    4. The context of P2 is loaded from PCB2 into the CPU.
    5. The memory management unit is reloaded with P2's page table, and the TLB is flushed or tagged.
    6. Execution resumes in P2 at its program counter.

    When it occurs: the time quantum expires, the running process blocks for input or output, a higher-priority process becomes ready, the process terminates, or a hardware interrupt requires the kernel.

    Example:
    ```
    Time    Running   Action
    0-10    P1        P1 executes
    10      -         interrupt: save P1 into PCB1, load P2 from PCB2
    10-25   P2        P2 executes
    25      -         P2 blocks on I/O: save P2, load P1
    25-40   P1        P1 resumes exactly where it stopped at t = 10
    ```
    When P1 resumes it finds its registers, its stack and its program counter exactly as they were, so it cannot tell that anything happened in between.

    Cost:
    - It is pure overhead; no useful work is done during the switch.
    - Direct cost is typically 1 to 100 microseconds.
    - The indirect cost is often larger: the cache and TLB hold the outgoing process's data, so the incoming process suffers a burst of misses. This is cache pollution.
    - This cost is the reason why a very small scheduling quantum is harmful, and why switching between threads of the same process is much cheaper than switching between processes: threads share the address space, so no page table reload is needed.
11. **Which Operating system is considered as an Open source?** *[BARI Assistant Maintenance Engineer 26.08.2022 compact it 702 (ET: N/A)]*


    Answer: Linux is the operating system most commonly cited as open source.

    What open source means: the source code is publicly available, and anyone may study it, modify it and redistribute it, subject to the terms of its licence. Linux is released under the GNU General Public License version 2, a copyleft licence which requires that any distributed modification also be released under the same terms.

    About Linux:
    - The kernel was written by Linus Torvalds and first released in 1991.
    - Combined with the GNU tools, it forms a complete operating system, properly called GNU/Linux.
    - Major distributions: Ubuntu, Debian, Fedora, CentOS and its successors, Red Hat Enterprise Linux, openSUSE, Arch, Linux Mint and Kali.
    - It dominates servers, supercomputers, cloud infrastructure and embedded systems, and it is the base of Android.

    Other open source operating systems:
    - FreeBSD, OpenBSD and NetBSD, under the permissive BSD licence.
    - Android Open Source Project, though the Google applications shipped with most phones are proprietary.
    - Chromium OS, the open base of Chrome OS.
    - Minix, ReactOS, Haiku and Fuchsia.

    Advantages of open source:
    - No licence cost, which matters greatly for a government or an educational institution deploying thousands of machines.
    - The code can be inspected, so security flaws and hidden functions can be found by anyone.
    - It can be customised for local needs, including local language support.
    - There is no vendor lock-in, since the code and the data formats remain accessible.
    - A large community produces rapid fixes and a great deal of documentation.
    - It is highly stable and is the reason most of the world's servers run Linux.

    Disadvantages:
    - Support is community-based unless a commercial contract is purchased, for example from Red Hat or Canonical.
    - Some commercial and specialised software, and some hardware drivers, are not available.
    - It requires more technical skill to administer.
    - No single party is legally accountable for a defect.

    Comparison with proprietary systems: Windows, macOS, iOS and the commercial Unix variants are proprietary; their source code is closed and modification and redistribution are forbidden by the licence.

    Relevance to Bangladesh: national ICT policy encourages the use of open source software in government offices, both to reduce licence cost and to avoid dependence on a single foreign vendor. Many government servers, the BdREN network and several e-governance systems run on Linux.
12. **What is kernel? Write down the objectives of kernel.** *[SPCB Sub-Assistant Programmer 2022 compact it 740 (ET: N/A)]*


    Answer: The kernel is the core of an operating system. It is the first part loaded at boot and it stays permanently in main memory. It has complete control of the hardware and it acts as the bridge between application programs and the physical machine.

    Objectives and functions of the kernel:
    - Process management: creating, scheduling, switching and terminating processes and threads.
    - Memory management: allocating and freeing memory, paging, swapping, virtual memory and protection between address spaces.
    - Device management: controlling all hardware through device drivers, and providing a uniform interface to programs so that the same read and write calls work for a disk, a terminal and a network card.
    - File system management: creating, reading, writing, deleting and protecting files and directories.
    - Interrupt and exception handling.
    - System call interface: providing the controlled entry points through which a user program requests a service from the kernel.
    - Security and protection: enforcing access control, isolating processes from one another and separating user mode from kernel mode.
    - Inter-process communication: pipes, message queues, shared memory, signals and sockets.
    - Resource allocation and accounting.

    Modes of execution: the CPU runs either in user mode, in which privileged instructions and direct hardware access are forbidden, or in kernel mode, in which everything is permitted. A system call is the controlled transition from one to the other, and this separation is what prevents an application from crashing the machine.

    Types of kernel:
    - Monolithic kernel: all services (memory, file system, drivers, networking) run in one large kernel address space. Fast, because calls between services are ordinary function calls, but a fault anywhere can bring down the whole system. Examples: Linux, Unix, MS-DOS.
    - Microkernel: only the minimum (scheduling, basic memory management and inter-process communication) runs in kernel mode; drivers, the file system and networking run as user-level servers. Reliable and modular, but slower because services must communicate by message passing. Examples: Minix, QNX, L4, Mach.
    - Hybrid kernel: a middle position, with some services in the kernel for speed and others outside for reliability. Examples: Windows NT and its successors, macOS with XNU.
    - Exokernel and nanokernel: research designs that push almost everything into user space.

    Linux is technically monolithic, but it is modular: drivers can be loaded and unloaded at run time as kernel modules, which gives much of the flexibility of a microkernel without the message-passing cost.
13. **IBM প্রতিষ্ঠান কর্তৃক কোন Operating System প্রস্তুত করা হয়?** *[BPSC Computer Operator 2021 compact it 781 (ET: N/A)]*


    Answer: আইবিএম প্রতিষ্ঠান কর্তৃক প্রস্তুত করা উল্লেখযোগ্য অপারেটিং সিস্টেমগুলো হলো:

    - PC-DOS (Personal Computer Disk Operating System): ১৯৮১ সালে আইবিএম পিসির সঙ্গে সরবরাহ করা হয়। এটি মাইক্রোসফটের MS-DOS এরই আইবিএম সংস্করণ; মাইক্রোসফট তৈরি করে দেয় এবং আইবিএম নিজের নামে বিতরণ করে।

    - OS/2: ১৯৮৭ সালে আইবিএম ও মাইক্রোসফট যৌথভাবে শুরু করে; ১৯৯০ সালের পর আইবিএম একাই এটি এগিয়ে নেয়। এটি ছিল ৩২ বিটের, প্রকৃত multitasking সমর্থনকারী এবং প্রযুক্তিগতভাবে উইন্ডোজের চেয়ে উন্নত। কিন্তু বাজারে সফল হয়নি এবং OS/2 Warp সংস্করণের পর বন্ধ হয়ে যায়।

    - AIX (Advanced Interactive eXecutive): ১৯৮৬ সাল থেকে; আইবিএমের নিজস্ব ইউনিক্স সংস্করণ, যা এখনো তাদের POWER সার্ভারে ব্যবহৃত হয়।

    - z/OS: আইবিএমের মেইনফ্রেম কম্পিউটারের প্রধান অপারেটিং সিস্টেম, যা ব্যাংক, বিমা ও বড় প্রতিষ্ঠানের লেনদেন প্রক্রিয়াকরণে বিশ্বব্যাপী ব্যবহৃত হয়। এর পূর্বসূরি ছিল OS/360, MVS ও OS/390।

    - OS/400 (বর্তমানে IBM i): AS/400 মিনিকম্পিউটারের জন্য তৈরি।

    - VM (Virtual Machine): ১৯৭২ সালের CP/CMS থেকে উদ্ভূত, যা আধুনিক ভার্চুয়ালাইজেশনের অগ্রদূত। আজকের VMware ও হাইপারভাইজারের ধারণা এখান থেকেই এসেছে।

    - OS/360: ১৯৬৪ সালে System/360 মেইনফ্রেমের জন্য; কম্পিউটারের ইতিহাসে অন্যতম বৃহৎ ও প্রভাবশালী সফটওয়্যার প্রকল্প। এর নির্মাণ অভিজ্ঞতা থেকেই ফ্রেডরিক ব্রুকস লেখেন বিখ্যাত গ্রন্থ "The Mythical Man-Month"।

    প্রশ্নটি যদি একটিমাত্র উত্তর চায়, তবে সবচেয়ে প্রচলিত উত্তর PC-DOS অথবা OS/2, এবং মেইনফ্রেমের প্রসঙ্গে z/OS।

    ঐতিহাসিক উল্লেখযোগ্য তথ্য: ১৯৮০ সালে আইবিএম তাদের নতুন পিসির জন্য অপারেটিং সিস্টেম খুঁজছিল। মাইক্রোসফট একটি ছোট প্রতিষ্ঠানের কাছ থেকে QDOS কিনে সেটিকে MS-DOS নামে আইবিএমকে লাইসেন্স দেয়, কিন্তু একচেটিয়া অধিকার দেয়নি। ফলে মাইক্রোসফট অন্য নির্মাতাদের কাছেও একই সিস্টেম বিক্রি করতে পারে, এবং সেখান থেকেই ব্যক্তিগত কম্পিউটার সফটওয়্যারে মাইক্রোসফটের আধিপত্যের সূচনা।
14. **Explain: Kernel, Cache, Virtual Memory and RAID.** *[SPCBL Assistant Maintenance Engineer 20.11.2021 compact it 872-873 (ET: N/A)]*


    Answer:

    Kernel:

    The kernel is the core of an operating system, loaded at boot and permanently resident in memory, with complete control of the hardware. It is the bridge between applications and the physical machine.

    - Functions: process management, memory management, device management through drivers, file system management, interrupt handling, the system call interface, security and isolation, and inter-process communication.
    - It runs in kernel mode, in which all instructions are permitted, while applications run in user mode. A system call is the controlled transition between the two, and this separation is what prevents an application from crashing the machine.
    - Types: monolithic (Linux, Unix), microkernel (Minix, QNX, L4) and hybrid (Windows NT, macOS XNU).
    - Linux is monolithic but modular, since drivers can be loaded and unloaded at run time.

    Cache:

    Cache memory is a small, extremely fast SRAM memory placed between the CPU and main memory, holding copies of the instructions and data most recently or most frequently used.

    - Purpose: to bridge the speed gap between the processor, which works in fractions of a nanosecond, and DRAM, which needs 50 to 100 nanoseconds.
    - Levels: L1 (32 to 64 KB, private per core, fastest), L2 (256 KB to 2 MB), L3 (8 to 64 MB, shared by all cores).
    - It works because of locality of reference, both temporal (a recently used item will be used again) and spatial (items near a used item will be needed).
    - Average memory access time = hit time + (miss ratio x miss penalty). With a hit time of 2 ns, a penalty of 100 ns and a 95 per cent hit ratio, the average is 7 ns instead of 100 ns.
    - It is managed entirely by hardware and is invisible to the programmer and to the operating system.

    Virtual Memory:

    Virtual memory is a technique that gives a program the illusion of a large contiguous memory by using part of the disk as an extension of RAM. Only the pages actually in use are resident; the rest stay on disk and are fetched on demand.

    - Mechanism: the address space is divided into pages and physical memory into frames of the same size. A page table maps pages to frames, and a valid-invalid bit records whether a page is resident. A reference to a non-resident page causes a page fault, which the operating system services by fetching the page.
    - Benefits: programs larger than RAM can run; more processes fit in memory so CPU utilisation rises; start-up is faster; each process has a private protected address space; external fragmentation disappears; and sharing of code between processes becomes easy.
    - Cost: a page fault takes milliseconds; hardware support is needed; and too many resident processes cause thrashing.

    RAID:

    RAID stands for Redundant Array of Independent Disks. It combines several physical disks into one logical unit to improve performance, provide fault tolerance, or both.

    - Techniques: striping (data spread across disks for speed), mirroring (an identical copy for safety) and parity (an XOR block that allows a lost disk to be reconstructed).
    - Common levels:
      - RAID 0: striping only. Fastest, 100 per cent capacity, no protection.
      - RAID 1: mirroring. Survives one failure, 50 per cent capacity usable.
      - RAID 5: striping with distributed parity. Survives one failure, (n-1)/n capacity.
      - RAID 6: double parity. Survives two failures.
      - RAID 10: mirrored pairs then striped. Best performance with protection, 50 per cent capacity.
    - Caution: RAID is not a backup. It protects against the mechanical failure of a disk, but not against deletion, corruption, ransomware, fire or theft, because every such event is written to all disks at once.

    What the four have in common: all four are techniques for hiding a limitation of the hardware. The kernel hides the complexity of the hardware from applications; cache hides the slowness of memory from the CPU; virtual memory hides the small size of RAM from programs; and RAID hides the unreliability and slowness of a single disk from the file system.
15. **(a) Briefly describe the function that measure the efficiency of an operating system.** *[BPSC Assistant Maintenance Engineer (ICT) 2020 compact it 1025 (ET: N/A)]*


    Answer: The efficiency of an operating system is measured by a set of quantitative functions or metrics, each capturing one aspect of how well the system uses the machine and serves its users.

    - CPU utilisation: the percentage of time the processor is executing useful work rather than idling. It is to be maximised. A batch system may aim for 90 to 100 per cent; a lightly loaded interactive system may run at 40 per cent and still be satisfactory.
      CPU utilisation = (busy time / total time) x 100

    - Throughput: the number of processes or transactions completed per unit of time. It is to be maximised, and it is the natural measure for a batch or a transaction-processing system.
      Throughput = number of processes completed / total time

    - Turnaround time: the total time from the submission of a process to its completion, including waiting, execution and input-output. It is to be minimised.
      Turnaround Time = Completion Time - Arrival Time

    - Waiting time: the total time a process spends in the ready queue. It is to be minimised, and it is the quantity a scheduling algorithm can actually influence, since the scheduler cannot change the burst time.
      Waiting Time = Turnaround Time - Burst Time

    - Response time: the time from the submission of a request to the first response, not to the completion of the whole task. It is to be minimised, and it is the metric that matters most in an interactive system, because it determines how the machine feels to a user.
      Response Time = time of first CPU allocation - Arrival Time

    - Fairness: whether every process receives a reasonable share of the CPU, and whether starvation is prevented. It is measured by the variance of the waiting times as well as by their average.

    - Reliability and availability: measured by mean time between failures (MTBF), mean time to repair (MTTR), and availability computed as MTBF / (MTBF + MTTR). A system quoted as having five nines availability is unavailable for about five minutes a year.

    - Memory utilisation: how much of the physical memory holds useful data, and how much is wasted in internal and external fragmentation.

    - Page fault rate and effective memory access time: EAT = (1 - p) x memory access time + p x page fault service time. A high fault rate indicates that the system is heading towards thrashing.

    - Cache hit ratio: the proportion of memory references satisfied without going to main memory, which governs the effective speed of the whole machine.

    - Disk input-output performance: measured by seek time, rotational latency, transfer rate and input-output operations per second.

    - Context switch overhead: the number of switches per second and the time each takes. It is pure overhead, and it grows as the scheduling quantum shrinks.

    - System overhead: the fraction of CPU time spent in the kernel rather than in user programs. It is visible on Linux in the sy column of vmstat or top.

    - Scalability: how performance changes as processors, memory or users are added. Amdahl's law limits it: if a fraction p of the work is parallel, the maximum speedup is 1/(1 - p).

    - Security and protection: the ability to isolate processes and enforce access control, which is not a numeric measure but is an essential aspect of quality.

    Conflicts among the metrics, which should be stated: these measures cannot all be optimised at once. Maximising throughput favours SJF, which starves long processes and gives poor response time. Minimising response time favours Round Robin with a small quantum, which increases context-switch overhead and worsens turnaround time. Maximising CPU utilisation by admitting more processes eventually causes thrashing. The design of an operating system is therefore a set of deliberate compromises, chosen according to whether the system is a batch, an interactive, a real-time or an embedded one.

    Tools used to measure these in practice: on Linux, top, htop, vmstat, iostat, sar, perf and the /proc file system; on Windows, Task Manager, Resource Monitor and Performance Monitor.

## Virtual Memory & Page Replacement (Thrashing) (15)

1. Consider the following page reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1. Assuming a system with 3 page frames initially empty, calculate the number of page faults using the following page replacement algorithms: (i) FIFO (First-In, First-Out), (ii) LRU (Least Recently Used), and (iii) Optimal Page Replacement. [BSCCPL AME 21-08-2026 (BUET)]


   Answer: Reference string: 7, 0, 1, 2, 0, 3, 0, 4, 2, 3, 0, 3, 2, 1, 2, 0, 1, 7, 0, 1
   Number of frames: 3, all initially empty.

   (i) FIFO (First-In, First-Out)

   The page that has been in memory longest is replaced.

   | Ref | 7 | 0 | 1 | 2 | 0 | 3 | 0 | 4 | 2 | 3 | 0 | 3 | 2 | 1 | 2 | 0 | 1 | 7 | 0 | 1 |
   |---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
   | F1 | 7 | 7 | 7 | 2 | 2 | 2 | 2 | 4 | 4 | 4 | 0 | 0 | 0 | 0 | 0 | 0 | 0 | 7 | 7 | 7 |
   | F2 | | 0 | 0 | 0 | 0 | 3 | 3 | 3 | 2 | 2 | 2 | 2 | 2 | 1 | 1 | 1 | 1 | 1 | 0 | 0 |
   | F3 | | | 1 | 1 | 1 | 1 | 0 | 0 | 0 | 3 | 3 | 3 | 3 | 3 | 3 | 0 | 0 | 0 | 0 | 1 |
   | Fault | F | F | F | F | | F | F | F | F | F | F | | | F | | F | | F | F | F |

   Number of page faults with FIFO = 15

   (ii) LRU (Least Recently Used)

   The page that has not been used for the longest time is replaced.

   Trace of the faults: 7, 0, 1 fill the frames (3 faults). Then 2 replaces 7 (the least recently used), 0 hits, 3 replaces 1, 0 hits, 4 replaces 2, 2 replaces 3, 3 replaces 0, 0 replaces 4, 3 hits, 2 hits, 1 replaces 3, 2 hits, 0 replaces 1, 1 replaces 2, 7 replaces 0, 0 hits, 1 hits.

   Number of page faults with LRU = 12

   (iii) Optimal Page Replacement

   The page that will not be used for the longest time in the future is replaced. This requires knowledge of the future, so it cannot be implemented; it is used as the theoretical lower bound against which other algorithms are measured.

   Number of page faults with Optimal = 9

   Summary:

   | Algorithm | Page faults | Hit ratio |
   |---|---|---|
   | FIFO | 15 | 5/20 = 25 per cent |
   | LRU | 12 | 8/20 = 40 per cent |
   | Optimal | 9 | 11/20 = 55 per cent |

   Conclusions to state:
   - Optimal replaces the page that will not be used for the longest time in the future. It gives the fewest faults, as it must, because it is provably the best possible. But we cannot actually build it, since the operating system cannot know future requests. We use it only as a benchmark, to judge how good the other algorithms are.
   - LRU replaces the page that has not been used for the longest time in the past. It performs well, because it uses the past to guess the future, which is close to what Optimal does. We can build it, but it is more complex and more costly than FIFO, because it must record a timestamp on every single page access.
   - FIFO keeps all the pages in a queue, with the oldest page at the front, and replaces that oldest page. It is the simplest, but it performs worst, because how long a page has been in memory says very little about whether it will be needed again. It replaces frequently used pages by mistake.
   - Belady's anomaly: with FIFO, increasing the number of page frames can actually increase the page fault rate, instead of reducing it. That is the opposite of what we expect. LRU and Optimal are stack algorithms, and they never suffer from this anomaly.
   - The practical algorithms used in real systems are approximations of LRU: the second-chance or clock algorithm, and the enhanced clock algorithm that also considers the modify bit.
2. **Explain the concept of thrashing in an operating system, describing how it occurs in a demand-paged virtual memory system and how it impacts CPU utilization and overall system performance.** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1422 (ET: E-Zone)]*


   Answer: Thrashing is the condition in which a computer system spends most of its time servicing page faults, moving pages between memory and disk, rather than executing useful instructions. Throughput collapses even though the CPU appears busy handling faults.

   How it occurs in a demand-paged system:
   - Every process needs a certain minimum set of pages to run without constant faulting. This is its working set, the set of pages it has referenced in the recent past.
   - If the number of frames allocated to a process is smaller than its working set, the process faults on almost every reference. Each fault evicts a page that will be needed again almost immediately.
   - The chain of events is as follows. The operating system observes low CPU utilisation, because processes are blocked waiting for pages. Concluding that the machine is under-loaded, the long-term scheduler admits more processes. More processes share the same frames, so each gets fewer, so each faults more often, so CPU utilisation falls further, so still more processes are admitted. The system spirals into collapse.
   - This feedback loop is the essential mechanism of thrashing: the very action taken to improve utilisation makes it worse.

   Impact on CPU utilisation and system performance:
   - CPU utilisation rises with the degree of multiprogramming up to a peak, and then falls sharply and dramatically once thrashing begins.
   ```
   CPU
   util
    |        _____
    |      /       \
    |    /           \      <- thrashing begins here
    |  /               \____________
    |/
    +----------------------------------> degree of multiprogramming
   ```
   - Effective memory access time becomes enormous. With a memory access of 200 nanoseconds and a page fault service time of 8 milliseconds, a fault rate of even 1 in 1000 raises the average access time to about 8.2 microseconds, some forty times slower.
   - The disk is saturated with paging traffic, so genuine file input and output also becomes slow.
   - Response time becomes unacceptable, and to the user the machine appears frozen.
   - Throughput approaches zero, since almost no instructions are retired.

   Detection: a high page fault rate combined with low CPU utilisation and a disk that is continuously busy. On Linux this shows in vmstat as large si and so columns with a low us and sy total.

   Prevention and cure:
   - The working set model: measure the set of pages each process has used in the last delta references and allocate at least that many frames. If the sum of the working sets exceeds the available frames, suspend a process.
   - Page fault frequency control: monitor the fault rate of each process; if it exceeds an upper limit, give the process more frames, and if it falls below a lower limit, take frames away.
   - Reduce the degree of multiprogramming by suspending and swapping out one or more processes, which is the direct remedy.
   - Use local rather than global page replacement, so that one greedy process cannot steal frames from others.
   - Increase physical memory, which is the permanent solution.
   - Use a faster backing store, for example an SSD instead of a hard disk, which reduces the cost of each fault.
   - Improve locality of reference in the program itself, for example by traversing a matrix in the order in which it is stored.
3. **a) Write about notes on i) Virtual memory, and ii) Cache memory.** *[BPSC (Ministry of Food) Network/Website Manager (ICT) 21.05.2025 compact it 1343 (ET: N/A)]*


   Answer:

   (i) Virtual memory

   Virtual memory is a memory management technique that gives a program the illusion of a very large, contiguous main memory, by using a portion of secondary storage as an extension of physical memory. Only the parts of a program that are actually in use are kept in RAM; the rest remain on disk and are brought in on demand.

   How it works:
   - The address space of a process is divided into fixed-size pages, and physical memory into frames of the same size.
   - A page table maps each page to a frame, and every entry carries a valid-invalid bit showing whether the page is currently in memory.
   - When the CPU refers to a page that is not resident, the hardware raises a page fault, the operating system fetches the page from disk into a free frame (evicting another page if necessary), updates the page table, and restarts the instruction.
   - The Memory Management Unit performs the translation in hardware, assisted by the Translation Lookaside Buffer, a small cache of recent translations.

   Why it is needed:
   - It allows a program larger than physical memory to run, which would otherwise be impossible.
   - It raises the degree of multiprogramming, because each process occupies less physical memory, so more processes fit and CPU utilisation rises.
   - It speeds up program start-up, since only the first few pages need be loaded.
   - It avoids wasting memory on code that is never executed in a particular run, such as error handling routines.
   - It gives each process its own private address space, which provides protection and isolation: one process cannot address another's memory.
   - It removes the requirement that a process occupy a contiguous block of physical memory, which eliminates external fragmentation.
   - It makes sharing easy: two processes can map the same physical frame, which is how shared libraries and shared memory are implemented.
   - It simplifies programming, because the programmer need not write overlays or manage memory manually.

   Costs and limitations:
   - A page fault costs a disk access, several milliseconds, which is hundreds of thousands of CPU cycles.
   - Hardware support is required for translation.
   - If the degree of multiprogramming is too high, the system spends nearly all its time paging rather than executing, which is thrashing.

   (ii) Cache memory

   Cache memory is a small, extremely fast memory placed between the CPU and the main memory. It is built from SRAM and holds copies of the instructions and data the processor has used recently or is most likely to need next.

   Purpose: to bridge the speed gap between the processor, which works in fractions of a nanosecond, and DRAM main memory, which needs 50 to 100 nanoseconds. Without it the CPU would spend most of its cycles waiting.

   Levels: L1 is the smallest and fastest and is private to each core, usually split into separate instruction and data caches; L2 is larger and usually per core; L3 is the largest and is shared by all cores.

   Principle on which it works, locality of reference:
   - Temporal locality: an item just used is likely to be used again soon.
   - Spatial locality: items near a recently used item are likely to be needed next, which is why a whole block is fetched rather than a single byte.

   Operation: on a request the cache is searched first. A hit delivers the data in a few nanoseconds; a miss causes the whole block containing the address to be fetched from main memory, placed in the cache, and then delivered.

   Average memory access time: AMAT = hit time + (miss ratio x miss penalty). With a hit time of 2 ns, a miss penalty of 100 ns and a hit ratio of 95 per cent, AMAT = 2 + (0.05 x 100) = 7 ns instead of 100 ns.

   Comparison of the two:

   | Point | Virtual memory | Cache memory |
   |---|---|---|
   | Purpose | To make memory appear larger than it is | To make memory appear faster than it is |
   | Levels involved | Between main memory and disk | Between CPU and main memory |
   | Managed by | The operating system, with hardware support | The hardware, automatically and invisibly |
   | Unit of transfer | A page, typically 4 KB | A cache line or block, typically 64 bytes |
   | Miss penalty | Milliseconds, a disk access | Nanoseconds, a main memory access |
   | Visible to the programmer | Indirectly, through paging behaviour | Not at all |
   | Miss is called | Page fault | Cache miss |

   What they have in common: both rely on the principle of locality, both keep the active subset in a faster level, both need a replacement policy when the faster level is full, and both are transparent to the application program.
4. **Consider a reference string 4,7,6,1,2,7,2 the number of frames in the memory is 3. Using page Replacement Algorithm (LRU), find the number of page fault.** *[BPDB Assistant Engineer (CSE) 10.05.2024 compact it 391 (ET: BUET)]*


   Answer: Given: reference string 4, 7, 6, 1, 2, 7, 2 with 3 frames, using LRU (Least Recently Used) page replacement. All frames are initially empty.

   In LRU the page that has not been referenced for the longest time is chosen as the victim.

   Step-by-step trace, showing the frames in order from least recently used to most recently used:

   | Step | Reference | Frames (LRU first) | Hit or Fault | Page replaced |
   |---|---|---|---|---|
   | 1 | 4 | [4] | Fault | - (empty frame) |
   | 2 | 7 | [4, 7] | Fault | - (empty frame) |
   | 3 | 6 | [4, 7, 6] | Fault | - (empty frame) |
   | 4 | 1 | [7, 6, 1] | Fault | 4, the least recently used |
   | 5 | 2 | [6, 1, 2] | Fault | 7, the least recently used |
   | 6 | 7 | [1, 2, 7] | Fault | 6, the least recently used |
   | 7 | 2 | [1, 7, 2] | Hit | - |

   Working of the critical steps:
   - Step 4: the frames hold 4, 7 and 6. The order of last use is 4 (oldest), then 7, then 6. So 4 is evicted and 1 takes its place.
   - Step 5: the frames hold 7, 6 and 1, last used in that order. So 7 is evicted and 2 takes its place.
   - Step 6: the frames hold 6, 1 and 2, last used in that order. So 6 is evicted and 7 takes its place.
   - Step 7: page 2 is already in memory, so this is a hit, and 2 becomes the most recently used.

   Result:
   - Total references = 7
   - Page faults = 6
   - Page hits = 1
   - Fault ratio = 6/7 = 85.7 per cent
   - Hit ratio = 1/7 = 14.3 per cent

   Final answer: the number of page faults using LRU is 6.

   Note: the first three faults are unavoidable, because the frames start empty; these are called compulsory or cold-start misses. Only the remaining four references could in principle have been hits, and three of them were faults, which shows how poorly this particular short reference string suits a three-frame cache. With four frames the sequence would give only 5 faults, since page 7 would still be resident at step 6.
5. **Why virtual memory needed?** *[Dhaka Mass Transit Company Limited (DMTCL) Assistant Engineer (ICT) 27.01.2023 compact it 477 (ET: N/A)]*


   Answer: Virtual memory is a memory management technique that gives a program the illusion of a very large, contiguous main memory, by using a portion of secondary storage as an extension of physical memory. Only the parts of a program that are actually in use are kept in RAM; the rest remain on disk and are brought in on demand.

   How it works:
   - The address space of a process is divided into fixed-size pages, and physical memory into frames of the same size.
   - A page table maps each page to a frame, and every entry carries a valid-invalid bit showing whether the page is currently in memory.
   - When the CPU refers to a page that is not resident, the hardware raises a page fault, the operating system fetches the page from disk into a free frame (evicting another page if necessary), updates the page table, and restarts the instruction.
   - The Memory Management Unit performs the translation in hardware, assisted by the Translation Lookaside Buffer, a small cache of recent translations.

   Why it is needed:
   - It allows a program larger than physical memory to run, which would otherwise be impossible.
   - It raises the degree of multiprogramming, because each process occupies less physical memory, so more processes fit and CPU utilisation rises.
   - It speeds up program start-up, since only the first few pages need be loaded.
   - It avoids wasting memory on code that is never executed in a particular run, such as error handling routines.
   - It gives each process its own private address space, which provides protection and isolation: one process cannot address another's memory.
   - It removes the requirement that a process occupy a contiguous block of physical memory, which eliminates external fragmentation.
   - It makes sharing easy: two processes can map the same physical frame, which is how shared libraries and shared memory are implemented.
   - It simplifies programming, because the programmer need not write overlays or manage memory manually.

   Costs and limitations:
   - A page fault costs a disk access, several milliseconds, which is hundreds of thousands of CPU cycles.
   - Hardware support is required for translation.
   - If the degree of multiprogramming is too high, the system spends nearly all its time paging rather than executing, which is thrashing.
6. **Consider page reference string 1, 3, 0, 3, 5, 6, 3 with 3 page frames. Find the number of page faults.** *[Combined Bank Assistant Programmer 09.06.2023 compact it 493 (ET: N/A)]*


   Answer: Given: reference string 1, 3, 0, 3, 5, 6, 3 with 3 page frames, all initially empty. The replacement algorithm is not named in the question, so all three standard algorithms are worked out.

   (a) FIFO, in which the page that entered memory first is replaced

   | Step | Reference | Frames (oldest first) | Hit or Fault | Evicted |
   |---|---|---|---|---|
   | 1 | 1 | [1] | Fault | - |
   | 2 | 3 | [1, 3] | Fault | - |
   | 3 | 0 | [1, 3, 0] | Fault | - |
   | 4 | 3 | [1, 3, 0] | Hit | - |
   | 5 | 5 | [3, 0, 5] | Fault | 1 |
   | 6 | 6 | [0, 5, 6] | Fault | 3 |
   | 7 | 3 | [5, 6, 3] | Fault | 0 |

   Page faults with FIFO = 6, hits = 1

   (b) LRU, in which the page least recently used is replaced

   | Step | Reference | Frames (LRU first) | Hit or Fault | Evicted |
   |---|---|---|---|---|
   | 1 | 1 | [1] | Fault | - |
   | 2 | 3 | [1, 3] | Fault | - |
   | 3 | 0 | [1, 3, 0] | Fault | - |
   | 4 | 3 | [1, 0, 3] | Hit | - |
   | 5 | 5 | [0, 3, 5] | Fault | 1 |
   | 6 | 6 | [3, 5, 6] | Fault | 0 |
   | 7 | 3 | [5, 6, 3] | Hit | - |

   Page faults with LRU = 5, hits = 2

   (c) Optimal, in which the page not needed for the longest time in future is replaced

   | Step | Reference | Frames | Hit or Fault | Evicted and why |
   |---|---|---|---|---|
   | 1 | 1 | [1] | Fault | - |
   | 2 | 3 | [1, 3] | Fault | - |
   | 3 | 0 | [1, 3, 0] | Fault | - |
   | 4 | 3 | [1, 3, 0] | Hit | - |
   | 5 | 5 | [5, 3, 0] | Fault | 1, never referenced again |
   | 6 | 6 | [5, 3, 6] | Fault | 0, never referenced again |
   | 7 | 3 | [5, 3, 6] | Hit | - |

   Page faults with Optimal = 5, hits = 2

   Summary:

   | Algorithm | Page faults | Hits | Hit ratio |
   |---|---|---|---|
   | FIFO | 6 | 1 | 14.3 per cent |
   | LRU | 5 | 2 | 28.6 per cent |
   | Optimal | 5 | 2 | 28.6 per cent |

   Conclusion: LRU and Optimal both give 5 faults, and FIFO gives 6. The difference arises at step 5. FIFO evicts page 1 merely because it arrived first, but at step 6 it then evicts page 3, which is needed again at step 7. LRU keeps page 3, because it was used recently, and is therefore rewarded with a hit at the end. This is exactly why age of arrival is a poor predictor while recency of use is a good one.

   If the question intends a single algorithm, LRU is the usual assumption in an examination, giving 5 page faults.
7. **Difference between physical memory and virtual memory, also describe the advantages and disadvantages of virtual memory.** *[Combined Bank Assistant Maintenance Engineer/ Assistant Hardware Engineer 23.11.2023 compact it 553 (ET: BIBM)]*


   Answer:

   Difference between physical memory and virtual memory:

   | Point | Physical Memory | Virtual Memory |
   |---|---|---|
   | What it is | The actual RAM chips installed in the machine | An abstraction that combines RAM with a portion of disk |
   | Nature | Hardware | A technique implemented by the operating system with hardware support |
   | Size | Limited by the slots and modules installed, for example 8 GB | Limited by the address space and by disk space, for example 4 GB per process on a 32-bit system |
   | Addresses | Physical addresses, used directly by the memory hardware | Logical or virtual addresses, generated by the CPU and translated |
   | Speed | Fast, 50 to 100 nanoseconds | Fast when the page is resident; milliseconds when a page fault occurs |
   | Cost | Expensive per gigabyte | Uses cheap disk space |
   | Shared between processes | One shared resource | Each process has its own private address space |
   | Contiguity | Allocation had to be contiguous in older schemes | Not required; pages may lie anywhere |
   | Managed by | The memory controller | The operating system's memory manager and the MMU |
   | Volatility | Volatile | The disk portion is non-volatile, but the contents are discarded when the process ends |

   Advantages of virtual memory:
   - A program larger than physical memory can be executed, which is otherwise impossible.
   - More processes fit in memory at once, so the degree of multiprogramming and CPU utilisation both rise.
   - Programs start faster, because only the first few pages need be loaded.
   - Memory is not wasted on code that is never executed in a particular run.
   - Each process gets a private address space, which provides isolation and protection between processes.
   - External fragmentation disappears, because a process need not occupy contiguous physical memory.
   - Sharing is easy: several processes can map the same physical frame, which is how shared libraries work.
   - The programmer is freed from writing overlays or managing memory by hand.

   Disadvantages of virtual memory:
   - A page fault costs a disk access of several milliseconds, hundreds of thousands of CPU cycles, so a high fault rate destroys performance.
   - Hardware support is essential: a memory management unit and a translation lookaside buffer.
   - Page tables themselves consume memory, and for a large address space they must be made hierarchical or inverted.
   - Address translation adds latency to every memory reference, mitigated but not removed by the TLB.
   - Thrashing can occur if too many processes are resident, collapsing throughput.
   - Disk space must be reserved for the swap area.
   - Performance becomes less predictable, which is why hard real-time systems often disable paging altogether.

   Effective access time: EAT = (1 - p) x memory access time + p x page fault service time. With 200 ns and 8 ms, a fault rate of only 0.001 gives an EAT of about 8.2 microseconds, forty times slower than memory alone. This single calculation explains why keeping the fault rate low is the central concern of virtual memory design.
8. **(c) Define paging and trashing in the context of OS.** *[BPSC (Multiple Ministry) Assistant Programmer (ICT) 19.07.2023 compact it 490 (ET: N/A)]*


   Answer:

   Paging:

   Paging is a memory management technique in which the logical address space of a process is divided into fixed-size blocks called pages, and physical memory is divided into blocks of the same size called frames. Any page may be placed in any free frame, so a process need not occupy a contiguous region of physical memory.

   - Typical page size is 4 KB, and the size is always a power of two so that the address can be split by simple bit selection.
   - The logical address divides into a page number and an offset. The page number indexes the page table, which yields a frame number; the frame number and the offset together form the physical address.
   - Physical address = (frame number x page size) + offset
   - The Memory Management Unit performs the translation in hardware, assisted by the Translation Lookaside Buffer, a small cache of recent page-table entries.
   - Advantages: no external fragmentation, no requirement of contiguous allocation, easy swapping and sharing, and simple hardware translation.
   - Disadvantage: internal fragmentation in the last page of each process, on average half a page, and the memory occupied by the page tables themselves.
   - Paging is invisible to the programmer, which distinguishes it from segmentation.

   Thrashing:

   Thrashing is the condition in which a system spends most of its time moving pages between memory and disk rather than executing instructions, so that throughput collapses.

   - Cause: a process is given fewer frames than its working set, the set of pages it is actively using. It then faults on almost every reference, and each fault evicts a page that is needed again immediately.
   - The vicious circle: low CPU utilisation is observed, so the scheduler admits more processes, so each process gets fewer frames, so the fault rate rises further, so utilisation falls further. The system spirals downward.
   - Symptoms: a very high page fault rate, a disk that is continuously busy, very low CPU utilisation, and a machine that appears frozen to the user.
   - Detection: on Linux, vmstat shows large si and so values with a low us plus sy total.
   - Remedies:
     - The working set model: give each process at least as many frames as its recent working set requires.
     - Page fault frequency control: raise a process's allocation when its fault rate exceeds an upper bound, and lower it when the rate falls below a lower bound.
     - Reduce the degree of multiprogramming by suspending and swapping out one or more processes.
     - Use local rather than global replacement, so one process cannot steal frames from others.
     - Add physical memory, which is the permanent cure.
     - Improve the locality of the program itself.

   Relationship between the two: paging is the mechanism, and thrashing is what happens when that mechanism is pushed beyond the capacity of the physical memory available. Paging is a benefit; thrashing is its pathological failure mode.
9. **What is page fault in computing systems? What does it occur?** *[BICIC Assistant Programmer 2022 compact it 632 (ET: BUET)]*


   Answer: A page fault is the exception raised by the hardware when a running program refers to a page that is not currently present in physical memory. It is not an error; it is the normal signal by which demand paging works.

   When it occurs:
   - When a page is referenced for the first time, since with demand paging nothing is loaded until it is needed. This is a compulsory or cold-start fault, and it happens whenever a program starts, when it first touches a new data structure, or when it enters a rarely used code path.
   - When a page that was previously in memory has since been evicted by a page replacement algorithm to make room for another, and is now referenced again. This is a capacity fault.
   - When a page has been swapped out to disk because the system was short of memory.
   - When a memory-mapped file is accessed and the corresponding block has not yet been read.
   - On a copy-on-write page, when a process writes to a page shared with its parent after a fork; the write triggers a fault so that a private copy can be made.
   - On the guard page below a stack, so that the operating system can grow the stack automatically.
   - An invalid page fault occurs when the address is not part of the process's address space at all, for example on dereferencing a null or wild pointer. In that case the process is terminated with a segmentation fault; this is the only case that is genuinely an error.

   The mechanism, step by step:
   1. The CPU issues a virtual address.
   2. The MMU looks up the page table and finds the valid-invalid bit set to invalid.
   3. A trap to the operating system is raised, and the state of the process is saved.
   4. The operating system checks whether the reference is legal. If not, the process is killed.
   5. A free frame is found; if none is free, a victim is chosen and, if it is dirty, written back to disk.
   6. A disk read is scheduled, and the process is blocked. The CPU is given to another process.
   7. On completion, an interrupt occurs, the page table and the TLB are updated, and the process is made ready.
   8. The instruction that faulted is restarted from the beginning.

   Types:
   - Minor (soft) page fault: the page is already in physical memory, for example in the page cache or in another process's mapping, so only the page table has to be updated. It is fast, costing microseconds.
   - Major (hard) page fault: the page must actually be read from disk, costing milliseconds.
   - Invalid page fault: an illegal reference, resulting in termination.

   Cost, and why the rate matters:

   Effective Access Time = (1 - p) x memory access time + p x page fault service time

   With a memory access of 200 nanoseconds and a fault service time of 8 milliseconds:
   - p = 0.001 gives EAT = 0.999 x 200 + 0.001 x 8,000,000 = 8199.8 ns, about 40 times slower than memory alone.
   - To limit the slowdown to 10 per cent, p must be below about 0.0000025, that is fewer than one fault in 400,000 references.

   How the fault rate is kept low: locality of reference in the program, a good page replacement algorithm such as LRU or the clock algorithm, an adequate number of frames per process guided by the working set model, prepaging of pages likely to be needed, and enough physical memory. If the rate cannot be kept low, the system enters thrashing.

   Observing it on Linux:
   ```bash
   ps -o min_flt,maj_flt,cmd -p <pid>   # minor and major faults of a process
   vmstat 1                              # system-wide paging activity
   /usr/bin/time -v ./program            # fault counts for one run
   ```
10. **Write short note on Virtual Memory and Cache memory.** *[SPCB Sub-Assistant Programmer 2022 compact it 738 (ET: N/A)]*


    Answer:

    Virtual memory

    Virtual memory is a memory management technique that gives a program the illusion of a very large, contiguous main memory, by using a portion of secondary storage as an extension of physical memory. Only the parts of a program that are actually in use are kept in RAM; the rest remain on disk and are brought in on demand.

    How it works:
    - The address space of a process is divided into fixed-size pages, and physical memory into frames of the same size.
    - A page table maps each page to a frame, and every entry carries a valid-invalid bit showing whether the page is currently in memory.
    - When the CPU refers to a page that is not resident, the hardware raises a page fault, the operating system fetches the page from disk into a free frame (evicting another page if necessary), updates the page table, and restarts the instruction.
    - The Memory Management Unit performs the translation in hardware, assisted by the Translation Lookaside Buffer, a small cache of recent translations.

    Why it is needed:
    - It allows a program larger than physical memory to run, which would otherwise be impossible.
    - It raises the degree of multiprogramming, because each process occupies less physical memory, so more processes fit and CPU utilisation rises.
    - It speeds up program start-up, since only the first few pages need be loaded.
    - It avoids wasting memory on code that is never executed in a particular run, such as error handling routines.
    - It gives each process its own private address space, which provides protection and isolation: one process cannot address another's memory.
    - It removes the requirement that a process occupy a contiguous block of physical memory, which eliminates external fragmentation.
    - It makes sharing easy: two processes can map the same physical frame, which is how shared libraries and shared memory are implemented.
    - It simplifies programming, because the programmer need not write overlays or manage memory manually.

    Costs and limitations:
    - A page fault costs a disk access, several milliseconds, which is hundreds of thousands of CPU cycles.
    - Hardware support is required for translation.
    - If the degree of multiprogramming is too high, the system spends nearly all its time paging rather than executing, which is thrashing.

    Cache memory

    Cache memory is a small, very fast SRAM memory placed between the CPU and main memory, holding copies of the data and instructions most recently or most frequently used, so that the processor need not wait for the slower DRAM.

    - Levels: L1 (32 to 64 KB, private to each core, fastest), L2 (256 KB to 2 MB), L3 (8 to 64 MB, shared).
    - It works because of locality of reference, both temporal and spatial.
    - A request that is satisfied from the cache is a hit; one that is not is a miss, and the whole block containing the address is then fetched.
    - Average memory access time = hit time + (miss ratio x miss penalty).
    - It is managed entirely by hardware and is invisible to both the programmer and the operating system.

    Key distinction between the two: virtual memory addresses the problem of capacity, letting a program larger than RAM run by keeping part of it on disk. Cache memory addresses the problem of speed, letting the CPU work at full rate by keeping the active data close. Both apply the same underlying idea, that a small active subset of the data can stand in for the whole, and both rely on the principle of locality.
11. **(ii) Virtual Memory এর প্রয়োজনীয়তা কি ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 786 (ET: N/A)]*


    Answer: Virtual Memory হলো এমন একটি মেমোরি ব্যবস্থাপনা কৌশল, যেখানে সেকেন্ডারি স্টোরেজের একটি অংশকে প্রধান স্মৃতির সম্প্রসারণ হিসেবে ব্যবহার করে প্রোগ্রামকে একটি বিশাল ও ধারাবাহিক মেমোরির বিভ্রম দেওয়া হয়। প্রোগ্রামের যে অংশটুকু বর্তমানে ব্যবহৃত হচ্ছে কেবল সেটুকুই RAM এ রাখা হয়, বাকিটা ডিস্কে থাকে এবং প্রয়োজনমতো আনা হয়।

    প্রয়োজনীয়তা:

    - প্রধান স্মৃতির চেয়ে বড় প্রোগ্রাম চালানো যায়: ৪ গিগাবাইট RAM এর মেশিনে ৮ গিগাবাইটের প্রোগ্রামও চলতে পারে, কারণ পুরোটা একসঙ্গে মেমোরিতে থাকার দরকার হয় না। ভার্চুয়াল মেমোরি ছাড়া এটি সম্পূর্ণ অসম্ভব।

    - বহুপ্রোগ্রামিংয়ের মাত্রা বাড়ে: প্রতিটি প্রসেস কম মেমোরি দখল করায় একই সময়ে বেশি প্রসেস মেমোরিতে রাখা যায়, ফলে সিপিইউ ব্যবহারের হার ও থ্রুপুট বাড়ে।

    - প্রোগ্রাম দ্রুত চালু হয়: শুরুতে কেবল প্রথম কয়েকটি পৃষ্ঠা লোড করলেই চলে, পুরো ফাইল ডিস্ক থেকে পড়ার দরকার হয় না।

    - স্মৃতির অপচয় কমে: প্রোগ্রামের যেসব অংশ কোনোদিন চলবে না (যেমন বিরল ত্রুটি সামলানোর কোড), সেগুলো কখনোই মেমোরিতে আনা হয় না।

    - প্রতিটি প্রসেস নিজস্ব ঠিকানা জগৎ পায়: এর ফলে একটি প্রসেস অন্যটির মেমোরি ছুঁতে পারে না, অর্থাৎ সুরক্ষা ও বিচ্ছিন্নতা নিশ্চিত হয়।

    - ধারাবাহিক মেমোরি বরাদ্দের প্রয়োজন থাকে না: প্রসেসের পৃষ্ঠাগুলো মেমোরির যেকোনো ফাঁকা ফ্রেমে ছড়িয়ে থাকতে পারে, ফলে external fragmentation সম্পূর্ণ দূর হয়।

    - ভাগাভাগি সহজ হয়: একাধিক প্রসেস একই ফিজিক্যাল ফ্রেমে ম্যাপ করতে পারে, যেভাবে শেয়ার্ড লাইব্রেরি ও শেয়ার্ড মেমোরি কাজ করে। একই লাইব্রেরির একটিমাত্র কপি বিশটি প্রোগ্রাম ব্যবহার করতে পারে।

    - প্রোগ্রামিং সহজ হয়: প্রোগ্রামারকে overlay লিখে নিজে মেমোরি ব্যবস্থাপনা করতে হয় না; তিনি ধরে নিতে পারেন মেমোরি অসীম।

    - প্রসেস অদলবদল সহজ হয়: পুরো প্রসেস নয়, কেবল প্রয়োজনীয় পৃষ্ঠাগুলো আনা-নেওয়া করলেই চলে।

    ব্যয় ও সীমাবদ্ধতা:
    - প্রতিটি page fault এ একটি ডিস্ক অ্যাক্সেস লাগে, যা কয়েক মিলিসেকেন্ড, অর্থাৎ লক্ষ লক্ষ সিপিইউ চক্রের সমান।
    - ঠিকানা রূপান্তরের জন্য হার্ডওয়্যার সহায়তা (MMU ও TLB) প্রয়োজন।
    - অতিরিক্ত প্রসেস মেমোরিতে রাখলে সিস্টেম thrashing এ পড়ে যায়, অর্থাৎ প্রায় সব সময় পৃষ্ঠা আনা-নেওয়াতেই ব্যয় হয়।

    কার্যকর অ্যাক্সেস সময়: EAT = (1 - p) x মেমোরি অ্যাক্সেস সময় + p x page fault সেবার সময়, যেখানে p হলো page fault এর হার। মেমোরি অ্যাক্সেস ২০০ ন্যানোসেকেন্ড ও fault সেবা ৮ মিলিসেকেন্ড হলে p = 0.001 এই সামান্য হারেও EAT দাঁড়ায় প্রায় ৮,২০০ ন্যানোসেকেন্ড, অর্থাৎ ৪০ গুণ ধীর। এ কারণেই page fault এর হার অত্যন্ত কম রাখা অপরিহার্য।
12. **A system uses 3 page frames for storing process pages in main memory. It uses the Least Recently Used (LRU) page replacement policy. Assume that all the page frames are initially empty. What is the total number of page faults that will occur while processing the page reference string given below? 4, 7, 6, 1, 7, 6, 1, 2, 7, 2.** *[BPDB Assistant Engineer (CSE) 2021 compact it 817 (ET: BUET)]*


    Answer: Given: reference string 4, 7, 6, 1, 7, 6, 1, 2, 7, 2 with 3 frames, using LRU page replacement. All frames are initially empty.

    Step-by-step trace, with the frames listed from least recently used to most recently used:

    | Step | Reference | Frames (LRU first) | Hit or Fault | Page evicted |
    |---|---|---|---|---|
    | 1 | 4 | [4] | Fault | - |
    | 2 | 7 | [4, 7] | Fault | - |
    | 3 | 6 | [4, 7, 6] | Fault | - |
    | 4 | 1 | [7, 6, 1] | Fault | 4 |
    | 5 | 7 | [6, 1, 7] | Hit | - |
    | 6 | 6 | [1, 7, 6] | Hit | - |
    | 7 | 1 | [7, 6, 1] | Hit | - |
    | 8 | 2 | [6, 1, 2] | Fault | 7 |
    | 9 | 7 | [1, 2, 7] | Fault | 6 |
    | 10 | 2 | [1, 7, 2] | Hit | - |

    Working of the critical steps:
    - Step 4: the frames hold 4, 7, 6, last used in that order, so 4 is the least recently used and is evicted.
    - Steps 5, 6 and 7: pages 7, 6 and 1 are all resident, so all three are hits, and each reference moves the page to the most-recently-used end.
    - Step 8: after step 7 the order is 7 (oldest), 6, 1. So 7 is evicted for page 2.
    - Step 9: the order is now 6 (oldest), 1, 2. So 6 is evicted for page 7.
    - Step 10: page 2 is resident, so this is a hit.

    Result:
    - Total references = 10
    - Page faults = 6
    - Page hits = 4
    - Fault ratio = 6/10 = 60 per cent
    - Hit ratio = 4/10 = 40 per cent

    Final answer: the total number of page faults is 6.

    Observation: three of the six faults are compulsory, occurring because the frames were empty at the start; only three are true replacement misses. The middle portion of the string, 7, 6, 1, is served entirely from memory, which shows LRU working exactly as intended: those three pages had all been used recently and were therefore retained.
13. **Briefly explain the concept of ‘Thrashing’ in terms of OS.** *[Titas Gas Assistant Engineer (CSE) 2021 compact it 822 (ET: BUET)]*


    Answer: Thrashing is the condition in which a computer system spends most of its time servicing page faults, moving pages between memory and disk, rather than executing useful instructions. Throughput collapses even though the CPU appears busy handling faults.

    How it occurs in a demand-paged system:
    - Every process needs a certain minimum set of pages to run without constant faulting. This is its working set, the set of pages it has referenced in the recent past.
    - If the number of frames allocated to a process is smaller than its working set, the process faults on almost every reference. Each fault evicts a page that will be needed again almost immediately.
    - The chain of events is as follows. The operating system observes low CPU utilisation, because processes are blocked waiting for pages. Concluding that the machine is under-loaded, the long-term scheduler admits more processes. More processes share the same frames, so each gets fewer, so each faults more often, so CPU utilisation falls further, so still more processes are admitted. The system spirals into collapse.
    - This feedback loop is the essential mechanism of thrashing: the very action taken to improve utilisation makes it worse.

    Impact on CPU utilisation and system performance:
    - CPU utilisation rises with the degree of multiprogramming up to a peak, and then falls sharply and dramatically once thrashing begins.
    ```
    CPU
    util
     |        _____
     |      /       \
     |    /           \      <- thrashing begins here
     |  /               \____________
     |/
     +----------------------------------> degree of multiprogramming
    ```
    - Effective memory access time becomes enormous. With a memory access of 200 nanoseconds and a page fault service time of 8 milliseconds, a fault rate of even 1 in 1000 raises the average access time to about 8.2 microseconds, some forty times slower.
    - The disk is saturated with paging traffic, so genuine file input and output also becomes slow.
    - Response time becomes unacceptable, and to the user the machine appears frozen.
    - Throughput approaches zero, since almost no instructions are retired.

    Detection: a high page fault rate combined with low CPU utilisation and a disk that is continuously busy. On Linux this shows in vmstat as large si and so columns with a low us and sy total.

    Prevention and cure:
    - The working set model: measure the set of pages each process has used in the last delta references and allocate at least that many frames. If the sum of the working sets exceeds the available frames, suspend a process.
    - Page fault frequency control: monitor the fault rate of each process; if it exceeds an upper limit, give the process more frames, and if it falls below a lower limit, take frames away.
    - Reduce the degree of multiprogramming by suspending and swapping out one or more processes, which is the direct remedy.
    - Use local rather than global page replacement, so that one greedy process cannot steal frames from others.
    - Increase physical memory, which is the permanent solution.
    - Use a faster backing store, for example an SSD instead of a hard disk, which reduces the cost of each fault.
    - Improve locality of reference in the program itself, for example by traversing a matrix in the order in which it is stored.
14. **(a) What do you mean by virtual memory?** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 895 (ET: N/A)]*


    Answer: Virtual memory is a memory management technique that gives a program the illusion of a very large, contiguous main memory, by using a portion of secondary storage as an extension of physical memory. Only the parts of a program that are actually in use are kept in RAM; the rest remain on disk and are brought in on demand.

    How it works:
    - The address space of a process is divided into fixed-size pages, and physical memory into frames of the same size.
    - A page table maps each page to a frame, and every entry carries a valid-invalid bit showing whether the page is currently in memory.
    - When the CPU refers to a page that is not resident, the hardware raises a page fault, the operating system fetches the page from disk into a free frame (evicting another page if necessary), updates the page table, and restarts the instruction.
    - The Memory Management Unit performs the translation in hardware, assisted by the Translation Lookaside Buffer, a small cache of recent translations.

    Why it is needed:
    - It allows a program larger than physical memory to run, which would otherwise be impossible.
    - It raises the degree of multiprogramming, because each process occupies less physical memory, so more processes fit and CPU utilisation rises.
    - It speeds up program start-up, since only the first few pages need be loaded.
    - It avoids wasting memory on code that is never executed in a particular run, such as error handling routines.
    - It gives each process its own private address space, which provides protection and isolation: one process cannot address another's memory.
    - It removes the requirement that a process occupy a contiguous block of physical memory, which eliminates external fragmentation.
    - It makes sharing easy: two processes can map the same physical frame, which is how shared libraries and shared memory are implemented.
    - It simplifies programming, because the programmer need not write overlays or manage memory manually.

    Costs and limitations:
    - A page fault costs a disk access, several milliseconds, which is hundreds of thousands of CPU cycles.
    - Hardware support is required for translation.
    - If the degree of multiprogramming is too high, the system spends nearly all its time paging rather than executing, which is thrashing.
15. **A system uses 8 page frames to store process pages in main memory. It uses the minimum page replacement policy. Assume that all page frames are initially blank. 64 separate pages were inserted and then the pages were inserted reverse order. How many pages will be miss?** *[SGFL Assistant General Engineer 2021 compact it 936 (ET: BUET)]*


    Answer: Given: 8 page frames, all initially blank, and the minimum (Optimal) page replacement policy. 64 separate pages are referenced in order, and then the same pages are referenced in reverse order.

    The reference string is therefore:
    1, 2, 3, ..., 63, 64, 64, 63, 62, ..., 2, 1
    with 128 references in total, of which 64 are distinct pages.

    Step 1 - the forward pass, references 1 to 64:
    - Every page is referenced for the first time, so every reference is a miss. These are compulsory misses, which no algorithm can avoid.
    - The first 8 fill the empty frames; the remaining 56 each cause a replacement.
    - Misses in the forward pass = 64

    Step 2 - which pages remain in memory at the end of the forward pass:
    - Optimal replacement evicts the page that will be needed farthest in the future. During the forward pass, the future consists of the reverse pass, in which high-numbered pages are needed soonest and low-numbered pages last.
    - Therefore, at every replacement, Optimal evicts the lowest-numbered page present, because that is the one that will be needed last.
    - After all 64 references, the 8 pages retained are the 8 highest, namely 57, 58, 59, 60, 61, 62, 63 and 64.

    Step 3 - the reverse pass, references 64 down to 1:
    - The first 8 references, 64, 63, 62, 61, 60, 59, 58 and 57, are all present, so they are hits.
    - The remaining 56 references, pages 56 down to 1, are not in memory, so each is a miss.
    - Misses in the reverse pass = 56

    Step 4 - total:
    - Total misses = 64 + 56 = 120
    - Total hits = 128 - 120 = 8
    - Hit ratio = 8/128 = 6.25 per cent

    Final answer: 120 page misses.

    Verification with the other algorithms: FIFO and LRU also give 120 misses for this reference string. LRU performs badly here for an instructive reason: at the end of the forward pass it retains the 8 most recently used pages, which are again 57 to 64, so it too gets 8 hits. FIFO retains the same 8 for the same arithmetic reason. This is the well-known worst case for LRU, a sequential scan of a data set larger than the cache followed by a scan in the opposite direction, in which recency is exactly the wrong predictor.

    General result: with f frames and n distinct pages referenced forward and then backward, where n is greater than f, the number of misses is n + (n - f), and the number of hits is f. Here n = 64 and f = 8, giving 64 + 56 = 120 misses and 8 hits.

    Practical significance: this pattern, a scan larger than the buffer, is common in database systems, and it is why database buffer managers do not use plain LRU. They detect sequential scans and apply a different policy, such as most-recently-used replacement or a dedicated small scan buffer, so that a single large scan does not flush the whole cache.

## Memory Management & Paging (13)

1. **A system uses 16 bit logical address and a page size of 1 KB.**
   **(i) How many pages are in logical address space?**
   **(ii) How many bits are used for the page number and offset?** *[Dhaka WASA Assistant Maintenance Engineer (Network) 04.07.2025 compact it 1437 (ET: BUET)]*


   Answer: Given: logical address = 16 bits, page size = 1 KB.

   (i) Number of pages in the logical address space

   Step 1 - size of the logical address space:
   - 16-bit address means 2^16 addressable bytes = 65,536 bytes = 64 KB

   Step 2 - number of pages:
   - Number of pages = logical address space / page size
   - = 2^16 / 2^10
   - = 2^6
   - = 64 pages

   (ii) Bits used for the page number and the offset

   Step 1 - offset bits. The offset must be able to address any byte within one page:
   - Page size = 1 KB = 2^10 bytes
   - Offset bits = log2(1024) = 10 bits

   Step 2 - page number bits. The page number must be able to identify any of the 64 pages:
   - Page number bits = total address bits - offset bits
   - = 16 - 10
   - = 6 bits
   - Check: 2^6 = 64 pages. Correct.

   Address division:

   ```
   |<--- 6 bits --->|<------- 10 bits ------->|
   |  Page number   |         Offset          |
   ```

   | Field | Bits | Range | Meaning |
   |---|---|---|---|
   | Page number (p) | 6 | 0 to 63 | Index into the page table |
   | Offset (d) | 10 | 0 to 1023 | Byte within the page |
   | Total | 16 | | |

   Worked example of translation: suppose the logical address is 0000110000000101 in binary.
   - Page number = the leading 6 bits = 000011 = 3
   - Offset = the trailing 10 bits = 0000000101 = 5
   - If the page table says page 3 is in frame 9, the physical address is (9 x 1024) + 5 = 9221.

   General rules worth stating:
   - Number of pages = 2^(logical address bits - offset bits)
   - Number of frames = 2^(physical address bits - offset bits)
   - The offset field is the same width in the logical and the physical address, because a page and a frame are the same size. Only the page or frame number is translated.
2. **Consider a logical address space of 512 pages, each of 2-KB page size, mapped onto a physical memory containing 128 frames.**
   **a. How many bits are required in the logical address?**
   **b. How many bits are required in the physical address?** *[Combined Bank Senior Officer (IT) 17.10.2025 compact it 1420 (ET: E-Zone)]*


   Answer: Given: logical address space of 512 pages, page size 2 KB, physical memory of 128 frames.

   (a) Bits required in the logical address

   Step 1 - bits for the page number:
   - Number of pages = 512 = 2^9
   - Page number bits = 9

   Step 2 - bits for the offset:
   - Page size = 2 KB = 2 x 1024 = 2048 bytes = 2^11
   - Offset bits = 11

   Step 3 - total logical address bits:
   - = page number bits + offset bits
   - = 9 + 11
   - = 20 bits

   Check: the logical address space is 512 x 2 KB = 1024 KB = 1 MB = 2^20 bytes, which needs exactly 20 bits.

   ```
   Logical address:
   |<--- 9 bits --->|<-------- 11 bits -------->|
   |  Page number   |          Offset           |
   ```

   (b) Bits required in the physical address

   Step 1 - bits for the frame number:
   - Number of frames = 128 = 2^7
   - Frame number bits = 7

   Step 2 - bits for the offset:
   - A frame is the same size as a page, that is 2 KB, so the offset is again 11 bits.

   Step 3 - total physical address bits:
   - = 7 + 11
   - = 18 bits

   Check: physical memory = 128 x 2 KB = 256 KB = 2^18 bytes, which needs exactly 18 bits.

   ```
   Physical address:
   |<-- 7 bits -->|<-------- 11 bits -------->|
   | Frame number |          Offset           |
   ```

   Summary:

   | Item | Value | Bits |
   |---|---|---|
   | Number of pages | 512 = 2^9 | 9 for the page number |
   | Page size | 2 KB = 2^11 | 11 for the offset |
   | Logical address | 1 MB = 2^20 | 20 |
   | Number of frames | 128 = 2^7 | 7 for the frame number |
   | Physical memory | 256 KB = 2^18 | 18 |

   Important observation: the logical address is larger than the physical address, 20 bits against 18. This is normal and is the whole purpose of virtual memory: the logical address space of a process may be larger than the physical memory installed, and pages not currently in memory are kept on disk and brought in on demand.

   Note also that the offset field is identical in both addresses, at 11 bits. Only the page number is translated into a frame number by the page table; the offset is copied through unchanged.
3. **(a) Consider a computer system with the following specifications:** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1351 (ET: N/A)]*
 * Physical memory (RAM): 4\text{ GB}
 * Page size: 4\text{ KB}
 * Virtual address space: 32\text{ bits}
 * Page table entry size: 8\text{ bytes}
**Answer the following:**
 * **(i) How many pages are there in the virtual address space? Explain your answer.**
 * **(ii) What is the size of the page table? Explain your answer.**


   Answer: Given:
   - Physical memory (RAM) = 4 GB
   - Page size = 4 KB
   - Virtual address space = 32 bits
   - Page table entry size = 8 bytes

   (i) Number of pages in the virtual address space

   Step 1 - size of the virtual address space:
   - 32-bit address means 2^32 bytes = 4,294,967,296 bytes = 4 GB

   Step 2 - page size in powers of two:
   - 4 KB = 4 x 1024 = 4096 bytes = 2^12

   Step 3 - number of pages:
   - Number of pages = virtual address space / page size
   - = 2^32 / 2^12
   - = 2^20
   - = 1,048,576 pages

   Answer (i): there are 2^20 = 1,048,576 pages, that is about one million pages.

   Explanation: the 32-bit virtual address divides into a page number and an offset. The offset needs 12 bits, because a page holds 2^12 bytes. The remaining 32 - 12 = 20 bits form the page number, and 20 bits can identify 2^20 distinct pages.

   ```
   |<------- 20 bits ------->|<--- 12 bits --->|
   |      Page number        |     Offset      |
   ```

   (ii) Size of the page table

   Step 1 - the page table needs one entry for every page in the virtual address space:
   - Number of entries = 2^20 = 1,048,576

   Step 2 - each entry occupies 8 bytes:
   - Page table size = number of entries x entry size
   - = 2^20 x 8
   - = 2^20 x 2^3
   - = 2^23 bytes

   Step 3 - express in convenient units:
   - 2^23 bytes = 8,388,608 bytes
   - = 8,388,608 / (1024 x 1024) MB
   - = 8 MB

   Answer (ii): the page table occupies 8 MB.

   Explanation and its significance: 8 MB is required for the page table of a single process. With one hundred processes running, the page tables alone would occupy 800 MB of physical memory, which is clearly unacceptable. This is precisely why real systems do not use a single flat page table.

   The solutions actually used:
   - Multi-level (hierarchical) paging: the page table is itself paged, so only the parts that are in use need be resident. A two-level scheme on this machine would use 10 bits for the outer table, 10 for the inner and 12 for the offset, and a typical process would need only a few pages of table rather than 8 MB.
   - Inverted page table: one entry per physical frame rather than per virtual page, so the table size depends on the size of RAM, not on the size of the virtual address space, and one table serves all processes.
   - Hashed page tables, used for large address spaces.
   - The Translation Lookaside Buffer (TLB): a small associative cache of recent translations, which avoids a memory access for the page table on most references. With a 98 per cent hit rate the effective access time is close to that of a single memory access.

   Additional calculations that follow from the same data:
   - Number of frames in physical memory = 4 GB / 4 KB = 2^32 / 2^12 = 2^20 = 1,048,576 frames, so the frame number also needs 20 bits.
   - The physical address is therefore also 32 bits, and the virtual and physical address spaces happen to be the same size here.
4. **Compare “Paging” and “Segmentation” memory management technique?** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1340 (ET: N/A)]*


   Answer: | Point | Paging | Segmentation |
   |---|---|---|
   | Division of memory | Memory is divided into fixed-size blocks called frames, and the process into equal-size pages | Memory is divided into variable-size blocks corresponding to logical units of the program |
   | Size of the block | Fixed, typically 4 KB | Variable, decided by the size of the segment |
   | Decided by | The hardware and the operating system | The programmer or the compiler |
   | Visible to the programmer | No; paging is invisible to the program | Yes; segments correspond to code, data, stack and heap |
   | Logical address | One number, split by hardware into page number and offset | Two parts: segment number and offset |
   | Mapping table | Page table, holding frame numbers | Segment table, holding base address and limit |
   | Internal fragmentation | Yes, in the last page of a process, on average half a page | No |
   | External fragmentation | No, since all frames are the same size | Yes, because free holes of different sizes appear |
   | Protection | Applied per page, which does not follow the logical structure | Applied per segment, which matches the logical structure and is therefore more natural |
   | Sharing | Possible but awkward, since a shared routine may not fill whole pages | Natural; a whole code segment can be shared by several processes |
   | Growth of a structure | Awkward | Easy; a segment can simply be given a larger limit |
   | Address translation | Physical address = frame number x page size + offset | Physical address = segment base + offset, after checking offset < limit |
   | Speed of translation | Fast, since it is a simple concatenation | Slightly slower, since an addition and a bounds check are needed |

   Combined scheme, which is what real systems use: segmentation with paging. The program is divided into logical segments, and each segment is then divided into pages. This gives the logical structure and protection of segmentation together with the absence of external fragmentation of paging. The Intel x86 architecture supports exactly this, and Linux uses it with a flat segmentation model so that in practice only paging is visible.
5. **The __________ swaps process in and out of the memory.** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: The medium-term scheduler, also called the swapper, swaps processes in and out of memory.

   Explanation:
   - Swapping is the technique of temporarily removing a process from main memory and storing it on a backing store, usually a dedicated area of disk called the swap space, and later bringing it back into memory to continue execution.
   - Removing a process is called swapping out or roll-out; bringing it back is swapping in or roll-in.

   Why it is done:
   - To free physical memory when the system is under memory pressure.
   - To reduce the degree of multiprogramming when too many processes are competing, which is the standard remedy for thrashing.
   - To improve the mix of processes in memory, keeping a balance between CPU-bound and input-output-bound work.
   - In a priority-based system, a lower-priority process may be swapped out so that a higher-priority process can run; this is called roll-out, roll-in.

   The three schedulers, for comparison:

   | Scheduler | Also called | Selects | Frequency |
   |---|---|---|---|
   | Long-term | Job scheduler | Which jobs enter memory | Seconds to minutes |
   | Short-term | CPU scheduler | Which ready process gets the CPU | Milliseconds |
   | Medium-term | Swapper | Which process to swap out or in | In between |

   State transitions caused by swapping: Ready to Suspended-Ready, and Blocked to Suspended-Blocked, and the reverse when the process is swapped back in.

   Practical note: the cost of swapping is dominated by the disk transfer time. Swapping a 100 MB process at 50 MB per second takes about 2 seconds each way, which is enormous compared with a context switch. Modern systems therefore rarely swap whole processes; instead they page, that is they move individual pages in and out on demand, which is far cheaper. The Linux command free -h shows the swap space in use, and the swappiness parameter controls how readily the kernel resorts to it.
6. **Difference between Paging and Segmentation.** *[BTCL - JAM ( Technical) 05.04.2024 compact it 383 (ET: BUET)]*


   Answer: | Point | Paging | Segmentation |
   |---|---|---|
   | Division of memory | Memory is divided into fixed-size blocks called frames, and the process into equal-size pages | Memory is divided into variable-size blocks corresponding to logical units of the program |
   | Size of the block | Fixed, typically 4 KB | Variable, decided by the size of the segment |
   | Decided by | The hardware and the operating system | The programmer or the compiler |
   | Visible to the programmer | No; paging is invisible to the program | Yes; segments correspond to code, data, stack and heap |
   | Logical address | One number, split by hardware into page number and offset | Two parts: segment number and offset |
   | Mapping table | Page table, holding frame numbers | Segment table, holding base address and limit |
   | Internal fragmentation | Yes, in the last page of a process, on average half a page | No |
   | External fragmentation | No, since all frames are the same size | Yes, because free holes of different sizes appear |
   | Protection | Applied per page, which does not follow the logical structure | Applied per segment, which matches the logical structure and is therefore more natural |
   | Sharing | Possible but awkward, since a shared routine may not fill whole pages | Natural; a whole code segment can be shared by several processes |
   | Growth of a structure | Awkward | Easy; a segment can simply be given a larger limit |
   | Address translation | Physical address = frame number x page size + offset | Physical address = segment base + offset, after checking offset < limit |
   | Speed of translation | Fast, since it is a simple concatenation | Slightly slower, since an addition and a bounds check are needed |

   Combined scheme, which is what real systems use: segmentation with paging. The program is divided into logical segments, and each segment is then divided into pages. This gives the logical structure and protection of segmentation together with the absence of external fragmentation of paging. The Intel x86 architecture supports exactly this, and Linux uses it with a flat segmentation model so that in practice only paging is visible.
7. **(ক) Swapping কী? Internal এবং External Fragmentation এর মধ্যে পার্থক্য লিখুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 414 (ET: N/A)]*


   Answer:

      Swapping কী:

      Swapping হলো এমন একটি কৌশল, যেখানে কোনো প্রসেসকে সাময়িকভাবে প্রধান মেমোরি থেকে সরিয়ে সেকেন্ডারি স্টোরেজে (সাধারণত ডিস্কের একটি নির্দিষ্ট অংশ, যাকে swap space বলা হয়) রেখে দেওয়া হয় এবং পরে প্রয়োজনে আবার মেমোরিতে ফিরিয়ে এনে চালানো হয়।

      - মেমোরি থেকে সরিয়ে নেওয়াকে বলে swap out বা roll out।
      - ফিরিয়ে আনাকে বলে swap in বা roll in।
      - এই কাজটি করে medium-term scheduler, যাকে swapper বলা হয়।

      কেন প্রয়োজন:
      - মেমোরির চাপ কমানো, যাতে বেশি প্রসেস একসঙ্গে চালানো যায়।
      - Thrashing দেখা দিলে multiprogramming এর মাত্রা কমানো।
      - উচ্চ অগ্রাধিকারের প্রসেসকে জায়গা করে দিতে নিম্ন অগ্রাধিকারের প্রসেস সরিয়ে রাখা।
      - CPU-নির্ভর ও I/O-নির্ভর প্রসেসের ভারসাম্য বজায় রাখা।

      সীমাবদ্ধতা: পুরো প্রসেস ডিস্কে লেখা ও পড়া অত্যন্ত সময়সাপেক্ষ। ১০০ মেগাবাইটের একটি প্রসেস ৫০ মেগাবাইট/সেকেন্ড গতিতে সরাতে প্রায় ২ সেকেন্ড লাগে। তাই আধুনিক সিস্টেমে সম্পূর্ণ প্রসেস অদলবদল না করে চাহিদা অনুযায়ী পৃষ্ঠা ধরে ধরে সরানো হয়, যাকে বলে demand paging।

      Internal ও External Fragmentation এর পার্থক্য:

   | Point | Internal Fragmentation | External Fragmentation |
      |---|---|---|
      | Definition | Wasted space inside an allocated block, because the block is larger than the request | Wasted space outside allocated blocks, in free holes that are individually too small to be useful |
      | Where the waste is | Within a partition or a page that has been allocated | Between allocated partitions |
      | Cause | Fixed-size allocation units | Variable-size allocation and repeated allocation and release |
      | Occurs in | Paging, and fixed partitioning | Segmentation, and dynamic or variable partitioning |
      | Amount | On average half a page or half a partition per process | Can be very large in total, though scattered |
      | Can the free space be used | No; it belongs to the allocated block and cannot be given to another process | Yes in total, but not as a contiguous piece, so it usually cannot satisfy a request |
      | Remedy | Use a smaller allocation unit, that is a smaller page size, at the cost of a larger page table | Compaction, which moves processes together to merge the holes; or paging, which removes the requirement of contiguity |

      Example of internal fragmentation: a process needs 18 KB and the page size is 4 KB. Five pages, that is 20 KB, must be allocated, so 2 KB of the last page is wasted and cannot be used by any other process.

      Example of external fragmentation: three free holes of 30 KB, 20 KB and 40 KB exist, a total of 90 KB free. A request for 50 KB fails, even though 90 KB is free in total, because no single hole is large enough.
8. **Find out total number of pages, when page size 4KB and address space 32 bit.** *[Sylhet Gas Field Limited (SGFL) Assistant Engineer (IT) 2023 compact it 588 (ET: BUET)]*


   Answer: Given: page size = 4 KB, address space = 32 bits.

   Step 1 - size of the address space:
   - 32-bit address means 2^32 bytes = 4,294,967,296 bytes = 4 GB

   Step 2 - express the page size as a power of two:
   - 4 KB = 4 x 1024 = 4096 bytes = 2^12

   Step 3 - number of pages:
   - Number of pages = address space / page size
   - = 2^32 / 2^12
   - = 2^(32-12)
   - = 2^20

   Step 4 - compute the value:
   - 2^20 = 1,048,576

   Final answer: there are 2^20 = 1,048,576 pages, that is about one million pages.

   Address division:
   - Offset bits = log2(4096) = 12
   - Page number bits = 32 - 12 = 20
   ```
   |<------- 20 bits ------->|<--- 12 bits --->|
   |      Page number        |     Offset      |
   ```

   General formulas worth remembering:
   - Number of pages = 2^(address bits) / 2^(offset bits) = 2^(address bits - offset bits)
   - Offset bits = log2(page size)
   - Page number bits = address bits - offset bits

   A related figure that is often asked in the same question: if each page table entry is 4 bytes, the page table for one process occupies 2^20 x 4 = 4 MB, which is why real systems use multi-level page tables or inverted page tables rather than a single flat table.
9. **(ক) Paging এবং Segmentation এর পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 609 (ET: N/A)]*


   Answer: Paging এবং Segmentation এর পার্থক্য:

   | Point | Paging | Segmentation |
      |---|---|---|
      | Division of memory | Memory is divided into fixed-size blocks called frames, and the process into equal-size pages | Memory is divided into variable-size blocks corresponding to logical units of the program |
      | Size of the block | Fixed, typically 4 KB | Variable, decided by the size of the segment |
      | Decided by | The hardware and the operating system | The programmer or the compiler |
      | Visible to the programmer | No; paging is invisible to the program | Yes; segments correspond to code, data, stack and heap |
      | Logical address | One number, split by hardware into page number and offset | Two parts: segment number and offset |
      | Mapping table | Page table, holding frame numbers | Segment table, holding base address and limit |
      | Internal fragmentation | Yes, in the last page of a process, on average half a page | No |
      | External fragmentation | No, since all frames are the same size | Yes, because free holes of different sizes appear |
      | Protection | Applied per page, which does not follow the logical structure | Applied per segment, which matches the logical structure and is therefore more natural |
      | Sharing | Possible but awkward, since a shared routine may not fill whole pages | Natural; a whole code segment can be shared by several processes |
      | Growth of a structure | Awkward | Easy; a segment can simply be given a larger limit |
      | Address translation | Physical address = frame number x page size + offset | Physical address = segment base + offset, after checking offset < limit |
      | Speed of translation | Fast, since it is a simple concatenation | Slightly slower, since an addition and a bounds check are needed |

      Combined scheme, which is what real systems use: segmentation with paging. The program is divided into logical segments, and each segment is then divided into pages. This gives the logical structure and protection of segmentation together with the absence of external fragmentation of paging. The Intel x86 architecture supports exactly this, and Linux uses it with a flat segmentation model so that in practice only paging is visible.
10. **(খ) Operating System-এর Memory hierarchy সচিত্র বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 611 (ET: N/A)]*


    Answer: Memory Hierarchy বলতে বোঝায় কম্পিউটারের বিভিন্ন ধরনের স্মৃতিকে গতি, ধারণক্ষমতা ও দামের ভিত্তিতে স্তরে স্তরে সাজানো একটি কাঠামো। সিপিইউ-এর যত কাছে, তত দ্রুত ও ব্যয়বহুল; যত দূরে, তত ধীর, সস্তা ও বড়।

    চিত্র:

    ```
                        ^  গতি বেশি, দাম বেশি, ধারণক্ষমতা কম
                        |
              +-------------------+
              |     Registers     |   < 1 ns, কয়েক বাইট
              +-------------------+
             +---------------------+
             |    Cache (L1/L2/L3) |  1-20 ns, KB থেকে MB
             +---------------------+
           +-------------------------+
           |    Main Memory (RAM)    |  50-100 ns, GB
           +-------------------------+
         +-----------------------------+
         |   Secondary Storage (SSD)   |  0.1 ms, শত GB
         +-----------------------------+
       +---------------------------------+
       |  Secondary Storage (Hard Disk)  |  5-10 ms, TB
       +---------------------------------+
     +-------------------------------------+
     |  Tertiary / Offline (Tape, Cloud)   |  সেকেন্ড থেকে মিনিট
     +-------------------------------------+
                        |
                        v  গতি কম, দাম কম, ধারণক্ষমতা বেশি
    ```

    স্তরগুলোর তুলনা:

    | স্তর | প্রযুক্তি | অ্যাক্সেস সময় | ধারণক্ষমতা | দাম (প্রতি বাইট) | অস্থিতিশীল |
    |---|---|---|---|---|---|
    | রেজিস্টার | ফ্লিপ-ফ্লপ | ১ ন্যানোসেকেন্ডের কম | কয়েকশ বাইট | সর্বোচ্চ | হ্যাঁ |
    | ক্যাশে | SRAM | ১-২০ ন্যানোসেকেন্ড | ৩২ কিলোবাইট - ৬৪ মেগাবাইট | খুব বেশি | হ্যাঁ |
    | প্রধান স্মৃতি | DRAM | ৫০-১০০ ন্যানোসেকেন্ড | ৪-৬৪ গিগাবাইট | মাঝারি | হ্যাঁ |
    | SSD | NAND ফ্ল্যাশ | ০.১ মিলিসেকেন্ড | শত গিগাবাইট | কম | না |
    | হার্ড ডিস্ক | চৌম্বকীয় | ৫-১০ মিলিসেকেন্ড | টেরাবাইট | খুব কম | না |
    | টেপ ও ক্লাউড | চৌম্বকীয় ও দূরবর্তী | সেকেন্ড-মিনিট | অসীম প্রায় | সর্বনিম্ন | না |

    এই কাঠামো কাজ করার মূলনীতি — স্থানিকতার নীতি (Principle of Locality):
    - কালিক স্থানিকতা (Temporal locality): যে তথ্য এইমাত্র ব্যবহৃত হয়েছে, তা শীঘ্রই আবার লাগার সম্ভাবনা বেশি। যেমন লুপের ভেরিয়েবল।
    - স্থানিক স্থানিকতা (Spatial locality): ব্যবহৃত তথ্যের পাশের তথ্যও শীঘ্রই লাগার সম্ভাবনা বেশি। যেমন অ্যারের পরপর উপাদান।

    এই নীতির কারণেই প্রোগ্রামের সক্রিয় ছোট অংশটুকু দ্রুত স্তরে রেখে দিলে প্রায় সবচেয়ে দ্রুত স্তরের গতি পাওয়া যায়, অথচ খরচ থাকে প্রায় সবচেয়ে সস্তা স্তরের সমান। এটিই মেমোরি হায়ারার্কির মূল সাফল্য।

    অপারেটিং সিস্টেমের ভূমিকা:
    - রেজিস্টার ব্যবস্থাপনা করে কম্পাইলার ও হার্ডওয়্যার।
    - ক্যাশে ব্যবস্থাপনা সম্পূর্ণ হার্ডওয়্যারনির্ভর, প্রোগ্রামার তা দেখতে পান না।
    - প্রধান স্মৃতি ব্যবস্থাপনা করে অপারেটিং সিস্টেমের মেমোরি ম্যানেজার — বরাদ্দ, মুক্তকরণ, পেজিং ও সুরক্ষা।
    - সহায়ক স্মৃতি ব্যবস্থাপনা করে ফাইল সিস্টেম।

    কার্যকর অ্যাক্সেস সময়ের সূত্র: Effective Access Time = হিট টাইম + (মিস রেশিও x মিস পেনাল্টি)। যেমন ক্যাশে হিট টাইম ২ ন্যানোসেকেন্ড, মিস পেনাল্টি ১০০ ন্যানোসেকেন্ড এবং হিট রেশিও ৯৫ শতাংশ হলে EAT = ২ + (০.০৫ x ১০০) = ৭ ন্যানোসেকেন্ড।
11. **(খ) Internal এবং External fragmentation এর মধ্যে পার্থক্য লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*


    Answer: Internal ও External fragmentation এর পার্থক্য:

    | Point | Internal Fragmentation | External Fragmentation |
        |---|---|---|
        | Definition | Wasted space inside an allocated block, because the block is larger than the request | Wasted space outside allocated blocks, in free holes that are individually too small to be useful |
        | Where the waste is | Within a partition or a page that has been allocated | Between allocated partitions |
        | Cause | Fixed-size allocation units | Variable-size allocation and repeated allocation and release |
        | Occurs in | Paging, and fixed partitioning | Segmentation, and dynamic or variable partitioning |
        | Amount | On average half a page or half a partition per process | Can be very large in total, though scattered |
        | Can the free space be used | No; it belongs to the allocated block and cannot be given to another process | Yes in total, but not as a contiguous piece, so it usually cannot satisfy a request |
        | Remedy | Use a smaller allocation unit, that is a smaller page size, at the cost of a larger page table | Compaction, which moves processes together to merge the holes; or paging, which removes the requirement of contiguity |

        Example of internal fragmentation: a process needs 18 KB and the page size is 4 KB. Five pages, that is 20 KB, must be allocated, so 2 KB of the last page is wasted and cannot be used by any other process.

        Example of external fragmentation: three free holes of 30 KB, 20 KB and 40 KB exist, a total of 90 KB free. A request for 50 KB fails, even though 90 KB is free in total, because no single hole is large enough.

        সমাধানের উপায়:
        - Internal fragmentation কমাতে পৃষ্ঠার আকার ছোট করা যায়, তবে তাতে page table বড় হয়ে যায়, তাই একটি ভারসাম্য রাখতে হয়। ৪ কিলোবাইট আকারটি এই ভারসাম্যেরই ফল।
        - External fragmentation দূর করতে compaction করা হয়, অর্থাৎ সব প্রসেসকে সরিয়ে একদিকে জড়ো করে ফাঁকা জায়গাগুলো এক করা হয়। কিন্তু এটি ব্যয়বহুল এবং চলাকালীন সব প্রসেস থামিয়ে দিতে হয়।
        - সবচেয়ে কার্যকর সমাধান paging, কারণ এতে প্রসেসকে মেমোরিতে ধারাবাহিকভাবে রাখার প্রয়োজন হয় না; ফলে external fragmentation সম্পূর্ণ দূর হয়ে যায়।
12. **(a) What is demand paging?** *[BITAC Assistant Maintenance Engineer (ICT) 2021 compact it 821 (ET: BUET)]*


    Answer: Demand paging is the memory management technique in which a page is brought from secondary storage into main memory only when it is actually referenced, rather than loading the whole process at the start. It is the practical implementation of virtual memory.

    How it works:
    - When a process starts, only a small part of it, or nothing at all, is loaded. This second form is called pure demand paging.
    - Every entry in the page table carries a valid-invalid bit. Valid means the page is present in a frame of physical memory; invalid means it is either not part of the address space or is currently on disk.
    - When the CPU generates an address whose page is marked invalid, the hardware raises a trap called a page fault.

    Steps in servicing a page fault:
    1. The memory reference is checked against the page table, and the entry is found to be invalid.
    2. A trap to the operating system occurs, and the state of the process is saved.
    3. The operating system determines whether the reference is legal. If the address is outside the process's address space, the process is terminated; otherwise the page must simply be fetched.
    4. A free frame is located. If none is free, a victim page is selected by a page replacement algorithm and, if it has been modified, written back to disk.
    5. A disk read is scheduled to bring the required page into the frame. The process is blocked and the CPU is given to another process.
    6. When the transfer completes, an interrupt occurs, the page table is updated to mark the page valid and to record the frame number, and the TLB entry is loaded.
    7. The process is moved back to the ready queue, and the instruction that caused the fault is restarted.

    Advantages:
    - A process larger than physical memory can run, because only the pages actually used need be resident.
    - The degree of multiprogramming rises, since each process occupies less memory, which raises CPU utilisation.
    - Program start-up is much faster, because only the first few pages are loaded.
    - Less input and output is performed, since pages that are never referenced are never read.
    - Memory is used efficiently, as no space is wasted on code paths that the run never takes, such as error handlers.

    Disadvantages:
    - Every page fault costs a disk access, which is several milliseconds and therefore hundreds of thousands of CPU cycles.
    - Address translation needs hardware support and a TLB.
    - If too many processes are resident, the system may spend nearly all its time paging rather than executing, which is called thrashing.

    Effective access time:

    EAT = (1 - p) x memory access time + p x page fault service time

    where p is the page fault rate. With a memory access time of 200 nanoseconds and a page fault service time of 8 milliseconds:
    - If p = 0.001, EAT = 0.999 x 200 + 0.001 x 8,000,000 = 199.8 + 8000 = 8199.8 ns, which is about 40 times slower than memory alone.
    - To keep the slowdown below 10 per cent, p must be less than about 0.0000025, that is fewer than one fault in 400,000 references.
    This calculation shows why the page fault rate must be kept extremely low, and it is the justification for careful page replacement algorithms and for the working set model.

    Related terms: lazy swapper (a pager that never brings in a page until it is needed), page fault, page replacement, thrashing, the working set model, and prepaging, in which several pages likely to be needed are fetched together to reduce the number of faults.
13. **In the given example, let us assume the jobs and the memory requirements as the following: Job1=90k, Job2=20k, Job3=50k, Job4=200k. Let the free pace memory allocation blocks are: Block1=50k, Block2=100k, Block3=90k, Block4=200k, Block5=50k.** *[Janata Bank Assistant System Administrator 2021 compact it 939-940 (ET: N/A)]*


    Answer: Given:

    | Job | Size |
    |---|---|
    | Job1 | 90 K |
    | Job2 | 20 K |
    | Job3 | 50 K |
    | Job4 | 200 K |

    | Block | Size |
    |---|---|
    | Block1 | 50 K |
    | Block2 | 100 K |
    | Block3 | 90 K |
    | Block4 | 200 K |
    | Block5 | 50 K |

    Total memory available = 50 + 100 + 90 + 200 + 50 = 490 K
    Total memory required = 90 + 20 + 50 + 200 = 360 K

    First Fit: allocate each job to the first block, scanning from the beginning, that is large enough.

    | Job | Size | Block allocated | Block size | Internal fragmentation left |
    |---|---|---|---|---|
    | Job1 | 90 K | Block2 | 100 K | 10 K |
    | Job2 | 20 K | Block1 | 50 K | 30 K |
    | Job3 | 50 K | Block3 | 90 K (now 90 K) | 40 K |
    | Job4 | 200 K | Block4 | 200 K | 0 K |

    Working: Job1 (90 K) does not fit in Block1 (50 K) but fits in Block2 (100 K). Job2 (20 K) fits in Block1 (50 K), the first block scanned. Job3 (50 K) does not fit in the 30 K left of Block1 nor in the 10 K left of Block2, but fits in Block3 (90 K). Job4 (200 K) fits only in Block4.

    All four jobs are allocated. Block5 (50 K) remains completely free. Total internal fragmentation = 10 + 30 + 40 + 0 = 80 K, and 50 K remains as an unused whole block.

    Best Fit: allocate each job to the smallest block that is large enough.

    | Job | Size | Block allocated | Block size | Left over |
    |---|---|---|---|---|
    | Job1 | 90 K | Block3 | 90 K | 0 K |
    | Job2 | 20 K | Block1 | 50 K | 30 K |
    | Job3 | 50 K | Block5 | 50 K | 0 K |
    | Job4 | 200 K | Block4 | 200 K | 0 K |

    Working: for Job1 the candidates are Block2 (100 K), Block3 (90 K) and Block4 (200 K); the smallest adequate one is Block3, and it fits exactly. For Job2 the smallest adequate block is Block1 or Block5, both 50 K; taking Block1 leaves 30 K. Job3 (50 K) then fits exactly into Block5. Job4 takes Block4 exactly.

    All four jobs are allocated. Block2 (100 K) remains entirely free, and only 30 K is wasted inside Block1. Total waste = 30 K, which is much better than First Fit.

    Worst Fit: allocate each job to the largest available block.

    | Job | Size | Block allocated | Block size before | Left over |
    |---|---|---|---|---|
    | Job1 | 90 K | Block4 | 200 K | 110 K |
    | Job2 | 20 K | Block4 (remaining) | 110 K | 90 K |
    | Job3 | 50 K | Block2 | 100 K | 50 K |
    | Job4 | 200 K | Not allocated | | |

    Working: Job1 takes the largest block, Block4 (200 K), leaving 110 K. Job2 takes the largest remaining, which is that same 110 K remnant, leaving 90 K. Job3 takes Block2 (100 K), leaving 50 K. Job4 (200 K) now finds no block of 200 K anywhere, although 50 + 90 + 50 + 50 = 240 K is free in total. Job4 cannot be allocated.

    Comparison:

    | Strategy | Jobs allocated | Comment |
    |---|---|---|
    | First Fit | All 4 | Fastest to compute; scans only until the first fit is found |
    | Best Fit | All 4 | Least waste; three blocks fitted exactly |
    | Worst Fit | 3 of 4 | Job4 fails; the largest block was broken up early |

    Conclusion: for this data Best Fit is the most effective, since it leaves the largest usable block, Block2 of 100 K, intact and wastes only 30 K. Worst Fit performs badly because it destroyed the only 200 K block before the 200 K job arrived. First Fit succeeds and is the fastest to compute, which is why it is the strategy most commonly used in practice.

    General observations:
    - First Fit is fast and performs well in practice, but it leaves small unusable fragments near the start of memory.
    - Best Fit produces the smallest leftover pieces, but those pieces are often too small to be useful, so external fragmentation still accumulates, and it must scan the whole list.
    - Worst Fit is intended to leave large usable remnants, but in practice it performs worst of the three, as this example shows.
    - Job4's failure is an example of external fragmentation: 240 K is free in total but no single hole is large enough. The remedy is compaction, or paging, which removes the need for contiguous allocation altogether.

## Process Management & Process States (10)

1. **(b) What is process? Describe different states of a process.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*


   Answer: A process is a program in execution. A program is a passive entity, a file of instructions stored on disk; a process is the active entity, with a program counter, registers, a stack, a data section and an entry in the process table. One program can give rise to many processes, as when several copies of a browser run at once.

   A process holds:
   - The program code, called the text section
   - The program counter and the contents of the CPU registers
   - The stack, holding temporary data such as function parameters, return addresses and local variables
   - The data section, holding global variables
   - The heap, memory allocated dynamically at run time

   The five states of a process:

   - New: the process has just been created. It has not started running yet, but its Process Control Block (PCB) is ready. The program still sits in secondary memory.

   - Ready: the process is loaded into main memory and is ready to run. It waits in the ready queue until the CPU becomes free. It has everything it needs except the processor itself.

   - Running: the CPU is currently executing the instructions of this process. On a single processor machine only one process can be in this state at a time.

   - Blocked, also called Waiting: the process cannot go on, because it is waiting for an event, such as an I/O operation finishing, user input arriving, or a locked resource being released. It is not competing for the CPU, so giving it the processor would be useless.

   - Terminated: the process has finished its execution, or it has been stopped. The OS deletes its PCB and frees every resource it had. The PCB may stay for a short while, so the parent can read the exit status. Such a process is called a zombie in Unix.

   Two more states in systems that use swapping:
   - Suspend Ready: a ready process that was moved to secondary storage because memory was short. It comes back to Ready when it is loaded into main memory again.
   - Suspend Blocked: a waiting process that was swapped out to disk.

   State transitions and what causes each:

   | Transition | What causes it |
   |---|---|
   | New → Ready | Resources are allocated and the process is loaded into main memory |
   | Ready → Running | The scheduler gives the CPU to this process |
   | Running → Blocked | The process waits for I/O, for input, or for a system resource |
   | Blocked → Ready | The event finishes, or the resource becomes free |
   | Running → Ready | The OS preempts the process, often because a higher priority task arrived |
   | Running → Terminated | The process finishes, or it is forcibly stopped |
   | Blocked → Terminated | The waiting process is aborted or killed |

   State transition diagram:

   ```mermaid
   stateDiagram-v2
     [*] --> New
     New --> Ready : admitted
     Ready --> Running : scheduler dispatch
     Running --> Ready : interrupt, quantum expired
     Running --> Waiting : I/O or event wait
     Waiting --> Ready : I/O or event completion
     Running --> Terminated : exit
     Terminated --> [*]
   ```

   In plain text:
   ```
                    admitted            dispatch
      New  ------------------> Ready -------------> Running
                                ^   \                  |  \
                                |    \  interrupt      |   \  exit
                                |     +----------------+    +------> Terminated
                                |                           |
                                |    I/O completion         |  I/O request
                                +---------- Waiting <-------+
   ```

   Explanation of each transition:
   - New to Ready (admitted): the long-term scheduler admits the process and allocates memory for it.
   - Ready to Running (dispatch): the short-term scheduler selects the process and the dispatcher gives it the CPU.
   - Running to Ready (interrupt): the time quantum expires, or a higher-priority process arrives and preempts it. The process is still able to run; it has only lost its turn.
   - Running to Waiting (I/O or event wait): the process issues a request that cannot be satisfied immediately, so it voluntarily gives up the CPU.
   - Waiting to Ready (completion): the awaited event occurs, and the process becomes eligible for the CPU again. Note that it goes to Ready, not directly to Running, because the CPU may be busy.
   - Running to Terminated (exit): the process finishes or is killed.

   Two transitions that can never occur, and are worth stating because they are frequently asked:
   - Ready to Waiting is impossible: a process cannot begin waiting for an event it has not yet requested, and it cannot request anything without running.
   - Waiting to Running is impossible: after its event completes, a process must join the ready queue and be selected by the scheduler like any other.
2. **(c) Define context switch with proper example.** *[BPSC (Ministry of Power, Energy & Mineral Resources) Assistant Director (ICT) (CS/CSE) 29.05.2025 compact it 1352 (ET: N/A)]*


   Answer: A context switch is the operation by which the CPU is transferred from one process to another. The state of the currently running process is saved so that it can be resumed later, and the saved state of the incoming process is restored.

   What is saved and restored, that is what constitutes the context:
   - The program counter, so that execution resumes at the right instruction
   - All CPU registers, including general-purpose registers, the stack pointer and the status or flag register
   - Memory management information: page table pointers or base and limit registers
   - The process state and scheduling information
   - Open file and input-output status

   All of this is written into the PCB of the outgoing process and read from the PCB of the incoming one.

   Steps in a context switch:
   1. An interrupt or a system call causes the CPU to enter kernel mode.
   2. The context of the running process P1 is saved into PCB1.
   3. The scheduler selects the next process P2 from the ready queue.
   4. The context of P2 is loaded from PCB2 into the CPU registers.
   5. The memory management unit is reloaded with P2's page table, and the TLB is flushed or tagged.
   6. Execution resumes in P2 at the instruction its program counter indicates.

   When it occurs:
   - The time quantum of the running process expires (a timer interrupt).
   - The running process makes an input-output request and blocks.
   - A higher-priority process becomes ready and preempts the running one.
   - The running process terminates or makes a system call that blocks.
   - A hardware interrupt occurs that requires the kernel to run.

   Example with two processes:
   ```
   Time    CPU is running        Action
   0-10    P1                    P1 executes
   10      -                     interrupt; save P1's context into PCB1;
                                 load P2's context from PCB2   (context switch)
   10-25   P2                    P2 executes
   25      -                     P2 requests input; save P2 into PCB2;
                                 load P1 from PCB1             (context switch)
   25-40   P1                    P1 resumes exactly where it stopped at time 10
   ```
   When P1 resumes it finds its program counter, its registers and its stack exactly as they were, so it has no way of knowing that fifteen milliseconds of another process ran in between.

   Cost of a context switch:
   - It is pure overhead: during the switch no useful work is done by any process.
   - Typical cost is 1 to 100 microseconds, depending on the hardware and the number of registers.
   - The indirect cost is often larger than the direct one: the cache and the TLB are filled with the outgoing process's data, so the incoming process suffers a burst of misses. This is called cache pollution.
   - The cost is the main reason why a very small scheduling quantum is harmful, and why threads, which share an address space and therefore need no page table reload, are cheaper to switch between than processes.

   Comparison of process and thread switching: switching between two threads of the same process is much cheaper, because the address space, the page table and the open files are shared and need not be changed; only the registers and the stack pointer are swapped.
3. **(খ) Process কী? বিভিন্ন ধরনের Process state এর কাজ বর্ণনা করুন।** *[18th NTRCA - College Lecturer (ICT) 13.07.2024 compact it 414 (ET: N/A)]*


   Answer: প্রসেস (Process) হলো চলমান অবস্থায় থাকা একটি প্রোগ্রাম। প্রোগ্রাম একটি নিষ্ক্রিয় সত্তা, অর্থাৎ ডিস্কে সংরক্ষিত নির্দেশের একটি ফাইল; আর প্রসেস হলো সক্রিয় সত্তা, যার নিজস্ব প্রোগ্রাম কাউন্টার, রেজিস্টার, স্ট্যাক, ডেটা অংশ এবং প্রসেস টেবিলে একটি এন্ট্রি থাকে। একই প্রোগ্রাম থেকে একাধিক প্রসেস তৈরি হতে পারে, যেমন একই ব্রাউজারের কয়েকটি কপি একসঙ্গে চালানো।

   একটি প্রসেসের অংশসমূহ: টেক্সট অংশ (প্রোগ্রাম কোড), প্রোগ্রাম কাউন্টার ও রেজিস্টার, স্ট্যাক (ফাংশনের প্যারামিটার, রিটার্ন ঠিকানা ও স্থানীয় ভেরিয়েবল), ডেটা অংশ (গ্লোবাল ভেরিয়েবল) এবং হিপ (চলাকালীন বরাদ্দকৃত মেমোরি)।

   প্রসেসের বিভিন্ন অবস্থা ও তাদের কাজ:

   - New (নতুন): প্রসেসটি তৈরি হচ্ছে। অপারেটিং সিস্টেম এর জন্য একটি Process Control Block তৈরি করেছে, কিন্তু এখনো একে ready queue তে যুক্ত করা হয়নি। এই ধাপে মেমোরি বরাদ্দ ও প্রয়োজনীয় সম্পদের ব্যবস্থা করা হয়।

   - Ready (প্রস্তুত): প্রসেসটি প্রধান মেমোরিতে লোড হয়ে গেছে এবং সিপিইউ পাওয়ার অপেক্ষায় আছে। চালানোর জন্য প্রয়োজনীয় সবকিছু আছে, কেবল প্রসেসরটি নেই। সব ready প্রসেস ready queue তে থাকে। এর কাজ হলো সিপিইউ মুক্ত হওয়া মাত্র কাজ শুরু করতে প্রস্তুত থাকা।

   - Running (চলমান): প্রসেসটি বর্তমানে সিপিইউতে চলছে, অর্থাৎ এর নির্দেশগুলো সম্পাদিত হচ্ছে। একক কোরের মেশিনে একই সময়ে কেবল একটি প্রসেসই এই অবস্থায় থাকতে পারে।

   - Waiting বা Blocked (অপেক্ষমাণ): প্রসেসটি কোনো ঘটনার জন্য অপেক্ষা করছে, যেমন ইনপুট-আউটপুট শেষ হওয়া, কোনো সংকেত আসা, বা কোনো রিসোর্স মুক্ত হওয়া। এই অবস্থায় সিপিইউ দিলেও প্রসেসটি কাজ করতে পারবে না, তাই একে সিপিইউ দেওয়া হয় না। এর কাজ হলো ধীরগতির ইনপুট-আউটপুট চলাকালে সিপিইউ ছেড়ে দেওয়া, যাতে অন্য প্রসেস চলতে পারে।

   - Terminated (সমাপ্ত): প্রসেসের কাজ শেষ হয়েছে বা একে বন্ধ করে দেওয়া হয়েছে। এর সম্পদ ফিরিয়ে নেওয়া হয়, তবে প্যারেন্ট প্রসেস প্রস্থান-অবস্থা পড়ার আগ পর্যন্ত PCB টি কিছুক্ষণ থাকতে পারে। ইউনিক্সে এই অবস্থাকে zombie বলা হয়।

   Swapping যুক্ত সিস্টেমে আরও দুটি অবস্থা:
   - Suspended-Ready: প্রস্তুত, কিন্তু মেমোরি থেকে সরিয়ে ডিস্কে রাখা হয়েছে।
   - Suspended-Blocked: অপেক্ষমাণ এবং ডিস্কে রাখা হয়েছে।

   অবস্থা পরিবর্তনের চিত্র:

   ```mermaid
   stateDiagram-v2
     [*] --> New
     New --> Ready : admitted
     Ready --> Running : dispatch
     Running --> Ready : interrupt
     Running --> Waiting : I/O request
     Waiting --> Ready : I/O completion
     Running --> Terminated : exit
     Terminated --> [*]
   ```

   পরিবর্তনগুলোর ব্যাখ্যা:
   - New থেকে Ready: long-term scheduler প্রসেসটিকে গ্রহণ করে মেমোরি বরাদ্দ দেয়।
   - Ready থেকে Running: short-term scheduler প্রসেসটি নির্বাচন করে এবং dispatcher একে সিপিইউ দেয়।
   - Running থেকে Ready: সময়ের কোটা শেষ হলে বা উচ্চতর অগ্রাধিকারের প্রসেস এলে বাধ্য হয়ে সিপিইউ ছাড়তে হয়।
   - Running থেকে Waiting: প্রসেসটি স্বেচ্ছায় সিপিইউ ছেড়ে দেয়, কারণ এটি এমন কিছুর জন্য অপেক্ষা করছে যা তাৎক্ষণিকভাবে পাওয়া যাবে না।
   - Waiting থেকে Ready: প্রত্যাশিত ঘটনাটি ঘটেছে, তাই প্রসেসটি আবার সিপিইউ পাওয়ার যোগ্য হয়েছে। লক্ষণীয়, এটি সরাসরি Running এ যায় না, কারণ সিপিইউ তখন অন্য প্রসেস ব্যবহার করছে থাকতে পারে।
   - Running থেকে Terminated: কাজ শেষ হলে বা বন্ধ করে দিলে।

   যে দুটি পরিবর্তন কখনোই সম্ভব নয়: Ready থেকে সরাসরি Waiting (কারণ না চললে কোনো অনুরোধই করা যায় না) এবং Waiting থেকে সরাসরি Running (কারণ ঘটনা ঘটার পরও scheduler এর নির্বাচনের অপেক্ষা করতে হয়)।
4. **Explain the process state.** *[EGCB Sub-Divisional Engineer (ICT) 28.01.2023 compact it 563 (ET: BUET)]*


   Answer: A process is a program in execution. A program is a passive entity, a file of instructions stored on disk; a process is the active entity, with a program counter, registers, a stack, a data section and an entry in the process table. One program can give rise to many processes, as when several copies of a browser run at once.

   A process holds:
   - The program code, called the text section
   - The program counter and the contents of the CPU registers
   - The stack, holding temporary data such as function parameters, return addresses and local variables
   - The data section, holding global variables
   - The heap, memory allocated dynamically at run time

   The five states of a process:

   - New: the process has just been created. It has not started running yet, but its Process Control Block (PCB) is ready. The program still sits in secondary memory.

   - Ready: the process is loaded into main memory and is ready to run. It waits in the ready queue until the CPU becomes free. It has everything it needs except the processor itself.

   - Running: the CPU is currently executing the instructions of this process. On a single processor machine only one process can be in this state at a time.

   - Blocked, also called Waiting: the process cannot go on, because it is waiting for an event, such as an I/O operation finishing, user input arriving, or a locked resource being released. It is not competing for the CPU, so giving it the processor would be useless.

   - Terminated: the process has finished its execution, or it has been stopped. The OS deletes its PCB and frees every resource it had. The PCB may stay for a short while, so the parent can read the exit status. Such a process is called a zombie in Unix.

   Two more states in systems that use swapping:
   - Suspend Ready: a ready process that was moved to secondary storage because memory was short. It comes back to Ready when it is loaded into main memory again.
   - Suspend Blocked: a waiting process that was swapped out to disk.

   State transitions and what causes each:

   | Transition | What causes it |
   |---|---|
   | New → Ready | Resources are allocated and the process is loaded into main memory |
   | Ready → Running | The scheduler gives the CPU to this process |
   | Running → Blocked | The process waits for I/O, for input, or for a system resource |
   | Blocked → Ready | The event finishes, or the resource becomes free |
   | Running → Ready | The OS preempts the process, often because a higher priority task arrived |
   | Running → Terminated | The process finishes, or it is forcibly stopped |
   | Blocked → Terminated | The waiting process is aborted or killed |

   State transition diagram:

   ```mermaid
   stateDiagram-v2
     [*] --> New
     New --> Ready : admitted
     Ready --> Running : scheduler dispatch
     Running --> Ready : interrupt, quantum expired
     Running --> Waiting : I/O or event wait
     Waiting --> Ready : I/O or event completion
     Running --> Terminated : exit
     Terminated --> [*]
   ```

   In plain text:
   ```
                    admitted            dispatch
      New  ------------------> Ready -------------> Running
                                ^   \                  |  \
                                |    \  interrupt      |   \  exit
                                |     +----------------+    +------> Terminated
                                |                           |
                                |    I/O completion         |  I/O request
                                +---------- Waiting <-------+
   ```

   Explanation of each transition:
   - New to Ready (admitted): the long-term scheduler admits the process and allocates memory for it.
   - Ready to Running (dispatch): the short-term scheduler selects the process and the dispatcher gives it the CPU.
   - Running to Ready (interrupt): the time quantum expires, or a higher-priority process arrives and preempts it. The process is still able to run; it has only lost its turn.
   - Running to Waiting (I/O or event wait): the process issues a request that cannot be satisfied immediately, so it voluntarily gives up the CPU.
   - Waiting to Ready (completion): the awaited event occurs, and the process becomes eligible for the CPU again. Note that it goes to Ready, not directly to Running, because the CPU may be busy.
   - Running to Terminated (exit): the process finishes or is killed.

   Two transitions that can never occur, and are worth stating because they are frequently asked:
   - Ready to Waiting is impossible: a process cannot begin waiting for an event it has not yet requested, and it cannot request anything without running.
   - Waiting to Running is impossible: after its event completes, a process must join the ready queue and be selected by the scheduler like any other.
5. **(ক) Process কী? একটি Process এর বিভিন্ন ধাপগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 623 (ET: N/A)]*


   Answer: প্রসেস (Process) হলো চলমান অবস্থায় থাকা একটি প্রোগ্রাম। প্রোগ্রাম নিষ্ক্রিয় (passive), অর্থাৎ ডিস্কে রাখা নির্দেশের একটি ফাইল; প্রসেস সক্রিয় (active), যার নিজস্ব প্রোগ্রাম কাউন্টার, রেজিস্টার, স্ট্যাক ও মেমোরি বরাদ্দ থাকে।

   একটি প্রসেসের জীবনচক্রের বিভিন্ন ধাপ:

   - ধাপ ১ — New (সৃষ্টি): প্রসেসটি তৈরি হচ্ছে। ইউনিক্সে fork() সিস্টেম কল দিয়ে নতুন প্রসেস তৈরি হয়। অপারেটিং সিস্টেম একটি PCB তৈরি করে, একটি PID বরাদ্দ দেয় এবং মেমোরি বরাদ্দের ব্যবস্থা করে।

   - ধাপ ২ — Ready (প্রস্তুত): প্রসেসটি মেমোরিতে লোড হয়ে ready queue তে অপেক্ষা করছে। এর চলার জন্য প্রয়োজনীয় সবকিছু আছে, কেবল সিপিইউ নেই।

   - ধাপ ৩ — Running (চলমান): scheduler প্রসেসটিকে নির্বাচন করেছে এবং dispatcher একে সিপিইউ দিয়েছে। এখন এর নির্দেশগুলো সম্পাদিত হচ্ছে।

   - ধাপ ৪ — Waiting বা Blocked (অপেক্ষমাণ): প্রসেসটি কোনো ইনপুট-আউটপুট বা অন্য ঘটনার জন্য অপেক্ষা করছে। এই সময়ে সিপিইউ অন্য প্রসেসকে দেওয়া হয়।

   - ধাপ ৫ — Terminated (সমাপ্ত): কাজ শেষ, বা ত্রুটির কারণে বা অন্য প্রসেসের নির্দেশে বন্ধ। সম্পদ ফিরিয়ে নেওয়া হয় এবং প্যারেন্ট প্রসেস exit status পড়ার পর PCB মুছে ফেলা হয়।

   ধাপগুলোর মধ্যে চলাচল:

   ```
                    admitted            dispatch
      New  ------------------> Ready -------------> Running
                                ^   \                  |  \
                                |    \  interrupt      |   \  exit
                                |     +----------------+    +------> Terminated
                                |                           |
                                |    I/O completion         |  I/O request
                                +---------- Waiting <-------+
   ```

   Swapping যুক্ত সিস্টেমে অতিরিক্ত দুটি ধাপ: Suspended-Ready ও Suspended-Blocked, অর্থাৎ প্রসেসটিকে মেমোরি থেকে সরিয়ে ডিস্কে রেখে দেওয়া হয়েছে।

   ইউনিক্স সিস্টেম কলের সঙ্গে সম্পর্ক:
   - fork() — নতুন প্রসেস তৈরি করে (New)
   - exec() — নতুন প্রোগ্রাম চালু করে প্রসেসের ছবি বদলে দেয়
   - wait() — প্যারেন্ট প্রসেস সন্তানের শেষ হওয়ার অপেক্ষা করে (Waiting)
   - exit() — প্রসেস শেষ করে (Terminated)
   - kill() — অন্য প্রসেসকে সংকেত পাঠিয়ে বন্ধ করে
6. **অথবা, (ক) Process Control Block (PCB) কী? এটি একটি Process সংক্রান্ত যে যে তথ্য রাখে সেগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*


   Answer: Process Control Block (PCB) হলো সেই ডেটা স্ট্রাকচার, যেখানে অপারেটিং সিস্টেম একটি নির্দিষ্ট প্রসেস সম্পর্কে সব তথ্য সংরক্ষণ করে। প্রতিটি প্রসেসের জন্য ঠিক একটি PCB থাকে; প্রসেস তৈরির সময় এটি তৈরি হয় এবং প্রসেস শেষ হলে মুছে ফেলা হয়। সব PCB মিলে গঠিত হয় process table। একে task control block ও বলা হয়।

   PCB তে যেসব তথ্য রাখা হয়:

   - প্রসেস শনাক্তকরণ: প্রসেস আইডি (PID), প্যারেন্ট প্রসেস আইডি (PPID), মালিকের ইউজার আইডি ও গ্রুপ আইডি।

   - প্রসেসের অবস্থা (Process State): new, ready, running, waiting নাকি terminated।

   - প্রোগ্রাম কাউন্টার: পরবর্তী যে নির্দেশটি চালানো হবে তার ঠিকানা।

   - সিপিইউ রেজিস্টারসমূহ: অ্যাকিউমুলেটর, ইনডেক্স রেজিস্টার, স্ট্যাক পয়েন্টার ও সাধারণ উদ্দেশ্যের রেজিস্টারের বিষয়বস্তু। প্রোগ্রাম কাউন্টারসহ এগুলোকেই বলা হয় প্রসেসের context, যা context switch এর সময় সংরক্ষণ ও পুনরুদ্ধার করা হয়।

   - সিপিইউ শিডিউলিং তথ্য: অগ্রাধিকার (priority), শিডিউলিং কিউয়ের পয়েন্টার, ব্যবহৃত সময়ের কোটা এবং মোট ব্যবহৃত সিপিইউ সময়।

   - মেমোরি ব্যবস্থাপনা তথ্য: base ও limit রেজিস্টারের মান, অথবা page table ও segment table এর পয়েন্টার, যা নির্ধারণ করে প্রসেসটি কোন মেমোরি ব্যবহার করতে পারবে।

   - হিসাব সংক্রান্ত তথ্য (Accounting): ব্যবহৃত সিপিইউ সময় ও প্রকৃত সময়, সময়সীমা, অ্যাকাউন্ট নম্বর ও প্রসেস নম্বর।

   - ইনপুট-আউটপুট অবস্থার তথ্য: খোলা ফাইলের তালিকা, ফাইল ডেসক্রিপ্টর টেবিল, বরাদ্দকৃত যন্ত্রের তালিকা ও অসমাপ্ত অনুরোধ।

   - পয়েন্টারসমূহ: প্যারেন্ট প্রসেস, সন্তান প্রসেস এবং ready বা waiting কিউয়ে এই PCB টির অবস্থান নির্দেশক লিংক।

   - সংকেত (signal) ব্যবস্থাপনার তথ্য ও প্রসেসের exit status।

   কেবল চারটি চাইলে যেগুলো অবশ্যই লিখতে হবে:
   - Process ID
   - Process State
   - Program Counter
   - CPU Registers

   PCB কেন গুরুত্বপূর্ণ: PCB ই multiprogramming সম্ভব করে তোলে। যখন কোনো প্রসেসকে সিপিইউ থেকে সরানো হয়, তখন তার সম্পূর্ণ অবস্থা PCB তে লিখে রাখা হয়; পরে আবার সিপিইউ দিলে PCB থেকে সেই অবস্থা ফিরিয়ে এনে প্রসেসটি ঠিক যেখানে থেমেছিল সেখান থেকেই চলতে থাকে, এবং সে বুঝতেও পারে না যে মাঝখানে থেমে ছিল। PCB না থাকলে কোনো প্রসেস থামিয়ে আবার চালু করা যেত না, অর্থাৎ multitasking সম্ভব হতো না।
7. **Write down the name of four information stored in PCB (Process Control Block).** *[RPGCL Assistant Manager (ICT) 2022 compact it 653 (ET: BUET)]*


   Answer: The Process Control Block (PCB), also called the task control block, is the data structure in which the operating system keeps all the information about a single process. There is exactly one PCB per process, and it is created when the process is created and destroyed when the process terminates. The collection of all PCBs forms the process table.

   Information stored in a PCB:

   - Process identification:
     - Process ID (PID), a unique number
     - Parent process ID (PPID)
     - User ID and group ID of the owner

   - Process state: new, ready, running, waiting or terminated.

   - Program counter: the address of the next instruction to execute.

   - CPU registers: the contents of the accumulator, index registers, stack pointer and general-purpose registers. These, together with the program counter, form the context that must be saved and restored on a context switch.

   - CPU scheduling information: the priority, pointers to the scheduling queues, the time quantum used, accumulated CPU time and any other parameters the scheduling algorithm needs.

   - Memory management information: the base and limit registers, or the page table or segment table pointers, defining the memory the process may access.

   - Accounting information: the amount of CPU time and real time used, time limits, account numbers, job or process numbers.

   - Input and output status information: the list of open files, the file descriptor table, the input and output devices allocated to the process, and pending requests.

   - Pointers: to the parent, to the children, and the link that places the PCB in a ready or waiting queue.

   - Signal handling information and the process's exit status.

   Four items that are always required, if only four are asked for:
   - Process ID
   - Process state
   - Program counter
   - CPU registers

   Why the PCB matters: it is what makes multiprogramming possible. When a process is taken off the CPU, its entire execution context is written into its PCB; when it is given the CPU again, the context is restored from the PCB and the process resumes exactly where it stopped, unaware that it was ever interrupted. Without the PCB there would be no way to suspend and resume a process, and therefore no multitasking.
8. **Operating System এর Process state diagram অঙ্কন করুন?** *[DESCO Sub-Assistant Engineer (CSE) 16.09.2022 compact it 698 (ET: DPI)]*


   Answer: A process is a program in execution. A program is a passive entity, a file of instructions stored on disk; a process is the active entity, with a program counter, registers, a stack, a data section and an entry in the process table. One program can give rise to many processes, as when several copies of a browser run at once.

   A process holds:
   - The program code, called the text section
   - The program counter and the contents of the CPU registers
   - The stack, holding temporary data such as function parameters, return addresses and local variables
   - The data section, holding global variables
   - The heap, memory allocated dynamically at run time

   The five states of a process:

   - New: the process has just been created. It has not started running yet, but its Process Control Block (PCB) is ready. The program still sits in secondary memory.

   - Ready: the process is loaded into main memory and is ready to run. It waits in the ready queue until the CPU becomes free. It has everything it needs except the processor itself.

   - Running: the CPU is currently executing the instructions of this process. On a single processor machine only one process can be in this state at a time.

   - Blocked, also called Waiting: the process cannot go on, because it is waiting for an event, such as an I/O operation finishing, user input arriving, or a locked resource being released. It is not competing for the CPU, so giving it the processor would be useless.

   - Terminated: the process has finished its execution, or it has been stopped. The OS deletes its PCB and frees every resource it had. The PCB may stay for a short while, so the parent can read the exit status. Such a process is called a zombie in Unix.

   Two more states in systems that use swapping:
   - Suspend Ready: a ready process that was moved to secondary storage because memory was short. It comes back to Ready when it is loaded into main memory again.
   - Suspend Blocked: a waiting process that was swapped out to disk.

   State transitions and what causes each:

   | Transition | What causes it |
   |---|---|
   | New → Ready | Resources are allocated and the process is loaded into main memory |
   | Ready → Running | The scheduler gives the CPU to this process |
   | Running → Blocked | The process waits for I/O, for input, or for a system resource |
   | Blocked → Ready | The event finishes, or the resource becomes free |
   | Running → Ready | The OS preempts the process, often because a higher priority task arrived |
   | Running → Terminated | The process finishes, or it is forcibly stopped |
   | Blocked → Terminated | The waiting process is aborted or killed |

   State transition diagram:

   ```mermaid
   stateDiagram-v2
     [*] --> New
     New --> Ready : admitted
     Ready --> Running : scheduler dispatch
     Running --> Ready : interrupt, quantum expired
     Running --> Waiting : I/O or event wait
     Waiting --> Ready : I/O or event completion
     Running --> Terminated : exit
     Terminated --> [*]
   ```

   In plain text:
   ```
                    admitted            dispatch
      New  ------------------> Ready -------------> Running
                                ^   \                  |  \
                                |    \  interrupt      |   \  exit
                                |     +----------------+    +------> Terminated
                                |                           |
                                |    I/O completion         |  I/O request
                                +---------- Waiting <-------+
   ```

   Explanation of each transition:
   - New to Ready (admitted): the long-term scheduler admits the process and allocates memory for it.
   - Ready to Running (dispatch): the short-term scheduler selects the process and the dispatcher gives it the CPU.
   - Running to Ready (interrupt): the time quantum expires, or a higher-priority process arrives and preempts it. The process is still able to run; it has only lost its turn.
   - Running to Waiting (I/O or event wait): the process issues a request that cannot be satisfied immediately, so it voluntarily gives up the CPU.
   - Waiting to Ready (completion): the awaited event occurs, and the process becomes eligible for the CPU again. Note that it goes to Ready, not directly to Running, because the CPU may be busy.
   - Running to Terminated (exit): the process finishes or is killed.

   Two transitions that can never occur, and are worth stating because they are frequently asked:
   - Ready to Waiting is impossible: a process cannot begin waiting for an event it has not yet requested, and it cannot request anything without running.
   - Waiting to Running is impossible: after its event completes, a process must join the ready queue and be selected by the scheduler like any other.
9. **(i) Operating System এর Process State Transition Diagram আঁকুন ও ব্যাখ্যা করুন।** *[BPSC Assistant Programmer (Ministry of Commerce) 2021 compact it 786 (ET: N/A)]*


   Answer: A process is a program in execution. A program is a passive entity, a file of instructions stored on disk; a process is the active entity, with a program counter, registers, a stack, a data section and an entry in the process table. One program can give rise to many processes, as when several copies of a browser run at once.

   A process holds:
   - The program code, called the text section
   - The program counter and the contents of the CPU registers
   - The stack, holding temporary data such as function parameters, return addresses and local variables
   - The data section, holding global variables
   - The heap, memory allocated dynamically at run time

   The five states of a process:

   - New: the process has just been created. It has not started running yet, but its Process Control Block (PCB) is ready. The program still sits in secondary memory.

   - Ready: the process is loaded into main memory and is ready to run. It waits in the ready queue until the CPU becomes free. It has everything it needs except the processor itself.

   - Running: the CPU is currently executing the instructions of this process. On a single processor machine only one process can be in this state at a time.

   - Blocked, also called Waiting: the process cannot go on, because it is waiting for an event, such as an I/O operation finishing, user input arriving, or a locked resource being released. It is not competing for the CPU, so giving it the processor would be useless.

   - Terminated: the process has finished its execution, or it has been stopped. The OS deletes its PCB and frees every resource it had. The PCB may stay for a short while, so the parent can read the exit status. Such a process is called a zombie in Unix.

   Two more states in systems that use swapping:
   - Suspend Ready: a ready process that was moved to secondary storage because memory was short. It comes back to Ready when it is loaded into main memory again.
   - Suspend Blocked: a waiting process that was swapped out to disk.

   State transitions and what causes each:

   | Transition | What causes it |
   |---|---|
   | New → Ready | Resources are allocated and the process is loaded into main memory |
   | Ready → Running | The scheduler gives the CPU to this process |
   | Running → Blocked | The process waits for I/O, for input, or for a system resource |
   | Blocked → Ready | The event finishes, or the resource becomes free |
   | Running → Ready | The OS preempts the process, often because a higher priority task arrived |
   | Running → Terminated | The process finishes, or it is forcibly stopped |
   | Blocked → Terminated | The waiting process is aborted or killed |

   State transition diagram:

   ```mermaid
   stateDiagram-v2
     [*] --> New
     New --> Ready : admitted
     Ready --> Running : scheduler dispatch
     Running --> Ready : interrupt, quantum expired
     Running --> Waiting : I/O or event wait
     Waiting --> Ready : I/O or event completion
     Running --> Terminated : exit
     Terminated --> [*]
   ```

   In plain text:
   ```
                    admitted            dispatch
      New  ------------------> Ready -------------> Running
                                ^   \                  |  \
                                |    \  interrupt      |   \  exit
                                |     +----------------+    +------> Terminated
                                |                           |
                                |    I/O completion         |  I/O request
                                +---------- Waiting <-------+
   ```

   Explanation of each transition:
   - New to Ready (admitted): the long-term scheduler admits the process and allocates memory for it.
   - Ready to Running (dispatch): the short-term scheduler selects the process and the dispatcher gives it the CPU.
   - Running to Ready (interrupt): the time quantum expires, or a higher-priority process arrives and preempts it. The process is still able to run; it has only lost its turn.
   - Running to Waiting (I/O or event wait): the process issues a request that cannot be satisfied immediately, so it voluntarily gives up the CPU.
   - Waiting to Ready (completion): the awaited event occurs, and the process becomes eligible for the CPU again. Note that it goes to Ready, not directly to Running, because the CPU may be busy.
   - Running to Terminated (exit): the process finishes or is killed.

   Two transitions that can never occur, and are worth stating because they are frequently asked:
   - Ready to Waiting is impossible: a process cannot begin waiting for an event it has not yet requested, and it cannot request anything without running.
   - Waiting to Running is impossible: after its event completes, a process must join the ready queue and be selected by the scheduler like any other.
10. **Operating System এর ক্ষেত্রে নিম্নোক্ত Process State গুলো ব্যবহার করে State Diagram অংকন করুন। [New, ready, Wait, Run, Terminated]** *[NWPGCL Assistant Manager(ICT) 2020 compact it 1040 (ET: DPI)]*


    Answer: A process is a program in execution. A program is a passive entity, a file of instructions stored on disk; a process is the active entity, with a program counter, registers, a stack, a data section and an entry in the process table. One program can give rise to many processes, as when several copies of a browser run at once.

    A process holds:
    - The program code, called the text section
    - The program counter and the contents of the CPU registers
    - The stack, holding temporary data such as function parameters, return addresses and local variables
    - The data section, holding global variables
    - The heap, memory allocated dynamically at run time

    The five states of a process:

    - New: the process has just been created. It has not started running yet, but its Process Control Block (PCB) is ready. The program still sits in secondary memory.

    - Ready: the process is loaded into main memory and is ready to run. It waits in the ready queue until the CPU becomes free. It has everything it needs except the processor itself.

    - Running: the CPU is currently executing the instructions of this process. On a single processor machine only one process can be in this state at a time.

    - Blocked, also called Waiting: the process cannot go on, because it is waiting for an event, such as an I/O operation finishing, user input arriving, or a locked resource being released. It is not competing for the CPU, so giving it the processor would be useless.

    - Terminated: the process has finished its execution, or it has been stopped. The OS deletes its PCB and frees every resource it had. The PCB may stay for a short while, so the parent can read the exit status. Such a process is called a zombie in Unix.

    Two further states in systems with swapping:
    - Suspended-Ready: ready, but swapped out to disk.
    - Suspended-Blocked: waiting, and swapped out to disk.

    State transition diagram:

    ```mermaid
    stateDiagram-v2
      [*] --> New
      New --> Ready : admitted
      Ready --> Running : scheduler dispatch
      Running --> Ready : interrupt, quantum expired
      Running --> Waiting : I/O or event wait
      Waiting --> Ready : I/O or event completion
      Running --> Terminated : exit
      Terminated --> [*]
    ```

    In plain text:
    ```
                     admitted            dispatch
       New  ------------------> Ready -------------> Running
                                 ^   \                  |  \
                                 |    \  interrupt      |   \  exit
                                 |     +----------------+    +------> Terminated
                                 |                           |
                                 |    I/O completion         |  I/O request
                                 +---------- Waiting <-------+
    ```

    Explanation of each transition:
    - New to Ready (admitted): the long-term scheduler admits the process and allocates memory for it.
    - Ready to Running (dispatch): the short-term scheduler selects the process and the dispatcher gives it the CPU.
    - Running to Ready (interrupt): the time quantum expires, or a higher-priority process arrives and preempts it. The process is still able to run; it has only lost its turn.
    - Running to Waiting (I/O or event wait): the process issues a request that cannot be satisfied immediately, so it voluntarily gives up the CPU.
    - Waiting to Ready (completion): the awaited event occurs, and the process becomes eligible for the CPU again. Note that it goes to Ready, not directly to Running, because the CPU may be busy.
    - Running to Terminated (exit): the process finishes or is killed.

    Two transitions that can never occur, and are worth stating because they are frequently asked:
    - Ready to Waiting is impossible: a process cannot begin waiting for an event it has not yet requested, and it cannot request anything without running.
    - Waiting to Running is impossible: after its event completes, a process must join the ready queue and be selected by the scheduler like any other.

## Concurrency, Threads & Synchronization (9)

1. Multi-threaded processing and distributed computing have become essential. *[Combined Bank Officer (IT) 03.01.2026 debug it (ET: N/A)]*


   Answer: Multi-threaded processing and distributed computing have become essential because the limits of single-processor performance were reached, while the size of the problems to be solved kept growing.

   Why multi-threaded processing became essential:
   - The end of frequency scaling: from about 2005 processor clock speeds stopped rising, because power consumption grows with the cube of frequency and the heat could no longer be removed. Manufacturers therefore added cores instead of megahertz. A single-threaded program cannot use those extra cores, so software had to become multi-threaded to gain any benefit from new hardware.
   - Responsiveness: an interactive application must remain usable while a long operation runs. Without threads, the interface freezes.
   - Efficient use of the CPU during input and output: while one thread waits for a disk or a network, another thread of the same process continues to compute.
   - Economy: creating and switching threads is far cheaper than creating and switching processes, because the address space is shared.
   - Natural structure: servers handling many clients, browsers with many tabs, and games running physics, rendering and audio all map naturally onto threads.

   Why distributed computing became essential:
   - Scale beyond one machine: the data sets and workloads of search engines, social platforms, banking systems and scientific simulation exceed what any single machine can hold or process.
   - Cost: a cluster of ordinary machines is far cheaper than one very large machine of the same total capacity, and it can be grown incrementally.
   - Reliability and availability: with replication across machines, the failure of one node does not stop the service. A single machine is a single point of failure.
   - Geographic distribution: users are spread across the world, and placing servers near them reduces latency.
   - Resource sharing: expensive resources such as storage arrays and GPUs can be shared by many users.
   - Elasticity: cloud platforms allow capacity to be added and removed as demand changes, which is impossible with a fixed single machine.

   How the two relate: a distributed system is made of many machines, and each machine is itself multi-core and runs multi-threaded software. The two levels of parallelism are complementary, and modern frameworks such as MapReduce, Spark and Kubernetes exploit both at once.

   The difficulties that come with them:
   - Multi-threading brings race conditions, deadlocks, and faults that depend on timing and cannot be reproduced reliably.
   - Distributed computing brings network partitions, partial failure, clock skew and the problem of consistency, formalised in the CAP theorem, which states that a distributed system cannot simultaneously guarantee consistency, availability and partition tolerance.
   - Amdahl's law limits the benefit of parallelism: if a fraction p of a program can be parallelised, the maximum speedup with any number of processors is 1/(1 - p). A program that is 90 per cent parallel can never be more than ten times faster, however many cores are added.

   Relevance to Bangladesh: national systems such as the NID database, mobile financial services and the e-GP platform must serve millions of concurrent users, which is possible only through multi-threaded servers running on distributed clusters, as in the National Data Center with its disaster recovery site.
2. **What is Multithreading programming? Why Multithreading used in programming?** *[Combined Bank Assistant Programmer 09.02.2024 compact it 296 (ET: BIBM)]*


   Answer: Multithreading is the technique of dividing a single process into two or more threads that execute concurrently, sharing the same address space, code, data and open files, while each keeps its own program counter, registers and stack.

   Why multithreading is used:

   - Responsiveness: an interactive program can continue to respond to the user while a long operation proceeds in another thread. A word processor can accept typing while it prints and while it checks spelling.
   - Resource sharing: threads share memory and files by default, so no special mechanism such as shared memory or message passing is needed for them to cooperate.
   - Economy: creating a thread is far cheaper than creating a process, typically ten to a hundred times, because no new address space or page table has to be built. Switching between threads is also much cheaper.
   - Scalability on multiprocessors: threads of one process can run genuinely in parallel on different cores, so a multithreaded program gets faster as cores are added, while a single-threaded program does not.
   - Better utilisation during input and output: while one thread blocks on a disk or network operation, another thread of the same process continues to use the CPU.
   - Natural program structure: a server that handles many clients, a game that runs physics, rendering and audio, or a browser that manages many tabs, all map naturally onto threads.
   - Simpler communication than between processes, since data is already shared.

   Difficulties that must be mentioned:
   - Shared data must be protected with mutexes, semaphores or monitors, otherwise race conditions occur.
   - Deadlock becomes possible when several locks are involved.
   - Debugging is harder, because faults depend on timing and are not reproducible.
   - One thread that crashes or corrupts memory brings down the entire process.
   - Excessive threads cause context-switch overhead rather than speedup.

   Models of threading:
   - Many-to-one: many user threads mapped to one kernel thread. Cheap, but one blocking call blocks all threads and no true parallelism is possible.
   - One-to-one: each user thread maps to a kernel thread. True parallelism and non-blocking behaviour, at the cost of more kernel resources. This is the model of Linux, Windows and modern Java.
   - Many-to-many: many user threads multiplexed onto a smaller number of kernel threads, combining the advantages of both.

   Example in Java:
   ```java
   class Worker extends Thread {
       private final String name;
       Worker(String name) { this.name = name; }
       public void run() {
           for (int i = 1; i <= 3; i++) {
               System.out.println(name + " step " + i);
               try { Thread.sleep(100); } catch (InterruptedException e) { }
           }
       }
   }

   public class ThreadDemo {
       public static void main(String[] args) throws InterruptedException {
           Worker t1 = new Worker("Downloader");
           Worker t2 = new Worker("Renderer");
           t1.start();          // starts a new thread
           t2.start();
           t1.join();           // wait for both to finish
           t2.join();
           System.out.println("Both threads finished");
       }
   }
   ```
   The two threads interleave, so the output order varies from run to run, which is itself an illustration of why shared data needs protection.
3. **What is Multithreading System?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1460 (ET: N/A)]*


   Answer: A multithreading system is one in which a single process is divided into several threads that execute concurrently, sharing the same address space, code, data and open files, while each thread keeps its own program counter, registers and stack.

   Multithreading is the technique of dividing a single process into two or more threads that execute concurrently, sharing the same address space, code, data and open files, while each keeps its own program counter, registers and stack.

   Why multithreading is used:

   - Responsiveness: an interactive program can continue to respond to the user while a long operation proceeds in another thread. A word processor can accept typing while it prints and while it checks spelling.
   - Resource sharing: threads share memory and files by default, so no special mechanism such as shared memory or message passing is needed for them to cooperate.
   - Economy: creating a thread is far cheaper than creating a process, typically ten to a hundred times, because no new address space or page table has to be built. Switching between threads is also much cheaper.
   - Scalability on multiprocessors: threads of one process can run genuinely in parallel on different cores, so a multithreaded program gets faster as cores are added, while a single-threaded program does not.
   - Better utilisation during input and output: while one thread blocks on a disk or network operation, another thread of the same process continues to use the CPU.
   - Natural program structure: a server that handles many clients, a game that runs physics, rendering and audio, or a browser that manages many tabs, all map naturally onto threads.
   - Simpler communication than between processes, since data is already shared.

   Difficulties that must be mentioned:
   - Shared data must be protected with mutexes, semaphores or monitors, otherwise race conditions occur.
   - Deadlock becomes possible when several locks are involved.
   - Debugging is harder, because faults depend on timing and are not reproducible.
   - One thread that crashes or corrupts memory brings down the entire process.
   - Excessive threads cause context-switch overhead rather than speedup.

   Models of threading:
   - Many-to-one: many user threads mapped to one kernel thread. Cheap, but one blocking call blocks all threads and no true parallelism is possible.
   - One-to-one: each user thread maps to a kernel thread. True parallelism and non-blocking behaviour, at the cost of more kernel resources. This is the model of Linux, Windows and modern Java.
   - Many-to-many: many user threads multiplexed onto a smaller number of kernel threads, combining the advantages of both.

   Example in Java:
   ```java
   class Worker extends Thread {
       private final String name;
       Worker(String name) { this.name = name; }
       public void run() {
           for (int i = 1; i <= 3; i++) {
               System.out.println(name + " step " + i);
               try { Thread.sleep(100); } catch (InterruptedException e) { }
           }
       }
   }

   public class ThreadDemo {
       public static void main(String[] args) throws InterruptedException {
           Worker t1 = new Worker("Downloader");
           Worker t2 = new Worker("Renderer");
           t1.start();          // starts a new thread
           t2.start();
           t1.join();           // wait for both to finish
           t2.join();
           System.out.println("Both threads finished");
       }
   }
   ```
   The two threads interleave, so the output order varies from run to run, which is itself an illustration of why shared data needs protection.
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


   Answer: The program creates four child processes with fork(), and each child prints the current value of i and then exits.

   Trace of what happens:
   - The parent enters the loop with i = 0 and calls fork(). Two processes now exist. In the child, fork() returns 0, so the child prints 0 and calls exit(0), leaving the loop at once. In the parent, fork() returns the child's PID, which is not 0, so the parent skips the if and continues the loop.
   - The same happens for i = 1, 2 and 3, so the parent creates four children in total, and each child prints its own value of i and exits immediately.
   - Because each child calls exit(0) inside the if block, no child ever reaches the next iteration of the loop. This is the crucial point: if exit(0) were removed, the children would themselves fork, and 2^4 - 1 = 15 processes would be created instead of 4.
   - The parent then calls wait(NULL) four times, collecting the four children.

   Output:
   ```
   0
   1
   2
   3
   ```
   Four lines are printed, one by each child.

   Important qualification about the order: the four children are independent processes scheduled by the operating system, so the order in which they run is not determined by the program. The four numbers may appear in any order, for example 2, 0, 3, 1. Only the set of values, and their count, is guaranteed. Any answer to this question should state that the output is non-deterministic in order.

   Total number of processes: 1 parent + 4 children = 5.

   Points worth stating in an answer:
   - fork() returns 0 in the child and the child's PID in the parent, which is how the two are distinguished. It returns -1 on failure.
   - After fork() the child receives a copy of the parent's memory, implemented efficiently by copy-on-write, so the child has its own copy of i with the value it had at the moment of the fork.
   - exit(0) terminates the calling process and flushes its standard output buffer, which is why the printf output appears.
   - wait(NULL) makes the parent block until one child terminates, and it reaps the child's process table entry. Without it the children would become zombies.
   - The header <stdio.h> is missing from the code as printed, which a compiler would warn about since printf is used.

   Variant to compare, without exit(0):
   ```c
   for (i = 0; i < 4; i++) {
       fork();
   }
   ```
   Here every process, parent and child alike, continues the loop, so the number of processes doubles at each iteration: 2^4 = 16 processes exist at the end, that is the original plus 15 new ones.
5. **অথবা, (ক) Thread এর সংজ্ঞা দিন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 619 (ET: N/A)]*


   Answer: Thread (থ্রেড) হলো একটি প্রসেসের ভেতরে চলমান নির্বাহের ক্ষুদ্রতম একক, অর্থাৎ প্রোগ্রাম কাউন্টার, রেজিস্টার সেট ও স্ট্যাক নিয়ে গঠিত একটি স্বাধীন নির্বাহপথ, যা একই প্রসেসের অন্য থ্রেডগুলোর সঙ্গে কোড, ডেটা ও খোলা ফাইল ভাগাভাগি করে ব্যবহার করে।

   একে বলা হয় lightweight process, কারণ এটি তৈরি ও পরিবর্তন করতে প্রসেসের তুলনায় অনেক কম খরচ হয়।

   একটি থ্রেডের নিজস্ব যা থাকে:
   - প্রোগ্রাম কাউন্টার
   - রেজিস্টার সেট
   - স্ট্যাক
   - থ্রেড আইডি ও অবস্থা

   একই প্রসেসের থ্রেডগুলো যা ভাগাভাগি করে:
   - কোড অংশ (text section)
   - ডেটা অংশ ও গ্লোবাল ভেরিয়েবল
   - হিপ
   - খোলা ফাইল ও সিগন্যাল হ্যান্ডলার
   - প্রসেসের অন্যান্য সম্পদ

   প্রতিটি প্রসেসে অন্তত একটি থ্রেড থাকে, যাকে বলা হয় প্রধান থ্রেড (main thread)। একাধিক থ্রেড থাকলে তাকে বলা হয় multithreaded process।

   উদাহরণ: একটি ওয়ার্ড প্রসেসরে একটি থ্রেড ব্যবহারকারীর টাইপিং গ্রহণ করে, আরেকটি বানান পরীক্ষা করে, তৃতীয়টি স্বয়ংক্রিয়ভাবে ফাইল সংরক্ষণ করে এবং চতুর্থটি ছাপার কাজ চালায়। সবগুলো একই নথির ওপর কাজ করে বলে একই ডেটা ব্যবহার করতে পারে।

   সুবিধা: দ্রুত সাড়াদান, সহজ সম্পদ ভাগাভাগি, কম খরচ এবং বহু-কোর প্রসেসরে প্রকৃত সমান্তরাল নির্বাহ।

   অসুবিধা: ভাগ করা ডেটা রক্ষা করতে সিঙ্ক্রোনাইজেশন লাগে, race condition ও deadlock এর ঝুঁকি থাকে, এবং একটি থ্রেড ভেঙে পড়লে পুরো প্রসেস বন্ধ হয়ে যায়।
6. **Write down the thread life cycle.** *[BDCCL Assistant Manager (Cyber Security) 14.10.2022 compact it 755 (ET: N/A)]*


   Answer: The life cycle of a thread consists of the states through which it passes from creation to termination. The names below are those used in Java, which is the standard reference for this question.

   The states:

   - New (born): the thread object has been created, for example with Thread t = new Thread(), but start() has not yet been called. No system resources have been allocated for execution and the thread is not yet alive.

   - Runnable (ready): start() has been called. The thread is eligible to run and has joined the pool of threads the scheduler may choose from. It may or may not be executing at this instant, because the scheduler decides. Java deliberately merges the ready and running states into one, since a program cannot tell the difference reliably.

   - Running: the scheduler has selected the thread and it is executing its run() method on a CPU. On a multi-core machine several threads can be running at once.

   - Blocked or Waiting: the thread is alive but not eligible to run. This happens when it calls sleep(), when it calls wait(), when it calls join() to await another thread, when it blocks on input or output, or when it is waiting to acquire a lock held by another thread. Java distinguishes three sub-states: BLOCKED (waiting for a monitor lock), WAITING (waiting indefinitely for another thread) and TIMED_WAITING (waiting with a timeout).

   - Terminated (dead): the run() method has returned, either normally or because of an uncaught exception. The thread cannot be restarted; calling start() again throws IllegalThreadStateException.

   Diagram:

   ```mermaid
   stateDiagram-v2
     [*] --> New
     New --> Runnable : start()
     Runnable --> Running : scheduler dispatch
     Running --> Runnable : yield() or quantum expired
     Running --> Waiting : sleep(), wait(), join(), I/O
     Waiting --> Runnable : notify(), timeout, I/O complete
     Running --> Terminated : run() returns
     Terminated --> [*]
   ```

   The transitions:
   - New to Runnable: caused by start(). Note that calling run() directly does not create a thread; it merely executes the method in the current thread.
   - Runnable to Running: the scheduler chooses the thread. The program has no control over when.
   - Running to Runnable: the time quantum expires, or the thread calls yield() to offer the CPU to others.
   - Running to Waiting: the thread calls sleep(ms), wait(), or join(), or issues a blocking input-output call, or fails to acquire a lock.
   - Waiting to Runnable: the sleep time expires, notify() or notifyAll() is called, the joined thread finishes, the input-output completes, or the lock becomes free. Note that it returns to Runnable, not directly to Running.
   - Running to Terminated: run() returns or throws.

   Example:
   ```java
   class MyThread extends Thread {
       public void run() {
           System.out.println(getName() + " state inside run: " + getState());
           try { Thread.sleep(500); } catch (InterruptedException e) { }
           System.out.println(getName() + " finishing");
       }
   }

   public class LifeCycleDemo {
       public static void main(String[] args) throws InterruptedException {
           MyThread t = new MyThread();
           System.out.println("After creation: " + t.getState());   // NEW
           t.start();
           System.out.println("After start:    " + t.getState());   // RUNNABLE
           Thread.sleep(100);
           System.out.println("During sleep:   " + t.getState());   // TIMED_WAITING
           t.join();
           System.out.println("After join:     " + t.getState());   // TERMINATED
       }
   }
   ```

   Two important rules to state:
   - A terminated thread can never be restarted; a new Thread object must be created.
   - start() creates a new thread of execution; calling run() directly does not, and is a common beginner's error.
7. **What is Multi-threading and multi-tasking? Difference between Multi-threading and Multi-tasking?** *[RAKUB Maintenance Engineer (PO) 05.10.2021 compact it 854 (ET: N/A)]*


   Answer:

   Multithreading:

   Multithreading is the technique of dividing a single process into several threads that run concurrently, sharing the same address space, code, data and open files, while each keeps its own program counter, registers and stack. It is concurrency within one process.

   Example: a web browser in which one thread renders the page, another downloads images, a third runs JavaScript and a fourth handles the user interface, all within a single browser process.

   Multitasking:

   Multitasking is the ability of an operating system to execute more than one task, that is more than one process, apparently at the same time, by rapidly switching the CPU among them. It is concurrency between processes.

   Two forms:
   - Preemptive multitasking: the operating system decides when to take the CPU away, using a timer interrupt. Used by Linux, Windows NT onwards, macOS and Unix.
   - Cooperative multitasking: a process keeps the CPU until it voluntarily yields. Used by Windows 3.x and early Mac OS. A single misbehaving program can freeze the whole system, which is why it was abandoned.

   Example: writing in a word processor, playing music in a media player and downloading a file in a browser, all at once.

   Difference between multithreading and multitasking:

   | Point | Multithreading | Multitasking |
   |---|---|---|
   | Unit of execution | Threads within one process | Separate processes |
   | Address space | Shared among the threads | Separate for each process |
   | Level | Within a single program | Across programs |
   | Creation cost | Low | High |
   | Context switch cost | Low, the address space does not change | High, the page table and TLB must be changed |
   | Communication | Through shared variables, which is immediate | Through inter-process communication: pipes, sockets, shared memory |
   | Isolation | Weak; a fault in one thread kills the whole process | Strong; a crash in one process does not affect others |
   | Synchronisation | Frequently required, since data is shared by default | Required only for explicitly shared resources |
   | Managed by | The programmer, using thread libraries, with kernel support | The operating system scheduler |
   | Purpose | To make one program faster and more responsive | To let several programs run together |
   | Example | Tabs and rendering inside one browser | A browser, a media player and an editor running together |

   Relationship: the two are complementary levels of concurrency. An operating system multitasks among processes, and each of those processes may itself be multithreaded. A modern machine therefore runs many processes, each with many threads, distributed across several cores.

   Related terms worth distinguishing:
   - Multiprogramming: keeping several programs in memory so that the CPU always has work; the ancestor of multitasking.
   - Multiprocessing: using more than one physical CPU or core, which allows genuine parallel execution rather than rapid switching.
   - Concurrency versus parallelism: concurrency means tasks make progress in overlapping time periods; parallelism means they literally execute at the same instant on different cores.
8. **(c) What is thread? Give some benefits of multi-threaded programming.** *[BPSC (Security Services Division) Assistant Programmer 13.12.2021 compact it 889-890 (ET: N/A)]*


   Answer: A thread is the smallest unit of execution within a process. It consists of a program counter, a register set and a stack, and it shares the code, the data, the heap and the open files with the other threads of the same process. It is often called a lightweight process, because creating and switching it costs far less than a full process.

   What is private to a thread: program counter, registers, stack, thread ID and thread state.
   What is shared among the threads of a process: code section, data section and global variables, heap, open files and signal handlers.

   Benefits of multi-threaded programming:

   - Responsiveness: an interactive application continues to respond to the user while a long operation runs in another thread. A browser remains usable while a large image downloads, and a word processor accepts typing while it prints.

   - Resource sharing: threads share the memory and the resources of their process by default. Processes must be given explicit shared memory or message passing, which is slower and more complex to write.

   - Economy: creating a thread is typically ten to a hundred times cheaper than creating a process, because no new address space and no new page table are needed. Switching between threads is also much cheaper, since the memory management state is unchanged.

   - Scalability on multiprocessors: the threads of one process can run truly in parallel on different cores, so a multi-threaded program becomes faster as cores are added. A single-threaded program cannot use a second core at all.

   - Better utilisation during input and output: while one thread blocks on a disk or a network operation, another thread of the same process keeps the CPU busy.

   - Simplified program structure: a server that handles many clients, a game with separate physics, rendering and audio loops, or a pipeline of processing stages all map naturally onto threads.

   - Faster communication: threads exchange data through ordinary variables, with no system call and no copying, whereas processes need inter-process communication.

   - Lower memory footprint: many threads in one process consume much less memory than the same number of processes, because the code and data exist only once.

   Costs that should also be stated:
   - Shared data must be protected with mutexes, semaphores or monitors, or race conditions occur.
   - Deadlock becomes possible when several locks are used.
   - Debugging is difficult, because faults depend on timing and are often not reproducible.
   - A single thread that crashes or corrupts memory brings down the whole process, since the address space is shared.
   - Creating too many threads causes context-switch overhead rather than speedup, which is why thread pools are used in practice.

   Simple example in Java:
   ```java
   class Downloader implements Runnable {
       private final String file;
       Downloader(String file) { this.file = file; }
       public void run() {
           System.out.println("Downloading " + file + " on " + Thread.currentThread().getName());
       }
   }

   public class ThreadBenefit {
       public static void main(String[] args) {
           new Thread(new Downloader("a.zip")).start();
           new Thread(new Downloader("b.zip")).start();
           System.out.println("Main thread is free to continue");
       }
   }
   ```
   The two downloads proceed while the main thread continues, which is the responsiveness benefit in its simplest form.
9. **(d) Differentiate between thread and process.** *[BPSC (Security Services Division) Assistant Maintenance Engineer 15.12.2021 compact it 891 (ET: N/A)]*


   Answer: | Point | Process | Thread |
   |---|---|---|
   | Definition | A program in execution, with its own address space | A lightweight unit of execution inside a process |
   | Address space | Its own, private and protected | Shared with all other threads of the same process |
   | Memory sharing | Processes do not share memory by default | Threads share the code, data and heap |
   | What is private | Everything | Only the program counter, the registers and the stack |
   | Creation cost | High; a new address space and page table must be built | Low, typically ten to a hundred times cheaper |
   | Context switch cost | High; the page table and TLB must be changed | Low; the address space is unchanged |
   | Communication | Through inter-process communication: pipes, message queues, shared memory, sockets | Directly through shared variables |
   | Isolation and safety | Strong; a crash in one process does not affect others | Weak; a crash in one thread usually kills the whole process |
   | Synchronisation needed | Only for explicitly shared resources | Frequently, because data is shared by default |
   | Termination | Independent | Ending the process ends all its threads |
   | Also called | Heavyweight process | Lightweight process (LWP) |
   | Example | Two separate copies of a browser | The tabs, the renderer and the network handler inside one browser |

   Relationship between them: every process has at least one thread, called the main thread. Multithreading means giving a process several threads, so that they can run concurrently, and truly in parallel on a multi-core machine, while sharing the same data.

## CPU Scheduling (6)

1. A system has three processes with the following arrival times and CPU burst times:

| Process | Arrival Time (ms) | Burst Time (ms) |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 3 |
| P3 | 2 | 2 |

Using the First-Come, First-Served (FCFS) CPU scheduling algorithm calculate the average waiting time and the average turnaround time. *[Officer (IT) 31 Jul 2026 bscs 02 (ET: N/A)]*


   Answer: Given:

   | Process | Arrival Time (ms) | Burst Time (ms) |
   |---|---|---|
   | P1 | 0 | 5 |
   | P2 | 1 | 3 |
   | P3 | 2 | 2 |

   FCFS is non-preemptive and serves processes in order of arrival, so the order is P1, P2, P3.

   Gantt chart:
   ```
   |    P1    |  P2  | P3 |
   0          5      8    10
   ```

   Calculation:
   - Turnaround Time = Completion Time - Arrival Time
   - Waiting Time = Turnaround Time - Burst Time

   | Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT |
   |---|---|---|---|---|---|
   | P1 | 0 | 5 | 5 | 5 - 0 = 5 | 5 - 5 = 0 |
   | P2 | 1 | 3 | 8 | 8 - 1 = 7 | 7 - 3 = 4 |
   | P3 | 2 | 2 | 10 | 10 - 2 = 8 | 8 - 2 = 6 |

   Average Waiting Time = (0 + 4 + 6) / 3
   = 10 / 3
   = 3.33 ms

   Average Turnaround Time = (5 + 7 + 8) / 3
   = 20 / 3
   = 6.67 ms

   Final answers:
   - Average waiting time = 3.33 ms
   - Average turnaround time = 6.67 ms

   Observation: FCFS is simple and starvation-free, but it suffers from the convoy effect. Here the longest process P1 happens to run first, so P2 and P3 wait behind it. Had the order been P3, P2, P1, that is shortest first, the waiting times would have been 0, 1 and 3 giving an average of only 1.33 ms, with exactly the same total work. This is why SJF gives the minimum average waiting time and why FCFS is unsuitable for interactive systems.
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


   Answer:

   (a) Distributed control and computing, and the role of a large language model in it:

   Distributed computing means solving a problem with many machines that cooperate over a network rather than with one machine. Its functions and benefits are:
   - Scale: data sets and workloads that exceed the capacity of any single machine can be processed by dividing the work across a cluster.
   - Fault tolerance: with replication across nodes, the failure of one machine does not stop the service, whereas a single machine is a single point of failure.
   - Cost: many ordinary machines are far cheaper than one very large one of the same total capacity, and capacity can be added incrementally.
   - Geographic distribution: servers placed near users reduce latency, which is why content delivery networks exist.
   - Resource sharing: expensive storage and accelerators are shared among many users.
   - Elasticity: capacity is added and removed as demand changes, which is the essence of cloud computing.
   - Parallel speedup: independent parts of a computation run at the same time, as in MapReduce and Spark.

   Distributed control means the decision-making is spread across nodes rather than concentrated in one controller. It avoids a single point of failure and scales better, but it requires consensus protocols such as Paxos or Raft to keep the nodes in agreement, and it faces the limits of the CAP theorem: a distributed system cannot simultaneously guarantee consistency, availability and tolerance of network partitions.

   A large language model in this setting is itself trained and served on a distributed cluster of accelerators, since neither the model nor the training data fits on one machine. In control and operations it is used for log analysis, anomaly detection, generating and reviewing configuration, and answering operational queries in natural language, always with human verification, because such a model can produce confident but wrong output.

   (b) Clock cycle, and the meaning of 3.5 GHz:

   A clock cycle is one complete oscillation of the processor's clock signal, from low to high and back to low. It is the smallest unit of time in the processor, and every internal operation is synchronised to it. Its duration is T = 1 / f.

   3.5 GHz means the clock oscillates 3,500,000,000 times per second, so one cycle lasts 1 / (3.5 x 10^9) = 0.286 nanoseconds.

   What it does not mean: it does not mean 3.5 billion instructions per second. One instruction may take several cycles (CPI greater than 1), while a superscalar processor may complete several instructions in one cycle (IPC greater than 1). Real performance is roughly clock speed multiplied by IPC, which is why a newer 3.5 GHz processor can outperform an older 4.0 GHz one. A cache miss can also stall the processor for hundreds of cycles, so the memory system often matters more than the clock.

   Related points: base clock and turbo clock differ, thermal throttling reduces the clock when the chip is hot, and dynamic power follows P = C x V^2 x f, which is why clock speeds stopped rising and core counts rose instead.

   (c) Scheduling calculations for the given table:

   | Process | Burst Time (ms) | Priority |
   |---|---|---|
   | P1 | 15 | 1 |
   | P2 | 2 | 1 |
   | P3 | 4 | 3 |
   | P4 | 2 | 4 |
   | P5 | 8 | 2 |

   All processes arrive at time 0, so Turnaround Time = Completion Time.

   FCFS, in the order P1 to P5:
   ```
   |        P1        |P2|  P3  |P4|     P5     |
   0                 15 17     21 23           31
   ```

   | Process | BT | CT | TAT | WT |
   |---|---|---|---|---|
   | P1 | 15 | 15 | 15 | 0 |
   | P2 | 2 | 17 | 17 | 15 |
   | P3 | 4 | 21 | 21 | 17 |
   | P4 | 2 | 23 | 23 | 21 |
   | P5 | 8 | 31 | 31 | 23 |

   Average Waiting Time = (0 + 15 + 17 + 21 + 23) / 5 = 76 / 5 = 15.20 ms
   Average Turnaround Time = (15 + 17 + 21 + 23 + 31) / 5 = 107 / 5 = 21.40 ms

   SJF (non-preemptive), in the order P2, P4, P3, P5, P1, with the tie between P2 and P4 broken by arrival order:
   ```
   |P2|P4|  P3  |     P5     |        P1        |
   0  2  4      8           16                 31
   ```

   | Process | BT | CT | TAT | WT |
   |---|---|---|---|---|
   | P1 | 15 | 31 | 31 | 16 |
   | P2 | 2 | 2 | 2 | 0 |
   | P3 | 4 | 8 | 8 | 4 |
   | P4 | 2 | 4 | 4 | 2 |
   | P5 | 8 | 16 | 16 | 8 |

   Average Waiting Time = (16 + 0 + 4 + 2 + 8) / 5 = 30 / 5 = 6.00 ms
   Average Turnaround Time = (31 + 2 + 8 + 4 + 16) / 5 = 61 / 5 = 12.20 ms

   Comparison:

   | Algorithm | Average Waiting Time | Average Turnaround Time |
   |---|---|---|
   | FCFS | 15.20 ms | 21.40 ms |
   | SJF | 6.00 ms | 12.20 ms |

   SJF reduces both averages by more than half. The reason is the convoy effect in FCFS: the longest process P1, of 15 ms, happens to run first and delays every shorter process behind it. SJF runs the short ones first, which is provably optimal for average waiting time when all processes are available at time 0.
3. **Consider the set of 3 processes whose arrival time and burst time are given below-**

| Process | AT | BT |
|---|---|---|
| P1 | 0 | 5 |
| P2 | 1 | 4 |
| P3 | 2 | 2 |

**If the CPU scheduling policy is round robin with time quantum=2, finds out the completion time, turnaround time, waiting time, and response time** *[Cadet College (Combined) Lecturer ICT 11.05.2025 compact it 1447 (ET: N/A)]*


   Answer: Given:

   | Process | Arrival Time | Burst Time |
   |---|---|---|
   | P1 | 0 | 5 |
   | P2 | 1 | 4 |
   | P3 | 2 | 2 |

   Scheduling policy: Round Robin with time quantum = 2.

   Trace of the ready queue:
   - t = 0: only P1 is present, so P1 runs for 2 units. During this time P2 arrives at t = 1 and joins the queue.
   - t = 2: P1's quantum expires with 3 units left. P3 arrives at t = 2 and joins the queue before the preempted P1 is re-added. Queue: P2, P3, P1. P2 runs.
   - t = 4: P2's quantum expires with 2 units left, and is re-added. Queue: P3, P1, P2. P3 runs.
   - t = 6: P3's quantum expires and P3 finishes exactly, since it needed only 2. Queue: P1, P2. P1 runs.
   - t = 8: P1's quantum expires with 1 unit left, and is re-added. Queue: P2, P1. P2 runs.
   - t = 10: P2 finishes, using its last 2 units. Queue: P1. P1 runs.
   - t = 11: P1 finishes its last 1 unit.

   Gantt chart:
   ```
   | P1 | P2 | P3 | P1 | P2 |P1|
   0    2    4    6    8   10 11
   ```

   Results:

   | Process | AT | BT | CT | TAT = CT - AT | WT = TAT - BT | First run | RT = first run - AT |
   |---|---|---|---|---|---|---|---|
   | P1 | 0 | 5 | 11 | 11 | 6 | 0 | 0 |
   | P2 | 1 | 4 | 10 | 9 | 5 | 2 | 1 |
   | P3 | 2 | 2 | 6 | 4 | 2 | 4 | 2 |

   Averages:
   - Average Completion Time = (11 + 10 + 6) / 3 = 27 / 3 = 9.00
   - Average Turnaround Time = (11 + 9 + 4) / 3 = 24 / 3 = 8.00
   - Average Waiting Time = (6 + 5 + 2) / 3 = 13 / 3 = 4.33
   - Average Response Time = (0 + 1 + 2) / 3 = 3 / 3 = 1.00

   Definitions used:
   - Completion Time: the instant at which the process finishes.
   - Turnaround Time = Completion Time - Arrival Time.
   - Waiting Time = Turnaround Time - Burst Time.
   - Response Time = time of first CPU allocation - Arrival Time. It measures how quickly the system reacts, and it is the metric that matters most in an interactive system.

   Observation: the response times are very small, 0, 1 and 2, because Round Robin gives every process a share of the CPU quickly. The turnaround times are correspondingly larger than they would be under SJF, because each process is interrupted repeatedly. This trade-off, better response at the cost of worse averages, is precisely why time-sharing systems use Round Robin.
4. **There are 3 tasks P1, P2, and P3. The arrival time and duration of each task is given below. Apply the round-robin scheduling algorithm with quantum size-20 to schedule the tasks in a single core machine. Calculate the turnaround time for each task. (All tasks have the same priority)** *[BPSC (Ministry of Food) Network/Website Manager (CSE) 21.05.2025 compact it 1338 (ET: N/A)]*

| Task | Arrival time (ms) | Duration (ms) |
|---|---|---|
| P1 | 0 | 40 |
| P2 | 5 | 40 |
| P3 | 10 | 20 |


   Answer: Given:

   | Task | Arrival Time (ms) | Duration (ms) |
   |---|---|---|
   | P1 | 0 | 40 |
   | P2 | 5 | 40 |
   | P3 | 10 | 20 |

   Scheduling: Round Robin with quantum = 20 ms on a single-core machine, all tasks of equal priority.

   Trace of the ready queue:
   - t = 0: only P1 is present, so P1 runs for its quantum of 20 ms. During this period P2 arrives at t = 5 and P3 at t = 10, joining the queue in that order.
   - t = 20: P1's quantum expires with 20 ms left. The queue already holds P2 and P3, so P1 is added after them. Queue: P2, P3, P1. P2 runs.
   - t = 40: P2's quantum expires with 20 ms left, and it is added at the back. Queue: P3, P1, P2. P3 runs.
   - t = 60: P3 has used 20 ms, which is exactly its whole duration, so P3 finishes. Queue: P1, P2. P1 runs.
   - t = 80: P1 uses its remaining 20 ms and finishes. Queue: P2. P2 runs.
   - t = 100: P2 uses its remaining 20 ms and finishes.

   Gantt chart:
   ```
   |    P1    |    P2    |    P3    |    P1    |    P2    |
   0         20         40         60         80        100
   ```

   Turnaround time for each task, where Turnaround Time = Completion Time - Arrival Time:

   | Task | Arrival | Duration | Completion | Turnaround = CT - AT | Waiting = TAT - Duration |
   |---|---|---|---|---|---|
   | P1 | 0 | 40 | 80 | 80 - 0 = 80 ms | 80 - 40 = 40 ms |
   | P2 | 5 | 40 | 100 | 100 - 5 = 95 ms | 95 - 40 = 55 ms |
   | P3 | 10 | 20 | 60 | 60 - 10 = 50 ms | 50 - 20 = 30 ms |

   Final answers:
   - Turnaround time of P1 = 80 ms
   - Turnaround time of P2 = 95 ms
   - Turnaround time of P3 = 50 ms

   Average turnaround time = (80 + 95 + 50) / 3 = 225 / 3 = 75 ms
   Average waiting time = (40 + 55 + 30) / 3 = 125 / 3 = 41.67 ms

   Note on the quantum: every task's duration is an exact multiple of the 20 ms quantum, so no task ever finishes in the middle of a slice and there are no partial quanta. Note also that P3, the shortest task, finishes first even though it arrived last, which shows how Round Robin favours short jobs indirectly by never letting a long job monopolise the CPU.

   Number of context switches: 4, at t = 20, 40, 60 and 80. If the quantum were reduced to 10 ms the number would double, improving response time but wasting more CPU on switching.
5. **Calculate the average waiting time.** *[BCIC Assistant Programmer 14.02.2025 compact it 1328 (ET: BUET)]*

| Process | Burst Time |
|---|---|
| P1 | 21 |
| P2 | 3 |
| P3 | 6 |


   Answer: Given:

   | Process | Burst Time (ms) |
   |---|---|
   | P1 | 21 |
   | P2 | 3 |
   | P3 | 6 |

   No arrival times are stated, so all processes are taken to arrive at time 0, which is the usual assumption. The algorithm is not named either, so the calculation is shown for both FCFS and SJF.

   Under FCFS, in the order P1, P2, P3:

   Gantt chart:
   ```
   |          P1          |P2|  P3  |
   0                     21 24     30
   ```

   Since all arrival times are 0, the waiting time of each process is the sum of the burst times before it.

   | Process | BT | CT | TAT | WT |
   |---|---|---|---|---|
   | P1 | 21 | 21 | 21 | 0 |
   | P2 | 3 | 24 | 24 | 21 |
   | P3 | 6 | 30 | 30 | 24 |

   Average Waiting Time = (0 + 21 + 24) / 3 = 45 / 3 = 15.00 ms
   Average Turnaround Time = (21 + 24 + 30) / 3 = 75 / 3 = 25.00 ms

   Under SJF, in the order P2 (3), P3 (6), P1 (21):

   Gantt chart:
   ```
   |P2|  P3  |          P1          |
   0  3      9                     30
   ```

   | Process | BT | CT | TAT | WT |
   |---|---|---|---|---|
   | P1 | 21 | 30 | 30 | 9 |
   | P2 | 3 | 3 | 3 | 0 |
   | P3 | 6 | 9 | 9 | 3 |

   Average Waiting Time = (9 + 0 + 3) / 3 = 12 / 3 = 4.00 ms
   Average Turnaround Time = (30 + 3 + 9) / 3 = 42 / 3 = 14.00 ms

   Comparison:

   | Algorithm | Average Waiting Time | Average Turnaround Time |
   |---|---|---|
   | FCFS | 15.00 ms | 4 times worse |
   | SJF | 4.00 ms | 14.00 ms |

   Final answer: under FCFS the average waiting time is 15 ms; under SJF it is 4 ms.

   Explanation of the large difference: this data set is the clearest possible illustration of the convoy effect. Under FCFS the very long process of 21 ms runs first, and the two short processes each wait for it, so their waiting times are 21 and 24 ms. Under SJF the two short processes are finished within 9 ms and only the long one waits, for 9 ms. The total work is 30 ms in both cases; only the distribution of waiting changes. This is why SJF is provably optimal for average waiting time when all processes are available at the same instant.
6. **(খ) CPU Scheduling কী? যে যে কারণে CPU Scheduling করতে হয় সেগুলো লিখুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*


   Answer: CPU Scheduling হলো সেই কাজ, যার মাধ্যমে অপারেটিং সিস্টেম সিদ্ধান্ত নেয় ready queue তে অপেক্ষমাণ প্রসেসগুলোর মধ্যে কোনটিকে পরবর্তীতে সিপিইউ দেওয়া হবে। এটি multiprogramming এর ভিত্তি: একটি প্রসেস যখন ইনপুট-আউটপুটের জন্য অপেক্ষা করে, তখন সিপিইউ অন্য একটি প্রসেসকে দিয়ে দেওয়া হয়, যাতে প্রসেসর কখনো অলস না থাকে।

   যে যে কারণে CPU Scheduling করতে হয়:

   - সিপিইউ-এর সর্বোচ্চ ব্যবহার নিশ্চিত করা: ইনপুট-আউটপুট কাজ সিপিইউ-এর তুলনায় হাজার গুণ ধীর। শিডিউলিং না থাকলে একটি প্রসেস ডিস্ক থেকে তথ্য পড়ার সময় সিপিইউ পুরোপুরি অলস বসে থাকত। শিডিউলিংয়ের ফলে সিপিইউ ব্যবহারের হার কয়েক শতাংশ থেকে ৯০ শতাংশের ওপরে ওঠে।

   - থ্রুপুট বাড়ানো: একক সময়ে বেশি সংখ্যক প্রসেস সম্পন্ন করা, কারণ সিপিইউ ও ইনপুট-আউটপুট যন্ত্র একসঙ্গে কাজ করতে পারে।

   - অপেক্ষমাণ সময় ও টার্ন-অ্যারাউন্ড সময় কমানো: বুদ্ধিমান ক্রমে প্রসেস চালালে মোট অপেক্ষার সময় কমে যায়। যেমন ছোট কাজ আগে চালালে (SJF) গড় অপেক্ষমাণ সময় সর্বনিম্ন হয়।

   - সাড়া দেওয়ার সময় (response time) কমানো: ইন্টারেক্টিভ ব্যবস্থায় ব্যবহারকারী কীবোর্ডে চাপ দেওয়ার পর দ্রুত ফল দেখতে চান। Round Robin এই সাড়াদানের সময় নির্দিষ্ট সীমার মধ্যে বেঁধে দেয়।

   - ন্যায্যতা রক্ষা ও starvation প্রতিরোধ: প্রতিটি প্রসেসকে যথাসময়ে সিপিইউ দেওয়া নিশ্চিত করা, যাতে কোনো প্রসেস অনির্দিষ্টকাল বসে না থাকে।

   - অগ্রাধিকার রক্ষা: গুরুত্বপূর্ণ ও জরুরি কাজ, যেমন সিস্টেম প্রসেস বা রিয়েল-টাইম কাজ, আগে সম্পন্ন করা।

   - Multiprogramming ও multitasking সম্ভব করা: শিডিউলিং ছাড়া একই সময়ে একাধিক প্রোগ্রাম চালানোর বিভ্রম তৈরি করা যেত না।

   - রিসোর্সের ভারসাম্যপূর্ণ ব্যবহার: সিপিইউ-নির্ভর ও ইনপুট-আউটপুট-নির্ভর প্রসেসের ভালো মিশ্রণ রাখলে প্রসেসর ও যন্ত্র দুটোই ব্যস্ত থাকে।

   - Convoy effect হ্রাস: একটি দীর্ঘ প্রসেস যেন তার পেছনের সব ছোট প্রসেসকে আটকে না রাখে।

   - রিয়েল-টাইম ব্যবস্থায় নির্ভরযোগ্যতা: Earliest Deadline First এর মতো অ্যালগরিদম নিশ্চিত করে যে নির্দিষ্ট সময়সীমার আগেই কাজ শেষ হবে, যা নিয়ন্ত্রণ ও নিরাপত্তা ব্যবস্থায় অপরিহার্য।

   শিডিউলিং কখন ঘটে: প্রসেস running থেকে waiting এ গেলে, running থেকে ready তে গেলে, waiting থেকে ready তে গেলে, এবং প্রসেস শেষ হলে। প্রথম ও শেষ ক্ষেত্রে হলে non-preemptive, চারটিতেই হলে preemptive।

   বিবেচ্য মানদণ্ড: সিপিইউ ব্যবহারের হার (বাড়াতে হবে), থ্রুপুট (বাড়াতে হবে), টার্ন-অ্যারাউন্ড সময় (কমাতে হবে), অপেক্ষমাণ সময় (কমাতে হবে), সাড়াদানের সময় (কমাতে হবে) এবং ন্যায্যতা।

   ব্যয়: শিডিউলিং নিজেই সিপিইউ সময় খরচ করে, এবং প্রতিটি preemption এ context switch হয়, যাতে রেজিস্টার সংরক্ষণ ও পুনরুদ্ধার এবং ক্যাশে ও TLB নষ্ট হওয়ার ক্ষতি হয়। তাই ভালো অ্যালগরিদম হলো সেটি, যা পরিবর্তনের সুফল ও খরচের মধ্যে ভারসাম্য রাখে।

## Windows & System Administration (4)

1. **How to check the IP address in the Windows Command Prompt?** *[BARI Assistant Maintenance Engineer 15.11.2025 compact it 1451 (ET: N/A)]*


   Answer: To check the IP address in the Windows Command Prompt:

   ```
   ipconfig
   ```

   This prints the IP address, the subnet mask and the default gateway of every network adapter.

   More detailed forms:
   ```
   ipconfig /all              show everything, including the MAC address, DHCP and DNS servers
   ipconfig /release          release the current DHCP lease
   ipconfig /renew            obtain a new address from the DHCP server
   ipconfig /flushdns         clear the DNS resolver cache
   ipconfig /displaydns       show the contents of the DNS cache
   ```

   Sample output:
   ```
   C:\> ipconfig

   Windows IP Configuration

   Ethernet adapter Ethernet:

      Connection-specific DNS Suffix  . : local
      IPv4 Address. . . . . . . . . . . : 192.168.1.105
      Subnet Mask . . . . . . . . . . . : 255.255.255.0
      Default Gateway . . . . . . . . . : 192.168.1.1
   ```

   Other commands that give the same or related information:
   ```
   netsh interface ip show config       full configuration of every interface
   getmac                               the MAC address of each adapter
   nslookup myip.opendns.com resolver1.opendns.com    the public IP address
   ping hostname                        test connectivity
   tracert hostname                     show the route to a destination
   netstat -an                          all connections and listening ports
   arp -a                               the ARP table
   ```

   In PowerShell:
   ```
   Get-NetIPAddress
   Get-NetIPConfiguration
   (Invoke-WebRequest ifconfig.me/ip).Content.Trim()     the public IP address
   ```

   The Linux equivalents, for comparison: ip addr show or the older ifconfig, and hostname -I for the addresses alone.

   Distinction worth stating: ipconfig shows the private address assigned within the local network, typically in the ranges 192.168.x.x, 10.x.x.x or 172.16-31.x.x. The public address seen by the internet is the one on the router's WAN side, which is why many devices at home appear to the outside world as a single address; this is network address translation.
2. **Assume that an office has three departments and each department has 50 to 70 employees who are using computers with Windows operating systems. The office space is designed in such a way that an employee can use any computer within a department. Once an employee logs in from a computer, he/she will get access to his files from the server. Let you are planning for network and server setup for this company.**
   * **(a) What is Active Directory? Do you need an Active Directory for such an office? If yes, briefly explain its use under this circumstance.** *[Combined Bank Senior Officer (IT) 17.05.2024 compact it 323 (ET: BIBM)]*


   Answer: The requirement is that any employee may sit at any computer within their department, log in, and immediately have access to their own files held on a server. This is the classic case for a centrally managed Windows domain.

   Recommended design:

   1. Active Directory Domain Services (AD DS)
   - Install Windows Server and promote it to a domain controller, creating a domain such as office.local.
   - Every user is given one domain account, and every computer is joined to the domain. The user then logs in with the same account at any machine, and authentication is performed by the domain controller rather than by the local machine. This is exactly what the requirement asks for.
   - Create three Organisational Units, one per department, so that policy can be applied per department.
   - Create security groups per department, and grant file permissions to groups rather than to individual users, so that a transfer between departments requires only a change of group membership.

   2. Roaming profiles and folder redirection
   - A roaming profile stores the user's desktop, settings and documents on the server, and they follow the user to whichever machine they log in from.
   - Folder redirection is the better modern practice: redirect Documents, Desktop and Favourites to a network share, so that only the files actually opened are transferred, instead of copying an entire profile at every login. This makes logins fast, which matters when 150 to 210 users log in each morning.
   - Set disk quotas so that no single user can fill the volume.

   3. File server and shares
   - Create a home directory share, for example \\FS01\Users\%username%, mapped automatically to a drive letter by a group policy or a login script. NTFS permissions give each user full control of their own folder and no access to others'.
   - Create a departmental share for each department, accessible only to that department's group.
   - Create an organisation-wide read-only share for common forms and notices.
   - Use NTFS permissions for the real security and keep share permissions simple, because the effective permission is the more restrictive of the two.

   4. Servers required
   - Two domain controllers, so that a failure of one does not prevent anyone from logging in. Each also runs DNS, which Active Directory requires, and one runs DHCP with a reservation scope per department.
   - One file server, with RAID storage.
   - Optionally a print server, and a WSUS server for controlled Windows updates.
   - Virtualise these roles on two physical hosts with Hyper-V, so that hardware is used efficiently and a host failure can be survived.

   5. Storage
   - RAID 10 for the file volume if performance matters, or RAID 6 for capacity, with a hot spare in either case.
   - Shadow Copies (Volume Shadow Copy Service) enabled on the share, so that users can restore a previous version of a file themselves without troubling the administrator.

   6. Network
   - A managed switch in each department, uplinked to a core switch.
   - Separate VLANs per department, with routing between them controlled by access lists, so that a problem in one department does not affect the others and traffic is contained.
   - Gigabit to the desktop and, if possible, a faster uplink to the server, since 150 to 210 users share it.
   - A firewall between the office network and the internet.

   7. Group Policy
   - Map the home drive and departmental drive automatically at login.
   - Deploy printers by department.
   - Enforce a password policy, screen lock, and restrictions on installing software.
   - Deploy antivirus and configure Windows Update.

   8. Backup and recovery
   - Daily incremental and weekly full backups of the file server and the system state of the domain controllers.
   - Follow the 3-2-1 rule: three copies, on two kinds of media, with one copy off site.
   - Test a restore periodically; a backup that has never been restored cannot be relied on.
   - Note that RAID is not a backup; it protects against a disk failure only, not against deletion, corruption or ransomware.

   9. Sizing
   - Users: 3 departments x 50 to 70 = 150 to 210 users.
   - File server storage: allowing 20 GB per user gives 3 to 4.2 TB of user data, so provision about 8 TB usable after RAID, to allow for growth and for shadow copies.
   - Domain controller: modest, since authentication is light.
   - Plan for peak load at the start of the working day, when nearly all users log in within a few minutes.

   10. Security
   - Least privilege: users are ordinary users, not local administrators.
   - Account lockout after repeated failed logins.
   - Auditing of file access on sensitive shares.
   - Encryption of backups and of any laptop, using BitLocker.

   Summary of why this design meets the requirement: because authentication is centralised in Active Directory and the user's files live on the server rather than on any particular workstation, an employee can sit at any computer in the department, log in with the same credentials, and see exactly the same files. Replacing a failed workstation then requires no data recovery at all, since nothing of value is stored on it.
3. **Describe the booting process in windows system.** *[Pubali Bank Limited Hardware Engineer 18.03.2023 compact it 565 (ET: N/A)]*


   Answer: The booting process is the sequence of steps by which a computer starts from power-on to a usable operating system. The Windows sequence is described below in both the modern UEFI and the older BIOS form.

   Step 1 - Power-on and POST
   - When power is applied, the power supply sends a Power Good signal and the processor begins executing firmware code from a fixed address.
   - The firmware runs the Power-On Self Test (POST), which checks the processor, memory, keyboard, display adapter and other essential hardware. A failure at this stage is reported by beep codes or by a diagnostic display, because the video system may not yet be available.

   Step 2 - Firmware initialisation and boot device selection
   - BIOS systems: the BIOS reads the boot order from CMOS, loads the first 512-byte sector of the chosen disk, the Master Boot Record, into memory and executes it.
   - UEFI systems: the firmware reads the boot entries from NVRAM, mounts the EFI System Partition, which is a small FAT32 partition, and loads the boot manager file directly, without needing a Master Boot Record. UEFI also supports Secure Boot, which verifies the digital signature of the boot loader before running it.

   Step 3 - Boot loader
   - BIOS path: the MBR code locates the active partition and loads its boot sector, which loads bootmgr.
   - UEFI path: the firmware loads bootmgfw.efi from the EFI System Partition.
   - The Windows Boot Manager reads the Boot Configuration Data store, which lists the installed operating systems. If more than one is present, it displays the menu.

   Step 4 - Windows Boot Loader
   - The boot manager launches winload.exe (or winload.efi on UEFI).
   - This loads the kernel, ntoskrnl.exe, the hardware abstraction layer hal.dll, and the SYSTEM registry hive.
   - It also loads the boot-class drivers, that is the minimum drivers needed to reach the disk, and their order is taken from the registry.
   - If the machine is resuming from hibernation, winresume.exe restores the saved memory image instead, and the remaining steps are skipped.

   Step 5 - Kernel initialisation
   - The kernel initialises the memory manager, the process and thread manager, the object manager, the security reference monitor and the input-output manager.
   - The hardware abstraction layer isolates the rest of the kernel from the particular hardware platform.
   - The Plug and Play manager detects devices and loads the rest of the drivers.
   - The kernel then starts the Session Manager, smss.exe.

   Step 6 - Session Manager and subsystems
   - smss.exe creates the paging file, completes the registry initialisation and starts the environment subsystems.
   - It launches csrss.exe, the Client-Server Runtime Subsystem, and wininit.exe for session 0, the system session.
   - wininit.exe starts services.exe, the Service Control Manager, which starts all the services marked automatic, and lsass.exe, the Local Security Authority, which handles authentication.

   Step 7 - Logon
   - winlogon.exe presents the logon screen through LogonUI.
   - Credentials are verified by lsass.exe, against the local SAM database or, on a domain-joined machine, against a domain controller.
   - On success, the user's registry hive and profile are loaded and the shell, explorer.exe, is started.
   - Startup programs listed in the registry and in the Startup folder are launched, and the desktop appears.

   Diagram of the sequence:
   ```
   Power on
      |
      v
   POST (firmware self-test)
      |
      v
   BIOS/UEFI selects the boot device
      |
      v
   MBR + bootmgr        or       bootmgfw.efi from the EFI System Partition
      |
      v
   Boot Configuration Data read; menu shown if needed
      |
      v
   winload.exe loads ntoskrnl.exe, hal.dll, SYSTEM hive, boot drivers
      |
      v
   Kernel initialises; Plug and Play loads remaining drivers
      |
      v
   smss.exe -> csrss.exe, wininit.exe -> services.exe, lsass.exe
      |
      v
   winlogon.exe -> logon -> explorer.exe -> desktop ready
   ```

   Two useful distinctions:
   - Cold boot means starting from a powered-off state; warm boot means restarting an already running machine, which skips part of the POST.
   - Fast Startup in Windows 10 and 11 is a hybrid: on shutdown the kernel session is hibernated to disk, so the next start restores it instead of initialising it, which is much faster but means that a shutdown does not fully reset the system. A restart does.

   Troubleshooting points worth mentioning: Safe Mode loads only the minimum drivers; Last Known Good Configuration restores the previous working registry control set; and bootrec /fixmbr, /fixboot and /rebuildbcd repair a damaged boot configuration from the recovery environment.
4. **১৯. বর্তমানে উইন্ডোজ অপারেটিং সিস্টেম এর কত তম ভার্সন বাজারজাত করা হয়েছে?** *[BPSC Ministry of Women and Children Affairs Assistant Programmer (CSE) 2021 compact it 942 (ET: N/A)]*


   Answer: মাইক্রোসফট উইন্ডোজ অপারেটিং সিস্টেমের বর্তমান সর্বশেষ প্রধান সংস্করণ Windows 11, যা ২০২১ সালের ৫ অক্টোবর বাজারে আসে।

   প্রধান সংস্করণগুলোর ধারাবাহিকতা:

   | সংস্করণ | প্রকাশের বছর |
   |---|---|
   | Windows 1.0 | ১৯৮৫ |
   | Windows 3.1 | ১৯৯২ |
   | Windows 95 | ১৯৯৫ |
   | Windows 98 | ১৯৯৮ |
   | Windows 2000 | ২০০০ |
   | Windows XP | ২০০১ |
   | Windows Vista | ২০০৭ |
   | Windows 7 | ২০০৯ |
   | Windows 8 | ২০১২ |
   | Windows 8.1 | ২০১৩ |
   | Windows 10 | ২০১৫ |
   | Windows 11 | ২০২১ |

   Windows 11 এর উল্লেখযোগ্য বৈশিষ্ট্য:
   - কেন্দ্রে সরানো স্টার্ট মেনু ও টাস্কবার এবং সম্পূর্ণ নতুন নকশা।
   - Snap Layouts ও Snap Groups, যা একাধিক জানালা সাজাতে সাহায্য করে।
   - Microsoft Teams সরাসরি অন্তর্ভুক্ত।
   - Android অ্যাপ চালানোর সুবিধা (নির্দিষ্ট অঞ্চলে)।
   - Windows Subsystem for Linux এর উন্নত সংস্করণ।
   - DirectStorage ও Auto HDR এর মাধ্যমে গেমিংয়ে উন্নতি।
   - Copilot নামে কৃত্রিম বুদ্ধিমত্তাভিত্তিক সহায়ক।

   হার্ডওয়্যার শর্ত: Windows 11 চালাতে TPM 2.0 চিপ, Secure Boot সমর্থন, ৬৪ বিট প্রসেসর, ৪ গিগাবাইট RAM ও ৬৪ গিগাবাইট স্টোরেজ প্রয়োজন। TPM 2.0 এর বাধ্যবাধকতা বহু পুরোনো কম্পিউটারকে অযোগ্য করে দিয়েছে, যা এই সংস্করণের সবচেয়ে আলোচিত দিক।

   উল্লেখযোগ্য: মাইক্রোসফট Windows 10 এর জন্য মূলধারার সহায়তা ২০২৫ সালের ১৪ অক্টোবর পর্যন্ত ঘোষণা করেছিল, তাই এখন Windows 11 ই সমর্থিত সর্বশেষ সংস্করণ। সার্ভার শ্রেণিতে সর্বশেষ সংস্করণ Windows Server 2022। সংস্করণ পরিবর্তনশীল বিষয়, তাই পরীক্ষার সময় সর্বশেষ তথ্য যাচাই করে নেওয়া উচিত। <!-- verify -->

## Process Synchronization & Concurrency (4)

1. Two independent applications running concurrently attempt to update the same file located at a same file location. Both applications may read and modify the file at nearly the same time, creating a possibility of race conditions, lost updates, or inconsistent data. What type of consistency problem can occur in this situation, and which synchronization technique(s) should be used to ensure that only one application can safely update the file at a time? Explain the mechanism and justify the most appropriate solution. [BSCCPL AME 21-08-2026 (BUET)]


   Answer: Two independent applications reading and writing the same file at nearly the same time create a classic concurrency problem.

   The consistency problems that can occur:

   - Race condition: the final state of the file depends on the exact interleaving of the two applications' operations, which is not controlled by either of them and varies from run to run. The same sequence of user actions can produce different results.

   - Lost update: application A reads the file, application B reads the same file, A writes its modified version, and then B writes its own version, which was computed from the value it read before A's change. A's update is silently overwritten and lost. This is the most common and most damaging form.

   - Dirty read (reading uncommitted data): B reads the file while A is half-way through writing it, so B sees a file that is internally inconsistent, for example with a header updated but the body not yet.

   - Inconsistent or partial write: if the write is not atomic and the process is interrupted, the file is left corrupted and may not be readable at all.

   - Non-repeatable read: A reads a value, and later in the same operation reads it again and finds it changed by B in the meantime, so A's own computation is based on two different versions of the truth.

   Worked illustration of a lost update, on a counter stored in a file:
   ```
   Initial value in file: 100

   Time   Application A               Application B
   t1     read file -> 100
   t2                                 read file -> 100
   t3     compute 100 + 50 = 150
   t4                                 compute 100 + 30 = 130
   t5     write 150 to file
   t6                                 write 130 to file

   Final value: 130.  Correct value: 180.  A's update of 50 has been lost.
   ```

   Synchronisation techniques that solve it:

   1. File locking, which is the most appropriate solution here.
   - An advisory or mandatory lock is taken on the file before it is read or written and released afterwards, so that only one application can be inside the critical section at a time.
   - Two kinds of lock are used: a shared (read) lock, which several readers may hold at once, and an exclusive (write) lock, which only one holder may have and which excludes all readers. This is the readers-writer lock, and it allows concurrent reading while still serialising writing.
   - On Linux the system calls are flock() and fcntl(); on Windows it is LockFileEx(). In Java, FileChannel.lock() provides the same.
   - Example:
   ```c
   int fd = open("data.txt", O_RDWR);
   flock(fd, LOCK_EX);        /* blocks until the exclusive lock is granted */
   /* critical section: read, modify, write */
   flock(fd, LOCK_UN);        /* release */
   close(fd);
   ```

   2. Mutex or binary semaphore, if the two applications are threads or processes on the same machine that can share a named synchronisation object.
   - wait() or lock() before the critical section, signal() or unlock() after it.
   - This guarantees mutual exclusion, but it works only among parties that agree to use the same mutex.

   3. Atomic write through rename, which is the standard robust technique for files.
   - Write the new content to a temporary file in the same directory, flush it to disk, then rename it over the original. On POSIX systems rename() within a file system is atomic, so a reader sees either the whole old file or the whole new file, never a half-written one.
   ```bash
   write to data.txt.tmp
   fsync(data.txt.tmp)
   rename("data.txt.tmp", "data.txt")   # atomic
   ```

   4. Optimistic concurrency control with a version number or timestamp.
   - Each writer records the version it read. Before writing, it checks that the version on disk is unchanged. If it has changed, the write is rejected and the operation is retried on the new data. This detects the lost update rather than preventing it, and is efficient when conflicts are rare.

   5. Use a database instead of a file, when the data is genuinely shared.
   - A database management system already provides transactions with the ACID properties, row-level locking, isolation levels and automatic deadlock detection and rollback. Re-implementing all of that on top of a flat file is difficult and rarely done correctly.

   Justification of the most appropriate solution:

   For two independent applications sharing one file, exclusive file locking combined with the write-to-temporary-and-rename pattern is the right answer.

   - File locking is the only mechanism that both applications can use without being redesigned as threads of one program, since a lock on the file is visible to any process that opens it.
   - An exclusive lock held across the whole read-modify-write sequence, not merely around the write, is what prevents the lost update. Locking only the write would not help, because both applications would still have read the same stale value.
   - A readers-writer lock is preferable to a plain mutex when reads are frequent, because it allows several readers to proceed concurrently and only serialises writers.
   - The atomic rename protects against the second failure mode, a crash or interruption in the middle of writing, which locking alone does not address.
   - The three requirements of any correct solution to the critical section problem are satisfied: mutual exclusion, because only one writer holds the exclusive lock; progress, because the lock is released as soon as the section ends; and bounded waiting, because the operating system queues waiters in order.

   If the data is more than a simple file, for example if several records must be updated together, the correct answer is to move it into a database and use a transaction, so that the update is atomic, consistent, isolated and durable.
2. **What is Semaphore? How would you improve performance when using semaphores?** *[WZPGCL Assistant Engineer (CSE) 27.05.2023 compact it 504 (ET: N/A)]*


   Answer: A semaphore is an integer variable, shared among processes or threads, that is used for synchronisation and is accessed only through two atomic operations, traditionally called wait (P, or down) and signal (V, or up). It was introduced by Edsger Dijkstra in 1965.

   The two operations:
   ```
   wait(S):                    signal(S):
       while (S <= 0);             S = S + 1;
       S = S - 1;
   ```
   Both must be executed atomically, that is without interruption, which the operating system guarantees by disabling interrupts briefly or by using a hardware instruction such as test-and-set or compare-and-swap.

   Types:
   - Binary semaphore, whose value is 0 or 1. It behaves like a lock and provides mutual exclusion. It is close to a mutex, though a mutex additionally has an owner and can only be released by the thread that took it.
   - Counting semaphore, whose value can be any non-negative integer. It controls access to a resource of which there are several identical instances, for example five printers, and is initialised to that number.

   Use for mutual exclusion:
   ```c
   semaphore mutex = 1;

   /* each process */
   wait(mutex);
       /* critical section */
   signal(mutex);
   ```

   Use for the producer-consumer problem with a bounded buffer:
   ```c
   semaphore empty = N;      /* number of free slots */
   semaphore full  = 0;      /* number of filled slots */
   semaphore mutex = 1;      /* protects the buffer */

   Producer:                        Consumer:
     wait(empty);                     wait(full);
     wait(mutex);                     wait(mutex);
       add item to buffer;              remove item from buffer;
     signal(mutex);                   signal(mutex);
     signal(full);                    signal(empty);
   ```
   Note the order: the counting semaphore must be taken before the mutex. Reversing them causes deadlock, because a producer could hold the mutex while waiting for a free slot that only a consumer, which needs the mutex, could create.

   How to improve performance when using semaphores:

   - Avoid busy waiting. The naive implementation given above spins in a while loop, wasting the whole time quantum. The correct implementation blocks the process instead: on wait, if the value is negative, the process is placed on a waiting queue associated with the semaphore and its state is changed to waiting; on signal, one waiting process is moved back to the ready queue. This turns a spinning loop into a scheduling operation.

   - Keep the critical section as short as possible. Only the code that genuinely touches the shared data should be inside it. Reading a file, formatting output or allocating memory should be done outside the lock. The length of the critical section is the single largest determinant of contention.

   - Use fine-grained rather than coarse-grained locking. One semaphore per record, or per bucket of a hash table, allows far more concurrency than one semaphore for the whole structure. The cost is more complex code and a greater risk of deadlock, so a balance is needed.

   - Use a readers-writer lock where reads dominate. Many readers may hold the lock at once, and only writers are serialised. For a data structure that is read a thousand times for every write, this is an enormous improvement over a plain mutex.

   - Prefer a spinlock only for very short critical sections on a multiprocessor. If the expected wait is shorter than the cost of two context switches, spinning is cheaper than blocking. An adaptive mutex, which spins briefly and then blocks, gives the best of both.

   - Reduce the number of lock acquisitions. Batch several operations into one critical section instead of taking and releasing the lock repeatedly in a loop.

   - Avoid holding a lock across a blocking operation. Never perform disk or network input-output while holding a semaphore, because every other process is then blocked for milliseconds.

   - Impose a strict lock ordering when several semaphores are used, so that circular wait, and therefore deadlock, is impossible.

   - Consider lock-free techniques for simple shared variables. An atomic increment with compare-and-swap avoids the semaphore entirely for a counter.

   - Use per-thread or per-core data where possible, and combine the results at the end, so that no lock is needed at all for most of the work. This is the most effective optimisation of all.

   - Avoid the thundering herd: signalling all waiters when only one can proceed wastes work. Wake exactly one where the semantics allow it.

   - Beware of priority inversion, in which a high-priority process waits on a semaphore held by a low-priority one that has itself been preempted. The remedy is priority inheritance, in which the holder temporarily takes the priority of the highest waiter.

   Problems that misuse of semaphores causes: deadlock, if two processes take two semaphores in opposite orders; starvation, if the waiting queue is LIFO rather than FIFO; and violation of mutual exclusion, if a programmer forgets a wait or a signal, which is precisely why higher-level constructs such as monitors and the synchronized keyword were introduced.
3. **(গ) Process Synchronization এর ক্ষেত্রে Race condition ব্যাখ্যা করুন।** *[17th NTRCA Lecturer (ICT) (ICT): 2023 compact it 624 (ET: N/A)]*


   Answer: Race condition (রেস কন্ডিশন) হলো এমন একটি পরিস্থিতি, যেখানে একাধিক প্রসেস বা থ্রেড একই সঙ্গে একই ভাগ করা তথ্য পড়তে ও লিখতে চায়, এবং চূড়ান্ত ফলাফল নির্ভর করে তারা ঠিক কোন ক্রমে চলেছে তার ওপর। এই ক্রম অপারেটিং সিস্টেমের শিডিউলার নির্ধারণ করে, প্রোগ্রাম নয়; তাই একই প্রোগ্রাম একই ইনপুট নিয়ে বিভিন্ন বার চালালে বিভিন্ন ফল দিতে পারে।

   কেন ঘটে: উচ্চস্তরের ভাষায় যে বিবৃতিটি একটিমাত্র লাইন মনে হয়, যন্ত্রস্তরে তা একাধিক নির্দেশে ভাগ হয়ে যায়, এবং যেকোনো দুই নির্দেশের মাঝখানে প্রসেসটিকে থামিয়ে দেওয়া যেতে পারে।

   উদাহরণ: counter++ বিবৃতিটি যন্ত্রস্তরে তিনটি ধাপে হয়:
   ```
   register = counter      ; মেমোরি থেকে পড়া
   register = register + 1 ; বৃদ্ধি করা
   counter = register      ; মেমোরিতে ফেরত লেখা
   ```

   দুইটি থ্রেড T1 ও T2 একই counter (প্রাথমিক মান ৫) বাড়াতে চাইলে:

   | সময় | T1 | T2 | counter এর মান |
   |---|---|---|---|
   | t1 | register1 = counter (৫ পড়ল) | | ৫ |
   | t2 | | register2 = counter (৫ পড়ল) | ৫ |
   | t3 | register1 = ৫ + ১ = ৬ | | ৫ |
   | t4 | | register2 = ৫ + ১ = ৬ | ৫ |
   | t5 | counter = ৬ | | ৬ |
   | t6 | | counter = ৬ | ৬ |

   দুইবার বাড়ানোর পর মান হওয়ার কথা ছিল ৭, কিন্তু হলো ৬। একটি বৃদ্ধি হারিয়ে গেল। একেই বলে lost update, যা race condition এর সবচেয়ে সাধারণ রূপ।

   বাস্তব উদাহরণ: একই ব্যাংক হিসাব থেকে দুটি এটিএম থেকে একই মুহূর্তে টাকা তোলা হলে, উভয় লেনদেন একই প্রারম্ভিক ব্যালেন্স পড়ে ফেলতে পারে এবং ফলে হিসাবে টাকার চেয়ে বেশি তোলা সম্ভব হয়ে যায়।

   বৈশিষ্ট্য:
   - ফলাফল অনির্ধারিত ও অপুনরাবৃত্তিযোগ্য (non-deterministic), তাই ডিবাগ করা অত্যন্ত কঠিন।
   - বেশির ভাগ সময় ঠিকঠাক চলে, কেবল নির্দিষ্ট সময়-সমাপতনে ভুল হয়। এ ধরনের ত্রুটিকে Heisenbug বলা হয়, কারণ পর্যবেক্ষণ করতে গেলেই সময়ের বিন্যাস বদলে যায় এবং ত্রুটি অদৃশ্য হয়ে যায়।
   - বহু-কোর প্রসেসরে প্রকৃত সমান্তরাল নির্বাহের কারণে এর সম্ভাবনা আরও বেশি।

   সমাধান: যে কোড অংশটি ভাগ করা তথ্য ব্যবহার করে, তাকে বলা হয় critical section। নিশ্চিত করতে হবে যে একই সময়ে কেবল একটি প্রসেস সেখানে থাকতে পারে, অর্থাৎ mutual exclusion প্রতিষ্ঠা করতে হবে।

   - Mutex বা binary semaphore:
   ```c
   wait(mutex);
       counter++;        /* critical section */
   signal(mutex);
   ```
   - Monitor: জাভার synchronized কীওয়ার্ড, যা স্বয়ংক্রিয়ভাবে লক নেয় ও ছাড়ে।
   - Atomic operation: হার্ডওয়্যারের test-and-set বা compare-and-swap নির্দেশ, যা পুরো পড়া-বাড়ানো-লেখা কাজটি অবিভাজ্যভাবে সম্পন্ন করে। জাভায় AtomicInteger এবং C++ এ std::atomic।
   - Peterson's solution ও Dekker's algorithm: কেবল সফটওয়্যার দিয়ে দুই প্রসেসের জন্য সমাধান, তাত্ত্বিকভাবে গুরুত্বপূর্ণ।
   - ভাগ করা তথ্য এড়িয়ে চলা: প্রতিটি থ্রেডকে নিজস্ব কপি দিয়ে শেষে ফলাফল একত্র করা। এটিই সবচেয়ে নিরাপদ পদ্ধতি।

   সঠিক সমাধানের তিনটি শর্ত:
   - Mutual Exclusion: একসঙ্গে একটির বেশি প্রসেস critical section এ থাকতে পারবে না।
   - Progress: কোনো প্রসেস critical section এ না থাকলে, প্রবেশে ইচ্ছুক প্রসেসগুলোর মধ্য থেকে সিদ্ধান্ত অনির্দিষ্টকাল ঝুলিয়ে রাখা যাবে না।
   - Bounded Waiting: একটি প্রসেস অনুরোধ করার পর অন্য প্রসেসগুলো কতবার প্রবেশ করতে পারবে তার একটি নির্দিষ্ট সীমা থাকতে হবে, যাতে starvation না হয়।
4. **(ক) Critical Section Problem কী? ইহা কীভাবে সমাধান করা যায়?** *[Software Assistant Programmer 13.10.2022 compact it 710 (ET: N/A)]*


   Answer: Critical Section Problem কী:

   Critical section হলো একটি প্রোগ্রামের সেই অংশ, যেখানে প্রসেস বা থ্রেডটি ভাগ করা সম্পদ ব্যবহার করে — যেমন ভাগ করা ভেরিয়েবল, ফাইল, ডেটাবেজের রেকর্ড বা কোনো যন্ত্র। Critical section problem হলো এমন একটি প্রোটোকল নকশা করার সমস্যা, যাতে নিশ্চিত করা যায় যে একই সময়ে একটির বেশি প্রসেস তার critical section এ থাকতে পারবে না।

   প্রতিটি প্রসেসের সাধারণ কাঠামো:
   ```c
   do {
       entry section;        /* অনুমতি চাওয়া */
           critical section; /* ভাগ করা সম্পদ ব্যবহার */
       exit section;         /* অনুমতি ছেড়ে দেওয়া */
           remainder section;/* বাকি কাজ */
   } while (true);
   ```

   সমস্যাটি কেন গুরুত্বপূর্ণ: সুরক্ষা না থাকলে race condition ঘটে। যেমন counter++ যন্ত্রস্তরে তিনটি ধাপে হয় — পড়া, বাড়ানো, লেখা। দুটি থ্রেড একই সঙ্গে ৫ পড়ে, উভয়েই ৬ লিখলে দুইবার বাড়ানোর পরও মান হয় ৬, ৭ নয়। একটি বৃদ্ধি হারিয়ে যায়।

   একটি সঠিক সমাধানের তিনটি আবশ্যিক শর্ত:

   - Mutual Exclusion (পারস্পরিক বর্জন): কোনো প্রসেস তার critical section এ থাকলে অন্য কোনো প্রসেস তার critical section এ ঢুকতে পারবে না।

   - Progress (অগ্রগতি): কোনো প্রসেস critical section এ না থাকলে এবং কিছু প্রসেস ঢুকতে চাইলে, কে ঢুকবে সেই সিদ্ধান্ত কেবল ইচ্ছুক প্রসেসগুলোর মধ্যেই হবে এবং তা অনির্দিষ্টকাল স্থগিত রাখা যাবে না। অর্থাৎ যে প্রসেস ঢুকতেই চায় না, সে অন্যকে আটকাতে পারবে না।

   - Bounded Waiting (সীমিত অপেক্ষা): একটি প্রসেস অনুরোধ করার পর অন্য প্রসেসগুলো সর্বোচ্চ কতবার critical section এ ঢুকতে পারবে, তার একটি নির্দিষ্ট সীমা থাকতে হবে। এটি starvation প্রতিরোধ করে।

   সমাধানের উপায়সমূহ:

   ১. সফটওয়্যারভিত্তিক সমাধান:
   - Peterson's Solution: দুটি প্রসেসের জন্য, দুটি ভাগ করা ভেরিয়েবল flag[2] ও turn ব্যবহার করে। এটি তিনটি শর্তই পূরণ করে এবং কেবল সফটওয়্যার দিয়ে কাজ করে।
   ```c
   /* প্রসেস i এর জন্য */
   flag[i] = true;
   turn = j;
   while (flag[j] && turn == j);   /* অপেক্ষা */
       critical section;
   flag[i] = false;
       remainder section;
   ```
   - Dekker's Algorithm: প্রথম সঠিক সফটওয়্যার সমাধান।
   - সীমাবদ্ধতা: আধুনিক প্রসেসরে নির্দেশ পুনর্বিন্যাস (instruction reordering) হয় বলে এগুলো memory barrier ছাড়া নির্ভরযোগ্য নয়, এবং এতে busy waiting হয়।

   ২. হার্ডওয়্যারভিত্তিক সমাধান:
   - Interrupt নিষ্ক্রিয় করা: critical section চলাকালে ইন্টারাপ্ট বন্ধ রাখা। একক প্রসেসরে কাজ করে, কিন্তু বহু-প্রসেসরে নয় এবং এটি বিপজ্জনক।
   - Test-and-Set নির্দেশ: একটি অবিভাজ্য নির্দেশ, যা একই সঙ্গে মান পড়ে ও সেট করে।
   ```c
   while (TestAndSet(&lock));     /* লক না পাওয়া পর্যন্ত অপেক্ষা */
       critical section;
   lock = false;
   ```
   - Compare-and-Swap: আধুনিক প্রসেসরের মূল সিঙ্ক্রোনাইজেশন নির্দেশ, যার ওপর প্রায় সব উচ্চস্তরের লক নির্মিত।

   ৩. অপারেটিং সিস্টেম ও ভাষাভিত্তিক সমাধান:
   - Mutex lock: acquire() ও release() দিয়ে সরল পারস্পরিক বর্জন।
   - Semaphore: wait() ও signal() দিয়ে; binary semaphore মিউটেক্সের মতো, counting semaphore একাধিক ইনস্ট্যান্সের সম্পদের জন্য।
   ```c
   semaphore mutex = 1;
   wait(mutex);
       critical section;
   signal(mutex);
   ```
   - Monitor: একটি উচ্চস্তরের নির্মাণ, যেখানে ভাগ করা তথ্য ও তার ওপর কাজ করা পদ্ধতিগুলো একসঙ্গে আবদ্ধ থাকে এবং একসঙ্গে কেবল একটি প্রসেস ভেতরে থাকতে পারে। জাভার synchronized কীওয়ার্ড এরই বাস্তবায়ন।
   ```java
   public synchronized void increment() {
       counter++;
   }
   ```
   - Condition variable: wait() ও signal() দিয়ে নির্দিষ্ট শর্ত পূরণের অপেক্ষা করা।

   ৪. আরও উন্নত পদ্ধতি:
   - Readers-writer lock: বহু পাঠক একসঙ্গে ঢুকতে পারে, কিন্তু লেখক একা।
   - Atomic variable: গণনার মতো সরল কাজে লক ছাড়াই কাজ চালানো, যেমন জাভার AtomicInteger।
   - ভাগ করা তথ্য সম্পূর্ণ এড়িয়ে চলা: প্রতিটি থ্রেডকে নিজস্ব কপি দেওয়া, যা সবচেয়ে নিরাপদ ও দ্রুততম পদ্ধতি।

   কার্যকারিতা বাড়ানোর নিয়ম: critical section যতটা সম্ভব ছোট রাখা, লক ধরে রেখে ইনপুট-আউটপুট না করা, একাধিক লক ব্যবহার করলে সবসময় একই ক্রমে নেওয়া (যাতে deadlock না হয়), এবং busy waiting এর বদলে ব্লকিং ব্যবহার করা।

## File Systems & Disk Management (4)

1. **NTFS stands for __________?** *[BARI Assistant Maintenance Engineer 10.05.2024 compact it 1462 (ET: N/A)]*


   Answer: NTFS stands for New Technology File System.

   It is the standard file system of the Windows NT family, which includes Windows 2000, XP, Vista, 7, 8, 10 and 11, and all versions of Windows Server. It was introduced in 1993 with Windows NT 3.1, replacing FAT.

   Main features:
   - Journaling: every change to the file system metadata is recorded in a log before it is applied, so that an interrupted operation can be completed or undone after a crash. This is why NTFS recovers quickly and rarely loses the directory structure.
   - Security: access control lists give per-user and per-group permissions on every file and folder, with inheritance from parent folders. FAT has no permissions at all.
   - Large volumes and files: a maximum volume size of 256 TB and a maximum file size limited in practice by the volume, against FAT32's limit of 4 GB per file and 32 GB per volume as formatted by Windows.
   - Compression, transparently per file or per folder.
   - Encryption through the Encrypting File System (EFS).
   - Disk quotas per user.
   - Sparse files, so that a large mostly empty file occupies little space.
   - Hard links, symbolic links and junction points.
   - Shadow copies, allowing previous versions of a file to be restored.
   - Long file names of up to 255 characters, in Unicode.
   - Cluster sizes from 512 bytes to 64 KB, chosen at format time.
   - Bad cluster remapping, done automatically.

   Comparison with the other Windows file systems:

   | Point | FAT32 | NTFS | exFAT |
   |---|---|---|---|
   | Maximum file size | 4 GB | Practically unlimited | Practically unlimited |
   | Maximum volume | 32 GB as formatted by Windows | 256 TB | 128 PB |
   | Journaling | No | Yes | No |
   | Permissions | No | Yes | No |
   | Compression and encryption | No | Yes | No |
   | Compatibility | Universal | Windows; read-only on macOS without extra software | Wide, and designed for flash media |
   | Best used for | Small removable media, boot partitions on old systems | Windows system and data drives | Large USB drives and memory cards shared between systems |

   Practical guidance: use NTFS for internal Windows drives, exFAT for large removable media that must work on both Windows and macOS, and FAT32 only where compatibility with very old devices is required.

   Comparable file systems on other operating systems: ext4, XFS and Btrfs on Linux, and APFS on macOS.
2. **(খ) Unix file system এর প্রকারভেদ বর্ণনা করুন।** *[17th NTRCA Lecturer (ICT) (CSE): 2023 compact it 610 (ET: N/A)]*


   Answer: ইউনিক্স ফাইল সিস্টেমে সবকিছুকেই ফাইল হিসেবে দেখা হয়, এমনকি যন্ত্রপাতি ও প্রসেসকেও। ফাইলগুলো প্রধানত সাতটি ধরনের।

   ১. সাধারণ ফাইল (Regular / Ordinary File):
   - সবচেয়ে সাধারণ ধরন। এতে টেক্সট, প্রোগ্রাম, ছবি, ভিডিও বা যেকোনো তথ্য থাকতে পারে।
   - ls -l এ প্রথম অক্ষর: -
   - উদাহরণ: report.txt, program.c, photo.jpg

   ২. ডিরেক্টরি ফাইল (Directory):
   - অন্যান্য ফাইল ও ডিরেক্টরির নাম এবং তাদের inode নম্বরের তালিকা ধারণ করে। এটি নিজেও একটি ফাইল।
   - ls -l এ প্রথম অক্ষর: d
   - উদাহরণ: /home, /etc, /usr

   ৩. ক্যারেক্টার ডিভাইস ফাইল (Character Special File):
   - এমন যন্ত্রকে প্রতিনিধিত্ব করে যা একটি একটি করে অক্ষর আদান-প্রদান করে, যেমন কীবোর্ড, মাউস, টার্মিনাল ও প্রিন্টার।
   - ls -l এ প্রথম অক্ষর: c
   - উদাহরণ: /dev/tty, /dev/null, /dev/random

   ৪. ব্লক ডিভাইস ফাইল (Block Special File):
   - এমন যন্ত্রকে প্রতিনিধিত্ব করে যা নির্দিষ্ট আকারের ব্লক ধরে তথ্য আদান-প্রদান করে, যেমন হার্ড ডিস্ক, এসএসডি, সিডি-রম ও পেন ড্রাইভ।
   - ls -l এ প্রথম অক্ষর: b
   - উদাহরণ: /dev/sda, /dev/sda1

   ৫. লিংক (Symbolic Link):
   - অন্য একটি ফাইলের পথ ধারণকারী ছোট ফাইল, যা শর্টকাটের মতো কাজ করে।
   - ls -l এ প্রথম অক্ষর: l
   - তৈরি করার কমান্ড: ln -s target linkname
   - হার্ড লিংকের আলাদা কোনো চিহ্ন নেই, কারণ সেটি একই inode এর দ্বিতীয় নাম মাত্র।

   ৬. নেমড পাইপ বা FIFO (Named Pipe):
   - দুটি প্রসেসের মধ্যে একমুখী যোগাযোগের জন্য ব্যবহৃত হয়। একটি প্রসেস লেখে, আরেকটি পড়ে।
   - ls -l এ প্রথম অক্ষর: p
   - তৈরি করার কমান্ড: mkfifo mypipe

   ৭. সকেট (Socket):
   - প্রসেসের মধ্যে দ্বিমুখী যোগাযোগের জন্য, এবং নেটওয়ার্ক যোগাযোগেও ব্যবহৃত হয়।
   - ls -l এ প্রথম অক্ষর: s
   - উদাহরণ: /var/run/docker.sock

   সারণি:

   | ধরন | চিহ্ন | উদাহরণ |
   |---|---|---|
   | সাধারণ ফাইল | - | report.txt |
   | ডিরেক্টরি | d | /home |
   | ক্যারেক্টার ডিভাইস | c | /dev/tty |
   | ব্লক ডিভাইস | b | /dev/sda |
   | সিম্বলিক লিংক | l | /bin -> /usr/bin |
   | নেমড পাইপ | p | mypipe |
   | সকেট | s | /var/run/docker.sock |

   ফাইলের ধরন জানার কমান্ড:
   ```bash
   ls -l filename        # প্রথম অক্ষর দেখে
   file filename         # বিষয়বস্তু বিশ্লেষণ করে
   stat filename         # বিস্তারিত তথ্য
   ```

   ইউনিক্স ফাইল সিস্টেমের কাঠামো: একটি ফাইল সিস্টেম চারটি অংশে বিভক্ত — Boot block (বুট লোডার), Super block (ফাইল সিস্টেমের বিবরণ ও মুক্ত ব্লকের তালিকা), Inode list (প্রতিটি ফাইলের মেটাডেটা: অনুমতি, মালিক, আকার, সময় ও ডেটা ব্লকের ঠিকানা) এবং Data blocks (প্রকৃত বিষয়বস্তু)।

   উল্লেখযোগ্য: ফাইলের নাম inode এ রাখা হয় না; নাম থাকে ডিরেক্টরিতে, যা নামকে inode নম্বরের সঙ্গে যুক্ত করে। এ কারণেই একই ফাইলের একাধিক নাম (হার্ড লিংক) থাকতে পারে।

   ফাইল সিস্টেমের প্রকারভেদ (অন্য অর্থে): ext2, ext3, ext4, XFS, Btrfs, ZFS, UFS, NFS (নেটওয়ার্ক ফাইল সিস্টেম), tmpfs (মেমোরিভিত্তিক) এবং procfs ও sysfs (কার্নেলের তথ্য প্রকাশকারী ভার্চুয়াল ফাইল সিস্টেম)।
3. **কোন ড্রাইভে ‘My Document’ রাখা হয় এবং NTFS কী?** *[BPSC Computer Operator 2021 compact it 780 (ET: N/A)]*


   Answer:

   'My Documents' কোন ড্রাইভে রাখা হয়:

   উইন্ডোজে 'My Documents' বা 'Documents' ফোল্ডারটি ডিফল্টভাবে সি ড্রাইভে (C:) রাখা হয়, ব্যবহারকারীর প্রোফাইল ফোল্ডারের ভেতরে।

   - সম্পূর্ণ পথ: C:\Users\<username>\Documents
   - পুরোনো সংস্করণে (Windows XP): C:\Documents and Settings\<username>\My Documents

   কারণ: C: ড্রাইভ হলো সিস্টেম ড্রাইভ, যেখানে উইন্ডোজ ইনস্টল করা থাকে এবং প্রতিটি ব্যবহারকারীর প্রোফাইল সংরক্ষিত হয়।

   গুরুত্বপূর্ণ পরামর্শ: ব্যক্তিগত নথি সি ড্রাইভে রাখা ঝুঁকিপূর্ণ, কারণ উইন্ডোজ পুনরায় ইনস্টল করলে বা সিস্টেম নষ্ট হলে সেগুলো হারিয়ে যেতে পারে। তাই Documents ফোল্ডারটি অন্য ড্রাইভে (যেমন D:) সরিয়ে নেওয়া উত্তম। পদ্ধতি: Documents ফোল্ডারে ডান ক্লিক → Properties → Location → Move → নতুন স্থান নির্বাচন। প্রতিষ্ঠানে এই কাজটি Group Policy এর Folder Redirection দিয়ে কেন্দ্রীয়ভাবে করা হয়, যাতে নথি সার্ভারে থাকে এবং ব্যবহারকারী যেকোনো কম্পিউটার থেকে সেগুলো পান।

   NTFS কী:

   NTFS এর পূর্ণরূপ New Technology File System। এটি উইন্ডোজ এনটি পরিবারের (Windows 2000, XP, Vista, 7, 8, 10, 11 এবং সব সার্ভার সংস্করণ) আদর্শ ফাইল সিস্টেম, যা ১৯৯৩ সালে Windows NT 3.1 এর সঙ্গে চালু হয় এবং FAT এর স্থান নেয়।

   প্রধান বৈশিষ্ট্য:
   - Journaling: ফাইল সিস্টেমের প্রতিটি পরিবর্তন প্রয়োগের আগে একটি লগে লিখে রাখা হয়, ফলে বিদ্যুৎ চলে গেলে বা সিস্টেম ক্র্যাশ করলেও ফাইল সিস্টেম দ্রুত ও নিরাপদে পুনরুদ্ধার হয়।
   - নিরাপত্তা: প্রতিটি ফাইল ও ফোল্ডারে ব্যবহারকারী ও গ্রুপভিত্তিক অনুমতি (Access Control List) দেওয়া যায়, যা FAT এ একেবারেই নেই।
   - বড় ফাইল ও ভলিউম: সর্বোচ্চ ভলিউম ২৫৬ টেরাবাইট এবং ফাইলের আকার কার্যত সীমাহীন। FAT32 এ একটি ফাইল সর্বোচ্চ ৪ গিগাবাইট হতে পারে।
   - সংকোচন (Compression) ও এনক্রিপশন (EFS) — ফাইল বা ফোল্ডার ভিত্তিতে।
   - Disk Quota: প্রতিটি ব্যবহারকারীর জন্য সর্বোচ্চ জায়গার সীমা নির্ধারণ।
   - Shadow Copy: ফাইলের পূর্ববর্তী সংস্করণ পুনরুদ্ধারের সুযোগ।
   - Hard link, symbolic link ও junction point এর সমর্থন।
   - Sparse file, যাতে বড় কিন্তু বেশিরভাগ ফাঁকা ফাইল কম জায়গা নেয়।
   - ২৫৫ অক্ষর পর্যন্ত ইউনিকোড ফাইলনাম।
   - নষ্ট ক্লাস্টার স্বয়ংক্রিয়ভাবে চিহ্নিত ও এড়িয়ে যাওয়া।

   FAT32 ও exFAT এর সঙ্গে তুলনা:

   | বিষয় | FAT32 | NTFS | exFAT |
   |---|---|---|---|
   | সর্বোচ্চ ফাইল আকার | ৪ গিগাবাইট | কার্যত সীমাহীন | কার্যত সীমাহীন |
   | সর্বোচ্চ ভলিউম | ৩২ গিগাবাইট (উইন্ডোজে ফরম্যাট করলে) | ২৫৬ টেরাবাইট | ১২৮ পেটাবাইট |
   | Journaling | নেই | আছে | নেই |
   | অনুমতি ব্যবস্থা | নেই | আছে | নেই |
   | সামঞ্জস্য | সর্বত্র | মূলত উইন্ডোজ | ব্যাপক, ফ্ল্যাশ মিডিয়ার জন্য |
   | উপযুক্ত ব্যবহার | পুরোনো ছোট যন্ত্র | উইন্ডোজের সিস্টেম ও ডেটা ড্রাইভ | বড় পেন ড্রাইভ ও মেমোরি কার্ড |
4. **A file system with 300 GB uses a file descriptor with 8 direct block address, 1 indirect block address and 1 doubly indirect block address. The size of each disk block is 128 Bytes and the size of each disk block address is 8 Bytes. The maximum possible file size in this file system.** *[BAUST Assistant Programmer 2021 compact it 917 (ET: N/A)]*


   Answer: Given:
   - 8 direct block addresses
   - 1 single indirect block address
   - 1 double indirect block address
   - Disk block size = 128 bytes
   - Disk block address size = 8 bytes

   Step 1 - how many addresses fit in one block:
   - Addresses per block = block size / address size
   - = 128 / 8
   - = 16 addresses per block

   Step 2 - blocks reachable through the direct pointers:
   - Each direct pointer names one data block.
   - Direct blocks = 8

   Step 3 - blocks reachable through the single indirect pointer:
   - The single indirect pointer names one block that contains addresses, and that block holds 16 addresses, each naming a data block.
   - Single indirect blocks = 16

   Step 4 - blocks reachable through the double indirect pointer:
   - The double indirect pointer names one block of 16 addresses.
   - Each of those 16 addresses names another block, which itself holds 16 addresses of data blocks.
   - Double indirect blocks = 16 x 16 = 256

   Step 5 - total number of data blocks:
   - Total = 8 + 16 + 256
   - = 280 blocks

   Step 6 - maximum file size:
   - Maximum file size = total blocks x block size
   - = 280 x 128 bytes
   - = 35,840 bytes

   Step 7 - express in convenient units:
   - 35,840 / 1024 = 35 KB

   Final answer: the maximum possible file size is 35,840 bytes, that is 35 KB.

   Summary table:

   | Pointer type | Number of pointers | Data blocks reached | Bytes |
   |---|---|---|---|
   | Direct | 8 | 8 | 1,024 |
   | Single indirect | 1 | 16 | 2,048 |
   | Double indirect | 1 | 256 | 32,768 |
   | Total | | 280 | 35,840 = 35 KB |

   Points worth stating:
   - The 300 GB size of the file system given in the question is a distractor. The maximum file size depends only on the structure of the file descriptor (the inode), not on the size of the volume.
   - The double indirect pointer contributes by far the most, 256 of the 280 blocks, which shows why indirection is used at all.
   - If a triple indirect pointer were added, it would contribute 16 x 16 x 16 = 4,096 further blocks, raising the total to 4,376 blocks, that is 560,128 bytes or about 547 KB.
   - The general formula, with d direct pointers and k = block size / address size addresses per block, for an inode with single, double and triple indirection, is:
     Maximum file size = (d + k + k^2 + k^3) x block size
   - Real systems use much larger blocks. With a 4 KB block and 4-byte addresses, k = 1024, and the same structure would allow (12 + 1024 + 1024^2 + 1024^3) x 4 KB, which is about 4 TB. This is the classic Unix inode arrangement.
   - The design is deliberately asymmetric: small files, which are the great majority, are reached entirely through the direct pointers with no extra disk access, while large files remain possible through indirection at the cost of one or two additional reads.
