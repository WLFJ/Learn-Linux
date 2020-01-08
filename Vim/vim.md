# 上古神器Vim使用指南

## 插入文本快捷键

使用`i`（insert）在光标的前面插入文本;使用'a'（append）可以在光标后边插入字符。

在命令模式下使用'shift+i'可以在行的开头插入文本，同理使用'shift+a'可以在行末插入！

使用'o'在当前行的下一行开启一个新行，使用'shift+o'在当前行的上一行开启一个新行。Maybe Outline?

## 方向切换

hjkl -> 左下上右

## 配置文件详解

'noremap a b'将a键替换为b

'map S :w<CR>' 将大写S替换为保存操作":w<Carrage Return>"我会在后面研究一下vim中的其他键位操作

其他详细配置可以在配置文件中看，其路径为~\.vim\vimrc

## Vim中的特殊键位操作

没有操作'<nop>':no operation
回车'<CR>' Carrage Return

## Vim中的高级操作


