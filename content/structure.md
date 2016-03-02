# 项目结构

在Rails之类的系统里，对项目结构做出了严格的要求，每个不同项目的目录结构都是一致的，这样的结构对于项目的规范化以及理解是比较有帮助的。目前在Meteor项目里面，没有明确的目录标准，对于一个特定的团队来说，对目录作出一定的约束还是比较有必要的。

## 目录含义

在Meteor项目里，一般的文件都会在client与server端同时加载，不过下面这些目录都有着特殊的含义：

* **client** client目录下的文件仅在客户端加载
* **server** server目录下的文件仅在服务端加载
* **public** public目录下的文件可以在客户端访问，访问这些文件时将public目录是为根目录。比如访问`public/bg.png`的url是`/bg.png`。
* **private** 仅服务端可访问，通过Assets的API访问。
* **tests** 目录并不在任何地方加载，仅用于测试代码。
* **node_modules**  放置npm安装的包，它并不被meteor直接加载，需要通过特定方式使用
* **packages** 本地的meteor包，不直接加载
* **.** 以.开头的目录或文件，不加载，比如.meteor和.git

## 加载顺序

从Meteor1.3开始，引入module机制，从而可以比较方便的控制文件加载的顺序，1.2以前的规则就不用考虑了。

## 目录结构

这里基于[todos](https://github.com/meteor/todos)项目给出一个推荐的目录结构
