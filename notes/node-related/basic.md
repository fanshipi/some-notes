# Basic

**Ubuntu-20.04(wsl)**

[window10下的linux子系统wsl](https://docs.qq.com/doc/DVnN6bEpQaHBnckpw?newPad=1&newPadType=clone&u=604865cc7e814d7482b2af8400353e57)

安装软件：（下载路径Miscrosoft Store）Ubuntu 20.04 LTS和windows terminal

**注**：wsl（linux）的文件目录在/mnt/c/...，
而开发的代码不建议放在linux目录下,否则修改代码后监听不了变化（不会刷新）

**查看node安装位置**

```
root@xxx-PC2:~# which node
/root/.nvm/versions/node/v14.15.0/bin/node
```

**查看目录基本信息**

```
root@xxx-PC2:~# ls -lh
total 20K
-rw-r--r--  1 root root  13K Nov 12  2020 install_nvm.sh
drwxr-xr-x 16 root root 4.0K Nov 19  2021 vscodefiles

root@xxx-PC2:~# ls -lh /root/.nvm/versions/node/
total 8.0K
drwxr-xr-x 6 root root 4.0K Nov 12  2020 v14.15.0
drwxr-xr-x 6 root root 4.0K Aug  2  2021 v16.6.0
```

**指定默认node版本**

```
root@xxx-PC2:~# nvm alias default 16.6.o
```