廖文华(liaowenhua)  18:02:54
过滤是 在我们这边做的，阈值提高了，一些人脸就可能被过滤掉了，表现就是有人 过去可能没抓拍
君正-姜忠钦(522348444)  18:09:22
这个可能需要根据具体的误测场景来进行分析定位原因，最好将客户的误测场景保存下来发给我们.
另外还有几种简单的方式：
1. 如果客户只是需求正脸或近似正脸，可以通过object中的yaw来进行过滤
2. 可以打开一个offset,通过IHwDet_Set_Offset接口，传参数0x9进去将1，4打开，误测会少一些。但是功耗会增加大约60mw.
