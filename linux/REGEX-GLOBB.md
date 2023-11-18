Regular expressions (regex or regexp) : searching, matching, and manipulating text based on patterns

Uses : They are widely used in various Linux commands and utilities, such as grep, sed, awk, and others

Common Constructs: 

	.	: Matches any single character except a newline.
	*	: Matches zero or more occurrences of the preceding character or group.
	+	: Matches one or more occurrences of the preceding character or group.
	?	: Matches zero or one occurrence of the preceding character or group.image?.jpg
	|	: Acts as a logical OR, allowing you to match one of multiple patterns.
	[]	: Defines a character class, allowing you to match any one character from a specified set.
	[^]	: Matches any character except those in the specified set. [^0-9]
	()	: Groups characters together to form sub-patterns.
	{ }	Specifies a group of alternatives separated by commas. {file1,file2}.txt
	**	Recursively matches files and directories in subdirectories.**/*.txt
	[ - ]	Specifies a range of characters within a character class [0-9] matches any single digit.
	\	In regular expressions, the backslash is used to escape characters with special meanings, such as . (dot), * (asterisk), ? (question mark), and others
	

