被遗失的快捷键们： J - 删除两段中间的行

下面是一些我们需要关注的宝藏： help options.txt --> 可以看在命令行可以输入什么
想要看这些命令的详细解释，我们要使用单引号包括
在map.txt中我们可以看到一些键位映射的方法 怎样窗口管理呢？我们要看window.txt
我们可以使用b返回上一个单词！
使用gg可以回第一行，使用ge可以返回到前一个单词的结尾
使用iskeyword设置判断一个单词的标准
使用大小写进行切换跳转可以十分方便跳转是空格分割单词还是符号分割的！
现在我们知道了对于一行有三种操作，使用$跳到最后，0跳到最开始，^跳到开头第一个非空的字符
同时可以使用2$的方式移动到下一行的末尾！
我们可以使用f指令来跳转到下一个指定开头的字符 使用F可以向左边搜索
使用f和t有什么区别呢？t会停在当前位置的前一个，而不是在当前搜索位置之上！
通过设置matchpairs可以指定%的配对内容
使用数字+G的方式可以方便跳转到从开头数的指定行号。
使用数字+%的形式可以跳转到整个文件行数的百分比
使用HML分别定位到行号的顶部/中间/末尾，用于在某页面的定位
使用number显示左边的行标号，使用ruler将在下面显示行号等信息
使用C-U和C-D可以方便翻过半屏幕
使用C-E和C-Y可以向上和向下滚动滚动条，这个应该怎么记呢?  使用C-F和C-B全屏滚动
使用zz将光标放在中间，使用zb在下面，zt在顶部。注意会移动页面，而不是只光标动
设置scrolloff可以指定页面的上下部分必须留下的空白
搜索输入的内容太麻烦？可以将光标停在下一个要搜索的位置，之后使用*（没有/）使用#反向搜索,使用g*和g#可以搜索本部分关键词
使用\< 和\>可以指定强制匹配 使用循环搜索 set wrapscan 使用:scriptnames
搜索加载了的脚本地址 ## 正则表达式专题 使用^标记行开头，使用$标记行末尾
通配符使用.  ## 跳转
普通的移动并不会记录为跳转，使用:jumps可以显示历史使用的所有跳转指令
使用ma的方式指定名称为a的标签，最多a-z
26个字母。使用’a跳转到当前行，使用`a跳转到当前列，更加精确
内置了一下记录的标记，使用‘’跳转到上一次跳转的位置，‘“上一次编辑的位置‘[上一次更改的开始位置']上一次更改的最后位置。
注意使用dw是要删除最后的空格的，但是de并不会。到那时cw和ce却又是相同的都不会删除后面的空格
使用x删除左边的字符，X删除右边的，D删除当前行到结尾，C改变当前行到结尾，s改变一个字符，S改变一整行（现在被替换了）
使用v进入最普通的写入模式，V进入行编辑模式，C-进入块编辑模式
使用o可以切换两个选择点
使用P可以在上一行粘贴，同时如果有一个字符打反了，可以使用xp命令
使用D可以删除当前位置到结尾，但是使用Y也是复制整个行！
"*作为前缀可以与系统剪贴板进行交互 ## 文字对象
使用xax的方式可以处理单词对象，使用xis处理带最后空格的句子，xas处理不带最后空格的句子
详细可以看text-object
使用~可以切换文字的大小写，通过设置tildeop将其可以与motion相结合

p代表段落对象，和前面的w、s齐了 ## vimrc 设置！

        source $VIMRUNTIME/defaults.vim

将内容转换成HTML TOhtml

查看当前编辑的文件列表 args 切换文件 next
previous（前面加上w可以顺便保存）还有first 和next（不支持加w快捷保存）
不关闭vim
可以使用args后加文件的方式重新指定要编辑的文件列表（原来以为是添加Orz）
转移到上一次离开文件时候的位置：`" 到上一次编辑的位置`.
双引号就像暂停符号一样，所以是离开文件时候的位置，而句点则说明编辑已经完成

之前看了打标签的方法，事实上我们可以使用大写字母在文件之间打标签，这样就可以按下后在文件之间切换了。

## 使用register
创建的时候必须在带有复制功能的命令前面紧跟"ax,比如说复制一个单词："wyaw
比如说在删除时候保存："sdis 使用时紧跟操作符之前："wp "ap 之类

在文件后面追加内容，通常在加log的时候。:write
>> logfile

以只读的形式打开文件：vim -R filename 或者更佳强制的方式：vim -M filename

修改文件名，不写入修改：:file filename
将文件写到一个新的文件名上（创建并写入，不修改源文件）:saveas filename

## 窗口管理

最基本的命令：split 可以追加文件名 关闭窗口：close 只保持当前窗口：only
打开新窗口：new

在右边分屏：:vsplit 分别关闭每一个窗口：:qall 分别保存每一个窗口：:wall
使用命令分别打开窗口 vim -o filemane 如果要竖屏打开则是-O

## VIMDIFF

对于折叠的块使用zo打开zc关闭 在浏览时如果不希望滚动条同时滚动，则set
noscrollbind 在展开之后快速定位下一个修改的地方：]a 上一个地方[a
dp会将窗口的不同同步过去，do会将不同同步过来

## 分割窗口位置

:leftabove {cmd}	left or above the current window :aboveleft {cmd}
idem :rightbelow {cmd}	right or below the current window :belowright {cmd}
idem :topleft {cmd}		at the top or left of the Vim window :botright
{cmd}		at the bottom or right of the Vim window

## 标签编辑文本

:tabedit filename

切换tab 使用 gt（goto tab）

## 高阶更改

录制键盘宏 qx 结束录制 q 使用 @x 前面添加数字可以执行指定次数
使用@@执行上一次的宏

先使用小写字母录制”小操作“，再使用大写字母录制”大操作“，就可以实现更佳复杂的操作！

同样的，使用复制功能时首先使用小写字母创建register，之后就可以使用大写字母将内容追加在其中了！（复制的内容都可以一行一行保存，多爽啊！）

现在我们要实现 将所有出现的单词所在的行保存：

this is a sentence.  I like programming.  Apple is the best.  My name is Tom.
this commang is as follows.  现在我们要将里面所有出现is的句子复制下来

## 替换

:[range]substitute/from/to/[flags] 不加range默认处理当前行，否则加上%处理全部行
substitute可以简写为s flags有 c-confirm g-globel p-print e-没有寻找到不算是错误
常用于宏 命令默认处理每一行第一次出现的，要全部处理加上g
加上p会打印最后处理的结果，使用c会询问每一次的决定


y		Yes; make this change.  n		No; skip this match.  a
All; make this change and all remaining ones without further confirmation.  q
Quit; don't make any more changes.  l Last; make this change and then quit.
CTRL-E Scroll the text one line up.  CTRL-Y Scroll the text one line down.

如果替换的内容中有slash，那么我们可以将编制命令中的所有slash替换成+


在:后面添加a,b的形式可以指定处理的范围，特殊的，.代表当前行，$代表最后一行，我们之前使用的%就是.,$的简称

更高级指定范围的方式： :?^Chapter?,/^Chapter/s=grey=gray=g

开始的范围搜索使用??包括，之后的范围使用//,最后的替换表达式使用=

我们还可以指定搜索区间的offset：:.+3,$-5
如果觉得位置规定太麻烦了，可以使用marks代替，使用时与跳转一样，:'a,'b

同时还可以在visual模式下选中区间，之后进行一些操作（要使用普通模式则要加上normal关键字）

上面的标记可以混用。:'>,$

如果知道要处理多少行，可以输入5:的形式，会自动补全从当前行开始的处理区间

## 区块模式

我们可以选中区间之后使用I批量添加

使用I插入时候短行不会有影响，而如果使用A不使用$匹配的话会在每行的结尾匹配，如果使用其他方式选择了一整行，则不会在对应位置插入。

使用c可以方便删除块内文本并进入写入模式，而C则会从块的开始位置删除到行结尾

～ 转换大小写 U 转大写 u 转小写

选中之后 使用rx可以将选区全部替换成指定字符

使用>可以将每一行文本中间插入tab 设置大小:set shiftwidth=4

## 格式化文本

使用gq运算符可以方便处理段落格式化问题

gqap--a paragraph 将文本按照段落划分

gggqG--将整个文章按照标准格式化

gqj--处理当前行和下一行，长了换行，短了补上

## 转换大小写

gU gu g~
注意这些都是操作符号，所以后面可以跟任何motion，重复只需要gUU就可以处理一整行了。

## 使用外部程序

!{motion}{program}

就可以选中区间，使用外部程序处理处理这些数据了

输入!!就可以对当前行下手了 !!  date 可以在当前行插入时间戳

其与read的区别是这个命令会替换选中的行，但是前者不会 read目前不能传入数据
write可以看到程序返回，但是不能写入文件

使用C-l重绘

## 恢复文件

使用vim -r help.txt


## 使用正则表达式的硬核操作

直接上公式：:%s/\([^,]*\), \(.*\)/\2 \1/ 就可以直接将前后名字替换了！

更多技巧见：sub-replace-special

## 统计

使用gC-g可以显示区域的统计信息 更多技巧见 count-items

## 打开指定文件

感觉自己要学的东西还有好多啊！

vim 'grep -l frame_counter *.c'

在打开文件之后，我们同样可以使用grep去寻找文件之中的关键字，不过在切换时 是有
cnext cprev clist

## 命令行编辑


## 历史记录

使用oldfiles去查看编辑文件历史 之后使用 :e #<2 来打开文件标号为2的文件

或者使用:browse oldfiles 也可以选择文件

## 记录会话

:mksession vimbook.vim :source vimbook.vim vim -S vimbook.vim

## 自动补全

输入一部分之后键入C-P向前查找，C-N向后查找

如果知道自己要查找那一部分，可以使用下面的快捷键： CTRL-X CTRL-F
file names CTRL-X CTRL-L		whole lines CTRL-X CTRL-D
macro definitions (also in included files) CTRL-X CTRL-I		current
and included files CTRL-X CTRL-K		words from a dictionary CTRL-X
CTRL-T		words from a thesaurus CTRL-X CTRL-]		tags CTRL-X
CTRL-V		Vim command line

同时应该看一看ins-completion

最关键的代码补全叫做omni，如果后面有需要我们可以看一下ft-c-omni

我们可以使用C-A重复之前的插入操作，或者使用C-@后会自动退出Insert模式
现在我们在编辑模式

在编辑模式下面的东西才是关键呀！
使用C-W删除前面的单词，使用C-U删除当前位置前面的全部，使用S-左右实现单词遍历
使用C-Y复制光标上面的字母，C-E是下面的

使用C-R插入寄存内容,如果里面含有特殊字符 输入两次C-R

## 略缩语

通过:abbreviate 或者:ab 可以看到所有略缩语
要设置不同模式下的略缩语（比如c代表command-line mode）可以使用:xab

删除略缩语使用:unab xxx

删除全部 :abclear

为了避免里面的部分命令触发其他定义，使用nore前缀

## 插入特殊字符

使用C-V加上按键，可以将格式控制字符插入

或者可以在后面添加按键编号


## 二合字母

通过C-K 加上代号输入二合字母，使用:digraphs查看表

通过C-o进入visual mode就可以输入很多指令了！

## 自动换行

设置textwidth

## 居中

使用描述区间的通用办法，center，后面可以跟上宽度的情况

同样还有left和right，不过后面的可选参数变成距离边界的距离了

## 调整文本


执行:packadd justify 或者在vimrc中添加：packadd! justify 或者执行外部命令:%!fmt
详情输入gf参考： $VIMRUNTIME/pack/dist/opt/justify/plugin/justify.vim.

## 自动对齐

set autoindent 要移动一块内容使用<>就好了 通过设置:set
softtabstop=4就可以控制移动距离了

## 横屏滚动


                              |<-- current window -->| some long text, part of
                              which is visible in the window ~ ze	  |<--
                              window     -->| zH	   |<--     window
                              -->| 4zh		  |<--	   window     -->| zh
                              |<--     window	 -->| zl
                              |<--	window	   -->| 4zl
                              |<--	   window     -->| zL
                              |<--	 window     -->| zs
                              |<--	window	   -->|


使用gv再次选中区间

使用C-A可以将内容自加1 使用C-X自减1 :set nrformats-=octal
可以在文中编辑时去掉自动识别八进制

## 在多个文件中操作

bufdo argdo windo 使用｜分割参数，使用update更新文件

## 更高级的搜索

/offset/2 会停留在搜索位置下面两行，-2则是上面两行 /const/b+2 /e-2
会让光标停留在指定位置

搜索带重复的内容，使用* 比如/a* 就会搜索 空、a、aa、aaa……
注意只对前面一个字符起作用，使用\(\)将其扩起来就好啦！

如果要去掉搜索空串，使用/ab\+

可选内容使用/folders\= 将会搜索folder和folders

想指定更详细一点，使用/ab\{3,4} 将会匹配abbb和abbbb

        pattern		match count ~ \{,4}		0, 1, 2, 3 or 4 \{3,}
        3, 4, 5, etc.  \{0,1}		0 or 1, same as \= \{0,}
        0 or more, same as * \{1,}		1 or more, same as \+ \{3}
        3 使用{-1,3}将会匹配最少数量的文本，而不是越多越好

使用或运算，我们可以实现强大的搜索功能，或为\| 使用/else\(if\|while\|for\|\)
可以匹配elseif elsewhile elsefor

/\(foo\|bar\)\+将会匹配foo和bar的任意组合

使用\&描述从匹配内容中抽取子项/forever\&...

正则表达式疯狂使用，比如查找双引号的内容
/"[^"]*"就可以了，这里中括号代表一个字符

还可以使用内置的类型描述，详细见/\s item	matches
equivalent ~ \d	digit			[0-9] \D	non-digit
[^0-9] \x	hex digit		[0-9a-fA-F] \X	non-hex digit
[^0-9a-fA-F] \s	white space		[ 	]     (<Tab> and <Space>) \S
non-white characters	[^ 	]     (not <Tab> and <Space>) \l
lowercase alpha		[a-z] \L	non-lowercase alpha	[^a-z] \u
uppercase alpha		[A-Z] \U	non-uppercase alpha	[^A-Z] item
matches				option ~ \i	identifier characters
'isident' \I	like \i, excluding digits \k	keyword characters
'iskeyword' \K	like \k, excluding digits \p	printable characters
'isprint' \P	like \p, excluding digits \f	file name characters
'isfname' \F	like \f, excluding digits \h
大小写字母带下划线，不包含数字 \w      \h + 数字

匹配特殊字符

使用\n表示换行，如果包含空格，使用\_s
将上面第一个表中说明的类型中加上_就可以额外匹配空格了
上面引言还可以这样匹配：/"\_[^"]*"

## 折叠

首先使用zf<motion> 创建一个fold，比如zfap

之后就可以使用zo打开 zc关闭了

使用zr
使所有折叠展开一层，zm全部折上一层，大写则变成全部打开/折叠,注意这里reduce的是fold的数量，m是增加fold的数量
使用zi可以方便切换打开/折叠状态

要将收缩状态创建是需要mkview的
后面加数字可以创建最多10个，使用loadview读取。使用viewdir查看所有存储

我们还可以指定在fold上显示的内容，详情见fold-marker

## CPP 支持

首先为每一个c文件创建标签 ctags *.c(注意这个在命令行中的！）

使用tag可以看到所有的标记，打开新窗口看标记使用stag tagname 或者C-W
]在新窗口打开当前文件

之后我们还要绑定一些tags文件，这里我们可以使用 :set tags=文件路径
类似这样去写：!/proj/**/tags

经过测试，要看一个文件的主函数：Main文件名

使用C-T返回上一个页面

使用ctags -R 目录地址 自动生成一个大的tags文件，最后再指定就行了

:tfirst			go to first match
:[count]tprevious	go to [count] previous match
:[count]tnext		go to [count] next match
:tlast			go to last match

因为不同的tag中有相同的函数，所以我们需要选择不同的tag，在搜索名字时候可以使用pattern

现在有一个小技巧：首先使用ctags --c-types=f -f functions *.c将文件中的function都导出来，之后使用我们定义快捷指令:noremap <buffer> <CR> 0ye<C-W>w:tag <C-R>"<CR> 就可以在函数窗口中将光标移动在名称上，然后在另一个窗口上打开这个函数了！

快捷跳转

在看宏定义的时候使用]#跳到当前开始，使用]#跳到当前检测的下一个case

使用[[跳到当前最外层寒暑体的第一行，使用[{跳到当前结构的开头，使用]}跳到结构的末尾，注意要到最外层函数需要使用][,这个位置是反的

在方法之间跳转使用[m 和]m.

在方法之间跳转我们认为自己更需要跳到自己的开头[[或者跳到下一个的结尾]]，于是想要跳到上一个的结尾使用[],跳到自己的结尾使用][

经过实践，在有类的时候这个东西不好用，于是我们还是找找插件吧！

使用[<tab>跳到所指内容第一次出现的位置，其等价操作为[i
我们可以使用[i跳到第一次出现的位置，]i到下面第一出现的位置，]I会列出下面出现的列表,使用[I会搜索只有一行的文本列表

如果是宏定义中的东西，使用d代替i

上面的会搜索所有的include的文件，如果只要的当前文件中搜索，可以使用gD在全文搜索，gd在函数内搜索

使用C-T在行前添加TAB，使用C-D删除

在normal模式下我们可以使用>i{会将括号内的东西缩进，而>a{则会全部缩进


Fri 14 Feb 2020 22:16:25 CST
完结撒花！还没有看undo tree，感觉用处不是很大Orz
