
 ### Some commands may provide help through different options, such as *`-h`* or *`--help`*:

 ```
 <command> --help
```
 ## 50 Linux commands with examples:
### - **ls** - List directory contents.
      Options:

  `-a, --all`                  do not ignore entries starting with .

  `-A, --almost-all`           do not list implied . and ..

  `-l`                         use a long listing format

  `-h, --human-readable`       with -l, print sizes in human readable format (e.g., 1K 234M 2G)

  `-S`                         sort by file size

  `-t`                         sort by modification time

The` -F` option in the **`ls`** command appends a character to each filename to indicate its type. Here’s what each character represents:

    / for directories
    * for executable files
    @ for symbolic links
    | for FIFOs (named pipes)
    = for sockets

When combined with the -l option, which provides a detailed listing format, the -F option still adds these type indicators to the filenames.
```
ls -l
```

### - **cd** - Change the current directory.
```
cd /home/user
```

### - **pwd** - Print the current working directory.
```
pwd
```
### - **cp** - Copy files and directories.

```
cp file1.txt file2.txt
```

### <span style="color:red">- **mv** - Move or rename files and directories. first see: mv --help</span>

```
mv oldname.txt newname.txt

```
### <span style="color:red">- **rm** - Remove files and directories. first see: rm --help</span>
```
rm file.txt
```

### - **mkdir** - Create a new directory.

  The **`-p`** option in the mkdir command stands for "parents". It allows the creation of parent directories as needed. If some of the parent directories in the specified path do not exist, mkdir -p will create them as well.
```
mkdir -p newdir/subdir
```


### - **rmdir** - Remove empty directories.
```
rmdir emptydir
```

### - **touch** - Create an empty file or update the timestamp of an existing file.
```
touch newfile.txt
```

### - **chmod** - Change file permissions.
```
chmod 755 script.sh
```

### - **chown** - Change file owner and group.
```
chown user:group file.txt
```

### - **ln** - Create hard and symbolic links.
<u>**Hard Links**</u>

  **Definition:** 
  
  A hard link is a direct reference to the physical data on the disk. Multiple hard links to a file act as additional directory entries for that file.

  **Creation:**    
  Use the ln command without any options.
```
ln original_file hard_link
```

Properties:

  ***Same Inode:*** Hard links share the same inode number as the original file. This means they point to the same data blocks on the disk.

  ***File Content:*** Deleting the original file does not affect the hard link. The data remains accessible through the hard link.
  
  ***Limitations:***
        Cannot span across different file systems.
        Cannot link to directories (to avoid filesystem corruption).

Example:
```
touch original_file
ln original_file hard_link
ls -li
```
Output (example):

```

    1234567 -rw-r--r-- 2 user group 0 May 21 12:34 original_file
    1234567 -rw-r--r-- 2 user group 0 May 21 12:34 hard_link

```
<u>**Soft (Symbolic) Links**</u>

  ***Definition:*** A soft link (or symbolic link) is a special file that contains a path to another file or directory. It acts as a shortcut.

  ***Creation:*** Use the ln command with the -s option.


```
ln -s original_file soft_link

```
Properties:

  ***Different Inode:*** Soft links have a different inode number from the original file. They do not point directly to the data but 
  
  ***File Content***: If the original file is deleted, the soft link becomes a dangling link (broken link) pointing to a non-existent file.
  
  ***Flexibility:***
        Can span across different file systems.
        Can link to directories.

Example:


```
touch original_file
ln -s original_file soft_link
ls -li

```
Output (example):


    1234567 -rw-r--r-- 1 user group 0 May 21 12:34 original_file
    2345678 lrwxrwxrwx 1 user group 14 May 21 12:34 soft_link -> original_file

**Key Differences**


Feature	Hard Link	Soft Link
Inode	Same as the original file	Different from the original file
Points to	Physical data on disk	Filename (path)
Across File Systems	No	Yes
Directories	No	Yes
Original File Deleted	Data remains accessible	Becomes a broken link
Use Cases

  **Hard Links:** Useful when you need multiple directory entries for a file within the same file system, allowing file sharing without duplicating data.
  
  **Soft Links:** Useful for creating shortcuts, linking files across different file systems, and linking to directories.

### - **cat** - Concatenate and display file content.
```
cat file.txt
```

### - **more** - View file content one screen at a time.
```
more file.txt
```

### - **less** - View file content with backward navigation.
```
less file.txt
```


The **`-n`** option in the <span style="color:red">**head** or **tail**</span> command specifies **`the number of lines to be displayed`** from the beggining or the end of the file. By default, head or tail displays the last 10 lines of a file. Using the **`-n`** option allows you to specify a different number of lines.

When you use head or tail **`-f`**, it allows you to monitor a file in real time as it is being updated.

### - **head** - Display the beginning of a file.

```
head file.txt  # by default 10 lines
```

```
head -n 5 file.txt # 5 lines
```

### - **tail** - Display the end of a file.
```
tail -n 5 file.txt
```

### - **grep** - Search for patterns in files.
```
grep "pattern" file.txt
```
or can pipe from... ex.: `cat large-file.txt | grep justo`  # will show the ALL lines with "justo" text...
or `ls -l | grep ^l` # will show only line that begins with "l"...
or `ls -l | grep -v ^l` # will show the ALL lines without "l" text...
or `ls -l | grep st$`  # will show the ALL "st" in the end...


### - **find** - Search for files and directories.
```
find /path -name "*.txt"
```

### - **locate** - Find files by name quickly using a database.
```
locate file.txt
```

### - **du** - Estimate file space usage.
```
du -h /path
```
### - **df** - Display disk space usage of file systems.
```
df -h
```
### - **top** - Display system tasks and processes.
```
top
```

### - **ps** - Report a snapshot of current processes.
```
ps aux
```

### - **kill** - Terminate processes by PID.
```
kill 1234
```

### - **killall** - Terminate processes by name.
```
killall firefox
```

### - **tar** - Archive files and directories.
```
tar -czvf archive.tar.gz /path/to/directory
```

### - **gzip** - Compress files.
```
gzip file.txt
```

### - **gunzip** - Decompress files.
```
gunzip file.txt.gz
```

### - **zip** - Package and compress files.
```
zip archive.zip file1.txt file2.txt
```

### - **unzip** - Extract compressed files.
```
unzip archive.zip
```

### - **wget** - Download files from the web.
```
wget http://example.com/file.zip
```

### - **curl** - Transfer data from or to a server.
```
curl -O http://example.com/file.zip
```

### - **scp** - Secure copy (remote file copy program).
```
scp user@remote:/path/to/file /local/path
```

### - **ssh** - OpenSSH SSH client (remote login program).
```
ssh user@remote
```

### - **rsync** - Remote file and directory synchronization.
```
rsync -avz /local/path user@remote:/remote/path
```

### - **ping** - Check network connectivity.
```
ping google.com
```

### - **traceroute** - Print the route packets take to a network host.
```
traceroute google.com
```

### - **netstat** - Print network connections, routing tables, interface statistics, etc.
```
netstat -tuln
```

### - **ifconfig** - Configure a network interface (deprecated, use ip).
```
ifconfig eth0
```

### - **ip** - Show/manipulate routing, devices, policy routing, and tunnels.
```
ip addr show
```

### - **systemctl** - Control the systemd system and service manager.
```
systemctl status sshd
```

### - **journalctl** - View logs collected by systemd.
```
journalctl -xe
```

### - **crontab** - Schedule periodic jobs using the cron daemon.
```
crontab -e
```

### - **at** - Schedule commands to be executed at a later time.
```
echo "sh script.sh" | at 10:00
```

### - **alias** - Create an alias for a command.
```
alias ll='ls -l'
```

### - **unalias** - Remove an alias.
```
unalias ll
```

### - **history** - Show command history.
```
history
```

### - **man** - Format and display the manual pages for commands.
```
man ls
```

### - **echo** - Display a line of text.
```
echo "Hello, World!"
```
