# Commonly Used Linux Commands: File, Searching, System Information, and Networking Commands

## FILE COMMANDS

| COMMAND | FUNCTIONS |
| --- | --- |
| ls | To list out all the files in current directory. |
| ls -l | To list out all the files in current directory in a detailed manner. |
| cd directory/folder Name | To move into specified folder or directory. |
| cd . . | To move into previous directory. |
| pwd | To print the current directory you are in. |
| ls -a | To show all the hidden files/folder. |
| mkdir folder-name | To create a new directory/folder. |
| rmdir folder-name | To remove an existing directory. |
| touch fileName | To create a new file. |
| cat file-Name | To display the content of the file. |
| cat &gt; file-Name | To create a file and edit it in command line, it will override the content if the file already exist. |
| cat &gt;&gt; file-Name | To edit a file content in command line without overriding (preferred). |
| cp source-file target-file | To copy the content of source file into target file |
| mv file-name folder-name | To move file into specified folder name. |
| mv file-one file-two | To rename file-one into file-two. |
| rm file-name | To remove a file, use this with caution as it will deleted permanently |
| rm -R folder-name | To delete a folder permanently. |
| chmod | change permession of a file or directory |
| grep "search\_term" file.txt | search for a pattern in a file or set of files |

## SEARCHING COMMANDS

| COMMAND | FUNCTIONS |
| --- | --- |
| find /home/user/ -name "\*.txt" | This command searches for all files with a .txt extension in the directory /home/user/ and any of its subdirectories. |
| locate myfile.txt | This command searches for any files named "myfile.txt" on the system, using a pre-built database of file locations. |
| which python | This command displays the location of the Python executable file in the system's PATH. |
| history | grep "search\_term" |
| find . | finds all the files/folder in the present directory. |
| find . . | Finds all the files/folder in the previous directory. |
| find . -type f -name “\*.txt” | find all the txt files present in the current directory. |
| find . -type f -name “file name” | find file with specified name in the current directory. |
| find . -type f -mmin +5 | find all the files that were modified more than 5 minutes ago in the current directory. |
| find . -type f -mtime -10 | shows all files that were modified less than ten days. |
| find . -type f -size +1M | shows all the file that are more than 1 MB in size. |
| find . -type f -size +1K | shows all the file that are more than 1 KB in size. |

## SYSTEM INFO COMMANDS

| COMMANDS | FUNCTIONS |
| --- | --- |
| uname | display information about the system and kernel version. |
| df | display disk space usage for file systems. |
| free | display information about memory usage. |
| top | display information about system resource usage in real-time. |
| ps | display information about running processes. |
| uptime | show uptime |

## NETWORKING COMMANDS

| COMMANDS | functions |
| --- | --- |
| ping | test network connectivity to a given host or IP address. |
| traceroute | display the route that network packets take to reach a given host or IP address. |
| nslookup | query DNS (Domain Name System) servers for information about a domain or hostname. |
| ifconfig | display network interface configuration information. |
| ip | show or manipulate routing, devices, policy routing, and tunnels. |
| netstat | display network connection information, routing tables, and interface statistics. |
| ssh | connect to a remote system over a secure shell (SSH) connection. |
| scp | copy files securely between systems over a SSH connection. |
| curl | transfer data from or to a server using one of the supported protocols. |
| wget | download files from the web. |

### **Shortcuts for Terminal**

<table><tbody><tr><td colspan="1" rowspan="1"><p><strong>Key Combination</strong></p></td><td colspan="1" rowspan="1"><p><strong>Use</strong></p></td></tr><tr><td colspan="1" rowspan="1"><p>CTRL + C</p></td><td colspan="1" rowspan="1"><p>To exit from Command Line</p></td></tr><tr><td colspan="1" rowspan="1"><p>CTRL + A</p></td><td colspan="1" rowspan="1"><p>To move cursor at start</p></td></tr><tr><td colspan="1" rowspan="1"><p>CTRL + E</p></td><td colspan="1" rowspan="1"><p>To move cursor at end</p></td></tr><tr><td colspan="1" rowspan="1"><p>CTRL + K</p></td><td colspan="1" rowspan="1"><p>To remove everything after the cursor</p></td></tr><tr><td colspan="1" rowspan="1"><p>CTRL + R</p></td><td colspan="1" rowspan="1"><p>For searching commands</p></td></tr><tr><td colspan="1" rowspan="1"><p>TAB KEY</p></td><td colspan="1" rowspan="1"><p>For autocompletion</p></td></tr><tr><td colspan="1" rowspan="1"><p>Page Up/ Page Down</p></td><td colspan="1" rowspan="1"><p>To navigate up and down for commands that were used</p></td></tr></tbody></table>

I hope this article helped you in a way. Follow me for a more detailed blog to help you in your development journey. Don't forget to share this blog with your friends.

You can also say other important commands in the comments that I have missed mentioning.

**HAPPY LEARNING JOURNEY**