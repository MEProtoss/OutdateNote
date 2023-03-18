

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

