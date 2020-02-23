#VIM的使用方法 | 版本0.5
该版本完全基于B站UP主**@theCW** 的视频。
	视频链接：[上古神器Vim：从恶言相向到爱不释手 - 终极Vim教程01 - 带你配置属于你自己的最强IDE](https://www.bilibili.com/video/av55498503)
		  [上古神器Vim：进阶使用/配置、必备插件介绍 - 终极Vim教程02 - 带你配置属于你自己的最强IDE](https://www.bilibili.com/video/av55664166)
##普通模式中：
	i 光标前插入
	a 光标后插入，尤其可以在"</br>"即“回车”这样特殊的字符前。
	非普通模式中:shift + a 一行的末尾
		      	shift +i 一行的开头
	o 转到下一行并进行“插入”操作。
	s 删除光标处字符并写入。
	x 删除光标处字符。
	p 在光标下一行进行插入粘贴操作。
        hjkl进行移动，左下上右。
~~<operatin><motion>即先“操作”，后“动作”以执行完“操作”。~~
	d 可加上方向键剪切一个字符。
		d 3 ->向右剪切3个字符。
		dd 剪切光标所在行。注意“2 dd”才是剪切“光标所在行和下面的一行、即两行”。
	y 复制，亦可加上“操作”如“3 ->”。
		yy 复制当前行。

        c 改变。删除（x）并进入插入模式。
		c 3 ->删除“光标所在字符和右边两个字符”
        w 对单词的操作。光标会移动到下一个词。
		cw删除这个词并进入写入模式
        b 对单词的操作，回到上一个单词。
		ciw改变词中change in word
		ci"删除引号中的，并进入写入模式
		yi"复制双引号内内容。y，复制
		di“删除双引号内动作但不会进入插入模式
		fv find v
		f：find：
		cf：一直删到冒号并进入插入模式
		df：
		lyf：	p
		j往下移动	noremap E 5j，往下移动5行
		0回到最开头
		zz将当前行放置在中心

##vimrc
~~写入vimrc  cd ~/.vim~~
           ~~vim vimrc~~
**noremap** a b   键盘映射。按下a，vim知道这是b。
           其中， "no"表示“不会递归”，即在里再次用其他键映射a，vim只会识别这个其他键为a，不会递归成b。
                  "remap"表示重新映射。
                   注： 大小写之间也可以进行映射。
	        	除了noremap，它的前面还可以加上n，i，v三者中的任意，表示在什么模式下生效。
                        n,normal mode	i,insert mode	v,visual mode
                   另注：*:help map    查看有关“映射”的帮助。*
                         *:help noremap*


**map** 映射“普通模式下的某个键”为“一系列操作”。
如map Q :q<CR>
命令:source $MYVIMRC可以重新读取vimrc。亦可以使用map R :source $MYVIMRC<CR>来达到快捷执行。
*其中，<CR>表示"ENTER"即“回车操作”。*

**syntax on** 开启代码自动高亮。

***set 属性***
**set number** 显示行号。
**set nonumber** 不显示行号。
**set relativenumber** 按相关关系显示行号，比如一个函数内从“1”开始显示行号。
**set cursorline** 在光标行显示一条覆盖整行的下划线。
**set wrap** 一行内过长文本自动亦换行模式呈现，不超过当前页面最大宽度。
**set showcmd** 
**set wildmenu** 在命令模式中，按“TAB键”以补全命令。

##搜索
按"/"搜索。
set hlsearch高亮所有搜索结果
set incsearch边输入边高亮
exec "nohlsearch"  清楚搜索结果的高亮
set ignorecase忽略大小写
set smartcase智能大小写

n下一个
N上一个

set mapleader=“”
默认反斜杠
noremap <LEADER><CR> :nohlsearch<CR>
:split上下分屏
:vsplit左右分屏
:q退出
##美化
:color
:color default

##插件
github	vim-plug
推荐的vim-airline
      vim-snazzy	:color snazzy
		let g：SnazzyTransparent = 1	使背景透明
      nerdtree右边是文件，左边是文件树。支持书签功能。
         nerdtree-git   git仓库工具      
      YouCompleteMe代码补全工具，配置：cd .vim
					cd plugged
					cd YouCompleteMe
					sudo python3 install.py
      ALE指出代码错误，提供代码帮助
      MarkdownPreview    实时markdown，可以配置哪个浏览器打开
      Taglist显示函数列表
      vim-table-mode表格工具
      Python-syntax    Python工具
      vim-indent-guide   显示函数分块
      Goyo     Focus写作
      vim-signature     为文件提供书签。详细使用查看官方文档。
      Undotree    vim版本工具
##Visual Mode可视模式
普通模式，按下v，使用方向键进行选中。后面可用操作同普通模式
	shfit + v  选中行
V模式，按下冒号，输入normal，空格，之后所有操作都会同步到每一行。
	:'<,'>normal Imy-wallpaper-
		     A.png
shfit + v G(普通模式中是到最后一行，gg开头）
Visual Block
ctrl + v，选上块文本，可以同普通模式下一样操作。更改单行，按esc后全部更改。
##分屏
：split
：set splitright
快捷键实例map si ：set splitright<CR>：vsplit<CR>
               n       no
               u       nosplitbelow<CR>:split<CR>
               e       splitbelow<CR>:split<CR>
	之后普通模式中同时按键即可。

还有很多操作。回头有需要再学习吧。
###分标签页
需要再去学吧。
##实用编辑器设置
vimrc
set nocompatible
filetype on
filetype indent on
filetype plugin on
filetype plugin indent on

set mouse=a可以使用鼠标
set encoding=utf-8编码
set tabstop=2缩进距离
set foldmethod=indent代码可以收起来
set autochdir让vim默认在此文件中执行操作
待确认au BufReadPost * if line ("\") >0|if line("\") <= line($)|exe("norm'\'")|else|exe "norm $"|endif|endif使用vim打开文件回到上次位置

###Chrome插件vimuim
###为什么UP使用vim？
因为个人最大的便捷。（与B站上一期的无聊ky人聊一聊还行，这个UP脾气太好了。）
Xcode iOS开发 -> 用适合的工具做适合的事情。顺手即可。
