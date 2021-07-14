## Makefile笔记

### 1.伪目标

当当前目录中含有与目标一样的文件时，执行目标时则不会执行目标，则我们可以在不生成目标文件的目标前加上关键词“.PHONY”表示伪目标，则不会检测当前目录下的文件就会执行该命令

### 2.Makefile说明

-------------------

目标名称1:依赖的文件或者其他目标

Tab 命令1

Tab 命令2

Tab ...

目标名称2:依赖的文件或者其他目标

Tab 命令1

Tab 命令2

Tab ...

-----------------

第一目标，在这里比如目标1是默认目标，执行make时会直接执行。如果有依赖其他文件则先执行其他目标。

### 3.Makefile默认规则

make有一条默认规则，当找不到xxx. o文件时，会查找目录下的同名xxx.c文件进行编译。

```makefile
hello_main: hello_main.o hello_func.o
	gcc -o hello_main hello_main.o hello_func.o
#以下是make的默认规则，下面可以不写
#hello_main.o: hello_main.c
	#gcc -c hello_main.c 
	#gcc -c hello_main.c -o hello_main.o (与上句指令效果相同)

#以下是make的默认规则，下面可以不写
#hello_func.o: hello_func.c
	#gcc -c hello_func.c 
	#gcc -c hello_func.c -o hello_func.o (与上句指令效果相同)
```

### 4.Makefile变量

使用变量方法：$(变量)

变量赋值的四种方式：

​	“=” ：延时赋值，该变量只有在调用的时候，才会被赋值

​	“:=” ：直接赋值，与延时赋值相反，使用直接赋值的话，变量的值定义时就已经确定了。

​	“?=” ：若变量的值为空，则进行赋值，通常用于设置默认值。

​	“+=” ：追加赋值，可以往变量后面增加新的内容。

自动化变量

| 符号 | 意义                                           |
| ---- | ---------------------------------------------- |
| $@   | 匹配目标文件                                   |
| $%   | 与$@类似，但$%仅匹配“库”类型的目标文件         |
| $<   | 依赖中的第一个目标文件                         |
| $^   | 所有的依赖目标，如果依赖中有重复的，只保留一份 |
| $+   | 所有的依赖目标，即使依赖中有重复的也原样保留   |
| $?   | 所有比目标要新的依赖目标                       |

### 5.分支

​	ifeq(arg1, arg2)       #如果arg1等于arg2，执行分支1，否则执行分支2
​		分支1
​	else
​		分支2
​	endif

### 6.Makefile函数

在Makefile中调用函数的方法跟变量的使用 类似，以“$()”或“${}”符号包含函数名和参数

​	$(函数名 参数)         ${函数名 参数}

常用函数

notdir：函数用于去除文件路径中的目录部分   

$(notdir 文件名) 		$(notdir ./sources/hello_func.c)结果为hello_func.c

wildcard：函数用于获取文件列表，并使用空格分隔开。例如函数调用“$(wildcard [*](http://doc.embedfire.com/linux/imx6/base/zh/latest/linux_app/makefile.html#id17).c)”，函数执行后会把当前目录的所 有c文件列出。

$(wildcard 匹配规则)

patsubst：函数功能为模式字符串替换

$(patsubst 匹配规则, 替换规则, 输入的字符串)