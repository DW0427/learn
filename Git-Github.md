# **1 日常作业要求** #

## **Git基础** ##

分布式版本管理控制系统（VSC）

### 基本工作流程 ###

​	工作目录 => 暂存区(add) => git仓库(commit)

### 使用 ###

**使用前配置**

- 命令行：`Git Bash Here`

  配置提交人姓名  `git config --global user.name 提交人姓名`

  配置提交人邮箱   `git config --global user.email 提交人邮箱`

  查看git配置信息   `git config --list`

- 配置文件

  C:\Users\xxx\ **.gitconfig**  在编辑器中修改并保存

  (xxx为当前使用的系统用户)

**提交步骤**

1. 初始化仓库  `git init`

2. 查看文件状态  `git status`

3. 追踪文件（工作目录 => 暂存区）  `git add 文件列表`

   将工作目录中的文件全部添加到暂存区  `git add .`

4. 向仓库中提交代码（暂存区 => git仓库）  `git commit -m 提交信息`

5. 查看提交记录  `git log`  (commit ID, Author, Date, message)

**撤销**

- 用暂存区中的文件覆盖工作目录中的文件（暂存区 -> 工作目录）  `git checkout 文件`
- 将文件从暂存区中删除  `git rm --cached 文件`
- 将git仓库中指定的更新记录恢复出来，并覆盖暂存区和工作目录（git仓库 -> 暂存区  `git rest --hard commitID`-



## 分支基础 ##

简单理解为分支是副本，了解`git push`命令中的分支名称用法

大作业中一般直接在master分支中进行操作

### 分支简分 ###

1. 主分支（master）
2. 开发分支（develop）
3. 功能分支（feature）

### 分支命令 ###

- 查看分支  `git branch`

- 创建分支  `git branch 分支名称`

- 切换分支  `git checkout 分支名称`

- 合并分支  `git merge 来源/开发分支` （在主分支上操作）

- 删除分支  `git branch -d 分支名称`  （`-D` 强制删除）

  分支被合并后才允许删除

### 暂时保存更改 ###

分支临时切换：暂时提取分支上所有的改动并存储，以便临时其他工作

- 存储临时改动  `git stash`

- 恢复改动  `git stash pop`

  （储存功能是独立于分支的，恢复改动时要确定好所在分支）



## **Github基础** ##

### 远程仓库命令 ###

1. `git push 远程仓库地址 分支名称`

2. `git push 远程仓库地址别名 分支名称`

3. `git push -u 远程仓库地址别名 分支名称`

   （`-u`记住推送地址及分支，下次推送只需要输入  `git push`  即可）

4. `git remote add 远程仓库地址别名 远程仓库地址`

### 拉取操作 ###

**克隆仓库**

克隆远程数据仓库到本地  `git clone 仓库地址`

**拉取最新版本**

拉取远程仓库中最新的版本  `git pull 远程仓库地址 分支名称`

### 其他文件 ###

**.gitignore**

在工作目录内创建git忽略清单文件（`.gitignore`）并将想忽略的文件夹名称及文件名写在里面

**readme.md**

记录详细说明



# **2 git规范** #

## git commit ##

可用工具`git-cz`

**格式**

```html
commit message格式
<type>(<scope>): <subject>
<!--空行-->    
<body>
<!--空行--> 
<footer>
```

三个部分：

- 标题行
- 主体
- 页脚

### **type：类型** ###

| 类型     | 描述                                                   |
| -------- | ------------------------------------------------------ |
| init     | 初始化                                                 |
| feat     | 增加新feature                                          |
| fix      | 修复BUG                                                |
| refactor | 代码重构，没有加入新功能或修复bug                      |
| docs     | 文档修改，如readme.md                                  |
| style    | 代码格式修改，如修改了空格、格式缩进等，不改变代码逻辑 |
| test     | 测试用例修改，如单元测试、集成测试等                   |
| build    | 构建项目                                               |
| perf     | 优化相关，如提升性能、体验                             |
| chore    | 其他修改，比如依赖管理                                 |
| revert   | 回滚到上一个版本                                       |
| merge    | 代码合并                                               |
| sync     | 同步主线或分支的BUG                                    |

### **scope：影响的范围** ###

范围标识，没有固定词，比如全局(global)，目录路径，对应功能名称

### **subject：概述** ###

不超过50个字符，结尾不加句号或其他标点符号

### **body：具体修改内容** ###

可以分为多行

### **footer：不兼容变动** ###

通常是 BREAKING CHANGE 或修复的 bug 的链接



## git 工作流 ##

为不同分支分配了明确的角色，并定义分支之间何时和如何进行**交互**

分别有历史分支、功能分支、发布分支和维护分支（热修复）

### 历史分支 ###

记录项目历史，需要长期维护

- `master分支` 记录了**正式发布**的历史 => 每次提交分配一个版本号

  ​	只允许 `release`分支和`hotfix`分支进行合并

- `develop分支` 作为**功能的集成**分支

  ​	`所有功能基于不稳定的develop`分支

### 功能分支 ###

从`develop`中拉出来的新分支，每个功能对应一个分支，使用`feature-*`进行命名标识

```git
假设开发a功能
git checkout -b feature-a develop
功能完成后合并回develop分支
git checkout develop
git merge --no-ff feature-a
git push
git branch -d feature-a
```

#`git checkout -b `创建并切换分支

#`--no-ff`不使用fast-forward方式合并，保留分支的commit历史 

​		快进式合并 https://blog.csdn.net/zombres/article/details/82179122

#`--squash`使用squash方式合并，把多次分支commit历史压缩为一次

### 发布分支 ###

当`develop`分支开发到需要发布时，从`develop`分支拉出一个发布分支，使用 `release-*`或 `release/*`进行命名标识

分支用于发布循环，只做BUG修复、文档生成等**面向发布**的任务，不再添加新功能

```git
git checkout -b release-0.1 develop
发布完成后合并到master分支
git checkout master
git merge --no-ff release-0.1
git push
打tag记录版本号
git tag -a 0.1 -m "release 0.1 publish" master
git push --tags
把修改合并到develop分支
git checkout develop
git merge --no-ff release-0.1
git push
git branch -d release-0.1

```

#`tag`是git版本库的一个标记，指向某个commit的指针 (master)

​		`git tag -a <tagName> -m "xxx..."`指定标签信息

​		`git checkout -b <branchName> <tagName>`检出标签

### 维护分支/热修复 ###

当线上版本出现bug时，从 `master`分支拉一个维护分支，用于快速给产品发布版本打补丁，使用 `hotfix`进行标识

**唯一**从 `master`分支拉出来的分支

```git
git checkout -b hotfix master
修复完成后马上合并回master和develop分支
git checkout master
git merge --no-ff hotfix 
git push
git checkout develop
git merge --no-ff hotfix 
git push
git branch -d hotfix
master用新版本号打tag
git tag -a 0.2 -m "release 0.2 publish" master
git push --tags
```





![img](https://user-gold-cdn.xitu.io/2017/11/7/0ca78a19f81e4ab1d0e6ed7892cc7422?imageslim)