# 项目结构

在Rails之类的系统里，对项目结构做出了严格的要求，每个不同项目的目录结构都是一致的，这样的结构对于项目的规范化以及理解是比较有帮助的。目前在Meteor项目里面，没有明确的目录标准，对于一个特定的团队来说，对目录作出一定的约束还是比较有必要的。

## 目录含义

Meteor的特点在于客户端和服务端共享代码，所以在Meteor项目里，一般不做特殊限制的文件都会在client与server端同时加载。

下面这些目录都有着特殊的含义：

* **client** client目录下的文件仅在客户端加载
* **server** server目录下的文件仅在服务端加载
* **imports**
* **public** public目录下的文件可以在客户端访问，访问这些文件时将public目录是为根目录。比如访问`public/bg.png`的url是`/bg.png`。
* **private** 仅服务端可访问，通过Assets的API访问。
* **tests** 目录并不在任何地方加载，仅用于测试代码。
* **node_modules**  放置npm安装的包，它并不被meteor直接加载，需要通过特定方式使用
* **packages** 本地的meteor包，不直接加载
* **.** 以.开头的目录或文件，不加载，比如.meteor和.git

## 加载顺序

从Meteor1.3开始，引入module机制，从而可以比较方便的控制文件加载的顺序，1.2以前的规则就不用考虑了。

## 目录结构

Meteor项目推荐的目录结构有几点简要说明：

* Meteor里面的目录结构是主要按照特性来区分的，而不仅是client/server形式
* LESS文件和Components放在同一目录下（就近原则）
* 每个文件一个单元， 包括template, component, method 和 test等
* 常规项目可以参考[todos](https://github.com/meteor/todos)的目录结构如下(Blaze&React)

```
-.meteor          项目相关信息
  -local          本地生成文件，需要gitignore
  packages        项目用到的meteor包列表，增减package可以直接编辑这个文件
  platform        支持平台列表，可以是server,browser,android,ios
  release         Meteor的主版本号，比如`METEOR@1.3`
  versions        每个meteor包的版本号
-client           客户端初始化内容
  main.js         通常是import了`imports/startup/client`目录下的内容
  main.less       通常是import了'imports/ui/'下面的一些内容
-i18n             多语言设置
  en.i18n.json    英语
-imports          可以import的文件
  -api            数据相关内容放在api目录下
    -lists
      -server
        publications.js
      lists.js
      lists.tests.js
      methods.js
    -...
  -startup        
    -client
      routes.js
    -server
      fixtures.js
      register-api.js
      security.js
  -ui             界面部分，多级子目录组成，React项目和Blaze项目的主要区别就是这个目录里的内容
    -stylesheets  样式文件
    -layouts      布局
    -containers   容器
    -components   组件
    -helpers      Helper功能
-node_modules     npm安装的module，每个一个子目录，通过npm install方式添加
-packages         meteor包，每个一个子目录, 可以直接添加或者通过submodule方式添加
-public
  -font           字体
  -icon           图标
-resources        项目资源
-server           服务端初始化内容
  main.js
.gitignore        
.gitmodules
mobile-config.js
package.json
README.md
```
