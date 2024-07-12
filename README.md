# 如何搭建使用?
## 1、前往serv00注册一台服务器（免费）
https://www.serv00.com/
请使用工具访问并注册，不然无法接收到邮件
What is the cost of hosting on serv00.com?
填free即可
![QQ_1720763615467](https://github.com/user-attachments/assets/57b5480c-b4c2-48e3-8395-63ab0e86bcc0)
## 2、根据邮件信息登录控制面板
### 1-开启权限
进入面板后点击Additional services->Run your own applications->Enable
### 2-开启端口
进入面板后点击Port reservation->Add port
Port [自己填写或者点随机]
Port type [tcp]
Description [空着可以不填]
## 3、根据邮件信息登录SSH
这个啥都行，你能登录就好
进入后cd进网站目录
```
cd domains/你注册的时填写的用户名.serv00.net/
```
复制脚本一件安装
```
wget -O 'start.sh' 'https://raw.githubusercontent.com/lettimepassby/serv00-vless/main/start.sh' && chmod +x start.sh && ./start.sh
```
结束后会有提示
## 4、进入网页面板更改参数
进入网页面板后点击File manager
找到domains/你注册的时填写的用户名.serv00.net/vless
点击app.js修改参数
### 1-UUID
UUID需要你在v2ray软件内随机生成一个
操作方法：
打开v2ray
点击服务器-添加vless服务器-点击用户id旁边的生成按钮
### 2-端口
端口就是在2-2中你开启的端口

修改好后点击save保存

## 5、测试运行
在ssh中运行
```
node /home/用户名/domains/用户名.serv00.net/vless/app.js
```

当他显示
listen: 端口号
即表示配置成功
## 6、配置连接
打开v2ray客户端
备注: 你可以填写任意的备注名称，例如 serv00-vless。
地址: 用户名.serv00.net
端口: 你设置的端口
用户ID (UUID): 你生成的uuid
加密方式: none
传输协议: WS
路径: /
## 7、持续化运行
直接输入
```
screen -S vless node /home/用户名/domains/用户名.serv00.net/vless/app.js
```
然后使用ctrl+a+d即可实现后台运行
但据传serv00会不定期重启服务器所以加个定时任务还是有必要的
还是进入网页管理端
Cron jobs->Add cron job-
Specify time [After reboot]
Command screen -S vless node /home/用户名/domains/用户名.serv00.net/vless/app.js

填这两项就够了
好了尽情享受吧
