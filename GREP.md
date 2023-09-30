The grep command in Linux is a powerful tool for searching and matching text patterns within files or the output of other commands

grep [options] pattern [files]

options:	 Various options to control the search behavior.
pattern: 	The regular expression pattern to search for.
files: 	Optional. Specify one or more files to search within. If omitted, grep reads from standard input.

grep "pattern" file.txt ,  grep "pattern" file1.txt file2.txt , grep -r "pattern" /path/to/directory


Common Options:

	-i: 	Ignore case (case-insensitive search).
	-v: 	Invert the match (show lines that do not match the pattern).
	-l: 	List only the names of files containing the pattern.
	-n: 	Display line numbers for matching lines.
	-c: 	Count the number of matching lines.
	-r or -R:	 Recursively search directories.
	-e pattern:	 Specify multiple patterns.
	-w: 	Match whole words only.

Examples:

	1. Search for a Pattern in a File:	 grep "apple" fruits.txt
	2. Case-Insensitive Search: 	grep -i "Linux" textfile.txt
	3. Invert Match:	 grep -v "error" logfile.txt
	4.  Search Multiple Files: 	grep "pattern" file1.txt file2.txt
	5. Display Line Numbers:	 grep -n "keyword" file.txt
	6. Count Matching Lines:	 grep -c "success" logfile.txt
	7.  Recursively Search Directories:	 grep -r "keyword" /path/to/directory
	8. Match Whole Words:	 grep -w "apple" file.txt
	9. Search for Lines with Multiple Patterns: 	grep "Linux.*commands" textfile.txt
	10.List Files Containing a Pattern: 	bash grep -rl "important" /path/to/directory
	11. Search Multiple Patterns Simultaneously:	 bash grep -e "error" -e "warning" logfile.txt
	12.Search Using Regular Expressions	bash grep "^error[0-9]+" logfile.txt

Practice:

	[diwakar@devops ~]$ grep 'Linux' text_processing.txt
	In many ways, Linux is similar to other operating systems you may have used before, such as Windows, macOS (formerly OS X), or iOS. Like other operating systems, Linux has a graphical interface, and the same types of software you are accustomed to, such as word processors, photo editors, video editors, and so on. In many cases, a software’s creator may have made a Linux version of the same program you use on other systems. In short: if you can use a computer or other electronic device, you can use Linux.
	
	[diwakar@devops ~]$ grep -i 'linux' text_processing.txt
	In many ways, Linux is similar to other operating systems you may have used before, such as Windows, macOS (formerly OS X), or iOS. Like other operating systems, Linux has a graphical interface, and the same types of software you are accustomed to, such as word processors, photo editors, video editors, and so on. In many cases, a software’s creator may have made a Linux version of the same program you use on other systems. In short: if you can use a computer or other electronic device, you can use Linux.
	
	[diwakar@devops ~]$ grep -v 'linux' text_processing.txt
	In many ways, Linux is similar to other operating systems you may have used before, such as Windows, macOS (formerly OS X), or iOS. Like other operating systems, Linux has a graphical interface, and the same types of software you are accustomed to, such as word processors, photo editors, video editors, and so on. In many cases, a software’s creator may have made a Linux version of the same program you use on other systems. In short: if you can use a computer or other electronic device, you can use Linux.
	
	[diwakar@devops ~]$ grep "error" diwakarfiles link_files character_files block_files output
	diwakarfiles:/home/diwakar/error
	link_files:/usr/lib64/libgpg-error.so.0
	link_files:/usr/lib64/libsamba-errors.so.1
	
	
	[diwakar@devops ~]$ grep -n 'Linux' text_processing.txt
	1:In many ways, Linux is similar to other operating systems you may have used before, such as Windows, macOS (formerly OS X), or iOS. Like other operating systems, Linux has a graphical interface, and the same types of software you are accustomed to, such as word processors, photo editors, video editors, and so on. In many cases, a software’s creator may have made a Linux version of the same program you use on other systems. In short: if you can use a computer or other electronic device, you can use Linux.
	
	[diwakar@devops ~]$ grep -c 'Linux' text_processing.txt
	17
	
	[diwakar@devops ~]$ grep -r 'error' .
	./.bash_history:ls -l /etc/Hosts 2 >> error
	./.bash_history:ls -l /etc/Hosts 2>> error
	./.bash_history:cat error
	./.bash_history:truncate -s 5mb error
	./.bash_history:truncate -s 5M error
	./.bash_history:cat error
	./.bash_history:find . -type f -name error -size +1k
	./link_files:/usr/lib64/libgpg-error.so.0
	./link_files:/usr/lib64/libsamba-errors.so.1
	./diwakarfiles:/home/diwakar/error
	
	[diwakar@devops ~]$ grep -w 'Linux' text_processing.txt
	In many ways, Linux is similar to other operating systems you may have used before, such as Windows, macOS (formerly OS X), or iOS. Like other operating systems, Linux has a graphical interface, and the same types of software you are accustomed to, such as word processors, photo editors, video editors, and so on. In many cases, a software’s creator may have made a Linux version of the same program you use on other systems. In short: if you can use a computer or other electronic device, you can use Linux.
	
	[diwakar@devops ~]$ grep "Linux.*kernel" text_processing.txt
	The term “Linux” technically refers to just the Linux kernel. Most people refer to the entire operating system as "Linux" because to most users an OS includes a bundle of programs, tools, and services (like a desktop, clock, an application menu, and so on). Some people, particularly members of the Free Software Foundation, refer to this collection as GNU/Linux, because many vital tools included are GNU components. However, not all Linux installations use GNU components as a part of the operating system: Android, for example, uses a Linux kernel but relies very little on GNU tools.
	Most of the Linux kernel is written in the C programming language, with a little bit of assembly and other languages sprinkled in. If you’re interested in writing code for the Linux kernel itself, a good place to get started is in the Kernel Newbies FAQ, which will explain some of the concepts and processes you’ll want to be familiar with.
	
	[diwakar@devops ~]$ grep -rl 'error' .
	./.bash_history
	./link_files
	./diwakarfiles
	
	[diwakar@devops ~]$ grep  "error.*" diwakarfiles
	/home/diwakar/error
	
	[diwakar@devops ~]$ grep -e 'Linux' -e 'kernel' text_processing.txt
	But the Linux community is much more than the kernel, and needs contributions from lots of other people besides programmers. Every distribution contains hundreds or thousands of programs that can be distributed along with it, and each of these programs, as well as the distribution itself, need a variety of people and skill sets to make them successful, including:

