# COBOL Code for use in Projects Honoring Grace Hopper. #
    
In honor of Rear Admiral Grace Hopper, computer pioneer and inventor
of the compiler, I learned enough COBOL over a weekend to write a simple
program that does some rudimentary statistics.

The name of the program, ACTUAL-BUG-INSTANCES, refers to the famous
joke she made at Harvard, when a moth caught in a relay caused a computer
failure and she taped the unfortunate insect into her logbook with the
note, "First actual case of bug being found."

You can see a picture of the log entry (and the moth!) here:
http://www.computerhistory.org/tdih/September/9/

I'm releasing this freely so that anyone who wants to include some COBOL
code in a design honoring Admiral Hopper can draw on it.

Jacob Rose

Brooklyn, New York

September 17, 2016

# If you just want to look at the COBOL code #

Here it is: https://raw.githubusercontent.com/jacobrose/grace_hopper/master/bugs.cobol

# Running the code #

You'll need to get a COBOL compiler. If you're on a Unix-style system,
for instance a Mac running OS X or any Linux PC, you can use GNU COBOL,
available from the Free Software Foundation here:

> https://directory.fsf.org/wiki/Cobol
>
> (Click "Download," then choose the most recent version)

You'll need to get their "Gmp" math library as well:

> https://directory.fsf.org/wiki/Gmp
>
> (Click "Download," then choose the most recent version)

And the "Berkeley DB" library from Oracle (formerly from Sleepycat software):

> https://directory.fsf.org/wiki/Berkeley_Database
>
> (Click "Download," then click the latest version, set up an Oracle account, log in, and your download will begin)

## If you're on a Mac, you'll need to install XCode ##

XCode is Apple's software development suite. It includes all the tools you'll need to build software on your computer. Get it from the App Store. It will take a long time to download and install, but it's the first tool you'll need if you are interested in writing software for OS X or iOS.

## Open a terminal and build the Gmp math library ##

Lines that start with "$" are commands you'll type.

NOTE: Don't type the "$"! Everything after the "#" is just my commentary on each step, and you don't need to type that either!

> $ cd ~/Downloads _# or wherever your downloads are_
>
> $ tar -xjf gmp-6.1.0.tar.bz2 _# or whatever version of Gmp you got_
>
> $ cd gmp-6.1.0 _# or whatever directory was created by the above tar command_
>
> $ ./configure
>
> _...a whole lot of text will scroll by as "configure" figures out how to build Gmp on your computer..._
>
> $ make
>
> _...a whole lot of text will scroll by as "make" builds the Gmp library..._
>
> $ sudo make install
>
> Password: 

Enter your password, and "make" will complete the installation of Gmp.

## Now build the Berkeley DB library ##

The steps are nearly identical, so I'm providing them with less commentary

> $ cd ~/Downloads
>
> $ tar -xzf db-6.2.23.tar.gz _# slightly different options because file is .gz, not .bz2_
>
> $ cd db-6.2.23
>
> $ dist/configure --enable-sql_compat _# Oracle puts "configure" in a sub-folder -- the option gives you sqlite3, too_
>
> ...
>
> $ make
>
> ...
>
> $ sudo make install
>
> Password:

## Now build the GNU Cobol compiler ##

By now you're a pro at this! Very similar steps to Gmp.

> $ cd ~/Downloads
>
> $ tar -xzf gnu-cobol-1.1.tar.gz
>
> $ cd gnu-cobol-1.1
>
> $ export CPATH=/usr/local/BerkeleyDB.6.2/include/ _# tell "configure" where to find Berkeley DB_
>
> $ export LIBRARY_PATH=/usr/local/BerkeleyDB.6.2/lib/
>
> $ ./configure
>
> ...
>
> $ make
>
> ...
>
> $ sudo make install
>
> Password:

Enter your password, and the COBOL compiler will be installed and ready to use!

## Now you can compile and run bugs.cobol ##

Go to the directory where you checked out this code.

> $ cd grace_hopper _# or wherever bugs.cobol is_
>
> $ cobc -L /usr/local/BerkeleyDB.6.2/lib/ bugs.cobol -x 
>
> $ ./bugs
