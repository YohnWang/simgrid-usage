# simgrid使用方法

simgrid本身并不是一个仿真器，他实际上就是一个库，通过这个库可以用来构建自己的仿真器。

## simgrid在ubuntu上的安装

官方手册有具体的安装步骤，但这里只提供我需要的。[官方网址](https://simgrid.org/doc/latest/Installing_SimGrid.html#installing-from-the-source)

首先到simgrid的github网址上找到该项目，可以选择下载最新版本的源代码，也可以下载稳定版本的源代码，稳定版本在release下可以找到

在ubuntu上安装两个预编译包

```
apt install libsimgrid-dev simgrid-java
```

由于simgrid使用cmake编译，所以还需要保证安装了cmake

simgrid项目依赖于boost库，所以需要安装它

```
apt install libboost-dev libboost-context-dev
```

一切准备就绪后，开始编译源码

```
tar xf SimGrid-3-XX.tar.gz                    //解压
cd SimGrid-*                                  //进入解压后的源码文件夹
cmake -DCMAKE_INSTALL_PREFIX=/opt/simgrid .   //-DCMAKE_INSTALL_PREFIX表示安装目录，自己设定，注意.是必须的 表示cmake产生的文件存放的目录，.就表示当前目录
make
make install
```

编译完成后，会在安装目录中得到一个include文件夹和lib文件夹，因为我们所使用的是这个库，所以后序会使用这两个文件夹。

因为该项目默认使用cmake构建自己的仿真器，并且有一个[官方模板](https://framagit.org/simgrid/simgrid.git)，可以尝试使用。

但考虑到项目比较简单，管理起来不是很复杂，后序仍然使用Makefile来构建项目。

*注意：simgrid使用c++编写，要求编译器支持c++11标准，如果编译器版本为5，则需要添加编译选项`-std=c++11*`

