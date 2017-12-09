[TOC]

## 流行框架 angularjs第一天

### 1.为什么要学习angularjs?
- 快速构建单页web应用

### 2.angularjs是什么?
- 一款非常优秀的前端高级JS框架
- 由谷歌团队负责开发维护

### 3.框架与库
- 无论是angularjs还是jQuery都是用原生JS封装的
- 库:
    + 对代码进行封装 调用封装的方法 简化操作
- 框架：
    + 提供代码书写规则 按照规则去写代码 框架会帮我们实现相应的功能

### 4.获取angularjs的方式
+ [在官网上下载](http://angularjs.org)
+ [通过CDN的方式引入到页面中](https://cdn.bootcss.com/angular.js/1.6.4/angular.min.js)
+ `<script src="https://cdn.bootcss.com/angular.js/1.6.4/angular.min.js"></script>`

### 5.angularjs快速入门
- 案例对比原生JS与angularjs
    + 原生JS实现值加1
    + angularjs实现值加1
- 基本的指令介绍
    + 在使用了angularjs的页面,以ng-开头的属性,称之为指令
    + ng-app
        * 页面加载完成以后angularjs会在页面中查找这个指令
        * 没有找到:angularjs将不会启动
        * 找到:angularjs将会执行指令所在标签内部包裹的代码
        * 可以接受模块名字作为参数 angularjs会将当前页面交给指令的模块管理
    + ng-model
        * 获取表单元素的值
        * 实现双向数据绑定
    + ng-click
        * 给指令所在元素绑定点击事件
    + ng-init
        * 初始化数据
- 插值表达式介绍
    + {{}} 这种双大括号的形式称之为插值表达式
- 插值表达式的作用
    + 在表达式中可以写ng中的变量
    + 可以显示字符串
    + 在表达式中可以进行计算
    + 可以在表达式中写三目运算符
    + 执行angularjs函数

### 6.angularjs基于模块开发项目
- 模块化开发带来的好处
    + 方便管理, 复用,后期维护方便
    + 解决代码冲突,方便多人协作开发
- angularjs中模块的种类
    + 入口模块
    + 功能模块
- 分析模块和控制器与页面之间的关系
- 定义模块的语法规则

### 7.angularjs中如何使用控制器
- 定义及使用控制器
- 控制器的作用
    + 为用户界面提供数据支持
    + 用户界面的逻辑主要写在控制器中
- ng-click
    + 函数调用
    + angularjs代码 不能写原生JS代码

### 8.angularjs双向数据绑定
- 双向数据绑定介绍
    + 双向: html 和 js
    + 数据：angularjs中的变量
    + html=>js  js=>html
    + html中通过表单元素将数据改变 js中跟着同步
    + js中将数据改变 html中跟着同步
- 实现双向数据绑定的必要条件
    * 必须是表单元素 并且元素身上有ng-model指令

### 9.控制器中的$scope为什么不能改成其他的名字

### 10.安全的方式创建控制器

### 11.angularjs常用指令
- 指令分类:内置指令(普通指令、事件指令) 自定义指令
- 普通指令
    + ng-repeat 遍历数据 多层遍历

    + ng-repeat 补充 $index $first ...

    + 在循环的过程中如果有重复项 需要加上 track by $index

    + ng-class指令 用来操作类名

    + ng-bind 数据绑定 解决表达式闪烁问题

    + ng-show、ng-hide 通过样式的方式控制元素显示隐藏

    + ng-if 控制元素显示隐藏
        * 和ng-show用法相同
        * 区别是ng-if是通过DOM节点的添加和删除使得元素显示和隐藏

- 事件指令
    + ng-click
    + ng-dblclick

- 其他指令
    + ng-src

### 12.监控数据变化
- $scope.$watch

### 13.单页Web应用介绍 (single page web application) 简称SPA
- 回顾传统网站(http://www.kuoda.com.cn/indexs.html)
- 单页应用网站(http://m.daqizhong.com/index.html#/)
- 单页Web应用,就是只有一张Web页面的应用
- 单页面应用程序的特点
    + 整个网站由一个页面构成
    + 利用Ajax局部刷新达到页面切换的目的
    + 锚点与页面对应

### 14.angularjs相关网站
- [官方网站](http://angularjs.org)
- [官方文档](https://code.angularjs.org/1.6.4/docs/api)
- [学习网站]
    + http://www.angularjs.net.cn
    + http://www.apjs.net
    + http://www.runoob.com/angularjs/angularjs-tutorial.html
    + https://stackoverflow.com/

### 15.[Todomvc](http://todomvc.com/examples/angularjs/#/)