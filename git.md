[原生笔记](https://mp.weixin.qq.com/s/Bf7uVhGiu47uOELjmC5uXQ)

[精简笔记](https://www.bilibili.com/video/BV1FE411P7B3)

## 前言
提示：这里可以添加本文要记录的大概内容：
例如：随着人工智能的不断发展，机器学习这门技术也越来越重要，很多人都开启了学习机器学习，本文就介绍了机器学习的基础内容。

## 一、git的安装和环境配置
官网：https://git-scm.com/
官网太慢，淘宝镜像下载：https://registry.npmmirror.com/binary.html?path=git-for-windows/

## 二、启动git
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudyaaade58a-80f4-48f5-b992-c11186eb40c0.png)
Git Bash：Unix与Linux风格的命令行，使用最多，推荐最多。
Git CMD：Windows风格的命令行。
Git GUI：图形界面的Git，不建议初学者使用，尽量先熟悉常用命令。

## 三、git环境配置
### 1.查看git所有配置
```
git config -l
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudy150f8e67-0e4a-4dec-8ccc-d893202e6620.png)
文件位置所在：
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudy37496e90-c105-432e-96d2-23289bc83c55.png)
### 2.查看git系统配置
```
git config --system -l
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudy5e48aae8-1d5c-43b8-9375-37960ab6592e.png)
### 3.查看用户自己配置的信息
```
git config --global --list
```
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudy4b1a3afb-c5fe-4ab6-912d-dd4db4d87ced.png)
文件位置所在：
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudyc82ee0c5-0680-427b-a2dc-a8e960a2244b.png)
### 4.设置用户名与邮箱（安装好git后必须要设置的一步）
```
git config --global user.name &quot;sywl&quot;
git config --global user.email xxx@qq.com
```

## 四、git基本理论
### 1.工作区域
Git本地有三个工作区域：工作目录（Working Directory）、暂存区（Stage/lndex）、资源库（Repository或Git Directory）。
如果在加上远程的git仓库（Remote Directory）就可以分为四个工作区域。
文件在这四个区域之间的转换关系如下：
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudyfb3ebf72-ba68-4156-ad6b-9e8e188db116.png)
- Workspace：工作区，就是你平时存放项目代码的地方。
- Index/Stage：暂存区，用于临时存放你的改动，事实上它只是一个文件，保存即将提交到文件列表信息。
- Repository：仓库区（或本地仓库），就是安全存放数据的位置，这里面有你提交到所有版本的数据。其中HEAD指向最新放入仓库的版本
- Remote：远程仓库，托管代码的服务器，可以简单的认为是你项目组中的一台电脑用于远程数据交换。

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudy3edf997b-b1fe-4740-8b02-5878e55a9395.png)

## 五、项目搭建
创建本地仓库的方法有两种：
### 1.一种是创建全新的仓库
1.创建全新的仓库，需要用GIT管理的项目的根目录执行：
```
#在当前目录新建一个Git代码库
$ git init
```
2.执行后可以看到，仅仅在项目目录多出了一个git目录，关于版本等的所有信息都在这个目录里面。

### 2.另一种是克隆远程仓库。
```
git clone [url]
```

## 六、git文件操作
### 1.文件的四种状态
版本控制就是对文件的版本控制，要对文件进行修改、提交等操作，首先要知道文件当前在什么状态，不然可能会提交了现在还不想提交的文件，或者要提交的文件没提交上。
- Untracked：未跟踪，此文件在文件夹中，但并没有加入到git库，不参与版本控制。通过冒git add状态变为【staged】
- Unmodify：文件已经入库，未修改，即版本库中的文件快照内容与文件夹中完全一致，这种类型的文件有两种去处，如果它被修改，而变为【Modified】。
如果使用git rm 移出版本库，则成为【untracked】文件。
- Modified：文件已修改，仅仅是修改，并没有进行其他的操作。这个文件也有两个去处，通过git add可进入暂存【staged】状态，使用git checkout则丢弃修改过，返回到【unmodify】状态，这个git checkout即从库中取出文件，覆盖当前修改。
- Staged：暂存状态。执行git commit则将修改同步到库中，这时库中的文件和本地文件又变为一致，文件为【unmodify】状态.
执行git reset HEAD filename取消暂存，文件状态为【Modified】。

### 2.查看文件状态
```
# 查看指定文件状态
git status [filename]

# 查看所有文件状态
git status

# 添加所有文件到暂存区
git add .

# 提交暂存区的内容到本地仓库，-m后面可以跟提交信息
git commit -m &quot;提交的信息&quot;
```

### 3.忽略文件
有些时候我们不想把某些文件纳入版本控制中，比如数据库文件，临时文件，设计文件等。
在主目录下建立&quot;.gitignore&quot;文件，此文件有如下规则：
1. 忽略文件中的空行或以井号（#）开始的行将会被忽略。
2. 可以使用Linux通配符。例如：星号（*）代表任意多个字符，问号（？）代表一个字符，方括号（[abc]）代表可选字符范围，大括号（{string1，string2.…}）代表可选的字符串等。
3. 如果名称的最前面有一个感叹号（！），表示例外规则，将不被忽略。
4. 如果名称的最前面是一个路径分隔符（/），表示要忽略的文件在此目录下，而子目录中的文件不忽略。
5. 如果名称的最后面是一个路径分隔符（/），表示要忽略的是此目录下该名称的子目录，而非文件（默认文件或目录都忽略）。

![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudycbbe8191-8999-48a7-8f8b-0ec282f4eb87.png)

## 七、码云使用
设置本机绑定SSH公钥，实现免密码登录！（免密码登录，这一步挺重要的，码云是远程仓库，我们是平时工作在本地仓库！）
![](https://kuangstudy.oss-cn-beijing.aliyuncs.com/bbs/2022/02/08/kuangstudy73046525-c424-4635-bc58-1ce175a0af7e.png)
设置教程：https://www.bilibili.com/video/BV1FE411P7B3?p=11

## 八、IDEA集成git
教程：https://www.bilibili.com/video/BV1FE411P7B3?p=12

## 九、git分支
分支在GIT中相对较难，分支就是科幻电影里面的平行宇宙，如果两个平行宇宙互不干扰，那对现在的你也没啥影响。
不过，在某个时间点，两个平行宇审合并了，我们就需要外理一此问题了！
```
# 列出所有本地分支
git branch
# 列出所有远程分支
git branch -r
# 新建一个分支，但依然停留在当前分支
git branch [branch-name]
# 新建一个分支，并切换到该分支
git checkout -b [branch-name]
# 合并指定分支到当前分支
git merge [branch-name]
# 删除分支
git branch -d [branch-name]
# 删除远程分支
git push origin --delete [branch-name]
git branch -dr [remote/branch]
```
多个分支如果并行执行，就会导致我们代码不冲突，也就是同时存在多个版本！

- 如果同一个文件在合并分支时都被修改了则会引起冲突：解决的办法是我们可以修改冲突文件后重新提交！选择要保留他的代码还是你的代码！
- master主分支应该非常稳定，用来发布新版本，一般情况下不允许在上面工作，工作一般情况下在新建的dev分支上工作，工作完后，比如要发布，或者说dev分支代码稳定后可以合并到主分支master上来。


## 总结
