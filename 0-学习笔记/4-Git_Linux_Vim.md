# Git 提交 流程

## 放弃工作区修改、放弃index、放弃commit

* 取消暂存：git reset HEAD`<file>`...

- 未提交到index，需要丢弃修改：git checkout -- filename
- 已提交到index，需要丢弃修改：git reset HEAD filename
- 已commit，需要回退：

  - hard：当然是都变啦。git reset --hard，直接丢弃work space中内容
  - soft：log 回退到某个版本，暂存区（已经add）的都不变，但工作区（没add)
  - mixed：log 回退到某个版本，暂存区（已经add）变回指定版本的，但工作区（没add，即 untracked file + unstage file)不变
  - keep：HEAD回退，暂存区不变，工作区变化
  - 参考Git reset --soft/mixed/hard的作用：https://www.jianshu.com/p/cbd5cd504f14
  - https://blog.csdn.net/CAIDEFEIQI/article/details/106416594

## pull+append current=rebase

先把最新的 mater内容，合并到当前分支。再让当前分支的commit追加到 master更新过来的commit之后
git rebase BRANCH_NAME

## 合并多个commit, committ1+commit2=commit

// 3次提交，第一次f1f92b，第二次，第三次想合并到一起，变成1个，则：https://my.oschina.net/u/1000241/blog/1841373

// 参数修改：pick second, s threed.
git rebase -i f1f92b

# git temp 提交命令

如何看懂git graph图：https://segmentfault.com/q/1010000007376119

## 关联分支，让本地和远程的分支连接起来

从本地推送分支，使用git push origin branch-name，如果推送失败，先用git pull抓取远程的新提交；

在本地创建和远程分支对应的分支，本地和远程分支的名称最好一致

- git checkout -b branch-name origin/branch-name

建立本地分支和远程分支的关联

- git branch --set-upstream branch-name origin/branch-name；

## 删除分支

删除分支 本地 远程
git branch -d localBranchName    // delete branch locally
git push origin --delete remoteBranchName  // delete branch remotely

## 修改最近的commit, 但是又不提交

- git commit --amend "new commit"
- 修改最近的commit之倒数第二个：https://www.cnblogs.com/johnson108178/p/9044338.html

## 紧急情况，stash存储

- 暂存当前工作区，暂存区内容，去修改其他分支的bug：
  当你正在敲着键盘，埋头开发一个新功能时，突然有人跑过来跟你说，哎，兄弟，你之前开发的那个功能出现了一个bug，赶紧改一下，这时候你新分支功能才刚刚开了一个头，如果直接commit一次肯定是可以的，不过有更好的处理办法 git stash
- git stash 后会把你工作目录的改动清空，然后存储到另外一个地方。需要注意的是， git stash 会忽略那些没有被track的文件，这时候需要加上参数-u,即 git stash -u
- 当你把bug修复后，切回工作分支。然后：git stash pop

# 分支关联

git branch --set-upstream cur_branch origin/cur_branch
如果报错：fatal: Not a valid object name: 'origin/uas_1-0-1075_BRANCHd'，先执行
git checkout master
git pull

查看远程分支

- git branch -vv

git pull 和 git push总结：
git pull 后不加参数的时候，跟git push 一样，默认就是git pull origin 当前分支名。当然远程仓库没有跟本地当前分支名一样的分支的话，肯定会报错。本地master分支执行git pull的时候，其实就是git pull origin master。

## Git 最基础的命令

1、主干合并分支
进入分支，更新分支代码
（branch）git pull；
切换主干
（branch）git checkout master；
在主干上合并分支branch
（master）git merge branch --squash
提交合并后的代码
（master）git commit -m ‘合并备注’
将代码推送到远程仓库
（master）git push
2、分支合并主干
进入主干，更新主干代码
（master）git pull；
切换分支
（master）git checkout branch；
在分支上合并主干
（branch）git merge master --squash
提交合并后的代码
（branch）git commit -m ‘合并备注’
将代码推送到远程仓库
（branch）git push

# Linux

## 查看满足指定条件的行

方法1：
head -m filename | tail -1                    //查看filename文件的第m行（tail -1 是数字1）
e.g.   head -100 data.txt | tail -1          //查看data.txt文件的第100行

方法2：
nl filename | sed -n 'mp'                     //查看filename文件的第m行
e.g.   nl  data.txt | sed -n '100p'             //查看data.txt文件的第100行

// 递归、显示行号、查看
grep -rn "4101}" part-00009-ffd52e87-7d07-45b0-b0e8-89e73084039f.c000.csv| grep -rn "12302" | tail -1

// 将左边的，挂在到右边去
sudo ln -s /apsarapangu/disk11/sunyindong.syd /home/admin/sunyindong.syd


命令 ： chmod -R 755 tools_command/



## 移动隐藏文件：mv .[^.]* ..

1. 匹配隐藏文件用 .[^.]* 为什么不用 .*, .* 会匹配目录 . 和 ..
2. .[^.]* 的意思是：以.开头，加不是.的一个任意字符，再加其他任意字符

# VIM

删除全文：ggdG,

- 其中，gg为跳转到文件首行
- dG为删除光标所在行以及其下所有行的内容
- d为删除，G为跳转到文件末尾行；
