# SHELL
A shell is a program that provides an
interface between the user and the
operating system. It allows users to
interact with the system by executing
commands, running programs, and
managing files and processes. Shells can
be command-line interfaces (CLI) or
graphical user interfaces (GUI), but the
term "shell" is most commonly
associated with CLI.

# BACKGROUND
Humans and computers commonly
interact in many different ways, such as
through a keyboard and mouse, touch
screen interfaces, or using speech
recognition systems. The most widely
used way to interact with personal
computers is called a graphical user
interface (GUI). With a GUI, we give
instructions by clicking a mouse and
using menu-driven interactions. While
the visual aid of a GUI makes it intuitive
to learn, this way of delivering
instructions to a computer scales very
poorly. Imagine the following task: for a
literature search, you have to copy the
third line of one thousand text files in
one thousand different directories and
paste it into a single file. Using a GUI,
you would not only be clicking at your
desk for several hours, but you could
potentially also commit an error in the
process of completing this repetitive
task. This is where we take advantage of
the Unix shell. The Unix shell is both a
command-line interface (CLI) and a
scripting language, allowing such
repetitive tasks to be done automatically
and fast. With the proper commands, the
shell can repeat tasks with or without
some modification as many times as we
want. Using the shell, the task in the
literature example can be accomplished
in seconds.

# PURPOSE
The purpose of a shell is to act as a
bridge between the user and the
operating system, enabling command
execution, system management, and task
automation. It interprets user commands,
executes programs, and manages
processes. The shell also allows for
scripting to automate repetitive tasks,
making workflows efficient. It provides
access to system utilities, manages
environment variables, and facilitates
customization through configuration
files. By offering an interactive interface,
the shell enhances user interaction and
productivity, supporting both basic and
advanced operations.
- Acts as a bridge between the user
and the operating system.
- Automates tasks through
scripting.
- Interprets commands and executes
programs.

# BENEFITS
The shell offers numerous benefits,
making it an essential tool for interacting
with operating systems efficiently. It
provides flexibility for users to execute
commands and manage files or processes
directly. Automation through shell
scripting reduces repetitive tasks, saving
time and effort. The shell's lightweight
nature makes it faster and more
resource-efficient compared to graphical
interfaces. It supports customization,
allowing users to tailor their environment
to their needs. Additionally, the shell
enhances productivity with features like
command history, aliases, and tab
completion, making complex tasks easier
to perform.
- Provides direct interaction with
the operating system.
- Enables automation of tasks
through scripting.
- Offers a lightweight and
resource-efficient interface.
- Supports customization for a
personalized environment.
- Enhances productivity with
features like command history and
aliases.
- Offers fast and resource-efficient
performance compared to
graphical interfaces.
- Automates repetitive tasks
through scripting, saving time and
effort.

# COMMANDS

Here are some basic shell commands commonly used in Linux/Unix systems:

| **Category**                 | **Command**        | **Description**                                         |
|------------------------------|--------------------|---------------------------------------------------------|
| **File & Directory Management** | ls               | Lists files & directories.                              |
|                              | cd               | Changes the current directory.                         |
|                              | pwd              | Prints the current working directory.                  |
|                              | mkdir            | Creates a new directory.                               |
|                              | rm               | Removes files or directories.                          |
|                              | cp               | Copies files or directories.                           |
|                              | mv               | Moves or renames files or directories.                 |
| **File Viewing & Editing**     | cat              | Displays file content.                                  |
|                              | less/more      | Views file content page by page.                       |
|                              | nano/vim       | Edits files directly in the shell.                     |
| **File Permissions & Ownership** | chmod           | Changes file permissions.                              |
|                              | chown            | Changes file ownership.                                |
| **Process Management**         | ps               | Displays running processes.                            |
|                              | kill             | Terminates a process by its ID.                        |
|                              | top              | Monitors system performance and processes.             |
| **System Information**         | uname            | Displays system information.                           |
|                              | df               | Shows disk space usage.                                |
|                              | free             | Displays memory usage.                                 |
| **Networking**                 | ping             | Checks network connectivity.                           |
|                              | curl/wget      | Fetches data from a URL.                               |
|                              | ifconfig/ip    | Displays network configuration.                        |
| **Archiving & Compression**    | tar              | Archives files.                                         |
|                              | gzip/gunzip    | Compresses or decompresses files.                      |
| **Miscellaneous**              | echo             | Prints text to the terminal.                           |
|                              | whoami           | Displays the current user.                             |
|                              | history          | Lists previously entered commands.                     |


# --help AND man
The --help and man commands are
essential tools for understanding how
commands and programs work in the
shell. They provide users with detailed
information and usage instructions,
making it easier to work with unfamiliar
commands or options. While --help gives
a quick summary, man provides
comprehensive documentation.
1. –help
- Displays a brief summary
of a command's usage and
options.
- Example: ls --help shows
options for listing files.
- Useful for quickly
checking syntax and
available flags.
2. man
- Opens the manual page for
a command, offering
detailed documentation.
- Example: man ls shows
extensive information
about the ls command.

# AUTOMATION IN SHELL
Automation in Shell refers to the
process of using shell scripts and
commands to perform repetitive tasks,
streamline workflows, and reduce
manual intervention. Shell automation is
widely used for system administration,
task scheduling, and software
deployment, enhancing efficiency and
consistency.
- Automates tasks by writing
sequences of commands in a
script file.
- Example: Backup files, clean
logs, or deploy applications.
- Scripts can include loops,
conditionals, and variables for
flexibility.

# TIPS
- If your screen gets too cluttered, you can clear your terminal using the clear command. You can still access previous commands using ↑ and ↓ to move line-by-line, or by scrolling in your terminal.
* To copy and paste the commands:<br>
1. Copy: ctrl+shift+c<br>
2. Paste: ctrl+shift+v
<br>
- Not only can we use ls on the current working directory, but we can use it to list the contents of a different directory.
- At our Desktop directory by running ls -F Desktop, i.e., the command ls with the -F option and the argument Desktop. The argument Desktop tells ls that we want a listing of something other than our current working directory:
- $ ls -F Desktop
- shell-lesson-data/
-You will notice that cd doesn’t print anything. This is normal. Many shell commands will not output anything to the screen when successfully executed. But if we run pwd after it, we can see that we are now in /Users/nelle/Desktop/shell-lesson-data/exercise-data.

- Complicated names of files and directories can make your life painful when working on the command line. Here we provide a few useful tips for the names of your files and directories.<br>
1. Spaces can make a name more meaningful, but since spaces are used to separate arguments on the command line it is better to avoid them in names of files and directories. You can use - or _ instead (e.g. north-pacific-gyre/ rather than north pacific gyre/). To test this out, try typing mkdir north pacific gyre and see what directory (or directories!) are made when you check with ls -F.<br>
2. Don’t begin the name with - (dash).
Commands treat names starting with - as options.
3. Stick with letters, numbers, . (period or ‘full stop’), - (dash) and _ (underscore).
Many other characters have special meanings on the command line.

# Loops
Loops are a programming construct which allow us to repeat a command or set of commands for each item in a list. As such they are key to productivity improvements through automation. Similar to wildcards and tab completion, using loops also reduces the amount of typing required (and hence reduces the number of typing mistakes).

## Here’s an example of automating the update and upgrade process in a shell script, scheduled to run every day at midnight.

Script: update_system.sh<br><br>
![Screenshot from 2024-12-28 13-58-26](https://github.com/user-attachments/assets/864d1351-ff4c-41fe-a4b5-d1cc4b6eac8f)

<br><br>
1. Save the script as update_system.sh
2. Make it executable
bash
$ chmod +x update_system.sh

To schedule this script to run every day at 12:00 AM:
1. Open the crontab editor
![Screenshot from 2024-12-28 14-04-24](https://github.com/user-attachments/assets/76c70c66-9cd7-4210-a3ff-c802478b6f6f)

<br><br>
Add the following line:
bash
0 0 * * * /home/update_system.sh

- Save and close the editor.
- Now, the system will automatically run the script at midnight each day.
