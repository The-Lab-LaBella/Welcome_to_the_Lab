# Quick Start Guide to the UNC Charlotte HPC

I've outlined below some guidelines for getting started with the UNC Charlotte research HPC. This is **not** the only way to set up your work.

Other resources include

-   The UNC Charlotte guide: <https://oneit.charlotte.edu/urc/get-started/>

[Getting access to the Research Cluster](#getting-access-to-the-research-cluster)

[Logging into the Research Cluster](#logging-into-the-research-cluster)

[Home, Scratch, and Projects](#home,-scratch,-and-projects)

[Transferring Data](#transferring-data)

[Editing Files & Text Editors](#editing-files-text-editors)

[Submitting jobs to the cluster](#submitting-jobs-to-the-cluster)

[Data Management](#data-management)

[Permissions](#permissions)

[Preserving session](#preserving-session)

[Using and Installing Programs and Packages](#using-and-installing-programs-and-packages)

[Dr. LaBella's favorite bash commands](#dr.-labellas-favorite-bash-commands)

[Getting Help](#getting-help)

### Getting access to the Research Cluster {#gettting-access-to-the-research-cluster}

There are two types of accounts on the cluster: student and research accounts. **If you had a student account for a class you will need a research account!**

To request a **research account** use this page: <https://oneit.charlotte.edu/urc/get-started>

### Logging into the Research Cluster {#logging-into-the-research-cluster}

Options for logging into the cluster for different systems include:

**MacOS**

-   ssh Client (Included in MacOS)

-   iTerm2 ([https://iterm2.com/)](https://iterm2.com/))

**Windows**

-   PuTTY ([https://www.chiark.greenend.org.uk/\~sgtatham/putty/)](https://www.chiark.greenend.org.uk/~sgtatham/putty/)) (this is what I use

-   MobaXTerm ([https://mobaxterm.mobatek.net/)](https://mobaxterm.mobatek.net/))

**Logging on off campus**

To log into the research cluster **off campus** you will need to set up a VPN. For instructions on the VPN see this link: <https://spaces.charlotte.edu/pages/viewpage.action?pageId=6653379> This requires DUO authentication

**Logging onto the HPC**

**Login:** (*Your NinerNET ID --- without "\@uncc.edu")*\
**Password:** (*Your NinerNET ID Password)*\
**SSH Server:** *hpc.uncc.edu*

**TIPS:**

-   MobaXTerm has an issue with Duo that can be solved by using the *Create/Save a Session* functionality as opposed to the *Start local terminal* function.

-   The server is hpc.uncc.edu NOT student_hpc.uncc.edu

-   Your NinerNet ID is NOT your 800 number (it should be letters followed by numbers)

-   There are two head nodes in the HPC 10.16.115.245 and 10.16.115.244. You can use one of those numbers to directly log into one of the head nodes. This is helpful if one of the head nodes isn't working correctly

### Home, Scratch, and Projects {#home,-scratch,-and-projects}

Each research user has automatic access to two places in the cluster.

**Home: /usrs/username**

Home is where you **keep your most precious data**. Each user has a 500 GB home directory that is backed up for disaster recovery. Space is limited so only keep what is absolutely necessary

**Scratch: /scratch/username**

You are automatically provided with a scratch directory. This is where you want to **conduct analyses.** You have up to 10TB of space here to test, run, analyze, and keep intermediate files. But remember, this is *not backed up*and could be lost.

**Projects: /projects/labella_lab**

To access our shared project space you will need to be approved. This is where we keep shared data that will need to be accessed by multiple people.

Note: if you create or add something here you will need to ensure you enable the proper permissions to allow others to see and/or edit the files.

### Transferring Data {#transferring-data}

HPC has put together some information for transferring data to and from the cluster which you can read here: <https://spaces.charlotte.edu/pages/viewpage.action?pageId=110232096>

You can use the command line to transfer data, but if you want to see the file/folder structure you can use a GUI (graphical user interface)

The added bonus of using a **GUI to transfer files** is that many of them allow you to edit your files in your text editor of choice (see below for text editors). Some even have a 2-in-1 and include a text editor (like MobaXTerm)

Two popular file transfer GUIS are

FileZilla <https://filezilla-project.org/>

CyberDuck <https://cyberduck.io/>

### Editing Files & Text Editors {#editing-files-text-editors}

There are several ways to edit files which are housed in the Cluster.

#### Editing files in the command line

Options include

-   Downloading and Uploading files

-   Editing in the command line

-   Using a GUI with a text editor

**Downloading and Uploading files**

This it the most cumbersome way to go about editing files but sometimes may be necessary. Just download the file, then re-upload and replace the original

**Editing in the Command Line**

You can edit files directly in the command line using something like VIM. For more info on using VIM see this cheat sheet: <https://vim.rtorr.com/> and introduction: <https://www.tutorialspoint.com/vim/vim_getting_familiar.htm>

**Editing with a GUI and text editor**

Some GUIs will have a built in text editor (like MobaX) while others will open files in your chosen text editor.

There are many free text editors geared towards programming including:

-   Sublime Text ( <https://www.sublimetext.com/> )

-   Notepad++ (windows only <https://notepad-plus-plus.org/> )

-   jEdit (oldschool but it's what I use <http://www.jedit.org/> )

Features in jEdit that I like (that are probably available in other text editors

-   Syntax highlighting for languages like perl and python

-   Regular expression search and replaces

-   Multiple file view

-   View and switch encoding (Unix (\\n), Windows (\\n\\r), and MacOS (\\r)

### Submitting jobs to the cluster {#submitting-jobs-to-the-cluster}

The *head nodes* are what you log into when you SSH into the cluster. They have limited capabilities to run jobs (not much memory) and everyone is using them to test/develop/organize/upload data.

Often we need to run many jobs at once (an array), long jobs (many days), or high memory jobs. These are run on the other cores in the cluster.

To run one of those jobs you need to submit a set of instructions (a **slurm script)** to the **scheduler**. The scheduler is in charge of deciding when to run what scripts on which cores to *maximize* the number of jobs running at once.

If you have a long or memory intensive job, you may have to wait until there is enough time/resources in the schedule to slot you in.

If you have a short job, you may jump to the front of the line in a space created before a long job is scheduled.

**Slurm Scripts**

To send the set of instructions in a slurm script you must *include every piece of information that the cluster would need to know!* This includes any modules you have loaded or other info

Our HPC has put together some guidelines for submitting slurm scripts here: <https://spaces.charlotte.edu/pages/viewpage.action?pageId=110232094> and here: <https://oneit.charlotte.edu/urc/research-clusters/orion-gpu-slurm-user-notes>

You can also find sample slurm scripts for a wide array of applications on the cluster here: **/apps/slurm/examples**

### Data Management {#data-management}

This section probably deserves it's own tutorial because **DATA MANAGEMENT IS SO IMPORTANT!!**

**ORGANIZE YOUR DATA -** Below are some of the basics of data organization

-   Create and maintain standard file names

-   Include README files in your folders describing the data and how/when it was generated

-   Give your folders and files short but descriptive names

**RECORD YOUR ANALYSES -** Nothing is worse than needing to re-generate data or update an analysis and **not remembering** what you did. Here are some tips to avoid that

-   Run all commands you would run in the head nodes through bash scripts to record the commands

-   Keep a lab notebook where you record what you have done every analysis day. This could be in a markdown file, on google drive, in a txt file.

### Permissions {#permissions}

Each file has a set of associated permissions that describes who can read, edit, and execute files.

You should **never modify the permission of files in your scratch or home directory**

However, if you are creating shared resources or programs for the project space you will need to modify those permissions.

Linux file permissions can be set to

-   Read

-   Write

-   Execute

And these can be applied to any or all of the following groups

-   User (you)

-   Group (members of the same group)

-   Other (all other users)

The linux permissions are displayed in this way:

![](images/linux.webp){width="339"}

To **view permissions** you can us `ls -l`

To **modify permissions** you use the command `chmod`

Use chmod with caution! If you need to change a file permission in the project space check with Dr. LaBella first

You can find a tutorial on updating file permissions here: <https://www.booleanworld.com/introduction-linux-file-permissions/>

### Preserving sessions {#preserving-session}

If you have unstable internet, the VPN is prone to disconnecting or you just want to be extra careful you can use **tmux to preserve your session.**

You can also do cool things like

-   Split the screen into multiple sessions

-   Save your session

-   Create custom sessions for different purposes

**tmux** is already installed on the cluster. You can learn more about how to use it at these resources:

-   <https://www.redhat.com/sysadmin/introduction-tmux-linux>

-   <https://github.com/tmux/tmux/wiki>

### Using and Installing Programs and Packages {#using-and-installing-programs-and-packages}

**Modules already installed**

There are many programs **already installed** on the cluster that you can access using the module system. You can learn about the modules and how to use them here: <https://spaces.charlotte.edu/pages/viewpage.action?pageId=110232107>

Common modules you may use are

-   vcftools

-   muscle

-   mafft

-   hmmer

-   blast

-   anaconda

-   R

-   raxml

**New programs or packages**

This will likely be one of the most frustrating and often painful things you will try to do. Try to remember that **sometimes it won't work**. There are often dependencies that we cannot install. Conflicts that arise when dependencies are updated. Sometimes experiments fail, and installing new packages or programs is an experiment.

Remember, you are installing **locally** to one of your own directories. If the package automatically installs to a particular place you may need to specify that it should be installed locally. If you are using `make` to install a package you can follow these instructions to install it locally--ie on your home or scratch drive <https://www.baeldung.com/linux/change-install-dir-make-install>

**Standalone Packages** - Sometimes you will find a program that comes with a tidy standalone packages that you can install using their instructions. This is the best case scenario! Make sure you use the linux version. You may also want to install it in your home directory

**Docker and Singularity** - Software today are often packaged in a *container (image)* such that almost everything you need is contained in this container. To learn more see here: <https://oneit.charlotte.edu/urc/research-clusters/singularity/>

**Python packages and programs** - The easiest way to install python based packages and programs is to do so in a **conda** environment. This will require the **Anaconda** environment/module to be loaded. You can learn more here: <https://astrobiomike.github.io/unix/conda-intro#creating-and-navigating-environments>

**R or Perl modules not installed on the cluster** - Email me, and we will go over it!

You can also open a help ticket and the cluster admins may install the package/software/dependencies for you!

**.bashrc and PATH**

This is **risky territory**. Changing your .bashrc file and PATH variable can make your experience unstable and render your profile unusable! (ok that's a bit dramatic but don't go into this lightly)

The hidden (note the `.` in front of the file name) **`.bashrc`** file contains a list of customization options for the bash shell and is loaded at each launch. You may want to edit your .bashrc file to

-   Automatically load particular modules

-   Create aliases (aka short version of long command)

-   Make functions

-   Modify your PATH variable

To learn more about the .bashrc file and how to change it see: <https://www.maketecheasier.com/what-is-bashrc/>

Your `PATH` is a special variable that stores information about where the system should *search for files while running programs.* So, if you install a program in a non-standard location and want to run it without a full path you will need to modify your `PATH`.

For instructions on how to modify your path see: <https://phoenixnap.com/kb/linux-add-to-path#ftoc-heading-1>

### Dr. LaBella's favorite bash commands {#dr.-labellas-favorite-bash-commands}

If you as me for help, I will probably use some combination of the commands below! Take a look and reference this if I ever send you a sample script

**Loops**

If you need to do something over and over again in bash you can use a loop!

This loop will identify every file ending in `.fas` , save it to a variable called file, and apply the perl script `fasta_to_one_line.pl` to the variable \$file

``` bash
for file in *fas
do
  perl fasta_to_one_line.pl $file
done
```

**notes:** when you first declare a variable (in the first line) you don't use the \$. When you then want to refer to the information stored in the variable later, you use the dollar sign \\\$

The `*` is a wildcard and will match anything any number of times. So it would include `abcdef.fas` and `12345.fas`

**Editing strings (aka file names) in a loop**

Let's imagine we want to do the same thing as above, but save the output into a new file with the name "out"

So if our file is `species1.fas` we would save the output into `species1.out` . This will preserve our file name! (Great file management)

``` bash
for file in *fas
do
  out=${file/fas/out}
  perl fasta_to_one_line.pl $file > $out
done
```

**notes:** Note again, that when we create the new variable `out` we don't use the \$ the first time around.

The syntax of the third line is

`${string/replace/with.this}`

**Editing a file with sed**

If you want to replace every instance of a file with another string a great way to do that is with `sed`

For a full tutorial see: <https://www.geeksforgeeks.org/sed-command-in-linux-unix-with-examples/>

But as a basic example, let's imagine we have a bunch of fasta files and we want to add the filename to the beginning of every sequence header. We can use sed!

``` bash
 for file in *fas
  do 
    name=${file/.fas/}
    echo $name
    sed -i 's/>/>$name /g' $file
  done
```

**notes:** using echo is a great way to make sure your variable is storing what you think it is! In this case if our files are still species1.fas and species2.fas it will print

`species1`

`species2`

### Getting Help {#getting-help}

-   Google

-   StackExchange

-   HPC Help - Open a Ticket <https://oneit.charlotte.edu/help/>

-   Email the makers of the software or look at their message boards! Most developers *want* you to use their software. So they will help you out or even make updates to help you!
