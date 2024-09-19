+++
title = "VimScript 备忘笔记"
date = 2024-09-19

[taxonomies]
categories = ["博客"]
tags = ["私人", "VIM"]
+++

# 命令

> 以下命令缺省“:”。

- 预备知识
```vim
" 获取 MYVIMRC 文件路径
echo $MYVIMRC " ~/.config/nvim/init.lua
```
- 打印信息
```vim
help echo " :ec[ho] expr1 ..
help echom " :echom[sg] expr1 ..
help messages " :message  -> 查看日志

echo "message" " 屏幕打印信息
echom "message" " 屏幕打印信息时，信息记录与 messages 中
messages " 查看echom命令输出的信息

" 练习: 每次打开 Vim 时显示 ( >^.^< )
" .vimrc echo >^.^<
```
- 设置选项
```vim
" 布尔选项 set <name> 打开选项 set no<name> 关闭选项
set number " 设置显示行号
set nonumber " 设置不显示行号
set number! " 切换当前选项
set number? " 查看当前选项

" 键值选项 set <name>=<value> 设置选项
set numberwidth=10 " 改变行号列宽
set numberwidth? " 查看行号列宽

" 常用选项
set wrap? " 单行文本截断
set shiftround? " shiftwidth整数倍对齐
set matchtime? " showmatch 开启时，显示括号匹配的时间

" 一次设置多个选项
set number numberwidth=6 " 设置显示行号，同时设置行号显示宽度

" 练习
help 'number' " nu[ber] 
help relativenumber " rnu | relativenumber
help numberwidth " nuw | numberwidth (default 4)
help wrap " wrap (default on)
help shiftround " sr | shiftround (default off)
help matchtime " mat[chtime] (default 5)
```
- 基本映射
```vim
" 基本映射
map - X
map - dd 
" 特殊字符
map <space> viw
map <c-d> dd
" 注释失效！！！
map <space> viw " 注释失效！！！
" 练习
" 映射 - 为“删除当前行，然后粘贴到下一行”
map - ddp
" 映射 _ 为当前行向上移动一行
map _ ddkkp
```
- 模式映射
```vim
" normal模式 删除当前行
nmap \ dd
" visual模式文本转换为大写
vmap \ U
" insert模式 删除一行
imap <c-d> <esc>ddi
" 练习
" insert模式 按下<c-u>当前光标单词转换为大写格式
imap <c-u> <esc>viwUi
" normal模式 按下<c-u>当前光标单词转换为大写，并进入插入模式
```
- 精确映射
```vim
" 非递归映射 《任何时候！！！》
nnoremap \ dd
" 练习
help unmap " unm[ap]  -> unm[ap] nun[map] vu[nmap] xu[nmap] sunm[ap] ou[nmap] unm[ap]! iu[nmap] lu[nmap] cu[nmap] tunma[p]
```
- Leaders
```vim
" 映射按键序列（前缀）
nnoremap -d dd
nnoremap -c ddO
" Leaders
let mapleader = "-"
nnoremap <leader>d dd
nnoremap <leader>c ddO
" LocalLeader 仅对部分文件设置
let maplocalleader = "\\" " 注意"\\" 是 "\" 的转义
nnoremap <localleader>d dd
nnoremap <localleader>c ddO
" 练习
help mapleader " map <leader>A oanther line<esc>
help maplocalleader " map <buffer> <localleader>A oanther line<esc>
```
- 编辑你的Vimrc文件
```vim
" 编辑我的vimrc文件
nnoremap <leader>ev :vspilt $MYVIMRC<cr>
" 重读我的vimrc文件
nnoremap <leader>sv :source $MYVIMRC<cr>
" 练习
help myvimrc
```
- Abbreviactions
```vim
" 适用于insert、replace、command模式
iabbrev adn and " 输入非字母、数字、下划线的字符，引发替换
set iskeyword? " iskeyword=@,48-57,_,192-255
iabbrev @@ echemoo@gmail.com
iabbrev ccopy Copyright 2024 Jonas Lee, all rights reserved.
" 按键映射 vs Abbreviations(按键映射输入即替换，易出错)
inoremap ssig -- <cr>Jonas Lee<cr>echemoo@gmail.com
" 练习
" 添加邮箱、博客网址、签名等abbreviations配置；
" 添加常用文本配置
```
- 更多的Mappings
```vim
" 更常用的退出(停顿 vs 无停顿)
inoremap jk <esc>
" 更复杂的Mapping（当前单词收尾插入引号）
nnoremap <leader>" viw<esc>a"<esc>hbi"<esc>lel
" 练习
" 创建单引号版本；
nnoremap <leader>' viw<esc>a'<esc>hbi'<esc>lel
" 引号将高亮选中的文本包裹。
vnoremap <leader>" <esc>`<i"<esc>`>la"<esc>
vnoremap <leader>' <esc>`<i'<esc>`>la'<esc>
" normal模式下 H 映射为当前行首部。
" normal模式下 L 映射为当前行尾部。
help H
help L
```


