By:
    Tung Lin Hsieh, Wang Ho Ha

Abstract:

    This is Rshell created for assignment 2 of CS100 in Spring 2016.

Known Bugs/Issues:

    -This rshell does not interpret bash operators besides "&&", "||",
     and ";" very well. An input like "ls &" will be read as 'execute ls
     in background' in bash while it is interpreted as 'ls with a flag "&"'
     in rshell. In rshell other non-related bash chaining operators will be
     treated as if they are part of a command.

    -By inputting "ls -e" to the program, the program is bugged because it returned
     a success signal to execvp(). However, according to the man page, option -e 
     will not work for ls. So, we cannot get what we want by returning the fail 
     value. We believe the reason is ls go through the execvp(), while the flags
     are not counted while we execute execvp().
