### Nano

add a file to nano with wordwrap

```bash
nano -$ filename.txt
```

```

Crawl a website and output files
```bash
wget --spider --force-html -r -l2 $url 2>&1 \
  | grep '^--' | awk '{ print $3 }' \
  | grep -v '\.\(css\|js\|png\|gif\|jpg\)$' \
  > urls.m3u
```


### Sorting files

Command:
```bash
sort -o output.txt file.txt
```

Using the -o option is functionally the same as redirecting the output to a file:
```bash
sort file.txt > output.txt 
```

Order files and remove duplicate lines:
```bash
cat filename | sort | uniq > newfilename.txt
```

FolderA will first need to be part of groupA - the folder's owner or root can perform this operation

```bash
chgrp groupA ./folderA
```

Add rwx (Read, write, execute) permissions of the folder for the group

```bash
chmod g+rwx  ./folderA
```


View last x lines of a file - useful for error logging

```bash
tail -30 /var/log/mysql/error.log
```

Check Version of Linux
uname -srm

Check version of Ubuntu
lsb_release -a


## String find/replace
use dbname;

source db.sql;

:%s/http:\/\/test.com/https:\/\/test.com/g
:%s/search/replace/g
