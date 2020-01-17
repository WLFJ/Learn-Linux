# 上古神器Vim使用指南

## 插入文本快捷键

使用`i`（insert）在光标的前面插入文本;使用'a'（append）可以在光标后边插入字符。

在命令模式下使用'shift+i'可以在行的开头插入文本，同理使用'shift+a'可以在行末插入！

使用'o'在当前行的下一行开启一个新行，使用'shift+o'在当前行的上一行开启一个新行。Maybe Outline?

## 方向切换

hjkl -> 左下上右

## 通用配置

代码高亮 syntax on

设置行号 set number

设置为相对行号 set relativenumber

设置光标线 set cursorline

自动换行 set wrap

显示输入的命令 set showcmd

在下边栏显示备选项 set wildmenu

在搜索时高亮显示 set hlsearch

每次打开文件时取消高亮 exec "nohlsearch"

忽略大小写 set ignorecase

智能大小写 在混杂大小写的时候是唯一的 set smartcase 
  
## 配置文件详解

'noremap a b'将a键替换为b

'map S :w<CR>' 将大写S替换为保存操作":w<Carrage Return>"我会在后面研究一下vim中的其他键位操作

其他详细配置可以在配置文件中看，其路径为~\.vim\vimrc

## Vim中的特殊键位操作

没有操作'<nop>':no operation
回车'<CR>' Carrage Return

## Vim中的高级操作

### x - 删除一个字符 - Operation

### d - Delete - Operation

删除光标左右n个字符 dn[左右剪头]

剪切一行 dd

#### di - Delete In ...

删除后并不会进入写入模式

### p - Paste - Operation

### y - Copy - Operation

操作同d

#### yi - Copy In ...

用法同ci

### c - Change - Operation

删除n个字符并进入写入模式，操作同d

#### ci - Change In ...

如果在一个单词的中间位置想要删除这个单词，使用ciw。
如果要删除符号内部的内容，使用ci符号实例。

### w - Word - Motion

将光标移动到下一个单词开始的位置（标点符号单算一个）

使用cw可以删除后面一个单词并进入编辑模式

### b - Back - Motion

### 0 - Motion

回到当前行的最开头

### f - Find - Operation

在当前行寻找最开始文本

同样可以与d、c、y操作相组合。

### z - ? - Operation

zz 将光标位置切换为中心点

## Number

用于指明操作几次。

# 搜索

使用/后面进行搜索

## Leadear键设置一键输入命令

首先在配置文件第一行设置 let mapleader = " "

之后添加映射 noremap <LEADER><CR> :nohlsearch<CR>

# 分屏

使用:splite 上下分屏，使用:vsplite左右分屏
