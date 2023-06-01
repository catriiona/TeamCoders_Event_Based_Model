# Basic Unix Shell (Terminal) Commands

If you haven't used the command line at the terminal before, we show here the basic commands to know, and you will use them while working with Git.

 We recommend you write the commands down in a list and refer to them until you get familiar.

The shell in the window typically uses $ as the prompt but may use a different symbol. 
At MacOS, the shell opens in the Terminal application and uses the % prompt. In the examples for this lesson, I'll show the prompt as $. Most importantly: when typing commands, either from these lessons or from other sources, do not type the prompt, only the commands that follow it. Also, note that you have to press the Enter key after you type a command to execute it.

The prompt is followed by a text cursor, a character that indicates the position where your typing will appear. 

## Navigate through directories (folders), and nested folders.

The operating system responsible for managing files and directories is called the file system. It organizes our data into files, which hold information, and directories (also called ‘folders’), which contain files or other directories. 

Several commands are frequently used to create, inspect, rename, and delete files and directories. The most frequent one is to know to navigate in directories (folders).
Let's say that we have a home directory `/Users/mary/`
We run the command `pwd` (which stands for ‘**p**rint **w**orking **d**irectory').
If we are at the directory, /Users/mary and run the command.


```bash
pwd
```

The output will be the home directory

```bash
/Users/mary 

```
<!-- Lets create a folder Thesis-->
```bash
mkdir Thesis		
 		

```
In the directory (folder) Thesis at      `/Users/mary/Thesis`  

<!-- Lets move into the folder and show files  -->
``` cd Thesis```
We are now in the directory (folder Thesis). Lets make another directory called Data

there are 6 different files. 
- introduction.doc,  
- data_vis.py
- text.txt, 

- Pictures,mk (this is a directory and ls has not . extension)
  .DS_store.

So let’s try our first command, `ls` (which is short for listing).
This command lists some of the contents of the current directory:

```bash
ls


```

Output

```bash
Pictures		data_vis.py
text.txt 		introduction.doc

```


***ls*** lists all the files which are visual in the current directory if you open the project_1 folder on your desktop.


For complete listing of all the files it's better to run ***ls -a*** (which is  listing  --all and don't ignore entries starting with . all these are hidden files)

```bash
ls -a
```

Output
```bash

.		 Pictures		data_vis.py
..		.DS_store		introduction.doc
.git	 text.txt

```
The files .DS_store and .git are hidden ones and we can only detect them using the *ls -a* command
The commands ***ls -a***,  and ***ls -f***, are the same.

To change directory the commands 'cd' and 'cd ..' could be used (both stand for change directory)
cd , shortcut to go back to the user’s home directory. the cd..  goes back to one level directory.

Lets say we are at the directory \Users\mary\project_1\Pictures 

```bash
cd
```

Output

```bash

\Users\mary

```
and if we start from the   \Users\mary\project_1\Pictures

```bash
cd ..
```

Output
``` bash
\Users\mary\project_1
```

## Files and folder creation 
How to create folders and files within folders (nested folders).
Let's say we are at the directory \Users\mary\project_1, and I want to create another directory called chapter_1.
We use the command ***mkdir***, (which stands for make directory)

Let's start again with the ***pwd*** to verify the directory we are in, then follow with ***ls -a*** to see all files and folders in the directory then with ***mkdir chapter_1*** to make the new directory and finally with ***ls -a*** to see all files and the new directory

```bash
pwd 
```
Output 
```bash 
\Users\mary\project_1 

```
```bash
ls -a
```

Output
```bash
		 Pictures		data_vis.py
..		.DS_store		introduction.doc
.git	 text.txt
```

Next we make a new directory called chapter_1 and check the list of files again. 

```bash
mkdir chapter_1
```
```bash
ls -a
```

Output
```bash
		 Pictures		data_vis.py
..		.DS_store		introduction.doc
.git	 text.txt       chapter_1

```
Now we want to move into the new chapter_1 directory with the **cd chapter_1** command. Then we are into the chapter_1 directory and the paths is  /Users/mary/project_1/chapter_1  

We see that we have created the chapter_1 new directory. 

```bash
cd chapter_1
```
```bash
pwd
```
Output
```bash 
/Users/mary/project_1/chapter_1
```

We want to create a new file called data.doc, into chapter_1 folder, we use the command ***touch*** either for creating one file or multiple ones.

```bash
touch data.doc
ls -a
```
Output 
```bash
.		..		data.doc
```
If we want to create multiple files, even with different extensions for different programmes we use the same command

```bash
touch text1.txt hello.py animals.pdf
ls -a
```
Output
```bash
.		animals.pdf	hello.py
..		data.doc	text1.txt
```
## Move and copy files 
In our  /Users/mary/project_1/chapter_1  directory we have a file text1.txt  which isn’t a particularly informative name, so let’s change the file’s name using ***mv***, which is short for ‘move’to quote.txt:
First thing to do is to create the file `quote.txt`  using the ***touch*** command. Then use the ***mv*** with two arguments (where is moving the file and to where the movement is done)

```bash
touch quotes.txt
mv chapter_1\text1.txt  chapter_1\quotes.txt 
ls -a
```

Output
```bash
.		animals.pdf	quotes.txt
..		data.doc	text1.txt
```
This overwrites what is in quotes.txt with the content of the test1.txt, so it has to be used with caution.
### Move file to another directory##
Lets ay that we want to move the file data.doc from the chapter_1 folder to the oen above directory which is the project_1. We again use ***mv*** but with different arguments.

To move in the nesting :  /Users/mary/project_1/chapter_1

```bash
mv data.doc ..  ## the .. denotes one directory up (here is project_1 )
ls -a    ## this lists files in the chapter_1 directory 
```
Output
```bash
.		..		animals.pdf	
quotes.txt	
text1.txt
```
The data.doc doesn't exists at the chapter_1 folder anymore
When you go up one directory at the project_1 folder and look in the file list, we will found it there.

```bash
cd  ..  ## goes up one directory up (here is project_ )
ls -a    ## this lists files in the project_1 directory 
```

Output

```bash
Pictures		data.doc		introduction.doc
chapter_1		data_vis.py		text.txt
```
The data.doc has moved to the project_1 folder.


### Copying files and directories

The ***cp*** command works very much like ***mv***, except it copies a file instead of moving it. We can check that it did the right thing using ***ls*** with two paths as arguments — like most Unix commands, ls can be given multiple paths at once:

```bash
cp data.doc draft.doc  ## copies the file data.doc to a new file draft.doc (it creates it automatically although  ##we haven't created )
ls -a    ## this lists files in teh chapter_1 directory 
```
Output
```bash
Pictures		data_vis.py		text.txt
chapter_1		draft.doc
data.doc		introduction.doc
```

If we want to copy a folder (directory) and all its contents by using the recursive option -r, e.g. to back up a directory:

```bash
cp -r Pictures Pictures_backup

ls 
```

Output
```bash
Pictures		data.doc		introduction.doc
Pictures_backup		data_vis.py		text.txt
chapter_1		draft.doc
```


## Delete files or directories
If we want to *delete a file* we use the **rm** file command which stands for remove

```bash
rm text.txt 
ls -a
```
Output
```bash
Pictures		data.doc		introduction.doc
Pictutes_backup		data_vis.py
chapter_1		draft.doc
```
The file text.txt doesn't exist anymore and it's been deleted forever. Beware that the unix shell doesn't have  a trash bin and we can recover deleted files. 


If we want to *delete a folder* we use the ***rm -r*** file command

```bash
rm -r Pictures 
ls 
```
Output
```bash
	Pictutes_backup		data_vis.py
	chapter_1		draft.doc
	data.doc		introduction.doc
```
The folder Pictures  doesn't exist anymore. 

## Open an editor from terminal
Writing a document using the terminal is not as straight forward.
The terminal does not support .doc or .md formats.
The way to write a text file is to open an editor called **nano** 

When we say, ‘nano is a text editor’ we really do mean ‘text’: it can only work with plain character data, not tables, images, or any other human-friendly media. We use it in examples because it is one of the least complex text editors. However, because of this trait, it may not be powerful enough or flexible enough for the work you need to do after this workshop. We use it to create text files and during the workshops we modify them to demonstrate the work with Git and GitHub


Let's open the text editor and start writing the text:

```bash

$ cd thesis
$ nano draft.txt
```

The steps how to write and save using the nano editor are in the picture
![nano editor](nano_edits.png) 

Let’s type in a few lines of text. Once we’re happy with our text, we can press Ctrl+O (press the Ctrl or Control key and, while holding it down, press the O key) to write our data to disk (we’ll be asked what file we want to save this to: press Return to accept the suggested default of draft.txt).


These are the most commonly used Unix shell commands, you will be more confortable to use them with practice.
There are commands that facilitate operations with multiple files and folders. Others that can create pipelines and filters. If you want to dive into the Unix shell and explore more the capabilities the [The Unix Shell](https://swcarpentry.github.io/shell-novice/) software carpentry course is recommended.


More commands at the site 