#Manipulating Files and Directories

*Excerpt from [The Linux Command Line by William E. Shotts Jr. pg 19 ](http://www.amazon.com/Linux-Command-Line-Complete-Introduction/dp/1593273894/ref=sr_1_1?s=books&ie=UTF8&qid=1456194414&sr=1-1)*

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

**more to come... stay tuned**