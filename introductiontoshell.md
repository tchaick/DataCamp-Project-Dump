# Introduction to Shell

Retook the course as a refresher this February 6, 2023 | Completed: February 9, 2023
My notes and solutions below. 

---

# Manipulating files and directories

### How does the shell compare to a desktop interface

What is the relationship between the graphical file explorer that most people use and the command-line shell?

- [ ] The file explorer lets you view and edit files, while the shell lets you run programs.
- [ ] The file explorer is built on top of the shell.
- [ ] The shell is part of the operating system, while the file explorer is separate.
- [x] They are both interfaces for issuing commands to the operating system.


### Where am I

Run ```pwd```. Where are you right now?

- [ ] /home
- [ ] /repl
- [x] /home/repl


### How can I identify files and directories

Use ls with an appropriate argument to list the files in the directory /home/repl/seasonal (which holds information on dental surgeries by date, broken down by season). Which of these files is not in that directory?

```
ls /home/repl/seasonal
```
- [ ] autumn.csv
- [ ] fall.csv
- [x] spring.csv
- [ ] winter.csv


### How else can I identify files and directories

The shell decides if a path is absolute or relative by looking at its first character: If it begins with /, it is absolute. If it does not begin with /, it is relative.

1. You are in /home/repl. Use ls with a relative path to list the file that has an absolute path of /home/repl/course.txt (and only that file).

    ``` 
    ls course.txt
    ```

2. You are in /home/repl. Use ls with a relative path to list the file /home/repl/seasonal/summer.csv (and only that file).
 
    ```
    ls seasonal/summer.csv
    ```

3. You are in /home/repl. Use ls with a relative path to list the contents of the directory /home/repl/people.

    ```
    ls people
    ```


### How can I move to another directory

1. You are in /home/repl/. Change directory to /home/repl/seasonal using a relative path.
    ```
    cd seasonal
    ```

2. Use pwd to check that you're there.

    ```
    pwd
    ```

3.  Use ls without any paths to see what's in that directory.
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

1. Make a copy of seasonal/summer.csv in the backup directory (which is also in /home/repl), calling the new file summer.bck.

```
cp seasonal/summer.csv backup/summer.bck
```

2. Copy spring.csv and summer.csv from the segit asonal directory into the backup directory without changing your current working directory (/home/repl).

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


---

# Manipulating Data


### How can I view a file's contents?

Print the contents of course.txt to the screen

``` 
cat course.txt
```


### How can I view a file's contens piece by piece?

**Good to know!** *less > display one page of the file at a time, :n > move to the next file. :p > to go back to previous one, :q > quit.*

Use less seasonal/spring.csv seasonal/summer.csv to view those two files in that order. Press spacebar to page down, :n to go to the second file, and :q to quit.

``` 
less seasonal/spring.csv seasonal/summer.csv 
```

``` 
:n 
```

``` 
:q 
```


### How can I look at the start of a file?

What does head do if there aren't 10 lines in the file? (To find out, use it to look at the top of people/agarwal.txt.)
- [ ] Print an error message because the file is too short.
- [x] Display as many lines as there are.
- [ ] Display enough blank lines to bring the total to 10.

### How can I type less?

*press tab to auto-complete file/path name.*

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
- [ ] cut -d , -f 1 seasonal/spring.csv
- [ ] cut -d, -f1 seasonal/spring.csv
- [x] Either of the above.
- [ ] Neither of the above, because -f must come before -d.


### What can't cut do?

What is the output of cut -d : -f 2-4 on the line:
> first:second:third:
- [ ] second
- [ ] second:third
- [x] second:third:
- [ ] None of the above, because there aren't four fields.


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

1. Print the contents of all of the lines containing the word molar in seasonal/autumn.csv by running a single command while in your home directory. Don't use any flags.

```
grep molar seasonal/autumn.csv
```

2. Invert the match to find all of the lines that don't contain the word molar in seasonal/spring.csv, and show their line numbers. Remember, it's considered good style to put all of the flags before other values like filenames or the search term "molar".
```
grep -v -n seasonal/spring.csv
```

3. Count how many lines contain the word incisor in autumn.csv and winter.csv combined. (Again, run a single command from your home directory.)
```
grep -c incisor seasonal/autumn.csv seasonal/winter.csv 
```


### Why isn't always safe to treat data as text?

Read the manual page for paste, and then run paste to combine the autumn and winter data files in a single table using a comma as a separator. What's wrong with the output from a data analysis point of view?
```
man paste
```
- [ ] The column headers are repeated.
- [x] The last few rows have the wrong number of columns.
- [ ] Some of the data from winter.csv is missing.



---

# Combining Tools



### How can I store a command's output in a file?

Combine tail with redirection to save the last 5 lines of seasonal/winter.csv in a file called last.csv.
``` 
tail -n 5 seasonal/winter.csv > last.csv
```


### How can I use a commands's output as an input?

1. Select the last two lines from seasonal/winter.csv and save them in a file called bottom.csv.
```
tail -n 2 seasonal/winter.csv > bottom.csv
```
2. Select the first line from bottom.csv in order to get the second-to-last line of the original file.
```
head -n 1 bottom.csv
```


### What's a better way to combine commands?

Use cut to select all of the tooth names from column 2 of the comma delimited file seasonal/summer.csv, then pipe the result to grep, with an inverted match, to exclude the header line containing the word "Tooth". cut and grep were covered in detail in Chapter 2, exercises 8 and 11 respectively.
``` 
cut -d , -f 2 seasonal/summer.csv | grep -v Tooth
```


### How can I combine many commands?

**Good to know!**
You can chain any number of commands together. For example, this command:

> cut -d , -f 1 seasonal/spring.csv | grep -v Date | head -n 10

will:

1. select the first column from the spring data;
2. remove the header line containing the word "Date"; and
3. select the first 10 lines of actual data.


In the previous exercise, you used the following command to select all the tooth names from column 2 of seasonal/summer.csv:

> cut -d , -f 2 seasonal/summer.csv | grep -v Tooth

Extend this pipeline with a head command to only select the very first tooth name.

``` 
cut -d , -f 2 seasonal/summer.csv | grep -v Tooth | head -n 1
```


### How can I count the records in a file?

Count how many records in seasonal/spring.csv have dates in July 2017 (2017-07).

To do this, use grep with a partial date to select the lines and pipe this result into wc with an appropriate flag to count the lines.

```
grep "2017-01" seasonal/spring.csv |wc -l-l 
```


### How can I specify many files at once? 

Write a single command using head to get the first three lines from both seasonal/spring.csv and seasonal/summer.csv, a total of six lines of data, but not from the autumn or winter data files. Use a wildcard instead of spelling out the files' names in full.

```
head -n 3 seasonal/s*
```


### What other wildcards can I use?

>**Good to know!**
>
> ? matches a single character, 
>> so 201?.txt will match 2017.txt or 2018.txt, but not 2017-01.txt.
> 
> [...] matches any one of the characters inside the square brackets, 
>> so 201[78].txt matches 2017.txt or 2018.txt, but not 2016.txt.
>
> {...} matches any of the comma-separated patterns inside the curly brackets, 
>> so {*.txt, *.csv} matches any file whose name ends with .txt or .csv, but not files whose names end with .pdf.

Which expression would match singh.pdf and johel.txt but not sandhu.pdf or sandhu.txt?

- [ ] [sj]*.{.pdf, .txt}
- [ ] {s*.pdf, j*.txt}
- [ ] [singh,johel]{*.pdf, *.txt}
- [x] {singh.pdf, j*.txt}

### How can I sort lines of text?

**Good to know!**

> use ```-b``` to ignore leading blanks and
>
> use ```-f``` for case sensitive query.

Remember the combination of cut and grep to select all the tooth names from column 2 of seasonal/summer.csv?

> cut -d , -f 2 seasonal/summer.csv | grep -v Tooth

Starting from this recipe, sort the names of the teeth in seasonal/winter.csv (not summer.csv) in descending alphabetical order. To do this, extend the pipeline with a sort step.

``` 
cut -d , -f 2 seasonal/winter.csv | grep -v Tooth | sort -r
```

### How can I remove duplicate lines?

**Good to know!**
> use ```uniq``` to remove duplicated lines

Write a pipeline to:

- get the second column from seasonal/winter.csv,
- remove the word "Tooth" from the output so that only tooth names are displayed,
- sort the output so that all occurrences of a particular tooth name are adjacent; and
- display each tooth name once along with a count of how often it occurs.
The start of your pipeline is the same as the previous exercise:

> cut -d , -f 2 seasonal/winter.csv | grep -v Tooth

Extend it with a sort command, and use uniq -c to display unique lines with a count of how often each occurs rather than using uniq and wc.

```
cut -d , -f 2 seasonal/winter.csv | grep -v Tooth | sort | uniq -c
```


### How can I save the output of a pipe?

What happens if we put redirection at the front of a pipeline as in:
> > result.txt head -n 3 seasonal/winter.csv

- [x] The command's output is redirected to the file as usual.
- [ ] The shell reports it as an error.
- [ ] The shell waits for input forever.


### How can I stop a running program?

Run the command:

```head```

with no arguments (so that it waits for input that will never come) and then stop it by typing Ctrl + C.

``` 
press Ctrl + C
```

### Wrapping up?
To wrap up, you will build a pipeline to find out how many records are in the shortest of the seasonal data files.

1. Use wc with appropriate parameters to list the number of lines in all of the seasonal data files. (Use a wildcard for the filenames instead of typing them all in by hand.)
```
wc -l seasonal/*
```

2. Add another command to the previous one using a pipe to remove the line containing the word "total".
```
wc -l seasonal/* | grep -v total
```

3. Add two more stages to the pipeline that use sort -n and head -n 1 to find the file containing the fewest lines.
```
wc -l seasonal/* | grep -v total | sort -n | head -n 1
```


# Batch Processing



### How does the shell store information?

use set and grep with a pipe to display the value of HISTFILESIZE, which determines how many old commands are stored in your command history. What is its value?

```
set | grep HISTFILESIZE
```

- [ ] 10
- [ ] 500
- [x] 2000
- [ ] The variable is not there.


### How can I print a variable's value?

*The $ symbol is used to access the value of a shell variable.*

The variable OSTYPE holds the name of the kind of operating system you are using. Display its value using echo.

```
echo $OSTYPE
```


### How else does the shell store information?

1. Define a variable called testing with the value seasonal/winter.csv.

```
testing=seasonal/winter.csv
```

2. Use head -n 1 SOMETHING to get the first line from seasonal/winter.csv using the value of the variable testing instead of the name of the file.
```
head -n 1 $testing 
```


### How can I repeat a command many times?

**Good to know!**
The `for` loop in bash is used to execute a set of commands repeatedly for a specified number of times, or `for` each item in a specified list. Here's the basic syntax for a for loop in bash:

```
for variable in list; do
  commands
done
```
- variable is a variable that will be used to store each item in the list as the loop iterates.
- list is a list of values or items that the loop will iterate over. This can be a list of words, a range of numbers, or the output of a command.
- commands are the commands that will be executed for each iteration of the loop. These commands will be executed once for each item in the list.

Modify the loop so that it prints:

docx
odt
pdf
Please use filetype as the name of the loop variable.

```
for filetype in docx odt pdf; do echo $filetype; done
```

### How can I repeat a command once for each file?


Modify the wildcard expression to people/* so that the loop prints the names of the files in the people directory regardless of what suffix they do or don't have. Please use filename as the name of your loop variable.

``` 
for filename in people/*; do echo $filename; done
```


### How can I record the names of a set of files?


If you run these two commands in your home directory, how many lines of output will they print?
```
files=seasonal/*.csv
for f in $files; do echo $f; done
```

- [ ] None: since files is defined on a separate line, it has no value in the second line.
- [ ] One: the word "files".
- [x] Four: the names of all four seasonal data files.


### A variable's name versus its value

*The $ symbol is used to access the value of a shell variable.*

If you were to run these two commands in your home directory, what output would be printed?
```
files=seasonal/*.csv
for f in files; do echo $f; done
```
- [x] One line: the word "files"
- [ ] Four lines: the names of all four seasonal data files.
- [ ] Four blank lines: the variable f isn't assigned a value.


### How can I run many commands in a single loop? 

Write a loop that prints the last entry from July 2017 (2017-07) in every seasonal file. It should produce a similar output to:

> grep 2017-07 seasonal/winter.csv | tail -n 1

but for each seasonal file separately. Please use file as the name of the loop variable, and remember to loop through the list of files seasonal/*.csv (instead of 'seasonal/winter.csv' as in the example).

```
for file in seasonal/*.csv; do grep 2017-07 $file | tail -n 1; done
```

### Why shouldn't I use spaces in filenames?

If you have two files called current.csv and last year.csv (with a space in its name) and you type:

> rm current.csv last year.csv

what will happen:

- [ ] The shell will print an error message because last and year.csv do not exist.
- [ ] The shell will delete current.csv.
- [x] Both of the above.
- [ ] Nothing.


### How can I do many things in a single loop?

Suppose you forget the semi-colon between the echo and head commands in the previous loop, so that you ask the shell to run:

> for f in seasonal/*.csv; do echo $f head -n 2 $f | tail -n 1; done

What will the shell do?


- [ ] Print an error message.
- [x] Print one line for each of the four files.
- [ ] Print one line for autumn.csv (the first file).
- [ ] Print the last line of each file.




# Creating new tools


### How can I edit a file? 

**Good to know!** 

> Move around *Nano* using these control-key combinations. 
>
>> - Ctrl + K: delete a line.
>> - Ctrl + U: un-delete a line.
>> - Ctrl + O: save the file ('O' stands for 'output'). *You will also need to press Enter to confirm the filename!*
>> -Ctrl + X: exit the editor.


Run nano names.txt to edit a new file in your home directory and enter the following four lines:

Lovelace
Hopper
Johnson
Wilson
To save what you have written, type Ctrl + O to write the file out, then Enter to confirm the filename, then Ctrl + X to exit the editor.

```
nano names.txt
```

```
Lovelace
Hopper
Johnson
Wilson
```
```
ctrl + O
ctrl + x
```


### How can I record what I just did? 


1. Copy the files seasonal/spring.csv and seasonal/summer.csv to your home directory.

```
cp seasonal/*s ~
```

2. Use grep with the -h flag (to stop it from printing filenames) and -v Tooth (to select lines that don't match the header line) to select the data records from spring.csv and summer.csv in that order and redirect the output to temp.csv.
```
grep -h -v Tooth spring.csv summer.csv > temp.csv
```

3. Pipe history into tail -n 3 and redirect the output to steps.txt to save the last three commands in a file. (You need to save three instead of just two because the history command itself will be in the list.)
```
history tail -n 3 > steps.txt
```


### How can I save commands to re-run later?

1. Use nano dates.sh to create a file called dates.sh that contains this command:

cut -d , -f 1 seasonal/*.csv
to extract the first column from all of the CSV files in seasonal.

``` 
nano dates.sh
```

```
cut -d , -f 1 seasonal/*.csv
ctrl + o enter
ctrl + x 
```

2. Use bash to run the file dates.sh

```
bash dates.sh
```

### How can I re-use pipes?

1. A file teeth.sh in your home directory has been prepared for you, but contains some blanks. Use Nano to edit the file and replace the two ____ placeholders with seasonal/*.csv and -c so that this script prints a count of the number of times each tooth name appears in the CSV files in the seasonal directory.


```
nano teeth.sh
1st ___ > seasonal/*.csv, 2nd ___ > -c
ctrl + o, enter
cntrl + x
```

2. Use bash to run teeth.sh and > to redirect its output to teeth.out.
```
bash teeth.sh > teeth.out
```

3. Run cat teeth.out to inspect your results.
```
cat teeth.out
```


### How can I pass filenames to scripts?
### How can I process a single argument?
### How can one shell script do many things?
### How can I write loops in a shell script?
### What happnees when I don't provide filenames?


