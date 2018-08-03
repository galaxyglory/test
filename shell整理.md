# Shell整理



#### 系统支持的Shell

```shell
#cat /etc/shells

/bin/sh
/bin/bash
/sbin/nologin
/bin/dash
/bin/tcsh
/bin/csh
```

#### Shell说明

`man test`

#### Shell &&和||

`#[ -f mbr.bin ]&&echo 1||echo 0`

> - &&:若前一个命令执行成功,才会接着执行下一个
> - 命令一||命令二||命令三     当命令一执行成功时,就不会再往下执行;若命令一执行失败,才会执行命令二;只有当前边两个命令都执行失败时,命令三才会被执行.
> - 命令一;命令二;命令三         各指令的执行互不影响
> - (命令一;命令二;命令三)      ()开启一个子shell环境执行
> - { 命令一;命令二;命令三 }    大括号两边有一个以上空格,在当前的shell环境执行

#### Shell文件测试

```shell
[root@centos ~]# [ -f /var/log ]&&echo 1||echo 0       
0
[root@centos ~]# [ -d /var/log ]&&echo 1||echo 0 
1
[root@centos ~]# [ -e /var/log ]&&echo 1||echo 0 
1
[root@centos ~]# [ -r mbr.bin ]&&echo 1||echo 0        

1
[root@centos ~]# [ -w mbr.bin ]&&echo 1||echo 0 

1
[root@centos ~]# [ -x mbr.bin ]&&echo 1||echo 0 
0
[root@centos ~]# ll mbr.bin 

-rw-r--r--. 1 root root 512 Nov 14 14:15 mbr.bin

[root@centos ~]# chmod 0000 mbr.bin 

[root@centos ~]# [ -r mbr.bin ]&&echo 1||echo 0
1
[root@centos ~]# ll mbr.bin 

----------. 1 root root 512 Nov 14 14:15 mbr.bin
```



