# AngularJs
近期投入的一个项目中，它前端技术使用到了angularJs，已现在的眼光来看已经算是有点老的技术了，但是这并不能说完全灭绝了。同时，以后也许会接手一些老的项目，用到angularJs的可能性还是有的，所以总结一些angularJs中基础的用法以便以后第一眼看到代码不会太生疏。
#### 简单介绍
AngularJS有着诸多特性，最为核心的是：MVVM、模块化、自动化双向数据绑定、语义化标签、依赖注入等等。  

#### AngularJS 模块  
其中有许多的模块，每个模块都负责其相对应的功能。
* ng  
  >AngularJS的默认模块，包含AngularJS的所有核心组件。  
* ngRoute  
  >AngularJS是一套前端的MVC框架。那么，为了实现视图的中转，肯定会涉及到路由的概念。ngRoute即是AngularJS的路由模块。  
* ngAnimate  
  >AngularJS的动画模块，使用ngAnimate各种核心指令能为你的应用程序提供动画效果。动画可使用css或者JavaScript回调函数。  
  
AngularJS中文网中还有其他的一些模块的介绍，但是我并没有用到所以概念不是很清晰，有兴趣的话可以去[AngularJS中文网](http://www.angularjs.net.cn/)深入研究。  
#### ng模块介绍  
AngularJS的默认模块，包含AngularJS的所有核心组件。如：指令directive，服务service，过滤器filter等一些东西。  
1. 指令directive  
AngularJS 指令是以 ng 作为前缀的 HTML 属性。我的理解就是跟vue中v-加在html属性前面差不多。代码如下  
   ```  
    <!DOCTYPE html>
    <html>
    <head>
    <meta charset="utf-8">
    <script src="http://cdn.static.runoob.com/libs/angular.js/1.4.6/angular.min.js"></script>
    </head>
    <body>
    
    <div ng-app="">
        <p>名字 : <input type="text" ng-model="name"></p>
        <h1>Hello {{name}}</h1>
    </div>
    
    </body>
    </html>
   ```
   当网页加载完毕，AngularJS 自动开启。其中几个指令如下解释：

   * ng-app 指令告诉 AngularJS，`<div>`元素是 AngularJS 应用程序 的"所有者"。跟vue中el属性差不多，为实例提供挂载的元素。

   * ng-model 指令把输入域的值绑定到应用程序变量 name。这个知道双向绑定的就都很清楚了。

2. 表达式  
AngularJS 使用 表达式 把数据绑定到 HTML。其中特点如下：
   * AngularJS 表达式写在双大括号内：{{ expression }}。  
   * AngularJS 将在表达式书写的位置"输出"数据。  
   * AngularJS 表达式 很像 JavaScript 表达式：它们可以包含文字、运算符和变量。  
   >实例： {{ 5 + 5 }} 或 {{ firstName + " " + lastName }}  
  
  我总结就是,在{{}}中能写js一些的代码，表达式可以包含字母，操作符，变量。但是，表达式不支持条件判断，循环及异常。