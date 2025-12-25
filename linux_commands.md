
## General Linux Commands

**ls**: list directory contents

 - **ls -l**: gives detailed file information

 - **ls -a**: shows hidden files

**cd**: change directory

 - **cd /path/to/directory**: moves to specified directory

 - **cd ..**: goes up one level

**pwd**: print working directory, shows current directory path

**cp**: copy files and directories

 - **cp file1.txt file2.txt**: copies file1.txt to file2.txt

 - **cp -r dir1/ dir2/**: copies directories recursively

**mv**: move or rename files

 - **mv file1.txt new_dir/**: moves file1.txt to new_dir

 - **mv oldname.txt newname.txt**: renames a file

**rm**: removes files and directories

 - **rm file.txt**: deletes the file

 - **rm -f dir/**: deletes a directory and its contents recursively

 - ** rm permanently deletes files

**touch file.txt**: creates file.txt file

 - **touch file1.txt file2.txt file3.md**: creates three new files

**mkdir**: make a new directory

 - **mkdir new_folder**: creates a directory named new_folder

 - **mkdir f1 f2 f3**: creates three new directories

**rmdir**: remove an empty directory

**find**: search for files and directories

 - **find /path -name "filename"**: searches for files named 'filename' starting from /path

 - **find . -name "*.py"**: finds all python files in current directory

**chmod**: change file permissions

 - **chmod +x script.sh**: makes script.sh executable

 - **chmod 777 file**: gives full permission (read, write, execute) to everyone

**chown**: change file owner

**echo "Hello World"**: displays "Hello World" in terminal

**cat**: display the contents of a file

 - **cat file.txt**: shows the contents of file.txt

**nano**/**vim**: text editors

 - **nano file.txt**: opens the file in a simple terminal editor

 - **vim file.txt**: opens the file in advanced Vim editor

**grep**: search for patterns within files

**ps**: view running processes

 - **ps aux**: shows all running processes

 - **ps -ef**: provides a detailed view of processes

**top**: task manager, displayes real-time system usage

**df**: display disk space usage

 - **df -h**: shows human-readable output of disk usage

**du**: display directory space usage

 - **du -sh**: gives a summary of the disk usage in the current directory

**man**: shows the manual (help) page for a command

 - **man ls**: shows the manual for the **ls** command

**sudo**: run commands as a superuser (administrator)

 - **sudo apt-get update**: runs the command with elevated permissions

