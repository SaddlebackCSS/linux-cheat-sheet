#Manipulating Files and Directories

*Excerpt from [The Linux Command Line by William E. Shotts Jr. ch. 4 ](http://www.amazon.com/Linux-Command-Line-Complete-Introduction/dp/1593273894/ref=sr_1_1?s=books&ie=UTF8&qid=1456194414&sr=1-1)*

* `cp` - Copy files and directories.
* `mv` - Move/rename files and directories.
* `mkdir` - Create directories.
* `rm` - Remove files and directories.
* `ln` Create hard and symbolic links.

##Wildcards

| Wildcard | Matches |
| --- | --- |
| `*` | Any characters |
| `?` | Any single character |
|`[characters]` | Any character that is a member of the set *characters*. |
| `[!characters]` | Any character that is not a member of the set *characters* |
| `[[:class:]]` | Any character that is a member of the specified *class* |

##Commonly Used Character Classes

| Character Class | Matches |
| --- | --- |
| `[:alnum:]` | Any alphanumeric character |
| `[:alpha:]` | Any alphabetic character |
| `[:digit:]` | Any numeral |
| `[:lower:]` | Any lowercase letter |
| `[:upper:]` | Any uppercase letter |

##Wildcard Examples

|Pattern|Matches|
|---|---|
|`*`|All files|
|`g*`|Any file beginning with *g*|
|`b*.txt`| Any file beginning with *b* followed by any character and ending with *.txt*|
|`Data???` | Any file beginning with *Data* followed by exactly three characters|
|`[abc]*`|Any file beginning with either *a*, *b*, or *c*.|
|`BACKUP.[0-9][0-9][0-9]`|Any file beginning with *BACKUP.* followed by exactly three numerals.|
|`[[:upper:]]*` | Any file beginning with an uppercase letter.|
|`[![:digit:]]*` | Any file not beginning with a numeral |
|`*[[:lower:]123]` | Any file ending with a lowercase letter or the numerals *1*, *2*, or *3* |

##`cp` -- Copy Files and Directories

The `cp` command copies files or directories. It can be used two different ways:

```cp item1 item2```

to copy the single file or directory *item1* to file or directory *item2* and:

```cp item... directory```

to copy multiple items (either files or directories) into a directory.

###`cp` Options

|Option|Meaning|
|---|---|
|`-a, --archive`| Copy the files and directories and all of their attributes, including ownerships and permissions. Normally, copies take on the default attributes of the user performing the copy.|
|`-i, --interactive`| Before overwriting an existing file, prompt the user for confirmation. <br>**If this option is not specified, `cp` will silently overwrite files.**|
|`-r, --recursive`| Recursively copy directories and their contents. This option (or the -a option) is required when copying directories.|
|`u, --update`|When copying files from one directory to another, copy only files that either don’t exist or are newer than the existing corresponding files in the destination directory.|
|`-v, --verbose`|Display informative messages as the copy is performed.|

###`cp` Examples

|Command|Results|
|---|---|
|`cp file1 file2`|Copy *file1* to *file2*. **If file2 exists, it is overwritten with the contents of file1.**<br>If file2 does not exist, it is created.|
|`cp -i file1 file2`|Same as aboce, except that if *file2* exists, the user is prompted before it is overwritten.|
|`cp file1 file2 dir1`|Copy *file1* and *file2* into directory *dir1*. *dir1* must already exist.|
|`cp dir1/* dir2`|Using a wildcard, all the files in *dir1* are copied into *dir2*. *dir2* must already exist.|
|`cp -r dir1 dir2`|Copy directory *dir1* (and its contents) to directory *dir2*.<br>If directory *dir2* does not exist, it is created and will contain the same contents as directory *dir1*.|

##`mv` -- Move and Rename Files
The `mv` command performs both file moving and file renaming, depending on how it is used. In either case, the original filename no longer exists after the operation. `mv` is used in much the same way as `cp`:

`mv item1 item2`

to move or rename file or directory item1 to item2 or

`mv item... directory`

to move one or more items from one directory to another.

###`mv` Options
|Option|Meaning|
|---|---|
|`-i, --interactive`|Before overwriting and existing file, prompt the user for confirmation. <br>**If this option is not specified, `mv` will silently overwrite files.|
|`-u, --update`|When moving files from one directory to another, move only files that either don't exist in the destination directory or are newer than the existing corresponding files in the destination directory.|
|`-v, --verbose`|Display informative messages as the move is performed.|

###`mv` Examples
|Command|Results|
|---|---|
|`mv file1 file2`|Move *file1* to *file2*.<br>**If *file2* exists, it is overwritten with the contents of *file1*.** If *file2* does not exist, it is created.<br>**In either case, *file1* ceases to exist.**|
|`mv -i file1 file2`|Same as above, except that if *file2* exists, the user is prompted before it is overwritten.|
|`mv file1 file2 dir1`|Move *file1* and *file2* into directory *dir1*. *dir1* must already exist.|
|`mv dir1 dir2`|Move directory *dir1* (and its contents) into directory *dir2*. If directory *dir2* does not exist, create directory *dir2*, move the contents of directory *dir1* into *dir2*, and delete directory *dir1*.|

##`rm` -- Remove Files and Directories
The `rm` command is used to remove (delete) files and directories, like this:

```rm item...```

Where *item* is the name of one or more files or directories.

###`rm` Options
|Option|Meaning|
|---|---|
|`-i, --interactive`|Before deleting an existing file, prompt the user for confirmation.<br>**If this option is not specified, `rm` will silently delete files.**|
|`-r, --recursive`|Recursively delete directories. This means that if a directory being deleted has subdirectories, delete them too. To delete a directory, this option must be specified.|
|`-f, --force`|Ignore nonexistent files and do not prompt. This overrides the `--interactive` option.|
|`-v, --verbose`|Display informative messages as the deletion is performed.|

###`rm` Examples
|Command|Results|
|---|---|
|`rm file1`|Delete *file1* silently.|
|`rm -i file1`|Before deleting *file1*, prompt the user for confirmation.|
|`rm -r file1 dir1`|Delete *file1* and *dir1* and its contents.|
|`rm -rf file1 dir1`|Same as above, except that if either *file1* or *dir1* does not exist, rm will continue silently.|

##`ln` -- Create Links
The ln command is used to create either hard or symbolic links. It is used in one of two ways:

```ln file link```

to create a hard link and

```ln -s item link```

to create a symbolic link where item is either a file or a directory.

###Hard Links
Hard links are the original Unix way of creating links; symbolic links are more modern. By default, every file has a single hard link that gives the file its name. When we create a hard link, we create an additional directory entry for a file. Hard links have two important limitations:

* A hard link cannot reference a file outside its own filesystem. This means a link cannot reference a file that is not on the same disk partition as the link itself.
* A hard link cannot reference a directory.

A hard link is indistinguishable from the file itself. Unlike a directory list containing a symbolic link, a directory list containing a hard link shows no special indication of the link. When a hard link is deleted, the link is removed, but the contents of the file itself continue to exist (that is, its space is not deallocated) until all links to the file are deleted.
It is important to be aware of hard links because you might encounter them from time to time, but modern practice prefers symbolic links, which we will cover next.

###Symbolic Links
Symbolic links were created to overcome the limitations of hard links. Symbolic links work by creating a special type of file that contains a text pointer to the referenced file or directory. In this regard they operate in much the same way as a Windows shortcut, though of course they predate the Windows feature by many years. A file pointed to by a symbolic link and the symbolic link itself are largely indistinguishable from one another. For example, if you write something to the symbolic link, the referenced file is also written to. However, when you delete a symbolic link, only the link is deleted, not the file itself.
If the file is deleted before the symbolic link, the link will continue to exist but will point to nothing. In this case, the link is said to be broken. In many implementations, the `ls` command will display broken links in a distinguishing color, such as red, to reveal their presence.
