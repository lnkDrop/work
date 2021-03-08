GitHub和Git的初步使用
=======
<font size="3">

# 一、注册GitHub
* 1进入GitHub，网址：https://github.com/
* 2点击右上角Sign up进入注册界面
* 3依次输入用户名，邮箱，密码，验证码
* 4登录自己的邮箱验证邮箱，然后登录GitHub
* 5建议使用chrome浏览器，在网址连接右边点击翻译此页后自动翻译页面为中文
</font><br /> 

---

<font size="3">

# 二、配置git获取秘钥
* 1 下载安装git，网址：https://git-scm.com/downloads
* 2 配置git的邮箱和密码，两串代码如下：
* $ git config --global user.name "输入你的用户名"
* $ git config --global user.email "输入你的邮箱"
* 3 打开git，输入 $ssh-keygen -t rsa -C "your_email@youremail.com" 
后面的your_email@youremail.com是你在github上注册使用的邮箱。
* 4 输入后Git要求确认路径和密码，直接回车默认设置，它会显示秘钥图像代表keys已经生成了，我们需要这串秘钥来和GitHub上的远程仓库和本地仓库进行远程连接。
* 5 秘钥路径在C：\用户\你的用户名（默认是Administrator文件夹）\.ssh 这个文件夹，找到打开后会看到一个id_rsa.pub文件，右键记事本或其他编辑器打开，复制全部keys。
</font><br /> 

---

<font size="3">

# 三、GitHub添加SSH秘钥
* 1登录自己的GitHub账号。
* 2点击右上角自己的头像，打开"setting"。
* ![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/sttings.png)
* 
* 3左侧栏找到"SSH and GPS keys" 点击进入。
* ![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/SSH.png)
* 4右上角点击"New SSH key",
![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/newSSHkey.png)

会进入一个输入界面，Title随便取一个名字，最好是你当前使用的计算机名以便区分，然后将刚刚复制的keys粘贴到key框框中，点击Add SSH key。
* 5验证一下连接是否成功回到本机，打开Git Bash,输入命令
$ ssh -T git@github.com，第一次输入会显示continue？，输入yes继续，看到显示You've successfully authenticated, but GitHub does not provide shell access代表连接已经成功。
</font><br /> 

---
<font size="3">

# 四、Git编辑本地仓库和上传至GitHub远程仓库
* 1首先进入要进行操作的项目文件夹或者新建，在当前目录下右键Gitbash，也可以用cd命令进入
* 2初始化仓库，这一步很重要，如果没有初始化过的仓库将无法执行任何操作，检查是否已经初始化可以在当前文件夹查看有没有.git文件夹（注意是隐藏文件，需要在文件夹选项中勾选查看隐藏项目）如果没有就输入 $ git init
* 3添加你的项目文件，一般GitHub默认有一个README文件，即说明文件，把他看做一个文本文件，用来说明描述项目或有关说明。我们首先创建它，输入$ echo "#测试说明" >> README.md 
* 4用git add添加文件进入git版本库，在此之前先输入$ git status来查看文件变动，看见标红的README.md文件说明此文件有新改动但是没有上传保存。我们将它添加进去，输入$ git add README.md 添加文件，再提交备注信息，输入$ git commit -m "你的备注信息"
* 5至此我们完成了文件的改动，但它还保留在本地，我们需要把他们上传到远程仓库GitHub里面，首先在你的GitHub上新建项目库（点击右上角头像左边的＋号，选择New repository）,然后在Repository name里自己起一个你的远程仓库名，其他默认，点击创建。
* ![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/new.png)
* * ![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/xmname.png)
* 6在创建好的项目库中提示添加你的项目文件，我们的项目文件在本地，所以选择第一种，复制它的SSH
* ![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/copy.png)
* 7回到你的本地项目文件夹，绑定远程仓库，只需要在gitbash中输入$ git remote add origin "粘贴第6步复制的SSH地址"(右键paste)，然后敲回车。没有报错就接着输入 ```$ git push -u origin main``` 回车之后等待一段时间，可以看到文件上传成功，回到GitHub仓库下刷新看看，添加的文件有没有导入进来。如果能显示刚刚添加README文件就证明已经上传成功啦！
* ![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/test.png)
* 项目合并 ``` git pull --rebase origin main ```
</ font> <br />

---

<font size="3">

# 五、6个常用命令
* 1
	$ git init    -->初始化本地仓库（每个项目文件夹下只需要初始化一次即可）
* 2
	$ git status -->查看状态
* 3
	$ git add 文件名-->跟踪修改文件（更新文件）
* 4
	$ git commit -m "你的备注信息"-->提交所有更新过的文件
* 5
	$ git remote add origin github的SSH地址.git-->添加远程版本库
* 6
	$ git push -u origin master-->上传代码及快速合并
* 7常用命令表：
* ![图片的alt信息，可空)](https://raw.githubusercontent.com/lnkDrop/work/master/img/git.jpg)

</font><br /> 

---

<font size="3">

# 六、更新本地文件到github
* 1假如你本地文件做出修改，需要同步上传到github，只要使用第五条6个常用命令的几个代码。
* 2假设你已对文件夹做出修改，在此文件夹下右键打开gitbash并输入
	$ git status 
会看到修改过的文件已经标红，意思是文件做出修改但未提交
* 3接着输入
	$ git add "刚才做出修改的文件的文件名"
或者用
	$ git add .   --->跟踪所有修改过的文件
* 4提交修改，输入
	$ git commit -m "备注信息"
* 5上传修改文件到github，输入
	$ git push -u origin main

</font><br /> 

---


### 注：img文件夹中有部分git指令运行截图,报错的先看有没有初始化本地仓库，然后看顺序有没有错。

### 需要反复执行的命令有第五条中的2,3,4,6点，1,5点第一次执行过就可以了，注意顺序不能颠倒。

### README说明文件需要用到md编辑器，推荐下载Markdown编辑器进行编辑
