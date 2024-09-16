# Installing american fuzzy lop (AFL) 
- Download AFL from http://lcamtuf.coredump.cx/afl/
- Go to https://lcamtuf.coredump.cx/afl/QuickStartGuide.txt for quick start guides.
- Go to inside of AFL using command `cd afl-latest\afl-2.52b` and run command `make`.
- This will build AFL on your system. For more details, please visit: https://afl-1.readthedocs.io/en/latest/quick_start.html 


# Fuzzing any c program using AFL: 
- Compile your program using command format: `afl-gcc your_program -o object_name`. For example, your can use this command `afl-gcc dvcp.c -o dvcp`, to compile dvcp.c file for fuzzing. 

<!-- where
-fsanitize is used to enable various sanitizers, here I used address and undefined that explicitly tells to detect buffer overflow, use after free and undefined behavior respectively. Some other options for -fsanitizer are thread, memory, leak.  -->


- Run command using format: `afl-fuzz -i input_directory -o output_directory -- object_name @@`. For example: `afl-fuzz -i input -o output -- ./dvcp @@` for fuzzing your program, where 
    -i specifices input directory for initial test case. 
    -o means output directory where AFL stores crashes, testcases and other results of the fuzzing. 
    - @@ refers to reading from file. 

Now, you should be able to see AFL fuzzing running on your program similar to the screenshot.




