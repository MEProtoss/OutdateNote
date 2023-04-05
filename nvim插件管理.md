

# nvim插件管理


```bash
#安装
call plug#begin('~/.vim/plugged')

call plug#end()

#使用以下命令检查状态
:PlugStatus

输入下面的命令，然后按回车键安装之前在配置文件中声明的插件
:PlugInstall

#更新插件
:PlugUpdate

#查看修改
:PlugDiff

#审查插件
#有时，更新的插件可能有新的 bug 或无法正常工作。要解决这个问题，你可以简单地回滚有问题的插件。输入 :PlugDiff 命令，然后按回车键查看上次 :PlugUpdate的更改，并在每个段落上按 X将每个插件回滚到更新前的前一个状态。

#删除插件
#删除一个插件删除或注释掉你以前在你的 vim 配置文件中添加的 plug 命令
#然后source或重启 Vim 编辑器
#最后，运行以下命令卸载插件：
:PlugClean
```

## 一些装起来比较麻烦但是有用的插件

### tagbar

可以用来查看文件中的函数 

安装方法

```
call plug#begin('~/.vim/plugged')
Plug 'majutsushi/tagbar'
call plug#end()
```

然后执行

```
source ~/.vimrc
:PlugInstall
```

还需要安装Ctgas依赖

```bash
git clone https://github.com/universal-ctags/ctags.git
cd ctags!
./autogen.sh
./configure --prefix=/where/you/want # defaults to /usr/local
make
make install # may require extra privileges depending on where to install
```

这样完就成了
然后可以在vim配置文件中添加以下配置

```
map <silent> <F4> :TagbarToggle<CR> 
let g:tagbar_width = 25
autocmd BufReadPost *.cpp,*.c,*.h,*.cc,*.cxx call tagbar#autoopen() 
```

上述的配置可让打开常见的源代码文件的时会自动打开Tagbar插件。或者用vim打开文件时，按F4就能打开tagbar window



###  neovim coc.vim

代码补全插件 能做的有很多

1. 安装neovim

2. 安装vim-plug

3. 自动补全需要安装的插件

4. 1. 安装coc.nvim插件 (前提是安装了nodejs)
   2. 我补全的是python, 在nvim中又运行了:CocInstall coc-pyright

5. 在~/.config/nvim/init.vim 里面添加的配置

```text
" Use tab for trigger completion with characters ahead and navigate.
" NOTE: Use command ':verbose imap <tab>' to make sure tab is not mapped by
" other plugin before putting this into your config.
inoremap <silent><expr> <TAB>
      \ pumvisible() ? "\<C-n>" :
      \ <SID>check_back_space() ? "\<TAB>" :
      \ coc#refresh()
inoremap <expr><S-TAB> pumvisible() ? "\<C-p>" : "\<C-h>"

function! s:check_back_space() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction
```

这样打python代码就自动打出来了。

## 一些插件的使用教程

### nerdtree

#### **【NERDTree目录导航】**

NERDTree中我们可以使用k/j上下移动键在文件/文件夹之间移动，但是当项目文件/文件夹很多时候，这种方式就显得很笨拙了。
NERDTree提供了如下所示的快捷移动方式；

NERDTree的目录导航分为项目级别导航和系统级别导航。

*注：NERDTree目录导航的对象只是文件夹。*

#### **项目级别NERDTree目录导航**

P 移动到本项目的根目录文件夹处（光标移到到导航栏的根目录）
p 移动文件/文件夹所属的子文件夹处（光标移到上一级目录）
K 移动到本项目的第一个文件夹处
J 移动到本项目的最后一个文件处
Ctrl-j 移动下一个文夹处
Ctrl-k 移动上一个文夹处
**o 打开折叠的文件夹，但是不打开子折叠文件夹（展开当前目录）**
**O 打开折叠的文件夹，同时打开子折叠文件夹（展开当前目录下的所有目录）**
x 折叠起来打开的文件夹，但是不折叠打开的子文件夹（折叠到上一级目录）
X 折叠起来打开的文件夹，同时折叠打开的子文件夹（折叠所有文件夹到上一级目录）
**e 在编辑器区打开当前文件夹的目录，用于详细阅读该文件夹内容**

*注：以上主要针对当前光标目录进行操作；*

#### **系统级别NERDTree目录导航**

==**C 将当前文件夹变为根目录（导航栏根目录）**==
==**U/u 将当前根目录的上一级目录作为根目录（相对当前导航栏的根目录）**==
r 刷新光标所在的文件夹
R 刷新当前根目录所有文件夹

*注：以上主要是针对NERDTree目录导航栏进行操作；*

**【NERDTree中文件/文件夹操作】**

NERDTree的文件/文件夹操作主要包括：
1、文件的打开方式；
2、对文件/文件夹的增、删、查、改操作；

#### **NERDTree中文件的打开方式**

o 直接在编辑区以替代的方式打开文件
**i 将编辑区横向切分窗口，并在新的窗口中打开文件**
s 将编辑区纵向切分窗口，并在新的窗口中打开文件

#### **NERDTree中对文件/文件夹的增、删、查、改操作**

打开NERDTree目录操作界面的方法为：将光标停靠在目录树中任意位置，按下快捷键m就弹出如下图所示的NERDTree目录树操作界面：

![img](https://img2022.cnblogs.com/blog/333765/202209/333765-20220926142919051-1623748769.jpg)

可以看出，对目录树中文件/文件夹可进行的操作包括如下表所示的内容：
a 在当前文件夹下新建一个文件/文件夹，只有自定义名字则创建文件，而在自定义名字后面加上/则创建文件；助记：a →(a)dd
m 修改文件/文件夹的名字；m →(m)ove，在Linux系统的move一个文件到自己的位置，就是修改文件/文件夹名字的操作。
d 删除文件/文件夹；d →(d)elete
r 在文件管理器中展示当前文件/文件夹；r →(r)eveal
o 使用系统默认编辑器打开当前文件/文件夹，如果是文件则使用文件管理器打开；o →(o)pen
c 复制当前的文件/文件夹，注意：复制完成后，需要选择需要粘贴的位置；c →(c)opy
p 复制当前文件/文件夹的路径到剪切板 p →(p)ath
l 列出当前文件/文件夹信息 l →(l)ist

**【NERDTree窗口切换】**

ctrl + w + h 光标 focus 左侧树形目录
ctrl + w + l 光标 focus 右侧文件显示窗口
ctrl + w + w 光标自动在左右侧窗口切换
