#MINISHELL

###TEAM MATES INFORMATIONS:
* NAME 1 : ABHISHEK JAIN
* NAME 2 : PRADYUMNA KAUSHIK
__________________________________________________________________________________________________________________________

##FILES :
	1. **minish.c** - C source code of the minish shell.
	2. **Makefile** - Makefile to 'make' the project (compile the minish shell) source
	   	      code and generate the executable.
	3. **README.md** - README file which includes details of the AUTHORS, instructions to run
		    the project and also includes bug logs, referenes etc.


##SOFTWARE REQUIREMENTS:
	1. **GCC version 5.2.0** and upwards.

	NOTE: Any lower version may result in **underfined behaviour** including compilation errors and memory corruptions.


##INSTRUCTIONS TO RUN THE SHELL:

	1. First we need to 'make' the project in-order to run the shell.
	   Do this by running the command as shown bellow :
		 ```
		 make
		 ```

	2. If make succeeds, do *ls* in the current directory and check for *shell*
	   executable.
	   Run the executable as shown below :
		 ```
		./shell
		```
	   This should start the minish shell.

	3. To clean up the project and to make again, first run the following command :
		```
		make clean
		```
	   This should have removed the object file in the project directory.

##FALLBACK EXECUTION INSTRUCTIONS IF make FAILS:

	*NOTE : SKIP THIS SECTION IF make was successful i.e. if make did not throw errors.*

	1. Say for some unexpected reason 'make' fails. Then compile the shell C source
	   code by using gcc as shown below:
		```
		gcc minish.c -o shell.o
		```
		*or*
		```
		gcc minish.c -o shell
		```
	2. Then run the shell as follows:
		```
		./shell.o
		```
		*or*
		```
		./shell
		```
	3. *make clean* may not work in this case so may require explicit command by
	    the user to remove the object files.

##BUGS IN THE PROGRAM:

	1. **regcomp()** in *regex.h* : the **regcomp()** module is buggy as it "sometimes" results in
	   malloc() error.
	   Please note that IF THIS ERROR OCCURS WHILE TESTING, the shell source code does
	   not contain any bugs. Its the library issue, as we believe the library is deprecated.
	   Reason to use it was to detect the foreground and background commands. The approach of tokenization
	   and detection may result in segmentation faults.
	   For example: the following will result in a segmentation fault:
		```
		minish>gcc test_sleep.c -o bin/test_sleep.o

 		<compiles successfully>

		minish>ls
		segmentation fault
		```

		The following link give more information on this :

		https://lists.ubuntu.com/archives/foundations-bugs/2012-May/089662.html


	  Any command after the above gcc command throws a segmentation fault.
	  We ran the code with gdb and realized that the **regcomp()** is throwing a segmentation fault.
	  But the following does not lead to segmentation fault :
		```
		minish>gcc test_sleep.o -o test_sleep.o

		<compiles successfully>

		minish>ls

		<works>
		```

		Other variants like **gcc <filename.c>** or **gcc <flags> <filename.c>** work. Only the
		**gcc <filename.c> -<flags> -o <folder>/<object_file.o>** throws a segmentation fault.

		Please NOTE that sometimes **gcc <filename.c> -o <executable>** gives a memory corruption error.

	2. Continuing a suspended process in foreground works fine, but after the process completes
	   execution it goes into an infinite loop. You will need to hit *<Ctrl-C>* to get back the prompt.

##REFERENCES:

	* http://stackoverflow.com/questions/19814906/which-child-process-send-sigchld
	* http://stackoverflow.com/questions/2595503/determine-pid-of-terminated-process
	* http://stackoverflow.com/questions/12587621/signal-handler-sa-sigaction-arguments
	* http://www.gnu.org/software/libc/manual/html_node/Sigaction-Function-Example.html
	* http://man7.org/linux/man-pages/man2/sigaction.2.html
	* http://stackoverflow.com/questions/4200373/just-check-status-process-in-c
	* https://en.wikipedia.org/wiki/Unix_signal
	* http://man7.org/linux/man-pages/man2/getpid.2.html
	* http://linux.die.net/man/3/tcsetpgrp
	* http://stackoverflow.com/questions/1157700/how-to-wait-for-exit-of-non-children-processes
	* http://stackoverflow.com/questions/1058047/wait-for-any-process-to-finish
	* http://www.gnu.org/software/libc/manual/html_node/Job-Control.html
	* https://ftp.gnu.org/old-gnu/Manuals/glibc-2.2.3/html_chapter/libc_27.html
	* http://www.gnu.org/software/libc/manual/html_node/Implementing-a-Shell.html
	* http://linuxcommand.org/lts0080.php
	* http://linux.die.net/man/3/execvp
	* http://www.csl.mtu.edu/cs4411.ck/www/NOTES/process/fork/exec.html
	* http://linux.die.net/man/2/waitpid
	* http://linux.die.net/man/3/waitpid
	* https://www.mkssoftware.com/docs/man3/waitpid.3.asp
	* https://support.sas.com/documentation/onlinedoc/sasc/doc/lr2/waitpid.htm
	* http://stackoverflow.com/questions/21248840/example-of-waitpid-in-use
	* http://linux.die.net/man/2/kill
	* http://linux.die.net/man/3/kill
	* http://tldp.org/LDP/lpg/node11.html
	* http://www.gnu.org/software/libc/manual/html_node/Creating-a-Pipe.html
	* http://man7.org/tlpi/code/online/diff/pipes/simple_pipe.c.html
	* https://www.cs.cf.ac.uk/Dave/C/node23.html
	* http://stackoverflow.com/questions/9493234/chdir-to-home-directory
	* http://stackoverflow.com/questions/298510/how-to-get-the-current-directory-in-a-c-program
	* http://linux.die.net/man/3/getcwd
	* http://www.gnu.org/software/libc/manual/html_node/Working-Directory.html
	* http://cboard.cprogramming.com/c-programming/100200-check-blank-spaces-string.html
	* http://stackoverflow.com/questions/17259250/fwrite-doesnt-print-anything-to-stdout
	* http://www.tutorialspoint.com/c_standard_library/c_function_fwrite.htm
	* http://stackoverflow.com/questions/13377773/proper-way-to-handle-signals-other-than-sigint-in-python
	* http://www.cons.org/cracauer/sigint.html
	* http://www.cplusplus.com/forum/beginner/1501/
	* http://stackoverflow.com/questions/6970224/providing-passing-argument-to-signal-handler
	* http://www.gnu.org/software/libc/manual/html_node/Permission-for-kill.html
	* http://pubs.opengroup.org/onlinepubs/009695399/functions/getpgrp.html
	* http://stackoverflow.com/questions/22422400/error-initialization-makes-pointer-from-integer-without-a-cast
	* http://stackoverflow.com/questions/5582211/what-does-define-gnu-source-imply
	* http://www.gnu.org/software/libc/manual/html_node/Feature-Test-Macros.html
	* http://www.regular-expressions.info/repeat.html
	* http://www.gnu.org/software/libc/manual/html_node/Process-Creation-Example.html
	* http://stackoverflow.com/questions/28457525/how-do-you-kill-zombie-process-using-wait
	* http://codereview.stackexchange.com/questions/20897/trim-function-in-c
	* http://stackoverflow.com/questions/122616/how-do-i-trim-leading-trailing-whitespace-in-a-standard-way
	* http://unix.stackexchange.com/questions/5642/what-if-kill-9-does-not-work
	* https://major.io/2010/03/18/sigterm-vs-sigkill/
	* http://unix.stackexchange.com/questions/132224/is-it-possible-to-get-process-group-id-from-proc
	* http://ubuntuforums.org/showthread.php?t=1430052
	* http://ubuntuforums.org/showthread.php?t=1749381
	* http://theunixshell.blogspot.com/2012/12/running-background-process-and.html
	* http://stackoverflow.com/questions/21871325/execvp-system-call-not-executing
	* http://www.computerhope.com/unix/ucsh.htm
	* http://www.peope.net/old/regex.html
	* ftp://ftp.gnu.org/old-gnu/Manuals/grep-2.4/html_chapter/grep_5.html
	* http://regexr.com
	* http://www.seeingwithc.org/topic7html.html
  * http://stackoverflow.com/questions/1631450/c-regular-expression-howto
	* http://stackoverflow.com/questions/18477153/c-compiler-warning-unknown-escape-sequence-using-regex-for-c-program
	* http://stackoverflow.com/questions/1395177/regex-to-exclude-a-specific-string-constant
	* https://blog.udemy.com/c-string-to-int/
	* http://stackoverflow.com/questions/3213827/how-to-iterate-over-a-string-in-c
	* http://stackoverflow.com/questions/21592494/initializer-element-is-not-constant-error-for-no-reason-in-linux-gcc-compilin
	* http://www.cplusplus.com/forum/general/8795/
	* http://pubs.opengroup.org/onlinepubs/009695399/functions/regcomp.html
	* http://stackoverflow.com/questions/22573292/glibc-detected-a-out-double-free-or-corruption-out-0xbfe69600
	* http://cboard.cprogramming.com/c-programming/98173-regular-expression-tutorial-help.html
	* http://www.gnu.org/software/libc/manual/html_node/Regexp-Cleanup.html#Regexp-Cleanup
	* http://stackoverflow.com/questions/23031590/reading-from-pipe-into-buffer-character-by-character-find-the-size-of-data-in-pi
	* http://www.cs.cornell.edu/Courses/cs414/2004su/homework/shell/shell.html
	* http://brennan.io/2015/01/16/write-a-shell-in-c/
	* http://stackoverflow.com/questions/1500004/how-can-i-implement-my-own-basic-unix-shell-in-c
