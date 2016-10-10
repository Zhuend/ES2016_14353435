# 实验文档一

## Description

DOL的全称是Distributed Operation Layer，是一个用于并行式程序开发的框架。我们本次实验的内容主要是完成DOL的安装与配置。

## How to install
整个安装过程均运行在Ubuntu 14.04操作系统下。

### 预备工作
首先，我们需要安装一些实验开发所必须的包。如：update、ant、openjdk以及unzip等等。安装使用了apt-get指令，如图：

![fig-1](http://p1.bqimg.com/567571/83ae69b4e8dfe1a8.jpg)

之后，我们需要使用刚才的unzip工具，将事先下载好的DOL安装包解压到指定的文件夹下，然后使用tar指令将systemC的压缩包进行解压即可。

### 编译systemC
接下来，我们进行systemC的编译。首先我们进入systemC解压所在的文件夹，并新建一个临时文件夹。
>cd systemc-2.3.1
mkdir objdir
cd objdir

然后，我们在该临时文件夹内运行configure文件，
>../configure CXX=g++ --disable-async-updates

可以得到如下结果：
![fig-2](http://p1.bqimg.com/567571/4d512e42c711b048.jpg)

然后，我们运行install指令，进行systemC的编译，编译后的文件夹目录有如下文件：
![fig-3](http://p1.bqimg.com/567571/e0cd646a6fe74f5e.jpg)

### 编译DOL
之后，我们进行DOL工具的编译。我们先需要对build_zip.xml文件进行修改:
>&lt;property name="systemc.inc" value="YYY/include"&gt;
&lt;property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"&gt;

我们需要将上面两行中的YYY更改为我们编译systemC后所设定的工作路径，可以使用PWD查看，如图：
![fig-4](http://i1.piimg.com/567571/919bc500b674b9dd.jpg)

修改后，我们可以进行编译，并运行第一个例子：
>ant -f build_zip.xml all
cd build/bin/main
ant -f runexample.xml -Dnumber=1

若配置成功可以得到如下的结果：
![fig-5](http://i1.piimg.com/567571/d4e7f93cdfa3eb28.jpg)
![fig-6](http://i1.piimg.com/567571/44f71c2850205185.jpg)

最后我们可以查看生成的dot文件：
![fig-7](http://p1.bpimg.com/567571/ca16d329fe2de0d0.jpg)

## Experimental experience
本次实验是本学期第一次实验，主要内容是相关软件环境的配置与安装，但是这些内容也是我们后续实验课程的基础。通过本次实验，我又温习了linux环境下命令行的使用，同时也在安装过程中对DOL有了一个较为浅显的认识。
同时本次实验报告的编写是使用了markdown，并上传至Github上。在这一过程中，我学习到了markdown的基本使用语法，以及通过Git来对Github上的远程仓库进行管理。这些知识在今后的学习开发中都是十分有用的。