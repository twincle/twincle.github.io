抗拒Angular2很久了，到底还是爱上，了她。

<!-- more -->

## AngularJS那些日子

刚认识AngularJS的时候才发现，原来前端可以这样解放双手，可以这样操纵页面，这才是前端应该有的样子！

虽然在远古时代，大家就知道展示应该和逻辑分离，把js和css单独作为一个文件编写，而不是直接在html文件中直接嵌入，但还是不可避免的需要在js中大量的操作DOM。所以一直以来，我都认为前端的逻辑和展示分离是一个骗局。

直到用了AngularJS两个星期，我才知道，我再也不用操心DOM了，我再也不用监听ajax带来的数据变化了。数据才是DOM的根源。简直就是翻身农奴把歌唱的节奏啊。

然而AngularJS也不是那么完美，现在看来还有很多问题。

### 复杂的页面组件

写前端页面，不可避免的有各种组件来组合成网页。比如AngularJS中的`controller`就负责一块网页内容的逻辑；`directive`其实本质上也是一样，更何况`controller`函数就是绑定在`directive`中的一个属性；基于`router`的`view`也同样绑定了`controller`。

所以从本质上来说，这些都可以算是`controller`系的亲兄弟，因此到底何时使用`controller`，何时选择`directive`是一个个人喜好的问题，并没有明显的官方范式可以遵循。

### 复杂的服务组件

这一点貌似网上有很多吐槽，就是关于`provider`、`factory`、`service`这三者的区别上。形式上确实有一些区别，但是通过源代码可以知道，这三者就是一个互相包装的关系，并没有本质区别，因此关于这三者如何使用也是新手比较头疼的问题。

### 复杂的作用域

Javascript本身的作用域链就够让人摸不清头脑的了，虽然AngularJS的作用域链非常类似Javascript的作用域链原理，还是被`$rootScope`、`$scope`及各种`controller`的嵌套、`view`的嵌套、`directive`中`scope`的多种声明方式甚至`directive`的各种嵌套搞得头昏脑涨，这让父子`controller`、父子`directive`之间的通信变得艰难无比，而且还很难以规划和测试。如果再遇上功能需求上的变化、页面结构的变化等，这些组件之间变换莫测的关系真是让人抓狂。

### 蹩脚的依赖注入、脏数据检查

虽然依赖注入是一件很炫酷的事情，但是对于Javascript这种弱类型的语言来说真心很难实践。AngularJS虽然一定程度上实现了，但根据参数名注入实例的方式，让uglify真的很尴尬，只能用比较不优雅的方式解决。

再说脏数据检查，简直成了AngularJS在React面前最大的痛点，虽然在`ng-repeat`中使用`track by item.id`的方式就可以为性能提升一大截，但是任然不能解决根本问题，级联式的脏数据检查很可能让一个小变化扩散到整个网页的每个角落。

性能问题同时也导致在前几年移动设备性能没有大幅提升的环境下被放大数倍，AngularJS也在移动网络的风口浪尖几年失去了领先优势。

## 前端变化风云莫测

Node和npm的出现，让前段项目的工程化提供了前所未有的便利，bower的前端依赖管理、grunt的脚本化项目管理、browserify前后端统一、gulp、webpack这些工程管理工具让前端变得越来越强大。

CoffeeScript、ES5、ES6、Babel、Typescript这些无论是语法糖、标准还是语言的出现，越来越使Javascript能够hold住复杂工程。

而就在这时，酝酿多时的Angular2驾到。

## Angular2彻头彻尾的变化

熟悉AngularJS的人，尤其是熟悉Javascript这种函数式编程的老前端们，真的很难接受Angular2。

有没有注意到，Angular2已经没有以JS结尾了，这是因为Javascript已经不再是Angular的主要语言，这在最初简直就是不可思议啊。

### 使用Dart的年代

我刚刚了解AngularJS的时候，Angular2已经有了一些思想上的雏形，那时候甚至还没有发布Angular2的Alpha版本。当时在AngularJS的讨论组里，内部人员宣布公开Angular2的全部设计过程，甚至还在Google Docs公开了他们针对Angular2（当时还被叫做AngularDart）讨论的[会议纪要（需要翻墙）](https://docs.google.com/document/d/1wVOAv8cNrBOWFpDFnAd6tm_Ej9CKXaP0wxlemi1MXMk)。

Dart是完全独立于Javascript的另一种语言，由Google发起设计实现，不像Typescript只是Javascript的超集。Dart有自己独立的编译器，曾经Google还打算把Dart的编译器集成到Chrome中，借此把Dart正式打入市场。但很快Google就放弃了这个打算，转而使用AtScript（也就是现在的Typescript）作为主要语言，现在官方文档中最完整的就是Typescript版本，当然这些都是后话。

当我刚刚认识Angular2的时候，我的内心是拒绝的。不仅原有的AngularJS的整体架构要被打散重新学习，甚至连语言就都换成不知哪里冒出来的Dart。再加上当时连AngularJS都还没掌握好，就暂时把跟进Angular2的计划搁置在一边了。

### ES5、ES6的到来

当我刚刚认识ES5/ES6的时候，我的内心，也，是拒绝的。既然是弱类型语言，既然是函数式编程，咱们就安分守己不好么？非要搞后端语言面向对象的那一套，就连函数作用域都要被`let`玩坏了。

然而历史的车轮是不会以码农的意志为转移的。ES5/ES6还没混熟，同样符合标准的Typescript也来凑热闹，而且还是坐着微软爸爸的跑车来碾压同类的。

当时Angular2由于在注解方面无法和TypeScript达成一致，转战Google的另一个亲儿子，作为Typescript超集的AtScript（甚至已经包含了ES7/ES8的一些特性）。后来微软和谷歌几经辗转，终于在语言层面[取得共识（需要翻墙）](https://twitter.com/ngconf/status/573521849780305920)，最终确定了Typescript这一官方认定语言。

### 正面肛React

老实说，目前的Angular2（目前为RC5版本）还是没有在React面前取得明显优势，虽然Angular2提供了前端一站式的服务框架，但缺少了虚拟DOM始终在React面前矮一头。

至于数据是否为双向绑定，这一点大家见仁见智。我个人认为前端的应用环境如果一味只强调数据的单向流动和Immutable特性，似乎会把大部分简单场景搞复杂。因此我还是看好现在的Angular2。

### 移动领域

React有Native，Angular2也宣称为移动而生，Ionic更是紧抱大腿，新发布Ionic2Beta版本已经支持了Angular2。

虽然Hyber App始终无法媲美Native App，但Ionic2配合Angular2作为前端插足移动领域不得不说是浑然天成的事情。

## 真的爱上了她

前段时间花了点经历了解Ionic2和Angular2，发现Typescript也不是那么难以接受，甚至还看到了后端类似Java语言的一些优美和简洁。而Typescript带来的强类型、面向对象、接口、注解、模块化等特性，也让Angular2的代码看起来如花似玉。

虽然才刚刚处于RC阶段的Angular2不能叫做相见恨晚，但内心感觉似乎错过了Angular2的一丝丝精彩。没关系，未来还很长，看好你哟。