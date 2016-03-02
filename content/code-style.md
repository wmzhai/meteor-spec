# 代码规范

* **目录**
  * 全小写字母命名
* **Collection**
  * 命名采用复数
  * 实例变量采用首字母大写驼峰复数
  * 数据库里面的Collection名称与实例变量一致
  * MongodB里面的字段采用camel-cased
* **Schema**
  * 直接在实例定义以后添加，比如 `Todos.schema = new SimpleSchema({})`
  * attach形式，比如：`Todos.attachSchema(Todos.schema);`
* **Methods和publications**
  * Camel cased，采用点做命名空间(namespace)的分隔
  * 使用mdg:validated-method来使用methods
* **Packages，文件和exports**
  * 使用ES2015exports
  * 每个文件表示单个逻辑模块，而不是使用一个类似utils.js的文件exports一堆不相关功能
  * 如果一个文件定义了一个类或者component，这个文件需要采用命名一致的小写模式文件名
* **Blaze Template**
  * Blaze的Template需要采用点来做命名空间，因为他们不可以作为module来export
  * 同一个Template的HTML，CSS和JS文件应该采用同样的文件名
* **React Components**
  * 按照正常的JavaScript模块和函数处理
* **路由**
* **避免使用jQuery**
* **Server 代码善用 throw new Meteor.Error**
