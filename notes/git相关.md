
# 基本指令 #
**git stash**

当在一个分支上码代码时，此时有一个bug需要及时修复，而当前分支所做的修改不能commit，这时可以采用git stash命令隐藏当前所做的修改，再对bug进行修复进而commit。
恢复修改，有两种方法：

（1）git stash apply，该方法stash还存在，删除需要命令git stash drop；

（2）git stash pop，恢复的同时把stash内容也删除了。

**git commit常用**

git commit -m'提交信息'

git commit -a -m'提交信息'/git commit -am'提交信息'----- -a参数是指可以把未add到staged的修改一起提交

git commit --amend 两个作用：1、修改上一次的提交信息
2、可将最近的修改追加到上一次的提交上

git commit 回车=》进入vim编辑器信息修改，i 插入文字的命令，修改后esc退出修改，w保存修改，q退出窗口

git commit --amend --no-edit（取消编辑）
# issue #
**bash:yarn command not found**

对于安装yarn，显示安装成功但运行时找不到该文件命令，考虑环境变量问题，用户环境变量pash及系统环境变量path设置：先找到安装路径，再进入环境变量设置path，path之间用;隔开.

**Error:Could not fork child process:There are no available terminals**

当git bash窗口打开报错：Error:Could not fork child process:There are no available terminals，打开cmd命令窗口，输入tasklist查看运行程序，找到git bash的进程号，执行taskkill /pid 9872 -t -f将进程终止

**代码stash误删**

https://blog.csdn.net/gang123123123/article/details/84253427

a.git fsck --lost-found查看记录。

b.git show commitid查看对应的信息记录，会显示大概的代码情况c.找到想要的代码之后git merge commitid

https://www.jianshu.com/p/8452eff3a75e 
https://juejin.im/post/6844903907592765448：git log -a 查看整体的信息
https://blog.csdn.net/fdipzone/article/details/50616386
