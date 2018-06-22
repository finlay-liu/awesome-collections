

# 安装Git #

在大多数*nix系统（Linux、OS X）上，Git已经被安装了。你通过发送下面的命令，可以通过Git自身，把它更新到最新的的开发版本（不推荐）。

    git clone https://github.com/git/git

# 设置Git #

在我们能用Git工作之前，我们需要做个一次性的配置。为了Git能跟踪到谁做了修改，我们需要设置你的用户名。

    git config --global user.name "your_username"
	git config --global user.email your_email@domain.com

# 创建一个本地代码库 #

我们首先需要告诉Git这个文件夹是我们需要跟踪的项目。所以我们发送这个命令来初始化一个新的本地Git代码库：

	git init

# 加载（Stage）文件 #

我们现在需要命令Git我们需要加载（stage）所有项目文件。发送：

	git add .

最后的“.”符号的意思是“所有文件、文件夹和子文件夹”。假如我们只想要把特定文件添加到源代码控制中去，我们可以指定它们：
	
	git add my_file, my_other_file

# 提交文件 #

现在，我们想要提交已加载（staged）的文件。阅读“添加一个时间点，在这里你的文件处在一个可还原的状态”。我们提交我们的文件时，总是附带着有意义的注释，描述了它们现在的状态。我一直用“initial commit”来作为第一个提交的注释。

	git commit -m "initial commit"

就这样。现在你随时都可以回滚到这个提交状态。如果你有需要检查你现在的已加载（staged）和未加载（unstaged）文件的状态、提交等，你可以询问git的状态：

	git status

# 创建分支 #

建立分支是你创建代码的独立版本的动作，独立于你的主干分支。默认地，每次你提交到Git的文件都会被储存到“master（主干）”分支。
现在我们来说说，你想要向项目里添加一个功能，但你想要能够回滚到现在版本，以防出现差错，或者你决定要放弃这个功能。这就是你创建分支的时候了。创建并同时切换到你新建的分支，发送：

	git checkout -b new_feature

或者，你可以先创建一个分支然后手动切换，就像这样：
	
	git branch new_featuregit checkout new_feature

要看你现在项目下所有的分支，发送这个：

	git branch

现在你可以在你的项目上无所顾忌地做任何你想做的：任何时候，你都可以回到你创建分支前的状态。注意，你同时可以有多个分支，甚至可以从一个分支上再创建一个分支。

# 合并分支 #

当你对你的新功能满意了的时候，你想要把它加到主干分支上。当你在你的新功能分支上时，你首先需要加载（stage）并且提交你的文件：

	git add .git commit -m "adds my new feature"

然后你移到你的主干分支：

	git checkout master

像这样合并：

	git merge new_feature

此时，你的主干分支和你的新功能分支会变成一样的了。

# 丢弃分支 #

相反，如果你打算丢弃你在分支里做的修改，你首先需要加载（stage）你的文件并且在分支里提交：

	git add .git commit -m "feature to be discarded"

然后，你移到主干分支：

	git checkout master

现在，你的代码处于你创建分支之前的状态了。

# 删除一个分支 #

如果你要把你的分支合并到主干分支，从主干（master）分支上发送：

	git branch -d new_feature

假如修改已经合并了，它只会删除分支。假如分支没有合并，你会得到一个错误信息。删除一个未合并的分支（通常你不想保留的修改），你需要发送一样的命令附带一个大写D。意思是“强制删除分支，无论如何我不想要它了。”：

	git branch -D new_feature

# 推送到远程代码库 #

在第一次你想推送一个本地代码库到远程代码库时，你需要把它添加到你的项目配置里。像这样做：

	git remote add origin https://your_username@bitbucket.org/your_username/name_of_remote_repository.git

# 取得远程代码库的一份本地拷贝 #

如果你还没有一份远程代码库的本地版本（例如，如果你在另一台机器上开始工作，这台机器上还没有用过这个项目），你首先需要拷贝（clone）它。去到你的代码库想要拷贝到的文件夹下，并发送：

	git clone https://your_username@bitbucket.org/your_username/name_of_remote_repository.git

另一方面，如果你已经在本地的项目上工作了，只是想从远程代码库上取得它最新的版本，移动到项目的根目录下，并发送：

	git pull origin master

# 别名 #

Git允许你为你常用的命令创建快捷方式（别名）。例如，如果你不想每次都输入git commit -m “some comment”，而是输入git c “some comment”，你可以向你的git全局配置里添加一个别名来实现，像这样：

	git config --global alias.c 'commit -m'

这是我使用的别名列表：

	git config --global alias.c 'commit -m'
	git config --global alias.co 'checkout'
	git config --global alias.cob 'checkout -b'
	git config --global alias.br 'branch'
	git config --global alias.m 'merge'
	git config --global alias.a 'add .'
	git config --global alias.s 'status'
	git config --global alias.dbr 'branch -d'
  
> 文章来源：[http://blog.jobbole.com/53573/](http://blog.jobbole.com/53573/)  #
