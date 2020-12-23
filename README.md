# miniShell

---- From cover page for original coursework ----

●	Command prompt, reading input, parsing string into pieces, able to handle different types of commands (exit and cd in particular), loop to repeat

○	Exit and cd are handled by checking the first token in the input string to see if it is exit or cd. If it is exit it changes the variable managing the entire while loop to false breaking the loop. If it is cd the chdir command to change the directory we are working in. We considered using a switch statement but were advised against it because of the complications with usings strings in c.

●	Doing the fork, and the execvp, and parent doing a waitpid

○	When we first make the fork we take the processor id and save it into the variable pid. We then use an if statement to check what processor we are in, and if we are in the child process we run the execvp to begin running a program. In the parent we do a waitpid to wait until the forked process is finished.

●	Handling both < and > (Input file and Output file)

○	We created a loop that looked through all the tokens for <, > and &. When the loop found a < or a >, it set a corresponding int variable, either the variable in or the variable out,  to 1 and set the char* variable for filename to the next token. The loop then removed the tokens from the token array. 
○	When the program finishes with the previous loop, the program goes to another loop. In this loop it first checks if any of the int variables corresponding to the input files or output files are set to 1. If they are, then the program runs the freopen() method and changes the filestream for that child process. It then runs the tokens left in the token array.

●	Handling & (Background processes)

○	As stated previously, the loop that looks for the tokens < and > also looks for the token &. This changes the corresponding int variable bg to 1
○	When the program gets to the next loop, it looks to see if the bg int variable is set to 1 and if it is, it runs the signal() method and kills the zombie process.
