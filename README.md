###By:
    Tung Lin (Tom) Hsieh, Wang Ho (Allen) Ha
---
###Abstract:
    This is Rshell created for assignment 2 of CS100 in Spring 2016.
    Part II updated in early March for assignment 3 of the same class.
---
###Known Bugs/Issues:
    -   This rshell does not interpret bash operators besides "&&", "||", and 
    ";" very well. An input like "ls &" will be read as 'execute ls in 
    background' in bash while it is interpreted as 'ls with a flag "&"' in 
    rshell. In rshell other non-related bash chaining operators will be 
    treated as if they are part of a command.

    -   Inputting "ls -e" to the program will bug it because execvp() returns a 
    success signal as ls is called successfully. However, option -e will not 
    work for ls, so ls will not do its job although successfully called. So, 
    we cannot get what we want which is for execvp() to return the fail value. 
    As a consequence, commands like "ls -e && echo why" will print 'why' in 
    rshell while it will not print 'why' in bash.

    -   Commands may not exceed 998 characters because strtok() interacts very 
    badly with dynamically allocated array and will not let it be freed 
    properly causing a unsolvable memory leak. After 3 hours of work I (Tom) 
    decided that we will not worry about single bash commands over 998 
    characters long (by single I mean commands with no connectors). Also there 
    cannot be more than 99 tokens in a single command for a similar reason.

    -   During a command that takes a significant amount of time 
    (e.g. ping -c 10 www.google.com), any input from the keyboard will be 
    recognized by rshell and executed or attached to the front of your next 
    input after the long-lasting command halted.

    -   !SHELL SCRIPTS ONLY! User commands in a heredoc input redirection into 
    rshell will not have a newline character displayed on the screen since we 
    use getline to received user input and getline rids the input string of 
    the '\n' delimiter. So if it is not typed out into rshell, it will not be 
    shown on your screen. The consequence of this is a weirdly formatted output
    when you are using a script, and have no substantial affects other than
    aesthetically displeasing.

    -   As we use strtok to break up user inputs, our program currently cannot
    treat arguments in the form of "[arguments with spaces]" as a whole. This
    also applies to other arguments that need a space inbewteen words.
---     
###Known Bugs/Issues part II:
    -   The "((" and "))" operator in bash is not interpreted as usual, so they
    will be interpreted as two separate regions covered by parentheses.

    -   The test command in its bracket form will need spaces between each argument
    (i.e. [-e bin] will not work but [ -e bin ] will). This is due to the use of
    strtok for its implementation.

    -   The shell script uses heredoc and assumes the directory of rshell to be
    at "~/rshell/bin/rshell".
---
