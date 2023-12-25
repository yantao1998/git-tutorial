# 这是一个GitHub使用教程

GitHub使用SSH的公开密钥认证进行已有仓库的连接，使用GitHub时需要创建SSH key

本地生成公私密钥，然后将公开密钥添加到远程的Github中，后续就可以通过本地的私钥进行验证

本地库生成公私钥密令，创建SSH Key命令

~~~b
ssh-keygen -t rsa -C "email"
~~~

然后按回车，可以设定密码。

最终生成的id_rsa文件是私有密钥，id_rsa.pub是公开密钥。

在Github添加公开的密钥.

## git

git是用于版本控制的的仓库，不仅可以进行代码文件的保存，还可以进行其他各中计算机文件的保存和控制。git可以记录代码的修改情况、各个提交记录、版本退回，可以方便的进行多人开发任务。

git是一种分布式的管理仓库，每个计算机设备都可以进行自己本地的版本控制管理称为本地库，GitHub是将库保存在远程服务器可以实现协同开发。

fix-B

## git常见命令

- 初始化仓库：在本地通过GitBash打开文件，运行该命令进行本地库的初始化

  ~~~b
  git init
  ~~~

  初始化成功的目录中会生成.git目录，存储着管理当前目录内容所需的仓库数据。称为附属于该仓库的工作树，文档的编辑等操作在工作树中进行，然后记录到仓库中，以管理文件的历史快照。

- 查看仓库的状态

~~~bash
git status
~~~

工作树和仓库在被操作的过程中，状态会不断发生变化，使用该命令查询当前状态。

- 向暂存区中添加文件

  ~~~ba
  git add 文件名/.
  ~~~

  如果对当前库中文件做了修改，并不会被Git仓库管理，需要执行该命令让文件称为Git仓库的管理对象，将其加入暂存区（提交之前的一个临时的区域)

- 保存仓库的历史记录

  ~~~b
  git commit -m "提交的版本说明"
  ~~~

  将暂存区的文件保存到仓库的历史记录中形成一个版本。

- 查看提交的日志

  ~~~bash
  git log
  ~~~

  查看仓库的提交记录。该命令后加上目录名便只会显示该目录下的日志，只能查看以当前状态为终点的历史日志

  查看当前仓库的所有操作日志

  ~~~bash
  git reflog
  ~~~

  

  ~~~bash
  git log --graph
  ~~~

  以图表形式查看分支

- 查看更改前后的差别

  ~~~bash
  git diff
  ~~~

  该命令可以查看工作树、暂存区、最新提交之间的差别。

  查看当前工作树与暂存区的差别

​     要查看与最新提交的差别，请执行以下命令。

~~~bash
git diff HEAD
~~~

​     HEAD 是指向当前分支中最新一次提交的指针。

**和分支相关的命令**

在多人协同开发时通常以master分支为中心，每个人创建自己的分支进行开发，然后合并到master分支。只要创建多个分支，就可以在不互相影响的情况下同时进行多个功能的开发。

- 显示所有分支

  ~~~bash
  git branch
  ~~~

  “*”（星号），表示这是我们当前所在的分支

- 创建新的分支

  ~~~bash
  git branch 分支名
  ~~~

- 切换分支

  ~~~bash
  git checkout 分支名
  ~~~

- 创建并切换分支

  ~~~bash
  git checkout -b 分支名
  ~~~

- 切换回上一个分支

  ~~~bash
  git checkout -
  ~~~

- 合并分支

  ~~~bash
  git merge --no-ff 分支名
  ~~~

  首先切换到主分支master然后合并指定分支

**更改提交的操作**

- 回溯到指定历史版本

  ~~~bash
  git reset --hard 哈希值
  ~~~

  需要提供提供目标时间点的哈希值，就可以完全恢复至该时间点的状态。

- 压缩历史,合并commit

  ~~~bash
  git rebase -i HEAD~2
  ~~~

  可以选定当前分支中包含HEAD（最新提交）在内的两个最新历史记录为对象进行编辑，将pick部分删除合并。

# 本地库和远程库的连接

- 如果本地库已经建立完毕，可以在远程库中建立同名库然后将二者连接起来

~~~bash
git remote add origin git@github.com:用户名/库名.git
~~~

远程库一般命名为origin

- 也可以通过克隆直接获取远程库

  ~~~bash
  git clone 粘贴
  ~~~

## push操作

推送至远程库

~~~bash
git push origin master
~~~

将master分支推送至远程库

-u参数可以在推送的同时，将 origin 仓库的 master 分 支设置为本地仓库当前分支的 upstream

也可以推送其他分支

~~~bash
git push origin 分支名
~~~

## pull操作

获取最新的远程仓库分支

~~~bash
git pull origin 分支名
~~~

