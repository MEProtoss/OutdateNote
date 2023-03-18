# python 环境安装

## Anaconda

### **什么是Anaconda？**

**1. 简介**

Anaconda（[官方网站](https://link.zhihu.com/?target=https%3A//www.anaconda.com/download/%23macos)）就是可以便捷获取包且对包能够进行管理，同时对环境可以统一管理的发行版本。Anaconda包含了conda、Python在内的超过180个科学包及其依赖项。

**2. 特点**

Anaconda具有如下特点：

▪ 开源

▪ 安装过程简单

▪ 高性能使用Python和R语言

▪ 免费的社区支持

其特点的实现主要基于Anaconda拥有的：

▪ conda包

▪ 环境管理器

▪ 1,000+开源库

如果日常工作或学习并不必要使用1,000多个库，那么可以考虑安装Miniconda（[下载界面请戳](https://link.zhihu.com/?target=https%3A//conda.io/miniconda.html)），这里不过多介绍Miniconda的安装及使用。

**3. Anaconda、conda、pip、virtualenv的区别**

**① Anaconda**

Anaconda是一个包含180+的科学包及其依赖项的发行版本。其包含的科学包包括：conda, numpy, scipy, ipython notebook等。

**② conda**

conda是包及其依赖项和环境的管理工具。

▪ 适用语言：Python, R, Ruby, Lua, Scala, Java, JavaScript, C/C++, FORTRAN。

▪ 适用平台：Windows, macOS, Linux

▪ 用途：

① 快速安装、运行和升级包及其依赖项。

② 在计算机中便捷地创建、保存、加载和切换环境。

> 如果你需要的包要求不同版本的Python，你无需切换到不同的环境，因为conda同样是一个环境管理器。仅需要几条命令，你可以创建一个完全独立的环境来运行不同的Python版本，同时继续在你常规的环境中使用你常用的Python版本。——[Conda官方网站](https://link.zhihu.com/?target=https%3A//conda.io/docs/)

▪ conda为Python项目而创造，但可适用于上述的多种语言。

▪ conda包和环境管理器包含于Anaconda的所有版本当中。

**③ pip**

pip是用于安装和管理软件包的包管理器。

▪ pip编写语言：Python。

▪ Python中默认安装的版本：

① Python 2.7.9及后续版本：默认安装，命令为 ***pip\***

② Python 3.4及后续版本：默认安装，命令为 ***pip3\***

▪ pip名称的由来：pip采用的是**递归缩写**进行命名的。其名字被普遍认为来源于2处：

① “Pip installs Packages”（“pip安装包”）

② “Pip installs Python”（“pip安装Python”）

**④ virtualenv**

virtualenv是用于创建一个**独立的**Python环境的工具。

### 安装

``` bash
#下载 在Windows中下载会报错
wget https://repo.anaconda.com/archive/Anaconda3-2021.05-Linux-x86_64.sh 
#安装
bash Anaconda3-2021.05-Linux-x86_64.sh
#安装完成之后输入添加到路径的命令：
nvim ~/.bashrc
#添加
PATH=/home/user/anaconda3/bin:$PATH
#
source /etc/profile
#检查
python3
#出现以下类似结果则成功
$ python3                                                                              ──(Sat,Mar18)─┘
Python 3.9.13 (main, Aug 25 2022, 23:26:10)
[GCC 11.2.0] :: Anaconda, Inc. on linux
Type "help", "copyright", "credits" or "license" for more information.
```
## pytorch

## opencv
```bash
pip install opencv-python-headless
pip install opencv-contrib-python-headless
```