Linux帮助系统常见技巧
######################
:date: 2012-04-04 08:55
:category: Technique
:tags: Linux, manpage
:slug: linux-manual

Linux下命令实在太多，学习命令行最佳途径当然是通过手册（manual），新手对帮助系统有所了解可以更快地上手Linux基本管理操作。

-  man cmdname

这是最基本的用法了，也是最有效的方法。man
page主要是面向unix程序员，因此事无巨细，对于常见的操作其实并不需要细看，了解书写格式，挑出几个选项就可以了。

-  cmdname --help或者cmdname -h

相比上一条，这个对于新手更加适用，因为它只显示最常用的选项，文字也更精简，真正可以让你快速参考。另外还要说明的是，许多打包的可执行安装文件都可以用这条命令显示安装帮助，如一些后缀名为bin或者run的文件，在安装前有必要阅读一下。这条命令只能作用于外部命令，shell内部命令无法使用（虽然还是有输出文字）。判断一条命令是外部或者内部命令，可以用type
cmdname查询某个命令或者help查看所有内部命令。

-  whatis cmdname

whatis命令显示的其实是manpage的名称一栏的注释，你可以试试man
whatis和whatis
whatis看看区别所在。如果只是想简单了解某条命令的用处，用whatis就再合适不过了。（whatis
man会出现三个带选项的man命令，为什么？）

-  info cmdname

info命令显示的帮助更加详尽，信息量更大，同时界面更加友好。不过不怎么常用

-  manual系统

每个命令的manpages其实包括8个章节，它们包括不同的内容，如下表：

+---------+-------------------------+------------+----------------+----------------+----------------+
|  章节   | 描述                    | 普通用户   | 软件开发人员   | 文档组织人员   | 系统管理人员   |
+=========+=========================+============+================+================+================+
|  1      |  用户命令               |  ✓         |                |                | ✓              |
+---------+-------------------------+------------+----------------+----------------+----------------+
|  2      |  系统调用               |            |  ✓             |                |                |
+---------+-------------------------+------------+----------------+----------------+----------------+
|  3      |  语言函数库调用         |            |  ✓             |                |                |
+---------+-------------------------+------------+----------------+----------------+----------------+
| 4       |  设备和网络界面         |            |                |                |  ✓             |
+---------+-------------------------+------------+----------------+----------------+----------------+
|  5      |  文件格式               |            |                |                |  ✓             |
+---------+-------------------------+------------+----------------+----------------+----------------+
|  6      | 游戏和示范              |            |                |                |                |
+---------+-------------------------+------------+----------------+----------------+----------------+
|  7      | troff的环境、表格和宏   |            |                |  ✓             |                |
+---------+-------------------------+------------+----------------+----------------+----------------+
|  8      | 关于系统维护的命令      |            |                |                |  ✓             |
+---------+-------------------------+------------+----------------+----------------+----------------+
| 9       | 其它                    |            |                |                |                |
+---------+-------------------------+------------+----------------+----------------+----------------+

在不同需求的情况下应当查看不同的章节，要查看指定的章节可以用man -sx
cmdname或者man x cmdname，其中x为章节对应的数字。比如查看库函数man -s3
open。

-  常用快捷键

快捷键帮助h(man状态下)

退出q

下一屏space或者f(forward)，上一屏b(backward)

下一行j，上一行k

前向搜索/pattern，反向搜索?pattern

下一个匹配n，上一个匹配N

风格其实和vim相似，比如Ctrl+f也是下一页。

-  man目录

/usr/share/doc/man/

-  中文manpages

`manpages-zh项目`_\ ，安装后即可查看常用命令的中文manpage，不过似乎中文排版有点问题，看起来有点丑陋。

-  彩色manpage

黑底白色的大量文字看久了很累，可以考虑自定义彩色的manpage，编辑～/.bashrc：

.. code-block:: bash

    # colorful man page
    export PAGER="`which less` -s"
    export BROWSER="$PAGER"
    export LESS_TERMCAP_mb=$'\E[01;34m'
    export LESS_TERMCAP_md=$'\E[01;34m'
    export LESS_TERMCAP_me=$'\E[0m'
    export LESS_TERMCAP_se=$'\E[0m'
    export LESS_TERMCAP_so=$'\E[01;44;33m'
    export LESS_TERMCAP_ue=$'\E[0m'
    export LESS_TERMCAP_us=$'\E[01;33m'这样一个简单可用的彩色manpage就搞定了，当然你也可以自己参照修改。

.. _manpages-zh项目: https://github.com/lidaobing/manpages-zh
