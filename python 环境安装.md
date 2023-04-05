# python 环境安装

## Anaconda

### **什么是Anaconda？**
环境管理工具

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

### 常用命令

1. 创建名字为Name的流程环境，指定python版本为version，同时下载othersoftware软件：
    conda create -n Name python=version othersoftware
    如:
    conda create -n sbhk python=3 sra-tools
    创建名字为sbhk的流程环境，指定python版本为3，同时下载sra-tools 软件
    注：建议指定python版本为为具体版本，如3.6，目前python=3似乎默认为3.9
    新建的环境实际上可以在miniconda3/envs文件夹下看到。。
2. 删除指定的流程环境，需指定流程环境的名字Name
    conda remove -n Name --all
3. 查看流程环境
    conda env list
4. 进入指定流程环境，需指定流程环境的名字Name
    conda activate Name
5. 退出当前流程环境
    conda deactivate
6. 重命名环境：先新建clone再进行删除
    conda create -n sbhk --clone sboei
    conda remove -n sbhk --all
7. 想要为某个环境安装第三方包的话，进入该环境后输入：

  ```text
  conda install package_name
  ```
## pytorch

深度学习工具包 一个框架

确定自己安装了显卡驱动
```
nvidia-smi
```

### cpu版

```text
conda install pytorch torchvision torchaudio cpuonly -c pytorch
```

### 验证

```text
import torch
torch.cuda.is_available() # to check if your GPU driver and CUDA/ROCm is enabled and accessible by PyTorch
x = torch.rand(5, 3)
print(x)
```
应该出现
tensor([[0.3380, 0.3845, 0.3217],
        [0.8337, 0.9050, 0.2650],
        [0.2979, 0.7141, 0.9069],
        [0.1449, 0.1132, 0.1375],
        [0.4675, 0.3947, 0.1426]])
        

### gpu版本
conda install pytorch torchvision torchaudio pytorch-cuda=11.7 -c pytorch -c nvidia
## opencv
```bash
pip install opencv-python-headless
pip install opencv-contrib-python-headless
```

## 可能遇到的问题

### 画图时qt无法加载，提示以下错误
Available platform plugins are：eglfs, minimal, minimalegl, offscreen, vnc, webgl, xcb.

因为相关依赖没装好没有图形化界面

解决方法
sudo apt-get update
sudo apt-get install build-essential
sudo apt-get install qtcreator
sudo apt-get install qt5-default
sudo apt-get install libfontconfig1
sudo apt-get install mesa-common-dev
sudo apt-get upgrade

### zsh的配置文件

/.zshrc 不是 /.bashrc

### libGL error: MESA-LOADER: failed to open swrast: /usr/lib/dri/swrast_dri.so: cannot open shared object file: No such file or directory (search paths /usr/lib/x86_64-linux-gnu/dri:\$${ORIGIN}/dri:/usr/lib/dri, suffix _dri) libGL error: failed to load driver: swrast