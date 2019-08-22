---
layout: post
title: 'vim相关问题'
date:   2017-09-08 10:22
tags: vim
---
##配置文件

配置文件为`.vimrc`，具体配置如下：
```vim
"--显示行号--
set number

"--缩进2个空格/制表符为2--
set tabstop=2
set softtabstop=2
set shiftwidth=2
"--将Tab转换为空格，但是这个选项并不会改变已经存在的文本--
"--如果需要应用此设置将所有Tab转换为空格，需要执行命令：retab!--
"set expandtab

"--缩进线设置--
"--若要显示缩进线，不能将Tab转为空格--
set noexpandtab
"--设置list模式--
set list
"--在 list 模式下将 tab 显示成 . 后加空格的样子--
"--注意最后有一个空格--
set listchars=tab:\.\ 

"--语法高亮--
syntax on

"--高亮光标列--
set cursorcolumn
"--高亮光标行--
set cursorline

"--不要备份文件（根据自己需要取舍）--
set nobackup

"--不要生成swap文件，当buffer被丢弃的时候隐藏它--
setlocal noswapfile
set bufhidden=hide

"--在搜索的时候忽略大小写--
set ignorecase

"--在搜索时，输入的词句的逐字符高亮（类似firefox的搜索）--
set incsearch

"--解决中文乱码问题--
set fileencodings=utf-8,ucs-bom,gb18030,gbk,gb2312,cp936
set termencoding=utf-8
set encoding=utf-8

"--自动补全 "" '' ()--
:inoremap ( ()<ESC>i
:inoremap ) <c-r>=ClosePair(')')<CR>
:inoremap " ""<ESC>i
:inoremap ' ''<ESC>i
function! ClosePair(char)
  if getline('.')[col('.') - 1] == a:char
    return
  else
    return a:char
  end if
endfunction

"------Fortran相关配置------

"--根据文件后缀名匹配格式--
"--未验证--
let s:extfname= expand("%:e")
  if s:extfname==? "f90"
    let fortran_free_source=1
    unlet! fortran_fixed_source
  else
    let fortran_fixed_source=1
    unlet! fortran_free_source
  endif

"--语法的缩进和高亮匹配--
let fortran_free_source=1
let fortran_more_precise=1
let fortran_do_enddo=1
"--去掉固定格式每行开头的红色填充--
let fortran_have_tabs=1

"--允许Fortran代码折叠--
let fortran_fold=1
"let fortran_fold_conditionals=1
"--折叠方式--
setfoldmethod=syntax
"--如果前面启用了代码折叠，那么文件一打开代码全部是折叠的，需再按“zO”打开全部折叠的代码--
"--如果想在文件打开后所有折叠都自动展开，请加入以下配置--
set foldlevelstart=99
```
在命令模式下，可以为program、module、subroutine、function折叠代码，常用命令如下：
- zc：折叠代码
- zo：展开代码
- zC：折叠所有代码
- zO：展开所有代码


##其他问题

###用vim清除文本中的`^M`
Windows系统的换行符为`/r/n`，而Linux/Unix系统则为`/n`，因此，在Windows里编辑过的文本文件到了Linux/Unix里，每一行都会多出一个`^M`。
可以在Vim里用以下命令清除该字符：
```
:%s/^M//g
```
命令中的`^M`是通过键入`<ctrl-v><enter>`或`<ctrl-v><ctrl-m>`生成的