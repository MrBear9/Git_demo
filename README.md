可以参考这篇CSDN：[Git（分布式版本控制工具）_hr是啥意思-CSDN博客](https://blog.csdn.net/a18307096730/article/details/124586216?spm=1001.2014.3001.5502)



~~~
git init
git add   ->to 暂存区
git commit -m “别名”    ->to 本地仓库

git log      ---自己设置的有 git-log
git reset --hard  commitID    ----就是别名对应的标识码，用滚轮点一下即可
git reflog   -----查看删除的操作，可以回滚到不小心删掉的那次


~~~

命令如下：

1. clone（克隆）: 从远程仓库中克隆代码到本地仓库
2. checkout （检出）:从本地仓库中检出一个仓库分支然后进行修订
3. add（添加）: 在提交前先将代码提交到暂存区
4. commit（提交）: 提交到本地仓库。本地仓库中保存修改的各个历史版本
5. fetch (抓取) ： 从远程库，抓取到本地仓库，不进行任何的合并动作，一般操作比较少。
6. pull (拉取) ： 从远程库拉到本地库，自动进行合并(merge)，然后放到到工作区，相当于**fetch+merge**
7. push（推送） : 修改完成后，需要和团队成员共享代码时，将代码推送到远程仓库

# Git安装与常用命令

本教程里的git命令例子都是在Git Bash中演示的，会用到一些基本的linux命令，在此为大家提前列举：

- ls/ll 查看当前目录 ll是查看当前文件夹下的所有文件，包括隐藏文件
- cat 查看文件内容
- **touch 创建文件**
- vi vi编辑器（使用vi编辑器是为了方便展示效果，学员可以记事本、editPlus、notPad++等其它编辑器）



## 配置SSH公钥

- 生成SSH公钥
  - ssh-keygen -t rsa
  - 不断回车
    - 如果公钥已经存在，则自动覆盖
- Gitee设置账户共公钥
  - 获取公钥
    - cat ~/.ssh/id_rsa.pub
- 验证是否配置成功
  - ssh -T git@gitee.com
  - ssh -T git@github.com



## 添加远程仓库

**此操作是先初始化本地库，然后与已创建的远程库进行对接**。

我们要将本地仓库和远程仓库连接起来，一般一个本地仓库对应一个远程仓库远侧，远程仓库默认名为origin

- 命令： git remote add <远端名称> <仓库路径SSH>
  - 远端名称，默认是origin，取决于远端服务器设置
  - 仓库路径，从远端服务器获取此SSH

## 查看远程仓库

- 命令：git remote
- 命令：git remote -v

## 推送到远程仓库

- 命令：git push [-f] [–set-upstream] [远端名称 [本地分支名][:远端分支名] ]

  - 如果远程分支名和本地分支名称相同，则可以只写本地分支

     本来是：git push origin master ：master 表示将本地仓库的master分支提交到远程仓库的master分支

    - git push origin master 这里表示将本地仓库当前master分支的内容推到远程仓库上面去

  - -f 表示强制覆盖

  - –set-upstream 推送到远端的同时并且建立起和远端分支的关联关系。

    - git push --set-upstream origin master

  - 如果**当前分支已经和远端分支关联**，则可以省略分支名和远端名。

    * git push 将master分支推送到已关联的远端分支。

  - [-f] 表示强制覆盖远程仓库的内容