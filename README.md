# git


**「常用命令」**
```
git init
git config --global user.name "xiaoxier"
git config --global user.email "25@qq.com"
git clone -b <分支名> xx.git  //从指定分支clone
git add .
git pull   //将与本地当前分支同名的远程分支 拉取到 本地当前分支上(需先关联远程分支)
git pull origin <远程分支名> //将远程指定分支拉取到本地当前分支上
git pull origin <远程分支名> :<本地分支名> //将远程指定分支 拉取到 本地指定分支上
git commit -m'tag 日志' 
git push 
git push --set-upstream origin <本地分支名> //将本地分支与远程同名分支相关联
git push origin <指定的分支名>  //将本地代码推送到远程指定分支
git push --force 
git push -u orgin/<remote 分支名> //远程有分支 本地已建立并创建分支
git push origin local_branch:remote_branch 远程无分支 本地已建立并切换分支
git push origin --delete <remote 分支名> //删除远程分支
git checkout -b <分支名> //新建分支并切换到新建分支
git checkout -b <分支名> origin/<remote分支名> //在本地创建和远程分支对应的分支 （基于远程分支创建新本地分支）
git merge <分支名>
git reset <分支名>
git status
git branch
git branch -d <分支名> //删除本地分支
git diff
git log
git config --list 
git remote -v
```

# 终端命令

```
Desktop   桌面
ls              展开目录
cd ..          退一步
cd             进一步       
mkdir      创建n个文件夹
touch      创建n个文件
rm           删除n个文件
rm -rf      删除 n个文件夹、文件
pwd        查看当前文件绝对路径
ifconfig   查看ip
```