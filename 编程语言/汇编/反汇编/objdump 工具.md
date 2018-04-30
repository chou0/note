如果你装的是arm-elf-objdump  
那么arm-elf-objdump -d a.elf > 1.txt
如果你装的是arm-eabi-objdump  
那么arm-eabi-objdump -d a.elf > 1.txt 

arm-elf-objdump:反汇编工具，将elf工具，转变成汇编代码。   
arm-elf-objdump -d a.out > 1.txt将a.out 转变成汇编代码并输出到1.txt文件