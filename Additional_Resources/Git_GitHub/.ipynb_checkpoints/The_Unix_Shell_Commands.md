# **Basic Unix Shell (Terminal) Commands**

If you haven't used the command line at the terminal before, we show here the basic commands to know, and you will use them while working with Git.

 We recommend you write the commands down in a list and refer to them until you get familiar.

The shell in the window typically uses the (dollar symbol) as the prompt . 
At MacOS, the shell opens in the Terminal application and uses the % prompt. In the examples for this lesson, I'll show the prompt as $. Most importantly: when typing commands, either from these lessons or from other sources, do not type the prompt, only the commands that follow it. Also, note that you have to press the Enter key after you type a command to execute it.

The prompt is followed by a text cursor, a character that indicates the position where your typing will appear. 

## **Navigate through directories (folders), and nested folders.**

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
To see what is into a directory use the ls command: To find the usage of ls type **man ls** (which stand for manual of ls)

***ls*** lists all the files which are visual in the current directory if you open the project_1 folder on your desktop.


For complete listing of all the files it's better to run ***ls -a*** (which is  listing  --all and don't ignore entries starting with . all these are hidden files)

```bash
ls -a
```

Output : For example is the following (it will not be  same at your directory!!)
```bash

.		 Pictures		data_vis.py
..		.DS_store		introduction.doc
.git	 text.txt

```
The files .DS_store and .git and everything that starts with (.) or(..) are hidden directories and we can only detect them using the *ls -a* command
The commands **ls -a** list all the files (and the hidden ones),  and **ls -F**, are the same. The **ls -F** lists the directories with the/ ending 

To change directory the commands 'cd' and 'cd ..' could be used (both stand for change directory)
cd , shortcut to go back to the user’s home directory. the cd..  goes back to one level directory.

Lets say I am  in the directory \Users\mary\Pictures\Flowers

```bash
pwd
```

Output:
```bash
Users\mary\Pictures\Flowers
```

\Users\mary (which is the homedirectory)


and if we start from the   \Users\mary\Pictures\Flowers

```bash
cd ..
```

The path that we will be in is 
\Users\mary\Pictures

## Files and folder's creation 
How to create folders and files within folders (nested folders).
Let's say we are at the directory \Users\mary\project_1, and I want to create another directory called chapter_1.
We use the command ***mkdir***, (which stands for make directory)

Let's start again with the ***pwd*** to verify the directory we are in, then follow with ***ls -a*** to see all files and folders in the directory and then with ***mkdir project_1*** to make the new directory and finally with ***ls -a*** to see all files and the new directory

```bash
pwd 
```
Output 
```bash 
\Users\mary

```


Next we make a new directory called chapter_1 and check the list of files again. 

```bash
mkdir project_1

```
Then change the directory and enter the project_1 directory 
```bash
cd project_1
```

Then make other directories called chapter_1 and chapter_2
```bash
mkdir chapter_1
mkdir chapter_2
```

Create a files using the **touch** command

```bash
touch text.txt
touch intro.doc
```
Lets see what is in the project_1 folder: Use **ls -a** 

```bash
ls -a 
```
Output
```bash
		 chapter_1		chapter_2
..		text.txt 		intro.doc

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
touch text1.txt hello.py animals.csv
ls -a
```
Output
```bash
.		animals.csv	hello.py
..		data.doc	text1.txt
```

## **Open an editor from terminal**
Writing a document using the terminal is not as straight forward.
The way to write a text file is to open an editor called **nano** 

When we say, ‘nano is a text editor’ we really do mean ‘text’: it can only work with plain character data, not tables, images, or any other human-friendly media. We use it in examples because it is one of the least complex text editors. However, because of this trait, it may not be powerful enough or flexible enough for the work you need to do after this workshop. We use it to create text files and during the workshops we modify them to demonstrate the work with Git and GitHub. Here I show how to create a .doc file but usually we use nano for .txt files


Let's open the text editor and start writing the text:

```bash
$ nano data.doc
```

The steps how to write and save using the nano editor are in the picture
![nano editor](./fig/nano_editor.jpg) 


Let’s type in a few lines of text. Once we’re happy with our text, we can press Ctrl+O (press the Ctrl or Control key and, while holding it down, press the O key) to write our data to disk (we’ll be asked what file we want to save this to: press Return to accept the suggested default of data.doc).


## **Move one file over another (overwrite)** 
In our  /Users/mary/project_1/chapter_1  directory we have a file text1.txt  which isn’t a particularly informative name, so let’s change the file’s name using ***mv***, which is short for ‘move’to quote.txt:
First thing to do is to create the file `quotes.txt`  using the ***touch*** command. Then use the ***mv*** with two arguments (where is moving the file and to where the movement is done)
(Just type the commands without the comments in green)

```bash
touch quotes.txt
mv text1.txt  quotes.txt  # moves a file from the an initial place to final (source to destination) 
ls -a
```

Output
```bash
.		animals.csv	hello.py
..		data.doc	quotes.txt
```
This overwrites what is in quotes.txt with the content of the test1.txt, so it has to be used with caution.
### **Move file to another directory**
Lets ay that we want to move the file data.doc from the chapter_1 folder to the oen above directory which is the project_1. We again use ***mv*** but with different arguments.

To move in the nesting :  /Users/mary/project_1/chapter_1

```bash
mv animals.csv ../chapter_2/animals.csv   
ls -a    
```
Output
```bash
.		..		data.doc	hello.py
quotes.txt	

```
In the command above the  ## the .. denotes to change the path one directory up (here is project_1 ) and then directs it into  chapter_2. 

The animal.csv doesn't exists at the chapter_1 folder anymore
When you go up one directory at the project_1 folder and then into the chapter_2 folder (../chapter_2) look in the file list, we will found it there.

(Just type the commands without the comments in green)

```bash
cd ../chapter_2  ## (..) goes up one directory  (here is project_ 1) and then in the chapter_2 subdirectories
ls     ## this lists files in the project_1 directory 
```

Output

```bash
animals.csv
```
The animals.csv has moved to the project_1/ chapter_2 folder.
Now move back to the project_1 directory 
```bash
cd ..

```
Output
/Users/mary/project_1/


## **Copying files and directories**

The ***cp*** command works very much like ***mv***, except it copies a file instead of moving it. We can check that it did the right thing using ***ls*** with two paths as arguments — like most Unix commands, ls can be given multiple paths at once:
You should be in the project directory(/Users/mary/project_1/)
(Just type the commands without the comments in green)

```bash
cp  chapter_1/data.doc backup.txt  ## copies the file data.doc that is in chapter_1 subdirectory to a new file backup.txt in the project_1 directory (it creates the file automatically although its didn't exist )
ls -F    ## this lists files and folders in the chapter_1 directory 
```
Output
```bash
backup.txt	chapter_2/	text.txt
chapter_1/	intro.txt	
```

If we want to see what is written at the backup.txt we use the **cat** command

```bash
cat backup.txt
```
Output:
```bash

This is document describes the structure of the data that we have collected.
```
It is  the sentence we wrote with the nano editor



If we want to **copy a folder (directory)** and all its contents by using the recursive option -r, e.g. to back up a directory:

```bash
cp -r chapter_1 chapter_1_backup

ls 
```

Output
```bash
backup.txt		chapter_1_backup/	intro.txt
chapter_1/		chapter_2/		text.txt
```
If I want to see what is in the chapter_1_backup folder 

```bash
 ls -F chapter_1_backup/

```

Output
```bash
data.doc	hello.py	quotes.txt
```
```bash
 ls -F chapter_1/

```
Output
```bash
data.doc	hello.py	quotes.txt
```
The output is the same in both folders as the folder (chapter_1_backup/) was copied from the (chapter_1)
## Delete files or directories
You should be in the project directory(/Users/mary/project_1/)
If we want to **delete a file** we use the **rm** file command which stands for remove

```bash
rm text.txt 
ls -F
```
Output
```bash
backup.txt		chapter_1_backup/	intro.txt
chapter_1/		chapter_2/cd 
```
The file text.txt doesn't exist anymore and it's been deleted forever. Beware that the unix shell doesn't have  a trash bin and we can recover deleted files. 


If we want to *delete a folder* we use the ***rm -r*** file command

```bash
rm -r chapter_2 
ls -Fls
```
Output
```bash
backup.txt		chapter_1_backup/
chapter_1/		intro.txt
```
The folder chapter_2  doesn't exist anymore. 


## Summary of the most common commands 

|Command  | Name | Function |Usage|
|---|---|---|---|
| pwd | Print Working Directory | Where am I?|pwd|
| mkdir | Make directory| Create a new directory| mkdir directoryName|
| cd | Change directory |Go to the following location|cd dir1 or cd /home/dir1|
| cd.. | Change to the directory above |Go to the directory that contains this one|cd .. |
|ls |List|Shows what is inside a directory|ls dir1|
|ls -help |List help option|understand  the command |ls help|
|man ls |Manual for the ls command|Shows the syntax |man ls|
|ls -F |List with F option |Shows what is inside a directory (directories / and executable*) |ls -F  dir1|
|ls -a |List with a option |Shows what is inside a directory, hidden directories) |ls -a  |
|cp|Copy|Copies a file to a new location|cp source-file destination-file|
| mv|Move|Moves a file to a new location|mv source-file destination-file|
| rm | Remove |Deletes a file |rm dir1/bad_file|
| rm -r| Remove |Deletes a  directory|rm -r  dir1|
| nano | Text editor|Edit plain text files|nano results.txt|
| cat|Concatenate | Concatenate| cat results.txt|
|touch|Touch|creates or modifies a file|touch pictures.txt|
-----------------



These are the most commonly used Unix shell commands, you will be more comfortable to use them with practice.
There are commands that facilitate operations with multiple files and folders. Others that can create pipelines and filters. If you want to dive into the Unix shell and explore more the capabilities the [The Unix Shell](https://swcarpentry.github.io/shell-novice/) software carpentry course is recommended.
