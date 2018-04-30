在使用Linux系统的过程中，有时候会遇到端口被占用而导致服务无法启动的情况。比如HTTP使用80端口，但当启动Apache时，却发现此端口正在使用。

这种情况大多数是由于软件冲突、或者默认端口设置不正确导致的，此时需要查看究竟哪个进程占用了端口，来决定进一步的处理方法。

 

 

查看端口占用情况的命令：lsof -i
1	[root@www ~]# lsof -i
2	 
3	COMMAND PID USER FD TYPE DEVICE SIZE NODE NAME
4	nginx 2333 root 6u IPv4 6242 TCP *:http (LISTEN)
5	nginx 2334 www 6u IPv4 6242 TCP *:http (LISTEN)
6	sshd 2349 root 3u IPv6 6283 TCP *:ndmp (LISTEN)
7	sshd 2349 root 4u IPv6 6286 TCP *:ssh (LISTEN)
这里返回了Linux当前所有打开端口的占用情况。第一段是进程，最后一列是侦听的协议、侦听的IP与端口号、状态。如果端口号是已知的常用服务（如80、21等），则会直接显示协议名称，如http、ftp、ssh等。

 

查看某一端口的占用情况： lsof -i:端口号
1	[root@www ~]# lsof -i:21
2	 
3	COMMAND PID USER FD TYPE DEVICE SIZE NODE NAME
4	pure-ftpd 2651 root 4u IPv4 7047 TCP *:ftp (LISTEN)
5	pure-ftpd 2651 root 5u IPv6 7048 TCP *:ftp (LISTEN)
这里显示出21号端口正在被pure-ftpd使用，状态是listen。

 

结束占用端口的进程：killall 进程名
虽然我们不建议用这种本末倒置的方法来解决冲突问题，但某些情况下还是可以直接结束掉占用进程的（比如重启Apache时进程没有完全退出，导致重启失败）

1	[root@www ~]# killall pure-ftpd
这样，所有的pure-ftpd进程都会被结束掉。

//=============================

http://www.bootf.com/186.html 

也可使用命令：
netstat -apn|grep <端口号>
例如：
Linux代码  
[root@SonarServer1 user0]# netstat -apn|grep 80  
tcp        0      0 :::80                       :::*                        LISTEN      19408/java    
 找到进程号以后，再使用以下命令查看详细信息：
ps -aux|grep <进程号>
