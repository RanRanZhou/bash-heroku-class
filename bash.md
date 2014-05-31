Using The Command Line
====

What is the command line?

How does the command line work? What do command line arguments look like?

A free, excellent book on the command line is available as a PDF download. I highly recommend it: [The Linux Command Line, by William Shots](http://linuxcommand.org/tlcl.php)

## pwd

Prints the current working directory. The working directory is the folder in which all your commands will be executed. Any files you create or try to read will be searched in this directory. It's like the folder you currently have open in the Finder or in Explorer.

When you first start up your command prompt, your working directory will be your *home* directory:

	mbp-phil:~ okcoders$ pwd
	/Users/okcoders		
	
Your home directory contains all your personal documents, settings and other files.	

## ls

Lists the contents of a directory. Without any arguments, it lists the contents of the current working directory:

	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public		Desktop		Downloads	Movies	Pictures
	
We can pass the `-l` flags to `ls` to show the long listing, which includes additional information about the files.

	mbp-phil:~ okcoders$ ls -l
	total 0
	drwx------   3 okcoders  staff   102 May 30 12:57 Applications
	drwx------+  3 okcoders  staff   102 May 30 12:48 Desktop
	drwx------+  4 okcoders  staff   136 May 31 14:38 Documents
	drwx------+  4 okcoders  staff   136 May 30 12:48 Downloads
	drwx------@ 46 okcoders  staff  1564 May 31 17:55 Library
	drwx------+  3 okcoders  staff   102 May 30 12:48 Movies
	drwx------+  3 okcoders  staff   102 May 30 12:48 Music
	drwx------+  4 okcoders  staff   136 May 31 14:37 Pictures
	drwxr-xr-x+  5 okcoders  staff   170 May 30 12:48 Public
	
The long listing includes file permissions info on the far left, tells us if the file is a directory or a program, gives us the size and the date last modified.

We can also have `ls` show us hidden files with the `-a` flag. It's useful to combine this with the long listing option:

	mbp-phil:~ okcoders$ ls -al
	total 64
	drwxr-xr-x+ 23 okcoders  staff   782 May 31 17:52 .
	drwxr-xr-x   6 root      admin   204 May 30 12:48 ..
	-rw-------   1 okcoders  staff     3 May 30 12:48 .CFUserTextEncoding
	-rw-r--r--@  1 okcoders  staff  6148 May 31 17:55 .DS_Store
	drwx------   2 okcoders  staff    68 May 31 17:52 .Trash
	-rw-------   1 okcoders  staff  2372 May 31 17:51 .bash_history
	-rw-r--r--   1 okcoders  staff    48 May 30 13:29 .bash_profile
	-rw-r--r--   1 okcoders  staff   145 May 31 14:54 .bashrc
	-rw-r--r--   1 okcoders  staff    52 May 30 17:38 .gitconfig
	drwxr-xr-x   6 okcoders  staff   204 May 31 15:08 .heroku
	-rw-------   1 okcoders  staff   201 May 31 14:39 .netrc
	drwxr-xr-x  65 okcoders  staff  2210 May 31 14:55 .npm
	drwx------   5 okcoders  staff   170 May 30 17:40 .ssh
	-rw-------   1 okcoders  staff  1742 May 31 14:58 .viminfo
	drwx------   3 okcoders  staff   102 May 30 12:57 Applications
	drwx------+  3 okcoders  staff   102 May 30 12:48 Desktop
	drwx------+  4 okcoders  staff   136 May 31 14:38 Documents
	drwx------+  4 okcoders  staff   136 May 30 12:48 Downloads
	drwx------@ 46 okcoders  staff  1564 May 31 17:55 Library
	drwx------+  3 okcoders  staff   102 May 30 12:48 Movies
	drwx------+  3 okcoders  staff   102 May 30 12:48 Music
	drwx------+  4 okcoders  staff   136 May 31 14:37 Pictures
	drwxr-xr-x+  5 okcoders  staff   170 May 30 12:48 Public
	
Notice the additional files that appear with the `.` prefix. The `.` prefix tells us the files are hidden and will not normally appear in the Terminal or in the Finder or Explorer.

The two additional directories at the top, `.` and `..` are special constructions to indicate the current directory and the directory one level up in the hierarchy, respectively.

We can list the contents of another directory by passing it as an argument to `ls`. I have one item in my *Documents* directory named *OK-Coders*:

	mbp-phil:~ okcoders$ ls Documents/
	OK-Coders
	
I can list the contents of OK-Coders as well by passing the full filepath *Documents/Ok-Coders*. Note the use of the forward slash to separate the folder names.

	mbp-phil:~ okcoders$ ls Documents/OK-Coders/
	1-bash-heroku
	
## cd

Changes the current directory. Normally you will pass a folder path to the command which identifies the directory you want to change to:

	mbp-phil:~ okcoders$ cd Documents/
	mbp-phil:Documents okcoders$ pwd
	/Users/okcoders/Documents

Notice that the prompt shows that I am in the Documents directory after I `cd` to it: *mbp-phil:Documents*. Prior to changing directories, the prompt showed *mbp-phil:~*.

Often we'll want to move back one level up the directory hierarchy, returning to the folder that contains the directory we're now in. Use the `..` construction to do this:

	mbp-phil:Documents okcoders$ cd ..
	mbp-phil:~ okcoders$ pwd
	/Users/okcoders

If you were in the *Documents* folder, `cd ..` returns you to the home directory, which contains it.

The `~`, or *tilde*, is a special symbol in the terminal which stands for your home directory. Use `~` like you would the name of a folder, and it acts as a shortcut to your home directory:

	mbp-phil:Documents okcoders$ cd ~
	mbp-phil:~ okcoders$ pwd
	/Users/okcoders
	
Using the tilde like this makes it easy to return to our home directory quickly. But actually we can already do this with `cd` when we pass it no arguments:

	mbp-phil:~ okcoders$ cd ~/Documents/OK-Coders/1-bash-heroku/
	mbp-phil:1-bash-heroku okcoders$ pwd
	/Users/okcoders/Documents/OK-Coders/1-bash-heroku
	mbp-phil:1-bash-heroku okcoders$ cd ~
	mbp-phil:~ okcoders$ pwd
	/Users/okcoders
	
Often