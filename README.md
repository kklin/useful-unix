# useful-unix

For our workshop, we'll be building a simple script to convert YouTube videos to mp3 files. You'll learn about some basic command line skills in the process.
Try not violate any copyright laws ;)

### Starting your VM
- *virtualbox ___*

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
- *piping* is a method of connecting multiple commands together. The output of one command becomes the input to another. *|* is the pipe character. For example:
  - *fortune* generates a random fortune (try it!)
  - *cowsay $TEXT* takes some text and makes it look like a cow.. is saying it
    - *cowsay join unix*
  - We could copy and paste the output of *fortune* to be the input to *cowsay* manually.. or we could pipe!
    - *fortune | cowsay* 
- A *for loop* lets you do something *for* each item in an input. The general format is:


*for item in $INPUT ; do command $item ; done*


This takes each word in *$INPUT*, puts in the variable *$item*, and then executes the command *command $item*
  - An example is: *for name in kklin nlsun atran victorchen shwang ianlee ; do echo $name lurvs unix ; done*
- *sudo* lets you run commands as *root*. *Root* can do anything, unlike normal users which are constrained by permissions. If you're interested in the details of permissions, you can ask the Unix team sometime :)

### Setting up youtube-dl and ffmpeg
- sudo apt-get install youtube-dl ffmpeg
- Try it!
  - *youtube-dl https://www.youtube.com/watch?v=719iIW8O37I*

### Time for scripting!
You're going to be modifying the template in ___

What if we want fix the metadata for the mp3's?
 - loop through all the mp3 files
 - print out the filename
 - allow the user to set the song title and artist
 
### Adding it to your PATH

### Extra features (what would you like to add?)
- Background processes
- Automatic metadata generation
- Integrate it with automator on Mac
