# git

**「常用命令」**
```
git init
git config --global user.name "xiaoxier" //设置全局name  --global去掉  仅设置当前项目下
git config --global user.email "25@qq.com"//设置全局email 
git clone -b <分支名> xx.git  //从指定分支clone
git add .
git pull   //将与本地当前分支同名的远程分支 拉取并merge到本地当前分支上(需先关联远程分支)
git pull origin <远程分支名> //将远程指定分支拉取到本地当前分支上
git pull origin <远程分支名> :<本地分支名> //将远程指定分支 拉取到 本地指定分支上
git fetch //从远程获取最新版本到本地 不会自动merge
git commit -m'tag 日志' 
git tag <tagname> // 打tag
git push 
git push --set-upstream origin <本地分支名> //将本地分支与远程同名分支相关联
git push origin <指定的分支名>  //将本地代码推送到远程指定分支
git push origin <tagname> //远端推送分支
git push --force 
git push -u orgin/<remote 分支名> //远程有分支 本地已建立并创建分支
git push origin local_branch:remote_branch 远程无分支 本地已建立并切换分支
git push origin --delete <remote 分支名> //删除远程分支
git checkout -b <分支名> //新建分支并切换到新建分支
git checkout -b <分支名> origin/<remote分支名> //在本地创建和远程分支对应的分支 （基于远程分支创建新本地分支）
git merge <分支名>
 git pull origin 指定分支
 git push //这两步操作相当于merge指定分支到本地操作
git reset <分支名>
git reset --hard HEAD^ //回退到上版本
git reset --hard commitId //回退到指定commId 回退前提交记录不可见
git revert //回退远程代码库 自动新建新的commit信息 覆盖上次修改 回滚前历史提交记录可见 
git stash //暂存
git stash save "message" //添加存储备注
git stash pop //应用最近一次暂存的修改，并删除暂存的记录
git stash apply stash@{1} //应用暂存列表的进度key
git stash list //查看存储
git stash clear //清空stash列表
git status
git branch
git branch -d <分支名> //删除本地分支
git diff
git log //查看commit历史
git log --pretty=oneline //仅查看commit id
git config --list 
git remote -v
git checkout <文件名> //更新文件
git checkout <branch>  path //当前分支某path目录/文件替换为其他分支的文件 切换到本地没有的分支时 先Git pull更新 本地会自动创建远程分支并关联
git config user.name //查看作者
git config user.email
git config --global user.name "hanpanpan"//设置作者
git config --global user.email "2380272325@qq.com"
git config --global alias.co.checkout //checkout简写co


$ git tag v1.0   //创建tag
$ git tag v1.0 <commitId> //指定commitId打tag
$ git tag -a <tagname> -m "blablabla..." //增加tagname 注释blablab
$ git tag //查看所有标签
$ git tag -l   ' v1.0.*' //查看某版本tag
$ git show v1.0 //查看tag信息
$ git checkout [tagName/branchName] //切换到某tag
$ git tag -d <tagname>  //删除本地tag
$ git push origin v1.0.0 //推送v1.0.0到远程
$ git push origin --tags //推送所有tag到远程 （tags[所有]）
$ git push origin --delete <tagname>  //远程删除
$ git push origin :refs/tags/<tagname>//删除线上tag

```


**.gitconfig 配置**
```
[alias]
st = status -sb
co = checkout
br = branch
mg = merge
ci = commit
ds = diff --staged
dt = difftool
mt = mergetool
last = log -1 HEAD
latest = for-each-ref --sort=-committerdate --format=\"%(committername)@%(refname:short) [%(committerdate:short)] %(contents)\"
ls = log --pretty=format:\"%C(yellow)%h %C(blue)%ad %C(red)%d %C(reset)%s %C(green)[%cn]\" --decorate --date=short
hist = log --pretty=format:\"%C(yellow)%h %C(red)%d %C(reset)%s %C(green)[%an] %C(blue)%ad\" --topo-order --graph --date=short
type = cat-file -t
dump = cat-file -p
lg = log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit

```

# shell

**「常用命令」**

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

```


# Chrome Devtools


**「常用操作」**


- Devtools模式下 (f12)  ctrl+shift+p 调出快捷栏

```
	?    查看所有命令
	...  打开文件
	:    前往文件
	@    前标识符
	!    运行脚本文件
	>    打开某菜单功能
	>     performance monitor  显示性能监视器及相关信息，例如CPU，JS堆大小和DOM节点。
	>     FPS选择第一项  实时监控性能
	>     screen 选择 Capture node screenhot  截图单个元素
```
- 选择特定DOM元素 右击选择Break on

```
	Break on->Subtree modifications: 子节点删除或添加时
	Break on->Attributes modifications: 属性修改时
	Break on->Node Removal: 节点删除时
```

- Blackbox Script 剔除多余脚本断点 source中选择文件 打开文件 右击 选择Blackbox Script


- Sources -> Event Listener Breakpoints

- Sources >; Overrides >; Enable local Overrides，选择本地文件夹  

```
	将本地文件夹映射到网络 工作区修改直接改动本地文件
```

- Chrome自身实现的jquery加强版  控制台内置指令

```
	 $('a').href;
	 $('[test-id="logo-img"]').src;
	 $('#movie_player').click();
	 $$('[name="type"]')  //全选择器
	 $x("//p[a]")//代码返回<p>包含<a>元素的所有元素
```
- getEventListeners($('.ant-btn'))   获取指定对象$('.ant-btn')的绑定事件


- 超强打印

```
	console.group()
	console.time()
	console.table()
	console.dir()

```

# sublime快捷键

```
shift+ctrl+1~6 调整透明度
cmd + p                      →   检索目标文件
cmd + shift +t               →   重新打开关闭的标签页
cmd + shift +p                   快速查找，更改设置
cmd + shift +f                   搜索整个ST项目下目录
cmd +  方向键                     实现文字行间跳转
cmd + ctrl +Up/Down              上下移动当前行
shift + 方向                     移动并选中
ctrl + m                         跳转到对应括号
ctrl + shift +m                  选中括号内容
cmd + m                          最小化到dock栏
ctrl + /                         注释切换
ctrl+shift+k                     删除整行
ctrl + kk                        从光标处删除至行尾
Shift+F11                        免打扰模式
Command + Ctrl + G               选中相同文本
cmd + d          				 选中下一次相同文本
cmd+d /cmd+l       			     选中一个/一行
cmd + t   						 列出所有文件   
cmd+shift+] 					 下一文件
Command + R    					 列出选择器
 
```
