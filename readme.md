
<!-- Transferring file to VM : scp source destination 

Extract file : tar zxvf fileNameHere.tgz 

Go to `cd afl-2.52b/` 

Compile : ./afl-gcc ../example/dvcp.c -o dvcp 


./afl-fuzz -i ../example/input_example/ -o output -- ./dvcp @@ -->

# Installing american fuzzy lop (AFL) 
- Download AFL source code from http://lcamtuf.coredump.cx/afl/ in your local computer. 
- Connect to VM using command `ssh username@ip_address` in a terminal. For example, `rayhan@137.99.252.45`. 
- Navigate to `opt` folder using command `cd /opt`. Create a new folder inside of `/opt` using command `mkdir afl`. 

- Transfer your file to VM using command `scp source destination`. In order to transfer afl-latest.tgz to `/opt/afl`, open a new terminal and run command `scp afl-latest.tgz rayhan@137.99.252.45:/opt/afl/`. Change rayhan by your username and afl-latest.tgz if you have different file name. If your current working directory is the source directory, provide the full path of your souce directory. To get current working directory, you can run command `pwd`. 

- Go back to the terminal that is connected to server, and run command `ls` inside afl folder. You will be now able to view afl-latest.tgz file. 

- As it is zip file, unzip it using command `tar zxvf filename.tgz`. For example, `tar zxvf afl-latest.tgz` and it will create a folder named: afl-2.52b

- Navigate to your afl folder using command: `cd afl-2.52b`  

- Run command command `make` insider of your afl folder, and it will build afl on your system, for more details: https://afl-1.readthedocs.io/en/latest/quick_start.html 

# Transfering vulnerable C program and input files 

- Similarly, create another folder inside of `/opt/afl` directory using command `mkdir example`. Navigate to inside of example directory using command `cd example`. 

- Transfer dvcp.c file to the example folder using command `scp dvcp.c rayhan@137.99.252.45:/opt/afl/example` (This is a another terminal other than the terminal that is connected to VM. You can work on the same terminal through screening terminal, but for simplicity, open a new terminal at the folder that contains dvcp.c file). 

- Run command `ls` to view dvcp.c in the VM. 

- Crete another folder for the input as `mkdir input_example`. 

- Transfer the content of input folder from Git repo to the `/opt/afl/input_example` using command: `scp image.img rayhan@137.99.252.45:/opt/afl/example/input_example`

# Fuzzing any c program using AFL: 
- Compile your program using command format: `./afl-gcc your_program -o object_name`. For example, your can use this command `./afl-gcc ../example/dvcp.c -o dvcp`, to compile dvcp.c file for fuzzing. 

<!-- where
-fsanitize is used to enable various sanitizers, here I used address and undefined that explicitly tells to detect buffer overflow, use after free and undefined behavior respectively. Some other options for -fsanitizer are thread, memory, leak.  -->


- Run command using format: `./afl-fuzz -i input_directory -o output_directory -- object_name @@`. For example: `./afl-fuzz -i ../example/input_example -o output -- ./dvcp @@` for fuzzing your program, where 
    - i specifices input directory for initial test case. 
    - o means output directory where AFL stores crashes, testcases and other results of the fuzzing. 
    - @@ refers program takes input from a file. 

Now, you should be able to see AFL fuzzing running on your program similar to the screenshot.




