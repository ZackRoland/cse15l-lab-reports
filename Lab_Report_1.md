# **LAB 1**
---
## *cd command*
1. 
   ```
   [user@sahara ~]$ cd
   [user@sahara ~]$ 
   ```
   ```
   [user@sahara ~/lecture1]$ cd
   [user@sahara ~]$
   ```
   Working Directory is the Home Directory, cd without any arguments returns you to the home directory automatically
   which is why the first case nothing changes and the second case exits the lecture1 and resets to the home directory so
   this is not an error as the output is expected
   
2. 
   ```
   [user@sahara ~]$ cd lecture1/
   [user@sahara ~/lecture1]$  
   ```
   Working Directory is the Home Directory, cd with the lecture1/ directory as a argument will result in a changing of
   directories to point to the lecture1 directory. Thus the following output is within the expected bounds and is not an error.
4. 
   ```
   [user@sahara ~]$ cd lecture1/messages/ja.txt
   bash: cd: lecture1/messages/ja.txt: Not a directory
   ```
   Working directory is the Home Directory,  cd with the file path as an argument results in an error since cd only works with
   directory changes therefore the output of the error message "Not a directory" is expected.
---
## *ls command*
1. 
   ```
    [user@sahara ~]$ ls
    lecture1
   ```
   Working Directory is the Home Directory, ls lists all the files in the arguments directory therefore
   without any argument the ls command by itself lists all the files in the current directory which in this case
   is the home directory therefore the output of lecture1 is expected since lecture1 is the only file within
   the home directory.
2. 
   ```
   [user@sahara ~]$ ls lecture1/
   Hello.class  Hello.java  messages  README
   ```
   Working Directory is the Home Directory, ls with a directory as an argument lists all the files that lies
   within the directory therefore the output is within the expected bounds since there are 4 possible files
   that are within lecture1.
3. 
   ```
   [user@sahara ~]$ ls lecture1/messages/ja.txt
   lecture1/messages/ja.txt
   ```
   Working Directory is the Home Directory, ls with the file path as an argument returns the file path in the
   argument. This output is expected since pointing to an specific file will result in no files being listed
   so this is not an error.
   
---
## *cat command*
1. 
   ```
   [user@sahara ~]$ cat

   ```
   Working Directory is the Home Directory, the cat takes in file as the argument and returns the contents of it,
   since there is no argument we get a blank line being returned signifying just nothing as there is nothing
   there to return. This is not an error.
2. 
   ```
   [user@sahara ~]$ cat lecture1/
   cat: lecture1/: Is a directory
   ```
   Working Directory is the Home Directory, having a directory as an argument results in an error which is expected
   since cat can only work with files and as such can only take in file paths as arguments.
5. 
   ```
   [user@sahara ~]$ cat lecture1/messages/ja.txt
   「こんにちは世界」
   ```
   Working Directory is the Home Directory, the cat command followed by the file path returns the contents that reside within
   the file which is why the output we get is within the expected bounds as what is allowed by the command.
---
