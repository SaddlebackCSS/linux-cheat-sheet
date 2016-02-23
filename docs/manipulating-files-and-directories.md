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

**more to come... stay tuned**
