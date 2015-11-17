# useful-unix

For our workshop, we'll be building a simple script to convert YouTube videos to mp3 files. You'll learn about some basic command line skills in the process.

Try not to violate any copyright laws ;)

### Your VM
- Starting the VM:
  - Open VirtualBox
  - File -> Import Appliance
- Enabling copy-paste:
  - Settings -> Advanced -> Shared Clipboard
    - Set to *Bidrectional*
- User credentials
  - You shouldn't need it, but:
    - Username: *useful-unix*
    - Password: *jo1nun1x*

### Unix Basics
Here are some commands and concepts that you'll find useful later:
- *variables*:
  - To reference a variable, you need to precede it with a dollar sign
  - To set a variable, you just do *variable="value"*. The lack of spaces is important!
  - e.g. *name="Kevin" ; echo "Hello $name"*
- *man $COMMAND*: displays documentation about the command
  - e.g. *man youtube-dl* 
- *cd*: changes your current working directory. Basically, this changes where you are in your computer.
- *ls*: list files in current working directory
  - You can also *ls* files that match a certain pattern. e.g. *ls *.avi* will list all files in the current directory that end in *.avi*.
- *mv $FILE $DEST*: moves a file (or multiple files) to a different place
- A *for loop* lets you do something *for* each item in an input. The general format is:
  - *for item in $INPUT ; do command $item ; done*
    - This takes each word in *$INPUT*, puts in the variable *$item*, and then executes the command *command $item*
  - An example is: *for name in kklin nlsun atran victorchen shwang ianlee ; do echo $name lurvs unix ; done*
  - If we want to loop over filenames in our current directory, we can replace $INPUT with a *regex*. For example, *for item in ** loops over all files, and *for item in *.mp3* loops over all mp3 files.
- *sudo* lets you run commands as *root*. *Root* can do anything, unlike normal users which are constrained by permissions. If you're interested in the details of permissions, you can ask the Unix team sometime :)
- Quotes are important. If you don't quote multi-word arguments, commands will think that you're providing multiple arguments when you're really only providing one.
- *piping* is a method of connecting multiple commands together. The output of one command becomes the input to another. *|* is the pipe character. For example:
  - *fortune* generates a random fortune (try it!)
  - *cowsay $TEXT* takes some text and makes it look like a cow.. is saying it
    - *cowsay join unix*
  - We could copy and paste the output of *fortune* to be the input to *cowsay* manually.. or we could pipe!
    - *fortune | cowsay* 

### Setting up ffmpeg
- sudo apt-get install ffmpeg

### Doing it by hand
 - *youtube-dl https://www.youtube.com/watch?v=719iIW8O37I*
 - *ffmpeg -i "[CS61C] - End of the Year Song (Fall 2014)-719iIW8O37I.mp4" "[CS61C] - End of the Year Song (Fall 2014)-719iIW8O37I.mp4.mp3"*
 
### Time for scripting!
You're going to be modifying the template in [ytmp3](ytmp3)

What if we want fix the metadata for the mp3's?
 - loop through all the mp3 files
 - print out the filename
 - allow the user to set the song title and artist
 
### Accessing Plex
 - Settings -> Network -> Adapter 1 -> Port Forwarding
 - Add a new rule where:
    - *Host IP* is *127.0.0.1*
    - *Host Port* is *32400*
    - *Guest IP* is *10.0.2.15*
    - *Guest Port* is *32400*
 - Now you can go to *http://127.0.0.1:32400/web/index.html* from outside the VM
    
### Adding it to your PATH
  - Ask a sysadmin

### Extra features (what would you like to add?)
- Background processes
- Only prompt for metadata if the appropriate option is set
- Automatic metadata generation
- Integrate it with automator on Mac
