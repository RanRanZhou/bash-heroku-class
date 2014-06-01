Using The Command Line
====

What is the command line?

How does the command line work? What do command line arguments look like?

	command -options arguments

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
	Applications	Documents	Library		Music	Public	Desktop		Downloads	Movies	Pictures
	
We can pass the `-l` flag to `ls` to show the long listing, which includes additional information about the files:

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
	
The long listing shows file permissions on the far left, tells us if the file is a directory or a program, and gives us the size and the date last modified.

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
	
I can list the contents of OK-Coders by passing the full filepath *Documents/Ok-Coders*. Note the use of the forward slash to separate the folder names.

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
	mbp-phil:1-bash-heroku okcoders$ cd
	mbp-phil:~ okcoders$ pwd
	/Users/okcoders
	
## mkdir

Creates a folder just like creating a new folder in the Finder or in Explorer. Pass it the name of the folder you want to create:

	mbp-phil:~ okcoders$ mkdir "OK-Coders"
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Pictures	Desktop		Downloads	Movies	OK-Coders	Public

Notice that *OK-Coders* now appears in my home folder, and we'll see it from the Finder or Explorer as well. It exists on my computer like any other folder.

Notice that I put the name of the folder in quotes. This is optional when the name does not contain any spaces or other special characters. Otherwise you must use quotes for the name. The applies to all commands that take filenames or filepaths.

Create many directories at the same time by passing thier names to `mkdir`, separated by a space:

	mbp-phil:~ okcoders$ mkdir dir1 dir2 dir3
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public		dir2	Desktop		Downloads	Movies	Pictures	dir1		dir3

## rmdir

Removes the directory specified. Go ahead and remove the *OK-Coders* directory you just created:

	mbp-phil:~ okcoders$ rmdir OK-Coders/
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public	Desktop		Downloads	Movies		Pictures
	
It's gone! Remove many directories at the same time by providing their names, separated by a space:

	mbp-phil:~ okcoders$ rmdir dir1 dir2 dir3
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public	Desktop		Downloads	Movies		Pictures

Normally you won't use the `rmdir` command; you'll use the `rm` command instead. See below for details.

## touch

Changes the date modified property of a file and is often used to create an empty file. We'll normally use it to create new, empty files:

	mbp-phil:~ okcoders$ touch newfile.txt
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public	Desktop		Downloads	Movies		Pictures	newfile.txt
	
## rm

Remove a file or directory, that is, delete it. Remove the *newfile.txt* file you just created:

	mbp-phil:~ okcoders$ rm newfile.txt
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public	Desktop		Downloads	Movies		Pictures

Removing a directory is not as straightforward. Create a new directory called *test* and try to remove it with `rm`:

	mbp-phil:~ okcoders$ mkdir test
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public	Desktop		Downloads	Movies		Pictures	test
	mbp-phil:~ okcoders$ rm test
	rm: test: is a directory

Without passing additional options, `rm` will not delete a diretory. It returns the error, *test: is a directory*. To delete a directory, include the `-r` option, which tells `rm` to empty the contents of the directory first and then delete the directory:

	mbp-phil:~ okcoders$ rm -r test
	mbp-phil:~ okcoders$ ls
	Applications	Documents	Library		Music	Public	Desktop		Downloads	Movies		Pictures

Be careful with `rm`. The command line assumes you know what you are doing. It will not ask if you are sure you want to execute a command, and commands cannot be undone. When you remove a file or folder, it is gone.

## mv

Move a file or directory. Move is also used to rename files.

## cp

Copy a file or directory.

## cat

Concatenate and print files. `cat` allows us to modify files from the command line and to quickly view the contents of files.

## which

Indicates which executable will be used for a program and where it is located. Use `which` to confirm that you have installed a command line program:

	mbp-phil:bash-heroku-class okcoders$ which node
	/usr/local/bin/node
	mbp-phil:bash-heroku-class okcoders$ which express
	/usr/local/bin/express
	
