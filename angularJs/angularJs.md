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
  
    我总结就是,在{{}}中能写js一些的代码，表达式可以包含字母，操作符，变量。但是，表达式不支持条件判断，循环及异常。跟vue中html中{}的功能差不多。    
3. 服务Service  
在 AngularJS 中，服务是一个函数或对象，可在你的 AngularJS 应用中使用。AngularJS 内建了30 多个服务。比如$http这种常用的内置服务，用来向服务器发送请求，还有过滤器$filter等常用的内置服务。这里主要说下创建自定义服务，因为内置的服务都能查到而且有解释。  
    ``` 
    app.service('counter', function() {
        this.add = function (x,y) {
            return x + y;
        }
        this.reduce = function (x,y) {
           return x - y;
        }
    }); 
    ```  
    * app是个angularJs的实例，我这么认为的，app.service可是说是它的一种功能，来创建服务用的，我认为就是重复的方法可以分装成函数在service里面，现在的项目中service都是用来分装请求的。  
    * 'counter'这个就是你创建服务的名字了，它跟内置的区别就是有没有$符号吧。当你用这个自定义创建的服务是，你需要先引入进去，然后看第二个参数函数里你定义了哪些方法。比如你需要1加2，那么你就可以这样```counter.add(1,2)```来调用创建的服务。相减的话是同样的道理```counter.reduce(2,1)```  
4. 控制器controller  
AngularJS 控制器 控制 AngularJS 应用程序的数据。AngularJS 控制器是常规的 JavaScript 对象。  
    ```
    <div ng-app="myApp" ng-controller="myCtrl">
      名: <input type="text" ng-model="firstName"><br>
      姓: <input type="text" ng-model="lastName"><br>
      <br>
      姓名: {{firstName + " " + lastName}}
    </div>
    <script>
      var app = angular.module('myApp', []);
      app.controller('myCtrl', function($scope) {
          $scope.firstName = "John";
          $scope.lastName = "Doe";
      });
    </script>  
    ```  
    * ng-controller="myCtrl" 属性是一个 AngularJS 指令。用于定义一个控制器。这个控制器能控制的范围就是它挂在的html标签所包含的范围。控制器内能定义一些页面初始化的参数，和调用一些服务和请求。  
5. 作用域$scope  
作用域顾名思义就是上面说到的控制器能控制到的范围，以上面控制器中的代码为例。控制器的写法是$scope,但是请注意在用之前都需要先引入这是一种规定。  
    * 上面的``` $scope.firstName = "John"```和```$scope.lastName = "Doe";```两行代码就是用来定义在控制器myCtrl的范围内有两个变量firstName和lastName。可以在控制器myCtrl挂在的div包裹范围内任意处使用。后面的传值就是用来初始化这两个变量，页面刚加载时，出现在页面中的这两个参数就是'John'和'Doe'。  
#### 总结  
AngularJS使用的这几天，就我个人而言。还是没有vue简便的。但是毕竟也是vue出来之前很常用的一套框架，所以一些老项目还是可能会用到，所以以后的改进和为何还是要会这套技术的。