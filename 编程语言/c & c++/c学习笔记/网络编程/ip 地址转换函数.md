## 字符串转换网络字节序地址
* 点分十进制数串字符串(例如192.168.1.1)
* ipv4 是 32位网络字节序地址
* ipv6 是 32位网络字节序地址

```
#include <arpa/inet.h>

int inet_aton(const char* strptr, struct in_addr *addrptr);
返回： 1----串有效
　　　 0----串有错
　　　 
in_addr_t inet_addr(const char* strptr);
返回： 成功，32位二进制的网络字节序地址
　　　 失败，返回INADDR_NONE
　　　 
int inet_pton(int family, const char* strptr, void *addrptr);
family：AF_INET/AF_INET6
返回： 1---成功
　　　 0---输入不是有效格式
　　　 -1--出错　　　 
```
* inet_aton 和 inet_addr 函数只支持 ipv4
* inet_pton 通用

## 网络字节序地址转换字符串
### ipv4 32位网络字节序地址 ==转换== 点分十进制数串字符串
```
char *inet_ntoa(struct in_addr inaddr);
```
### ipv6
```
const char *inet_ntop(int family, const void *addrptr, char *strptr, size_t len);
返回： NULL 出错
```