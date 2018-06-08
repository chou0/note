* 文件chmod后其mode某些位是改变了的，如果严格的比较原文件和chmod后的文件，两者是有区别的，但是源代码通常只关心文本内容，因此chmod产生的变化可以忽略，
```
切到源码的根目录下
git config --add core.filemode false
```