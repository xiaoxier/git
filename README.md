# git

**「常用命令」**
```
git init
git config --global user.name "xiaoxier" //设置全局name  --global去掉 仅设置当前项目下
git config --global user.email "25@qq.com"//设置全局email 
git clone -b <分支名> xx.git  //从指定分支clone
git add .
git pull   //将与本地当前分支同名的远程分支 拉取并merge到本地当前分支上(需先关联远程分支)
git pull origin <远程分支名> //将远程指定分支拉取到本地当前分支上
git pull origin <远程分支名> :<本地分支名> //将远程指定分支 拉取到 本地指定分支上
git pull = git fetch + git merge
git fetch //从远程获取最新版本到本地 不会自动merge
git commit //vim编辑正文 自动生成标题 esc退出编辑 :wq保存
git commit -m'tag 日志' //不推荐使用 日志只包含标题
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
git merge --no-ff //合并时禁用fast forward模式 该模式合并时不保留原分支信息 直接并入merge后分支
git reset <分支名>
git reset --hard HEAD //回退到当前最新提交
git reset --hard HEAD^ //回退到上版本 （回退操作去掉暂存区记录 hard会连同本地工作区去掉记录 vscode工具会自动携带回退前不要的内容上去，内容会含在commit记录里面）
git reset --hard HEAD-n //回退到上n次提交
git reset --hard commitId //回退到指定commId 回退前提交记录不可见 可以重返未来版本 reflog有记录
git reset --hard origin/B //用B的代码完全替换当前分支的代码 需要提交到线上 就git push -f
git revert -n commitId //去掉指定commitId提交 生成新版本附带新commitId信息 保留历史记录 同一文件撤退指定提交需手动删除提交内容
git revert -n commitIdA..commitIdB //去掉A-B之间所有的commitId 按照提交先后 先A后B
git restore <文件名> //删除未存入暂存区的本地内容 扔掉
git stash //暂存  删除未存入暂存区的本地内容 并且存入缓存
git stash save "message" //添加存储备注
git stash drop //删除暂存记录
git stash pop //应用最近一次暂存的修改，并删除暂存的记录
git stash apply stash@{1} //应用暂存列表的进度key
git stash list //查看存储
git stash clear //清空stash列表
git rebase <branch> //合并多个commit为一个完整的commit
git rebase --continue //rebase过程中修复冲突后执行此命令 修复完冲突只需要git add 直接运行此命令提交
git rebase --abort //终止rebase操作 回到rebase前代码
git cherry-pick feature //将feature分支的最近一次提交，转移到当前分支
git cherry-pick <HashA> <HashB> //支持一次转移多个提交
git cherry-pick A..B //A早于B才会成功 转移A到B 不包含A的所有提交
git cherry-pick A^..B //包含A的 转移A到B的所有提交
git status //仅记录commit日志
git reflog //记录所有操作（历史提交及被回退的提交） 运行分支及commit日志
git branch -a //本地分支为本地分支名 远程分支为<远程仓库名>/分支名
git branch -D <分支名> //删除本地分支
git push origin -d <分支名> //删除远程分支
git diff
git diff <branch1> <branch2> //分支间比较
git diff SHA1 SHA2 //比较两个历史版本之间的差异
git diff HEAD^ HEAD //比较上次与上上次差异

git log //查看commit历史
git log --pretty=oneline //仅查看commit id
git config --list 
git remote -v //查看详细
git remote //查看不详细
git checkout <文件名> //更新文件
git checkout <branch>  path //当前分支某path目录/文件替换为其他分支的文件 切换到本地没有的分支时 先Git pull更新 本地会自动创建远程分支并关联
git config user.name //查看作者
git config user.email
git config --global user.name "hanpanpan"//设置作者
git config --global user.email "2380272325@qq.com"
git config --global alias.co.checkout //checkout简写co


$ git tag v1.0 //创建tag
$ git tag v1.0 <commitId> //指定commitId打tag
$ git tag -a <tagname> -m "blablabla..." //增加tagname 注释blablab
$ git tag //查看所有标签
$ git tag -l   ' v1.0.*' //查看某版本tag
$ git show v1.0 //查看tag信息
$ git checkout [tagName/branchName] //切换到某tag
$ git tag -d <tagname>  //删除本地tag
$ git push origin v1.0.0 //推送指定tagv1.0.0到远程
$ git push origin --tags //推送所有tag到远程 （tags[所有]）
$ git push origin --delete <tagname>  //删除远程删标签
$ git push origin :refs/tags/<tagname>//删除线上tag
$ git pull origin --tags //更新到本地

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

sublime快捷键
选择类
Ctrl+D ：选中光标所占的文本，继续操作则会选中下一个相同的文本。
Alt+F3：选中文本按下快捷键，即可一次性选择全部的相同文本进行同时编辑。举个栗子：快速选中并更改所有相同的变量名、函数名等。
Ctrl+L：选中整行，继续操作则继续选择下一行，效果和 Shift+↓ 效果一样。
Ctrl+Shift+L ：先选中多行，再按下快捷键，会在每行行尾插入光标，即可同时编辑这些行。
Ctrl+Shift+M：选择括号内的内容（继续选择父括号）。举个栗子：快速选中删除函数中的代码，重写函数体代码或重写括号内里的内容。
Ctrl+M：光标移动至括号内结束或开始的位置。
Ctrl+Enter：在下一行插入新行。举个例子：即使光标不在行尾，也能快速向下插入一行。
Ctrl+Shift+Enter： 在上一行插入新行。举个栗子：即使光标不在行首，也能快速向上插入一行。
Ctrl+Shift+[ ：选中代码，按下快捷键，折叠代码。
Ctrl+Shift+] ：选中代码，按下快捷键，展开代码。
Ctrl+K+0 ：展开所有折叠代码。
Ctrl+← ：向左单位性地移动光标，快速移动光标。
Ctrl+→ ：向右单位性地移动光标，快速移动光标。
shift+↑ ：向上选中多行。
shift+↓ ：向下选中多行。
Shift+← ：向左选中文本。
Shift+→： 向右选中文本。
Ctrl+Shift+←：向左单位性地选中文本。
Ctrl+Shift+→：向右单位性地选中文本。
Ctrl+Shift+↑：将光标所在行和上一行代码互换（将光标所在行插入到上一行之前）。
Ctrl+Shift+↓：将光标所在行和下一行代码互换（将光标所在行插入到下一行之后）。
Ctrl+Alt+↑：向上添加多行光标，可同时编辑多行。
Ctrl+Alt+↓：向下添加多行光标，可同时编辑多行。
搜索类
Ctrl+J：合并选中的多行代码为一行。举个栗子：将多行格式的CSS属性合并为一行。
Ctrl+Shift+D：复制光标所在整行，插入到下一行。
Tab：向右缩进。
Shift+Tab：向左缩进。
Ctrl+K+K：从光标处开始删除代码至行尾。
Ctrl+Shift+K：删除整行。
Ctrl+/：注释单行。
Ctrl+Shift+/ ：注释多行。
Ctrl+K+U：转换大写。
Ctrl+K+L：转换小写。
Ctrl+Z：撤销。
Ctrl+Y：恢复撤销。
Ctrl+U：软撤销，感觉和 Gtrl+Z 一样。
Ctrl+F2：设置书签
Ctrl+T：左右字母互换。
F6： 单词检测拼写
--------------------------------------------------------------------------------
显示类
Ctrl+Tab：按文件浏览过的顺序，切换当前窗口的标签页。
Ctrl+PageDown：向左切换当前窗口的标签页。
Ctrl+PageUp： 向右切换当前窗口的标签页。
Alt+Shift+1： 窗口分屏，恢复默认1屏（非小键盘的数字）
Alt+Shift+2： 左右分屏-2列
Alt+Shift+3： 左右分屏-3列
Alt+Shift+4： 左右分屏-4列
Alt+Shift+5： 等分4屏
Alt+Shift+8： 垂直分屏-2屏
Alt+Shift+9： 垂直分屏-3屏
Ctrl+K+B： 开启/关闭侧边栏。
F11： 全屏模式
Shift+F11：免打扰模式
 
```
