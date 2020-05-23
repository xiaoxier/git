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
 git pull origin 指定分支
 git push //这两步操作相当于merge指定分支到本地操作
git reset <分支名>
git reset --hard HEAD^ //回退到上版本
git reset --hard commitId //回退到指定commId
git status
git branch
git branch -d <分支名> //删除本地分支
git diff
git log //查看commit历史
git log --pretty=oneline //仅查看commit id
git config --list 
git remote -v
git checkout <文件名> //更新文件
git config user.name //查看作者
git config user.email
git config --global user.name "hanpanpan"//设置作者
git config --global user.email "2380272325@qq.com"


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
