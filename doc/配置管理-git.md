# GIT

### 安装及配置

#### 1. 生成SSH密钥

在`git bash`中输入 ，并根据提示填写信息

```
 ssh-keygen -t rsa -C "youremail@example.com"
```

在用户目录下找到`ssh`文件夹，里面有`id_rsa`和`id_rsa.pub` 两个文件，这两个就是SSH Key的秘钥对，`id_rsa`是私钥，`id_rsa.pub`是公钥。 

#### 2. 添加至GitHub SSH配置

在自己的GitHub设置中添加一个SSH key，复制本地公钥并粘贴，之后就有权限对GitHub仓库读写的权限了。



### 创建项目

#### 1. 创建项目repository 

在自己的GitHub上创建源并且初始化

#### 2. 克隆至本地

在`git bash`中输入

```
git clone git@github.com:markrujun/BLOG.git
```

因为上面已经添加了本地的SSH密钥，所以使用SSH地址直接克隆项目，如是克隆别人的项目来开发，请先将项目`fork`到自己的git仓库，再用自己的SSH地址。



### 创建分支

在多人开发时，每个人在自己的`branch`（分支）上开发。

在`git bash`中输入（`xxx`代表自己的分支名，`-b`代表新建一个分支）

```
git checkout -b xxx
```

当在自己的`xxx`分支完成操作需要提交时，

```
git add .
git commit
git push
```

如果远程分支尚未创建，`push`会报错

```
fatal: The current branch xxx has no upstream branch.
To push the current branch and set the remote as upstream, use
    git push --set-upstream origin xxx
```

之后执行

``` 
git push --set-upstream origin xxx
```

创建远程`xxx`分支，当然，创建远超分支需要管理master的权限。



### 合并分支

如果需要将B分支，合并到A分支上。

切换到A分支，后`merge`

``` 
git checkout A
git merge B
```

当然，文件冲突或版本不同步会导致`merge`失败。