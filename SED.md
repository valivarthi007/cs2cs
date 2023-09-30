The sed command, short for "stream editor," is a powerful text manipulation tool in Unix-like operating systems, including Linux. sed is primarily used for performing text transformations on an input stream (a file or input from a pipe) and printing the results to the standard output. 

It is particularly useful for tasks like searching, replacing, inserting, deleting, and modifying text.

 basic syntax of the sed command:  sed [options] 'script' input_file

options: Optional. Various options to control the behavior of sed.

'script': A sequence of sed commands enclosed in single quotes. These commands define the text transformations.
input_file: Optional. The file to read input from. If omitted, sed reads from standard input (e.g., via a pipe or user input).

Common sed Commands:

	1. Substitute (Search and Replace):
		○ s/pattern/replacement/: Substitute the first occurrence of pattern with replacement on each line.
		○ s/pattern/replacement/g: Substitute all occurrences of pattern with replacement on each line. Example: sed 's/apple/orange/g' fruits.txt
	2. Print Lines:
		○ p: Print the current pattern space (line). Example: sed -n '2,4p' data.txt
	3. Delete Lines:
		○ d: Delete the current pattern space (line). Example: sed '/pattern/d' file.txt
	4. Insert and Append Lines:
		○ i text: Insert text before the current pattern space.
		○ a text: Append text after the current pattern space. Example: sed '/pattern/i NewLine' file.txt
	5. Range Selection:
		○ start, end: Apply sed commands within a specified range of lines. Example: sed '2,4s/pattern/replacement/' file.txt
	6. Regex Patterns:
		○ ^:    Match the start of a line.
		○ $:    Match the end of a line.
		○ [...]: Match any character within square brackets.
		○ [^...]: Match any character not in square brackets.
		○ *:    Match zero or more occurrences.
		○ .:    Match any single character.
		○ \:   Escape special characters.

Practice

Substitute (Search and Replace):
								
	[diwakar@devops ~]$ cat sedexample
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	Enthusiasts to spread the word about Linux and open source in general.
	And of course developers to write the software itself.
	
	[diwakar@devops ~]$ # replacing Testers with Developers just for single occurance
	[diwakar@devops ~]$ sed 's/Testers/Developers/' sedexample
	Developers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	Enthusiasts to spread the word about Linux and open source in general.
	And of course developers to write the software itself.
	
	[diwakar@devops ~]$ # replacing to with ot within entire text
	[diwakar@devops ~]$ sed 's/to/ot/g' sedexample
	Testers ot make sure everything works on different configurations of hardware and software, and ot report the bugs when it does not.
	Designers ot create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-ots, and other important text distributed with software.
	Translaotrs ot take programs and documentation from their native languages and make them accessible ot people around the world.
	Packagers ot take software programs and put all the parts otgether ot make sure they run flawlessly in different distributions.
	Enthusiasts ot spread the word about Linux and open source in general.
	And of course developers ot write the software itself.
	
Print Lines:
											
	[diwakar@devops ~]$ # Print the lines from Designers to Packagers
	[diwakar@devops ~]$ sed -n '2,5p' sedexample
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	[diwakar@devops ~]$
	
Delete Lines:
	
	[diwakar@devops ~]$ # exclude the line of Packagers and print
	[diwakar@devops ~]$ sed '/Packagers/d' sedexample
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Enthusiasts to spread the word about Linux and open source in general.
	And of course developers to write the software itself.
	
Insert and Append Lines:
									
	[diwakar@devops ~]$ # inserting and appending line before and after Testers
	[diwakar@devops ~]$ sed '/Testers/i\Developers who actually write code' sedexample
	Developers who actually write code
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	Enthusiasts to spread the word about Linux and open source in general.
	And of course developers to write the software itself.
	
	[diwakar@devops ~]$ sed '/Testers/a\Developers who actually write code' sedexample
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Developers who actually write code
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	Enthusiasts to spread the word about Linux and open source in general.
	And of course developers to write the software itself.
	
Range Selection:
										
	[diwakar@devops ~]$ # changing to to ot between 2 to 6 lines
	[diwakar@devops ~]$ sed '2,6s/to/ot/g' sedexample
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Designers ot create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-ots, and other important text distributed with software.
	Translaotrs ot take programs and documentation from their native languages and make them accessible ot people around the world.
	Packagers ot take software programs and put all the parts otgether ot make sure they run flawlessly in different distributions.
	Enthusiasts ot spread the word about Linux and open source in general.
	And of course developers to write the software itself.
	
Regex Patterns:
										
	[diwakar@devops ~]$ # making the changes persistent
	[diwakar@devops ~]$ cat sedexample
	Developers who actually write code
	
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	
	Designers to create user interfaces and graphics distributed with various programs.
	
	Writers who can create documentation, how-tos, and other important text distributed with software.
	
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	
	Enthusiasts to spread the word about Linux and open source in general.
	
	And of course developers to write the software itself.
	[diwakar@devops ~]$ sed -i '/^$/d' sedexample
	[diwakar@devops ~]$ cat sedexample
	Developers who actually write code
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	Enthusiasts to spread the word about Linux and open source in general.
	And of course developers to write the software itself.
	
	
Extract Text Between Patterns:
	
	[diwakar@devops ~]$ sed -n '/Developers/,/Enthusiasts/p' sedexample
	Developers who actually write code
	Testers to make sure everything works on different configurations of hardware and software, and to report the bugs when it does not.
	Designers to create user interfaces and graphics distributed with various programs.
	Writers who can create documentation, how-tos, and other important text distributed with software.
	Translators to take programs and documentation from their native languages and make them accessible to people around the world.
	Packagers to take software programs and put all the parts together to make sure they run flawlessly in different distributions.
	Enthusiasts to spread the word about Linux and open source in general.


