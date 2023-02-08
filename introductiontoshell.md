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

## 
