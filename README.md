nam-example
===========

An example repository for testing purposes to demonstrate the interaction of git with DBPF files.

Installation
------------

First, clone the repository to your computer. The remaining steps are optional, but highly recommended.

Get the zip file [DBPFDiff.zip](https://www.dropbox.com/sh/1prl1db7funq7v5/4x1PGFsIEQ) and extract it to any (permanent) location. Make sure to keep the lib folder next to the jar file.

Next, open the file `nam-example/.git/config` of your local repository in a text editor and add the following lines

```
[diff "dbpf"]
	textconv = java -jar C:/your/path/to/DBPFDiff.jar
	cachetextconv = true
	binary = true
[merge "dbpf"]
	name = dbpf merge driver
	driver = java -jar C:/your/path/to/DBPFDiff.jar %A %O %B
```

where you have to replace both occurences of `C:/your/path/to/DBPFDiff.jar` by the actual location of the jar file. This will enable the binary-to-text conversion of DBPF files, which allows to display meaningful diffs between commits, as well as a custom merge driver that allows automatic merging of DBPF files. (The merge functionality is still very limited--expect it to fail, if a file contains multiple instances of the same TGI or if subfiles of the same TGI get edited in both files to merge.)
