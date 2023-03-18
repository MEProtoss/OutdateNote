# wsl下安装ubuntu 以及配置

1. Microsoft store中安装Ubuntu

2. 开启Windows的wsl系统功能

3. 升级wsl内核
   https://wslstorestorage.blob.core.windows.net/wslblob/wsl_update_x64.msi

4. 启动创建账户

## 常用软件及环境配置

=**############以下内容建议全程手机热点###########**=

```bash
#替换镜像
https://mirror.tuna.tsinghua.edu.cn/help/ubuntu/
#更新系统
sudo apt update
#安装zsl
sudo apt install -y zsh
git clone https://github.com/robbyrussell/oh-my-zsh.git ~/.oh-my-zsh
#更改为默认bash
cp ~/.oh-my-zsh/templates/zshrc.zsh-template ~/.zshrc
chsh -s /bin/zsh
#更改主题
sudo nano ~/.zshrc
#将其中的ZSH_THEME修改为你想要的 github可以找到
#启动zsh
zsh
#更新p配置
source .zshrc
#使用大佬配置
git clone https://github.com/MarsWang42/My-Vim-Conf.git
#进入库
cd My-Vim-Conf
chmod +x ./setup.sh ./tmux.sh
./setup.sh
source ~/.zshrc
#卸载没用的东西（强迫症）
sudo apt autoremove
#卸载重装neovim 因为人家的配置你不熟悉 最好自己配
sudo apt-get remove neovim
sudo add-apt-repository ppa:neovim-ppa/stable
sudo apt-get update
sudo apt-get install -y neovim
#创建配置文件，这个配置文件是用来配置nvim的·
nvim ~/.config/nvim/init.vim
#去vimawesome 安装插件
#github安装vimplug管理插件
sh -c 'curl -fLo "${XDG_DATA_HOME:-$HOME/.local/share}"/nvim/site/autoload/plug.vim --create-dirs \
       https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim'
#如果443错误 得修改下hosts sudo修改/etc/hosts, 在末尾加入
199.232.68.133 raw.github.com
199.232.28.133 raw.githubusercontent.com

#装好后再打开init.vim 配置文件 添加默认配置

call plug#begin('~/.vim/plugged')
Plug 'vim-airline/vim-airline'
Plug 'vim-airline/vim-airline-themes'
Plug 'mhinz/vim-startify'
Plug 'Yggdroot/indentLine'
Plug 'preservim/nerdtree'
Plug 'crusoexia/vim-monokai'
Plug 'octol/vim-cpp-enhanced-highlight'
Plug 'neoclide/coc.nvim', {'branch': 'release'}
Plug 'Raimondi/delimitMate'
call plug#end()

#退出再载入 然后Pluginstall 安装好 一次不行就多retry几次 务必安好 不然后面没法装clangd


#对了 C和C++用户可以安装一下Clangd 配置一下一键调试脚本
#安装npm
sudo apt install npm
#更新nodejs
sudo npm install n -g
sudo n stable
#记得重启shell或重新加载source


#依次运行
sudo npm install -g yarn
cd ~/.vim/plugged/coc.nvim	#创建这个路径
yarn install
yarn build #会报错 别管
#安装clangd
sudo apt install clangd

#然后去init.vim中
:CocInstal clangd
```



#下面是大佬的脚本安的东西 大家自行取舍 
https://github.com/MarsWang42/My-Vim-Conf/blob/master/.config/nvim/init.vim


#特别鸣谢！！！！！！
#本文参考如下！！！！！
https://www.bilibili.com/video/BV1kT411C7vm/?spm_id_from=333.999.0.0&vd_source=54c7f15515681874f0bdf2982482d588

https://www.bilibili.com/video/BV1t54y1R7F3/?spm_id_from=333.999.0.0

