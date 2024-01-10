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
2. 
   ```
   [user@sahara ~]$ cd lecture1/
   [user@sahara ~/lecture1]$  
   ```
3. 
   ```
   [user@sahara ~]$ cd lecture1/messages/ja.txt
   bash: cd: lecture1/messages/ja.txt: Not a directory
   ```
---
## *ls command*
1. 
    ```
    [user@sahara ~]$ ls
    lecture1
    ```
2. 
   ```
   [user@sahara ~]$ ls lecture1/
   Hello.class  Hello.java  messages  README
   ```
3. 
   ```
   [user@sahara ~]$ ls lecture1/messages/ja.txt
   lecture1/messages/ja.txt
   ``` 
---
## *cat command*
1. .
   ```
   [user@sahara ~]$ cat
   
   ```
2. 
   ```
   [user@sahara ~]$ cat lecture1/
   cat: lecture1/: Is a directory
   ```
3. 
   ```
   [user@sahara ~]$ cat lecture1/messages/ja.txt
   「こんにちは世界」
   ``` 
---
