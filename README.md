Git的配置
1.配置用户名：git config --global user.name "您的用户名"

2.配置用户邮箱：git config --global user.email "您的邮箱地址"

3.保存用户名和密码：git config --global credential.helper store

4.查看配置信息：git config --global --list

注：1.global可以替换为local或者system，local表示支队本地仓库有限，system表示对所有用户有效。2.第1和第2点也可以用于修改用户信息。

创建仓库
方式一：git init，创建本地仓库

方式二：git clone，从远程服务器克隆一个仓库到本地

区
工作区：working directory

暂存区：staging ara/index

本地仓库：local repository

文件状态
未跟踪：Untrak

未修改：Unmodified

已修改：Modified

已暂存：Staged

git status：查看仓库的状态

gitbash操作命令
cd xxx，进入文件夹

cd ..，回到上一级

cd d:切换盘符

ls：列出工作区的所有文件

git ls-files，查看暂存区的文件

echo “内容” > file1.txt，创建文本文档file1.txt，并向其中写入内容

cat file1.txt，查看文件file1.txt的内容

删除本地文件：rm file1.txt

删除本地文件夹：rm -rf foledername

vi file1.txt，修改文件内容，修改完按ESC退出编辑模式，输入:wq保存

新增到暂存区
git add file1.txt

git add *.txt，将当前文件夹所有.txt的文件添加

git add .，将当前文件夹所有文件添加

git rm --cache file1.txt，从暂存区删除文件

提交到仓库
git commit -m "提交信息"，提交暂存区的文件到仓库

查看提交记录
git log，查看commit提交记录

git log --oneline，查看简洁的提交记录

回退
git reset --soft 版本id，回退某个版本，并且保留工作区和暂存区的所有修改内容，可以合并多次提交为一次提交

git reset --hard 版本id，回退某个版本，并且丢弃工作区和暂存区的所有修改内容，谨慎使用，会删除工作区和暂存区的所有修改

git reset --mixed 版本id，回退某个版本，并且保留工作区的内容，而丢弃暂存区的所有修改内容，和soft类似，只是需要重新add一次

git reflog，回溯之前所有的git操作。如果误操作了，可以使用这个命令，然后配合reset --hard回到某个版本

差异
git diff，查看工作区和暂存区的差异

git diff head/版本id，查看工作区和版本库之间的差异

git diff --cached，查看暂存区和版本库之间的差异

git diff 版本id1 版本号2，比较两个版本之间的差异内容

git diff 分支id1 分支号2，比较两个分支之间的差异内容

git diff head~/head^ head，比较当前版本和上一个版本之间的差异内容

git diff head~2 head，比较当前版本和之前的2个版本之间的差异内容

注：如果在命令后加上具体的文件名，只是查看具体的文件差异，例如git diff head~2 head file1.txt

删除文件
rm file1.txt，删除本地文件

git restore file1.txt，从暂存区恢复文件

git rm file1.txt，同时从工作区、暂存区、版本库中都删除文件

git rm --cache file1.txt，把文件从在暂存区删除，保留工作区

git rm -r *，递归删除某个目录下的所有目录和文件

.gitignore文件
忽略不需要添加到仓库的文件，例如：

1.系统或软件自动生产的文件

2.编译产生的中间文件和结果文件

3.运行时生产的日志文件、缓存文件、临时文件

4.涉及身份、密码、口令、密钥等敏感信息文件

添加忽略文件的规则：

file1.txt，忽略指定文件

*.txt，忽略所有txt的文件

temp/，忽略文件夹及里面的所有内容，注意要以"/"结尾


一些示例
远程仓库
创建ssh：ssh-keygen -t rsa -b 4096

私钥文件：id_rsa

公钥文件：id_rsa.pub

克隆仓库：git clone repo-address

git pull，从远程仓库同步代码到本地仓库

git push，从本地仓库同步代码到远程仓库

添加远程仓库的步骤：

1.git remote add origin repo-address：关联本地仓库和远程仓库

2.git push -u <远程仓库名> <分支名>

分支
git branch，查看仓库的所有分支

git branch <分支名>，创建新的分支

git checkout <分支名>，切换分支

git switch <分支名>，切换分支，建议使用这个

git merge <分支名>，合并分支到目标分支（当前所处的分支）

git log --graph --oneline，查看分支图

git branch -d <分支名>，删除已经合并的分支

git branch -D <分支名>，删除分支，无论是否已经被合并

git rebase <分支名>，变基合并吗，原理示例图如下：




Rebase合并
