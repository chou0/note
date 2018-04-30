* Linux 平台下的汇编工具虽然种类很多,但同 DOS/Windows 一样,最基本的仍然
是汇编器、连接器和调试器

### 汇编器
汇编器(assembler)的作用是将用汇编语言编写的源程序转换成二进制形式的目标
代码。

1. Linux 平台的标准汇编器是 GAS,它是 GCC 所依赖的后台汇编工具,通常包含在 binutils 软件包中。
* GAS 使用标准的 AT&T汇编语法,可以用来汇编用
AT&T 格式编写的程序
```
wangzhe@wangzhe-laptop:~$ as -o hello.o hello.s
```
2. Linux 平台上另一个经常用到的汇编器是 nasm,它提供了很好的宏指令功能,并
能够支持相当多的目标代码格式,包括 bin、a.out、coff、elf、rdf 等。
* NASM 采用的是人工编写的语法分析器,因而执行速度要比 GAS 快很多,
* 更重要的是它使用的是 Intel 汇编语法,可以用来编译用 Intel 语法格式编写的汇编程序
```
wangzhe@wangzhe-laptop:~$ nasm -f elf hello2.asm 
```
### 链接器
由汇编器产生的目标代码是不能直接在计算机上运行的,它必须经过链接器的处理
才能生成可执行代码。链接器通常用来将多个目标代码连接成一个可执行代码,这
样可以先将整个程序分成几个模块来单独开发,然后才将它们组合(链接)成一个应
用程序。 
* Linux 使用 ld 作为标准的链接程序,它同样也包含在 binutils 软件包中。
汇编程序在成功通过 GAS 或 NASM 的编译并生成目标代码后,就可以使用 ld 将
其链接成可执行程序了
```
wangzhe@wangzhe-laptop:~$ ld -o hello hello.o
```
### 调试器
有人说程序不是编出来而是调出来的,足见调试在软件开发中的重要作用,在用汇
编语言编写程序时尤其如此。Linux 下调试汇编代码既可以用 GDB、DDD 这类通
用的调试器,也可以使用专门用来调试汇编代码的 ALD(Assembly Language
Debugger)。
从调试的角度来看,使用 GAS 的好处是可以在生成的目标代码中包含符号表
(symbol table),这样就可以使用 GDB 和 DDD 来进行源码级的调试了。要在生成
的可执行程序中包含符号表,可以采用下面的方式进行编译和链接:
```
wangzhe@wangzhe-laptop:~$ as --gstabs -o hello.o hello.s
wangzhe@wangzhe-laptop:~$ ld -o hello hello.o
wangzhe@wangzhe-laptop:gdb -q hello
```