
# Basic #
**git stash**

当在一个分支上码代码时，此时有一个bug需要及时修复，而当前分支所做的修改不能commit，这时可以采用git stash命令隐藏当前所做的修改，再对bug进行修复进而commit。
恢复修改，有两种方法：

（1）git stash apply，该方法stash还存在，删除需要命令git stash drop；

（2）git stash pop，恢复的同时把stash内容也删除了。
**git add**

git add -A 提交所有变化

git add -u 提交被修改(modified)和被删除(deleted)文件，不包括新文件(new)

git add . 提交新文件(new)和被修改(modified)文件，不包括被删除(deleted)文件

git 版本不同会有所区别

**Git Version 1.x**

Directives|New Files|Modified Files|Deleted Files|Descriptions
|----------------|---------------|---------------|----------------|-----------|
git add -A|&check;|&check;|&check;|Staged All(new, modified, deleted) files
git add .|&check;|&check;|&cross;|Stage New and Modified files only
git add -u|&cross;|&check;|&check;|Stage Modified and Deleted files only

**Git Version 2.x**

Directives|New Files|Modified Files|Deleted Files|Descriptions
|----------------|---------------|---------------|----------------|-----------|
git add -A|&check;|&check;|&check;|Staged All(new, modified, deleted) files
git add .|&check;|&check;|&check;|Staged All(new, modified, deleted) files
git add --ignore-removal|&check;|&check;|&cross;|Stage New and Modified files only
git add -u|&cross;|&check;|&check;|Stage Modified and Deleted files only


**git commit常用**

git commit -m'提交信息'

git commit -a -m'提交信息'

git commit -am'提交信息'----- -a参数是指可以把未add到staged的修改一起提交

git commit --amend 两个作用：

1、修改上一次的提交信息

2、可将最近的修改追加到上一次的提交上

git commit 回车=》进入vim编辑器信息修改，i 插入文字的命令，修改后esc退出修改，w保存修改，q退出窗口

git commit --amend --no-edit（取消编辑）
# Issue #
**bash:yarn command not found**

对于安装yarn，显示安装成功但运行时找不到该文件命令，考虑环境变量问题，用户环境变量pash及系统环境变量path设置：先找到安装路径，再进入环境变量设置path，path之间用;隔开.

**Error:Could not fork child process:There are no available terminals**

当git bash窗口打开报错：Error:Could not fork child process:There are no available terminals，打开cmd命令窗口，输入tasklist查看运行程序，找到git bash的进程号，执行taskkill /pid 9872 -t -f将进程终止

**代码stash误删**

参考链接：[git stash 删除后找回的方法](https://blog.csdn.net/gang123123123/article/details/84253427)

a.git fsck --lost-found查看记录。

b.git show commitid查看对应的信息记录，会显示大概的代码情况c.找到想要的代码之后git merge commitid

参考链接：

1.[git stash内容误删找回](https://www.jianshu.com/p/8452eff3a75e)

2.[本地git分支被误删，如何找到该分支的提交记录和代码?](https://juejin.im/post/6844903907592765448)

git log -a 查看整体的信息

3.[git 误删分支恢复方法](https://blog.csdn.net/fdipzone/article/details/50616386)

**.gitignore文件不生效**

.gitignore文件：用于push代码到远程的时候，忽略掉文件中提及的文件

当配置完成并push到了远程，代码检查工具检查后依然未生效时，考虑git本地缓存问题，用git rm -r --cached删除缓存，再重新add并commit，参考链接： [.gitignore不生效的解决方案](https://blog.csdn.net/zwkkkk1/article/details/83550032)，
可参考 [git配置运维总结](https://www.cnblogs.com/kevingrace/p/5690241.html)、[github/gitignore](https://github.com/github/gitignore)
