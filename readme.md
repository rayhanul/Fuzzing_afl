
<!-- Transferring file to VM : scp source destination 

Extract file : tar zxvf fileNameHere.tgz 

Go to `cd afl-2.52b/` 

Compile : ./afl-gcc ../example/dvcp.c -o dvcp 


./afl-fuzz -i ../example/input_example/ -o output -- ./dvcp @@ -->

# Installing american fuzzy lop (AFL) 
- Download AFL source code from http://lcamtuf.coredump.cx/afl/
- Transfer your file to VM using command `scp source destination`, for example I transfered our file using command `scp afl-latest.tgz rayhan@137.99.252.45:/opt/afl/`. Change rayhan by your username. 

- If it is zip file, unzip it using command `tar zxvf filename.tgz`. For example, `tar zxvf afl-latest.tgz` and it will create a folder named: afl-2.52b

- Navigate to your afl folder using command: `cd afl-2.52b`  

- Run command command `make` insider of your afl folder, and it will build afl on your system, for more details: https://afl-1.readthedocs.io/en/latest/quick_start.html 


# Fuzzing any c program using AFL: 
- Compile your program using command format: `./afl-gcc your_program -o object_name`. For example, your can use this command `./afl-gcc ../example/dvcp.c -o dvcp`, to compile dvcp.c file for fuzzing. 

<!-- where
-fsanitize is used to enable various sanitizers, here I used address and undefined that explicitly tells to detect buffer overflow, use after free and undefined behavior respectively. Some other options for -fsanitizer are thread, memory, leak.  -->


- Run command using format: `afl-fuzz -i input_directory -o output_directory -- object_name @@`. For example: `afl-fuzz -i ../example/input_example -o output -- ./dvcp @@` for fuzzing your program, where 
    - i specifices input directory for initial test case. 
    - o means output directory where AFL stores crashes, testcases and other results of the fuzzing. 
    - @@ refers program takes input from a file. 

Now, you should be able to see AFL fuzzing running on your program similar to the screenshot.




