[TOC]

## 流行框架 angularjs第二天

### 1.自定义指令
- 作用:
    + 操作DOM
    + 自定义HTML标签
        * 在原生JS中,可以将公共的代码封装成函数
        * 在angularjs中,可以将公共的HTML结构封装成自定义标签
        
- 语法：
    + 如何定义一个最基本的自定义指令
    ```javascript
    模块对象.directive('指令名称',[function(){
        return {
            // 指令的具体配置
        }
    }])
    ```

    + 指令的配置参数介绍
        * template和templateUrl使用方法
            - template 模板字符串
            - templateUrl 外链模板
        * link函数的作用及参数说明
            - 作用：写DOM操作的地方
            - 有三个参数 scope element attributes
            - scope:类似于$scope 向指令的摸板中暴露数据
            - element:当前指令所要操作的元素
            - attributes:当前指令所在标签的属性结合 对象类型
        * transclude的作用
            - 如果指令所在标签内部有内容 会将内容保存到ng-transclude中
            - 然后在模板内将ng-transclude保存的内容写在想要显示的位置即可
            - 默认值是false 不保存原有内容 也就是直接用模板内容替换原有内容

### 2.angularjs中请求数据的方式
- angularjs中提供了一些方法,我们可以用这些方法向后台发送请求,获取数据
- 语法：
    + 标准的请求方式(通过例子说明)
        * $http()
    + 简化的请求方式(通过例子说明)
        * $http.get()
        * $http.post()
- [ng-bind-html](https://cdn.bootcss.com/angular.js/1.6.4/angular-sanitize.min.js)
- angularjs中没有类似于jquery中beforeSend这样的方法
- angularjs中不能将请求设置为同步

### 3.angularjs中的过滤器
- 对数据的格式进行处理
- 使用过滤器的语法：
    + {{ 数据模型 | 过滤器的名字:过滤器的参数:多个参数以冒号隔开 }}
- 内置过滤器介绍
    + currency 货币过滤器
    + date 日期过滤器
    + filter 过滤数据
    + limitTo 限制
        * 第一个参数:limit 限制的数量,可以为负数,从后往前开始限制 
        * 第二个参数:begin 从第几个开始限制
    + orderBy 排序
        orderBy:'字段'  默认是升序
        orderBy:'-字段' 降序

### 4.自定义过滤器
- angularjs自身只是提供了一些常用的过滤器,在实际项目中,我们往往会遇到一些比较具体的需求,比如电话号码中间星、单词首字母大写等等比较个性化的数据格式需求
- 语法：
    + 如何定义自定义过滤器
    ```javascript
    模块对象.filter('自定义过滤器名字',[function(){
        return function(要处理的数据,滤过器参数1,滤过器参数2,...){
            // 具体处理数据的代码
            return 处理后的数据;
        }
    }])
    ```
- 通过例子演示自定义过滤器的使用(首字母大写、电话号码加星)

### 5.angularjs中服务
- 作用
    + 抽取公共代码
    + 在多个控制器之间共享数据
- 语法
    + `angular.module('myService',[]).service('serviceName',[function(){}])`
    + 服务也是模块下的方法,要创建服务,先创建模块
    + 在模块对象下面有一个service方法
    + 第一个参数是服务名称
    + 第二参数以数组的形式存在,和控制器的使用方法一样
- 使用
    + 将服务对应的JS文件在页面中用script标签引入
    + 将服务模块作为主模块的依赖模块
    + 在需要使用的控制器中将服务作为控制器回调函数的形参

    ```html
    <body ng-app="myApp">
        <div ng-controller="ctrlA"></div>
        <div ng-controller="ctrlB"></div>
        <script src="node_modules/angular/angular.min.js"></script>
        <script src="js/service.js"></script>
        <script>
            angular.module('myApp',['myService'])
                
                // 在两个控制器中依赖的serviceName服务 是同一个对象
                所以在A控制器中修改了服务的值 在控制器B中也会得到体现
                
                .controller('ctrlA',['$scope','serviceName',function($scope,serviceName){
                    serviceName.name = '123';
                }])
                .controller('ctrlB',['$scope','serviceName',function($scope,serviceName){
                    console.log(serviceName);
                }])
        </script>
    </body>
    ```
