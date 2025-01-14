---
description: ....
title: Getting Help
---

# Getting Help

Everyone needs some help from time to time. Basically thats what the man pages are for.

## Man pages

Man (`man` stands for manual) pages are used to describe the features of commands. They will provide you with a basic description of the purpose of the command, as well as provide details regarding the options of the command.

![Man page of uname command](./img/man_uname.png)

The man command uses a "pager" to display documents. Normally this pager is the `less` command. A pager is something that most administrators use frequently, to view files, read the results of long command output, and more. Common pager utils are `more` and `less`.

The most used commands inside the man pages are listed in the next table.

| Command | Description |
| ---- | ---- |
| `ENTER` | Go down a line |
| `SPACE` | Go down a page |
| `/keyword` | Search for keyword |
| `n` | Find next search item |
| `N` | Find previous search item |
| `g` | Goto beginning |
| `G` | Goto end |
| `h` | Show help |
| `q` | Quit man pages |

### Sections of a man page

Man pages are broken into **sections**. Each section is designed to provide specific information about a command.

* **NAME**: Name of command and brief description.
* **SYNOPSIS**: Provides examples.
* **DESCRIPTION**: More detailed description.
* **OPTIONS**: Lists the options for the command with a description.
* **FILES**: Lists the files that are associated with the command as well as a description of how they are used. These files may be used to configure the command's more advanced features.
* **AUTHOR**: The name of the person who created the man page and (sometimes) how to contact the person.
* **REPORTING BUGS**: Provides details on how to report problems with the command.
* **COPYRIGHT**: Provides basic copyright information.
* **SEE ALSO**: Provides you with an idea of where you can find additional information.This also will often include other commands that are related to this command.

Sometimes configuration files also have man pages. Configuration files (sometimes called system files) contain information that is used to store information about the Operating System or services.

### Sections of the man pages

There are thousands of man pages on a typical Linux distribution. To organize all of these man pages, the pages are **categorized by sections**, much like each individual man page is broken into sections.

1. Executable programs or shell commands
1. System calls (functions provided by the kernel)
1. Library calls (functions within program libraries)
1. Special files (usually found in /dev)
1. File formats and conventions, e.g. /etc/passwd
1. Games
1. Miscellaneous (including macro packages and conventions)
1. System administration commands (usually only for root)
1. Kernel routines [Non standard]

When you use the man` command, it searches each of these sections **in order** until it finds the first "match".

For example:

```bash
[bioboost@linux][~]$ man echo
```

To determine which section a specific man page belongs to, look at the numeric value on the first line of the output of the man page.

![Man page section](./img/man_echo.png)

In some cases you will need to specify the section in order to display the correct man page. This is necessary because sometimes there will be man pages with the same name in different sections.

There is for example a man page about the `passwd` command (section 1) but also about the file `/etc/passwd` (section 5). To request a man page from a specific section, just add the number before the name of the man page.

```bash
[bioboost@linux][~]$ man 5 passwd
```

### Partial Matches

The `-f` option to the `man` command will display man pages that match, or partially match, a specific name and provide a brief description of each man page.

```bash
[bioboost@linux][~]$ man -f ip
```

::: output
<pre>
ip (7)               - Linux IPv4 protocol implementation
ip (8)               - show / manipulate routing, network devices, interfaces...
</pre>
:::

Note that on most Linux distributions, the `whatis` command does the same thing as `man -f`.

```bash
[bioboost@linux][~]$ whatis ip
```

::: output
<pre>
ip (7)               - Linux IPv4 protocol implementation
ip (8)               - show / manipulate routing, network devices, interfaces...
</pre>
:::

### Search by Keyword

You can search for a keyword in the man pages names and the short descriptions by using the `-k` option.

```bash
[bioboost@linux][~]$ man -k ssh
```

::: output
<pre>
authorized_keys (5)  - OpenSSH SSH daemon
rlogin (1)           - OpenSSH SSH client (remote login program)
</pre>
:::

The `apropos` command does the same thing as `man -k`.

```bash
[bioboost@linux][~]$ apropos ssh
```

::: output
<pre>
authorized_keys (5)  - OpenSSH SSH daemon
rlogin (1)           - OpenSSH SSH client (remote login program)
</pre>
:::

You can use the `apropos` command to find a specific command based on its description. This is especially helpfull when you know what you want to achieve but don't know what command to use.

## Info

The `info` command also provides documentation on operating system commands and features. The goal of this command is slightly different from the man pages.

Consider man pages to be more of a reference resource and info documents to be more of a learning guide.

You may need to install info: `sudo apt install info`

```bash
[bioboost@linux][~]$ info ls
```

The info command automatically redirects to man pages if no info exists.

Like the `man` command, you can get a listing of traverse keys by typing the letter `h` while reading the info documentation.

## Command help

Many commands will also provide you basic information, very similar to the SYNOPSIS found in man pages, when you apply the `--help`, `-h` or `-?` option to the command.

```bash
[bioboost@linux][~]$ passwd --help
```

::: output
<pre>
Usage: passwd [options] [LOGIN]

Options:
  -a, --all                     report password status on all accounts
  -d, --delete                  delete the password for the named account
  -e, --expire                  force expire the password for the named account
  -h, --help                    display this help message and exit
  -k, --keep-tokens             change password only if expired
  -i, --inactive INACTIVE       set password inactive after expiration
</pre>
:::

## Documentation

On most systems, there is a directory where additional documentation is found. This will often be a place where vendors who create additional (third party) software can store documentation files. These documentation files are often called readme files, since the files typically have names such as `README` or `readme.txt`.

Typical locations include `/usr/share/doc` and `/usr/doc`.

## Challenges

Find all the info you need in the man-pages. Make sure to comment the commands you used to find this information. No google!

Mark challenges using a ✅ once they are finished.

### ✅ The free command

*Describe in your own words what the `free` command does. Give an example and a partial output.*

```bash
[jensva@LEGION-Y540-JENS][~]$ man free
```

Info out of man page → It displays the amount of used and free space left on the system.

```bash
[jensva@LEGION-Y540-JENS][~]$ free
```

Output:

```text
              total        used        free      shared  buff/cache   available
Mem:       13025992       94128    12569540          72      362324    12681356
Swap:       4194304           0     4194304
```

### ✅ The id command

*Describe in your own words what the `id` command does. Give an example and a partial output.*

```bash
[jensva@LEGION-Y540-JENS][~]$ man id
```

Info out of man page → It gives info about the user of the system.

```bash
[jensva@LEGION-Y540-JENS][~]$ id
```

Output:

```text
uid=1000(jensva) gid=1000(jensva) groups=1000(jensva),4(adm),20(dialout),24(cdrom),25(floppy),27(sudo),29(audio),30(dip),44(video),46(plugdev),117(netdev)
```

### ✅ The tree command

*Describe in your own words what the `tree` command does. How do you list all subdirectories too? How can you only include directories? If the `tree` command is not available on your system you can install it using `sudo apt install tree`*

```bash
[jensva@LEGION-Y540-JENS][/]$ man tree
```

Info out of man page → It lists all the directories in the form of a tree. (Just like a family tree)

To list all the subdirectories:

```bash
[jensva@LEGION-Y540-JENS][/]$ tree
```

Output:

```text
.
├── 1RHvwKQmejt
├── 3D Objects
│   └── desktop.ini
├── AppData
│   ├── Local
│   │   ├── Adobe
│   │   │   ├── ARM
│   │   │   │   ├── Reader_19.010.20098
│   │   │   │   ├── Reader_20.009.20067
│   │   │   │   ├── Reader_20.009.20074
│   │   │   │   ├── Reader_20.012.20041
│   │   │   │   ├── Reader_20.012.20043
│   │   │   │   ├── Reader_20.012.20048
```

To include only directories:

```bash
[jensva@LEGION-Y540-JENS][/]$ tree -d
```

Output:

```text
.
├── 3D Objects
├── AppData
│   ├── Local
│   │   ├── Adobe
│   │   │   ├── ARM
│   │   │   │   ├── Reader_19.010.20098
│   │   │   │   ├── Reader_20.009.20067
│   │   │   │   ├── Reader_20.009.20074
│   │   │   │   ├── Reader_20.012.20041
```

### ✅ The which command

*Describe in your own words what the `which` command does. What is the result for `pwd` ?*

```bash
[jensva@LEGION-Y540-JENS][/]$ man which
```

Info out of man page → It returns the links/pathnames of the given filename.

```bash
[jensva@LEGION-Y540-JENS][/]$ which pwd
```

Output:

```text
/usr/bin/pwd
```

### ✅ The file command

*Describe in your own words what the `file` command does. What is the result for `~/.bashrc` ?*

```bash
[jensva@LEGION-Y540-JENS][/]$ man file
```

Info out of man page → It returns the type of the file (text, executable, data...).

```bash
[jensva@LEGION-Y540-JENS][/]$ ~/.bashrc
```

Output:

```text
/home/jensva/.bashrc: ASCII text
```

### ✅ The type command

*Describe in your own words what the `type` command does. What is the result for `ls` and what is the result for `g++` ?*

```bash
[jensva@LEGION-Y540-JENS][/]$ type --help
```

Info out of help page → The type command gives info about a command type.

```bash
[jensva@LEGION-Y540-JENS][/]$ type ls
```

```text
Output: ls is aliased to `ls --color=auto'
```

```bash
[jensva@LEGION-Y540-JENS][/]$ type g++
```

```text
Output: g++ is /usr/bin/g++
```

### ✅ Counting lines and words

*What command can be used to count lines and words in text? Give an example and explain the output.*

```bash
[jensva@LEGION-Y540-JENS][/]$ apropos count
```

Command (You should provide a filename):

```bash
[jensva@LEGION-Y540-JENS][/]$ wc Flowchart.docx
```

Output:

```text
47   276 14809 Flowchart.docx
```

### ✅ The wget command

*How can you download a file from the Internet using the command line?. Find a file online to use it on and demonstrate its usage.*

Let's download an old version of linux:

```bash
[jensva@LEGION-Y540-JENS][~]$ wget https://mirrors.edge.kernel.org/pub/linux/kernel/Historic/linux-0.01.tar.gz

```

To extract the tar.gz file:

```bash
[jensva@LEGION-Y540-JENS][~]]$ tar -xvf linux-0.01.tar.gz
```

To look inside some of the code:

```bash
[jensva@LEGION-Y540-JENS][~/linux/init]$ nano main.c
```

I found some text written by a somewhat frustrated programmer :)

```text
/*
 * Yeah, yeah, it's ugly, but I cannot find how to do this correctly
 * and this seems to work. I anybody has more info on the real-time
 * clock I'd be interested. Most of this was trial and error, and some
 * bios-listing reading. Urghh.
 */
```

### ✅ The dmesg command

*Describe in your own words what the `dmesg` command does. Give an example and a partial output.*

```bash
[jensva@LEGION-Y540-JENS][/]$ man dmesg
```

Info out of man page → It prints messages related to operations from the kernal. The messages are stored in a ring buffer (new message comes in and pushes the oldest message away).

Output:

```text
[    0.000000] Command line: initrd=\initrd.img panic=-1 pty.legacy_count=0 nr_cpus=12
[    0.000000] KERNEL supported cpus:
[    0.000000]   Intel GenuineIntel
[    0.000000]   AMD AuthenticAMD
[    0.000000]   Centaur CentaurHauls
[    0.000000] x86/fpu: Supporting XSAVE feature 0x001: 'x87 floating point registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x002: 'SSE registers'
[    0.000000] x86/fpu: Supporting XSAVE feature 0x004: 'AVX registers'
```

### ✅ Checksums

*Go to the website of Raspberry Pi - [https://www.raspberrypi.org/software/operating-systems](https://www.raspberrypi.org/software/operating-systems) and download the Raspberry Pi OS image using the `wget` command line tool. Now check if the SHA-256 checksum complies with the one being advertised on the website.*

```bash
[jensva@LEGION-Y540-JENS][/]$ wget https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2021-05-28/2021-05-07-raspios-buster-armhf-lite.zip
```

*What tool did you use to calculate the checksum? Demonstrate its usage.*

```bash
[jensva@LEGION-Y540-JENS][/]$ apropos checksum
[jensva@LEGION-Y540-JENS][/]$ man shasum
```

```bash
[jensva@LEGION-Y540-JENS][/]$ shasum -a 256 2021-05-07-raspios-buster-armhf-lite.zip.1
```

Output:

```text
c5dad159a2775c687e9281b1a0e586f7471690ae28f2f2282c90e7d59f64273c  2021-05-07-raspios-buster-armhf-lite.zip.1
```

The SHA-256 checksum is the same as the one on the website. (c5dad159a2775c687e9281b1a0e586f7471690ae28f2f2282c90e7d59f64273c)

*What is the use of this hash?*

This hash encrypts the data so it isn't readable. It prevents data being sent in plain-text.

### ✅ The printenv command

*Describe in your own words what the `printenv` command does.*

```bash
[jensva@LEGION-Y540-JENS][/]$ man printenv
```

Info out of man page → It prints the environment variables. If no variable is given, it prints them all.

### ✅ IP Address

*Find the IP address of your WiFi interface. What command did you use?*

```bash
[jensva@LEGION-Y540-JENS][/]$ ifconfig
```

I found the IP-address 172.20.122.39

### ✅ IP of Sivir Server

*What is the IP address of the internal server `sivir.devbit.be`? Make sure you are connected to the `Devbit` network.*

```bash
[jensva@LEGION-Y540-JENS][/]$ nslookup sivir.devbit.be
```

Output:

```text
Server:         172.20.112.1
Address:        172.20.112.1#53

Non-authoritative answer:
Name:   sivir.devbit.be
Address: 172.16.10.5
```

Answer: 172.16.10.5
