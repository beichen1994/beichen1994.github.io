---
title: 我的i3、tmux、ranger使用
date: 2020-04-26 19:38:40
tags:
categories:
- 神器
---

## ranger
ranger是一个文件管理器，可以让我们在终端下方便快捷的操作文件和文件夹，我的ranger配置文件可以在我的[github仓库](https://github.com/beichen1994/MyLinuxConfig/tree/master/.config)中找到。

ranger的操作方式有点类似vim，下面是我的常用命令

~~~
hjkl左下上右

gh (/home

gm (/mnt

gd (/dev

gp (/tmp

cw 重命名

pp 粘贴

dd 剪切

yy 复制

space 选中
~~~

在安装与配置ranger时，我是参照了以下教程
* [Ranger 用法总结](http://www.huangpan.net/posts/ji-ke/2019-08-21-ranger.html#toc-heading-75)

* [ranger文件管理器](https://www.cnblogs.com/zhangsf/p/3322627.html)

* [ranger文档](https://wiki.archlinux.org/index.php/ranger_(%E7%AE%80%E4%BD%93%E4%B8%AD%E6%96%87))

## tmux

tmux可以让我们在一个终端中同时开启多个会话，看起来更加酷炫，从此不再多个窗口来回切换。但是比较受限于屏幕大小，如果屏幕太小，窗口被切分的太小，看起来不舒服。

我常用的tmux命令如下:
***

* 启动与退出

~~~

tmux

exit
~~~

***

* 会话（Session）管理

~~~

tmux ls

tmux new -s mysess

tmux detach

tmux attach -t mysess

tmux switch -t mysess

tmux rename-session -t 0 bc

tmux kill-session -t mysess
~~~

***

*窗格（pane）管理

~~~
tmux split-window
划分上下两个窗格

tmux split-window -h
划分左右两个窗格

tmux select-pane -U
光标移动到上方窗格

tmux select-pane -D
光标移动到下方窗格

tmux select-pane -L
光标移动到左方窗格

tmux select-pane -R
光标移动到右方窗格


tmux swap-pane -U
当前窗格上移

tmux swap-pane -D
当前窗格下移
~~~

***

* 快捷键

~~~

Ctrl+b    %
划分左右两个窗格

Ctrl+b    "
划分上下两个窗格

Ctrl+b    箭头
光标移动到其他窗格

Ctrl+b    {
当前窗格左移

Ctrl+b    }
当前窗格右移

Ctrl+b    Ctrl+o
当前窗格上移

Ctrl+b    Alt+o
当前窗格下移

Ctrl+b x
关闭当前窗格

Ctrl+b !
将当前窗格拆分为一个独立窗口

Ctrl+b q
显示窗格编号

窗口管理

tmux new-window  -n bc1
新建一个窗口

tmux select-window -t bc1
切换窗口

tmux rename-window bc1
重命名窗口

快捷键

Ctrl+b    c
创建一个新窗口

Ctrl+b    w
从列表中选择窗口


Ctrl+b    ,
重命名窗口

Ctrl+b    p
切换到上一个窗口

Ctrl+b    n
切换到下一个窗口

Ctrl+b    窗口编号
切换到指定编号的窗口
~~~

## i3

i3是一个可以高度自定义的窗口管理器，对于i3的安装与配置，我是参考了以下4个教程。

* [手把手教你使用Linux安装i3wm桌面](https://blog.csdn.net/mkosto/article/details/97238317)

* [Ubuntu18+i3配置](https://www.jianshu.com/p/f4b3abc9a282)

* [ubuntu系统配置i3wm窗口管理器](https://www.jianshu.com/p/81917864271e)

* [i3文档](https://i3wm.org/docs/)

我的i3配置文件可以在我的[github仓库](https://github.com/beichen1994/MyLinuxConfig/tree/master/.config)中找到