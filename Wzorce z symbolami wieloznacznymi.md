**Wzorce z symbolami wieloznacznymi** *(ang. wildcard patterns, glob patterns)*. Podobne do nich (choć znacznie potężniejsze) są [[Regular Expressions]].



> [!NOTE] ChatGPT

Glob patterns, also known as globbing patterns, are a way to specify and match sets of filenames or paths based on wildcard characters. They are used in various contexts, including command-line shells, programming languages, and tools.

Glob patterns allow you to define flexible patterns to match multiple filenames or paths that share a common structure. The most commonly used wildcard characters in glob patterns are:

* (asterisk): Matches any number of characters (including none) within a path segment. For example, *.txt matches all files ending with ".txt" in a directory.

? (question mark): Matches a single character within a path segment. For example, file?.txt matches files like "file1.txt" or "fileA.txt" but not "file10.txt".

[ ] (brackets): Matches a single character within a specified range or set of characters. For example, [abc].txt matches files like "a.txt", "b.txt", or "c.txt".

[! ] (exclamation mark followed by brackets): Matches a single character not within the specified range or set of characters. For example, [!0-9].txt matches any file that doesn't start with a digit and ends with ".txt".

** (double asterisks): Matches zero or more directories and subdirectories. This is often used for recursive matching. For example, dir/**/*.txt matches all ".txt" files in the "dir" directory and its subdirectories.

Glob patterns provide a convenient way to specify file or path patterns that can be used for tasks such as file matching, file listing, or directory traversal. They are commonly used in command-line utilities, build tools, scripting languages, and file system operations to select or filter files based on their names or paths.