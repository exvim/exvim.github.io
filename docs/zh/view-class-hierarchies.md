---
layout: docs
title: 类继承视图
---

exVim 将会允许用户生成指定类的类继承图。这是由 [ex-hierarchy](http://github.com/exvim/ex-hierarchy) 插件完成的. 

当运行`:Update`命令后，exVim将会生成继承文件。这个文件将会从你的ctags生成信息里面提取继承信息。它记录
你工程中类的继承关系。

[ex-hierarchy](http://github.com/exvim/ex-hierarchy) 插件在你输入一个类时将会解析这个继承文件，它将会生成一个
Graphviz点格式文件，然后使用Graphviz画一个.png格式的图片。

目前, [ex-hierarchy](http://github.com/exvim/ex-hierarchy) 支持c++,jvava ,python等等。

下面是一张在ex2D中`exPlane`类继承图：

![hv-explane]({{site.url}}/docs/images/hv-explane.png)

## 显示类继承图

[ex-hierarchy](http://github.com/exvim/ex-hierarchy)有三个命令用于打印和显示类继承图：

 1. `:HV <class>`: 将会显示`<class>`的子类和父类. 
 1. `:HVP <class>`: 将会 `<class>`的父类.
 1. `:HVC <class>`: 将会`<class>`的子类.

让我们以上面的图片作为例子。上面的图片是由`:HV exPlane`命令生成的。当你使用`:HVP exPlane`
时，结果将如下所示：

![hvp-explane]({{site.url}}/docs/images/hvp-explane.png)

`:HVC exPlane` 命令的结果将是:

![hvc-explane]({{site.url}}/docs/images/hvc-explane.png)

你也可以使用 `<leader>hv` 键绑定用于运行`:HV` 命令用于生成当前类的继承关系图：

**注意:** 生成的图片保存在 `.exvim.your-project/hv.png`, exVim 将尝试使用你默认的图片浏览器打开它。
