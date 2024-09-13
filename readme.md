# Installing american fuzzy lop (AFL) 
- Download AFL from http://lcamtuf.coredump.cx/afl/
- Read QuickStartGuide in the doc folder

# Running AFL on any c program: 
- Compile your program using command `afl-gcc -fsanitize=address -fsanitize=undefined -o dvcp.c`.
- Run command `afl-fuzz -i input -o output -m none -- ./dvcp @@` for fuzzing your program. 

Now, you should be able to see AFL fuzzing running on your program similar to the screenshot.




