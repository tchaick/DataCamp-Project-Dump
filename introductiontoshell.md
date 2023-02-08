# Introduction to Shell

Retook the course as a refresher this February 6, 2023. 
My notes and solutions below. 

## Manipulating files and directories

### How does the shell compare to a desktop interface

What is the relationship between the graphical file explorer that most people use and the command-line shell?

- [ ] The file explorer lets you view and edit files, while the shell lets you run programs.
- [ ] The file explorer is built on top of the shell.
- [ ] The shell is part of the operating system, while the file explorer is separate.
- [x] They are both interfaces for issuing commands to the operating system.
---
### Where am I
Run ```pwd```. Where are you right now?

- [ ] /home
- [ ] /repl
- [x] /home/repl
---
### How can I identify files and directories

Use ls with an appropriate argument to list the files in the directory /home/repl/seasonal (which holds information on dental surgeries by date, broken down by season). Which of these files is not in that directory?

```ls /home/repl/seasonal```
- [ ] autumn.csv
- [ ] fall.csv
- [x] spring.csv
- [ ] winter.csv

### How else can I identify files and directories

The shell decides if a path is absolute or relative by looking at its first character: If it begins with /, it is absolute. If it does not begin with /, it is relative.

- You are in /home/repl. Use ls with a relative path to list the file that has an absolute path of /home/repl/course.txt (and only that file).

    ``` 
    ls course.txt
    ```

- You are in /home/repl. Use ls with a relative path to list the file /home/repl/seasonal/summer.csv (and only that file).
 
    ```
    ls seasonal/summer.csv
    ```

- You are in /home/repl. Use ls with a relative path to list the contents of the directory /home/repl/people.

    ```
    ls people
    ```

### How can I move to another directory
- You are in /home/repl/. Change directory to /home/repl/seasonal using a relative path.
    ```
    cd seasonal
    ```

- Use pwd to check that you're there.

    ```
    pwd
    ```

- Use ls without any paths to see what's in that directory.
    ```
    ls
    ```

### How can I move up a directory

If you are in /home/repl/seasonal, where does cd ~/../. take you?
- [ ] /home/repl
- [ ] /repl
- [x] /home/repl/seasonal
- [ ] / (the root directly)

### How can I copy files
- Make a copy of seasonal/summer.csv in the backup directory (which is also in /home/repl), calling the new file summer.bck.

```
cp seasonal/summer.csv backup/summer.bck
```

- Copy spring.csv and summer.csv from the segit asonal directory into the backup directory without changing your current working directory (/home/repl).

```
cp/seasonal/spring.csv seasonal/summer.csv backup 
```


### How can I move a file
You are in /home/repl, which has sub-directories seasonal and backup. Using a single command, move spring.csv and summer.csv from seasonal to backup.

```
cd seasonal
mv spring.csv summer.csv ../backup/
```

### How can I rename files

1. Go into the seasonal directory. 
```
cd seasonal
```

2. Rename the file winter.csv to be winter.csv.bck
```
mv winter.csv winter.csv.bck
```

3. Run ls to check that everything has worked. 
```
ls
```

### How can I delete files
1. You are in /home/repl. Go into the seasonal directory.
    ```
    cd seasonal
    ```
2. Remove autumn.csv
    ```
    rm autumn.csv 
    ```
3. Go back to your home directory. 
    ```
    cd ..
    ```
4. Remove seasonal/summer.csv
    ```
    rm seasonal/summer.csv
    ```

### How can I create and delete directories?
1. Without changing directories, delete the file agarwal.txt in the people directory.
```
rm people/agarwal.txt
```

2. Now that the people directory is empty, use a single command to delete it.
```
rmdir people
```
    
3. Since a directory is not a file, you must use the command mkdir directory_name to create a new (empty) directory. Use this command to create a new directory called yearly below your home directory.
```
mkdir yearly
```

4. Now that yearly exists, create another directory called 2017 inside it without leaving your home directory.
```
mkdir yearly/2017
```



### Wrapping up
1. Use cd to go into /tmp.
```
cd /tmp
```

2. List the contents of /tmp without typing a directory name.
```
ls
```

3. Make a new directory inside /tmp called scratch.
```
mkdir
```

4. Move /home/repl/people/agarwal.txt into /tmp/scratch. We suggest you use the ~ shortcut for your home directory and a relative path for the second rather than the absolute path.
```
mv ~/people/agarwal.txt /tmp/scratch
```


# Manipulating Data

### How can I view a file's contents?
Print the contents of course.txt to the screen

``` 
cat course.txt
```

### How can I view a file's contens piece by piece?
**Good to know!** *less > display one page of the file at a time, :n > move to the next file. :p > to go back to previous one, :q > quit.*

Use less seasonal/spring.csv seasonal/summer.csv to view those two files in that order. Press spacebar to page down, :n to go to the second file, and :q to quit.

``` $ less seasonal/spring.csv seasonal/summer.csv ```

``` :n ```

``` :q ```

### How can I look at the start of a file?

What does head do if there aren't 10 lines in the file? (To find out, use it to look at the top of people/agarwal.txt.)


- [ ] Print an error message because the file is too short.
- [x] Display as many lines as there are.
- [ ] Display enough blank lines to bring the total to 10.

### How can I type less?
*the power of pressing tab to autocomplete file/path.*

1. Run head seasonal/autumn.csv without typing the full filename.

``` 
type head sea, press tab, type au, press tab. 
```

2. Run head seasonal/spring.csv without typing the full filename.
```
type head sea, press tab, type sp, press tab.
```

### How can I control what commands do?
Display the first 5 lines of winter.csv in the seasonal directory.

```
head -n 5 seasonal/winter.csv
```

### How can I list everything below a directory?
To help you know what is what, ls has another flag -F that prints a / after the name of every directory and a * after the name of every runnable program. Run ls with the two flags, -R and -F, and the absolute path to your home directory to see everything it contains. (The order of the flags doesn't matter, but the directory name must come last.)

```
ls -R -F /home/repl
```
### How can I get help for a command?
1. Read the manual page for the tail command to find out what putting a + sign in front of the number used with the -n flag does. (Remember to press spacebar to page down and/or type q to quit.)
``` 
man tail 
```
2. Use tail with the flag -n +7 to display all but the first six lines of seasonal/spring.csv.
```
tail -n +7 seasonal/spring.csv
```

### How can I select columns from a file? 
What command will select the first column (containing dates) from the file spring.csv?
-[ ] cut -d , -f 1 seasonal/spring.csv
-[ ] cut -d, -f1 seasonal/spring.csv
-[x] Either of the above.
-[ ] Neither of the above, because -f must come before -d.

### What can't cut do?
What is the output of cut -d : -f 2-4 on the line:
> first:second:third:
-[ ] second
-[ ] second:third
-[x] second:third:
-[ ] None of the above, because there aren't four fields.

### How can I repeat commands?
1. Run head summer.csv in your home directory (which should fail).
```
head summer.csv
```
2. Change directory to seasonal.
```
cd seasonal
```
3. Re-run the head command with !head.
```
!head
```
4. Use history to look at what you have done.
```
history
```
5. Re-run head again using ! followed by a command number.
```
!1
```

### How can I select lines containing specific values?
**Good to know!**

```head``` and ```tail``` select rows, ```cut``` selects columns, and ```grep``` selects lines according to what they contain. In its simplest form, ```grep``` takes a piece of text followed by one or more filenames and prints all of the lines in those files that contain that text. For example, ```grep bicuspid seasonal/winter.csv``` prints lines from ```winter.csv``` that contain "bicuspid".

```grep``` can search for patterns as well; we will explore those in the next course. What's more important right now is some of grep's more common flags:

- ```-c```: print a count of matching lines rather than the lines themselves
- ```-h```: do not print the names of files when searching multiple files
- ```-i```: ignore case (e.g., treat "Regression" and "regression" as matches)
- ```-l```: print the names of files that contain matches, not the matches
- ```-n```: print line numbers for matching lines
- ```-v```: invert the match, i.e., only show lines that don't match

### Why isn't always safe tp treat data as text?
