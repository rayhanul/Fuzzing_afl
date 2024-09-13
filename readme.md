# Install american fuzzy lop (afl): http://lcamtuf.coredump.cx/afl/
- Download afl.
- Read QuickStartGuide in the doc folder

# Once you are done with installing AFL, run the following commands:
- compile your program using command `afl-gcc -fsanitize=address -fsanitize=undefined -o dvcp.c` 
- run command `afl-fuzz -i input -o output -m none -- ./dvcp` to running fuzzing 

Now you should be able to see AFL fuzzing your program. 




