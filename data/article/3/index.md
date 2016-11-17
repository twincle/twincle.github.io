Angular2的源码基于[Typescript](http://www.typescriptlang.org/)编写，但是作为前端开发人员的我们可以选择Typescript、Javascript或Dart作为开发语言。当然官方推荐使用Typescript编写出优美简洁的代码。

<!-- more -->

## 使用官方工程管理工具Angular CLI

在刚刚接触Angular2的时候，有很多背景知识需要了解。而作为新手的我们，Angular2还没混个脸熟，先去认识一大堆不认识的库，实在让我们更加头疼。因此这里推荐大家使用官方提供的Angular2工程管理工具[Angular CLI](https://cli.angular.io/)，Github项目地址[angular-cli](https://github.com/angular/angular-cli)，它可以帮助我们初始化项目，添加各种依赖，并根据最佳实践建立文件结构，让我们的关注点集中在Angular2本身。等我们对Angular2有一定了解后，再去对这些周边设施一一勘察。

> 如果你熟悉AngularJS，可能会抱怨Angular2的复杂性。没错，在AngularJS的时候，如果你只想做一个简单的学习，只要引入AngularJS库就可以，没有任何其他依赖，非常简洁明了。

### 扩展阅读

> 在使用Typescript的同时，我们就需要在项目中依赖Typescript及其编译库。同时Angular2也依赖了其他的前端开源项目，用来提供更优雅的编程体验。例如在异步编程中提供Observable实现的[ReactiveX](http://reactivex.io/)的Javascript语言扩展[rxjs](https://github.com/Reactive-Extensions/RxJS)、谷歌的另一个亲儿子，用于在异步编程中保持持久性传递的[zone.js](https://github.com/angular/zone.js/)、辅助老旧浏览器兼容ES6的[es6-shim](https://github.com/paulmillr/es6-shim)、动态样式语言[Sass](http://sass-lang.com/)、以及在项目中处理动态模块加载的[Systemjs](https://github.com/systemjs/systemjs)等。因此在项目初期配置这些依赖、创建各种依赖的配置文件等工作是非常繁琐且耗费时间的。

### 准备开发环境

#### Node.js和npm是前端开发必不可少的环境

众所周知的原因，国外的很多网站不能在国内访问，因此使用npm安装依赖库的时候，经常出现下载、安装、编译错误等，建议使用中国大陆的npm镜像库[cnpm](https://npm.taobao.org/)。

在npm下安装cnpm：

```bash
$ npm install -g cnpm --registry=https://registry.npm.taobao.org
```

cnpm库每10分钟与官方库同步一次，因此还是很有保障的。安装好cnpm后，之后所有的npm库安装均可使用`cnpm`命令替代`npm`命令。

不过貌似很多码农都有强迫症，不愿意安装cnpm。下面安装所有的npm库均使用npm命令完成，有需要的同学可以自行将`npm`更换为`cnpm`，效果都是一样的。

#### 安装angular-cli

angular-cli是Angular2官方提供的工具，可以方便的初始化项目，编译构建，打包发布，还自带一个liveload服务器方便调试。对于新手来说，angular-cli可以帮你排除其他影响，专心学习Angular2。

在cnpm下安装angular-cli

```bash
$ npm install -g angular-cli@webpack
```

> Angular2一直以来所依赖的动态模块加载库是Systemjs，但是目前最新的angular-cli（beta11版本）[声明](https://github.com/angular/angular-cli/blob/master/WEBPACK_UPDATE.md)将使用[webpack](http://webpack.github.io/)代替Systemjs。相信他们做了这个决定一定是经过慎重考虑的。
>
> 因此这里我们使用最新的webpack版angular-cli

> 个人认为目前webpack相比Systemjs要更加普遍易用，因此让我们也尽早开始熟悉webpack吧。

安装好angular-cli后，就可以在命令行中使用`ng`命令来操作我们的项目了。

```bash
$ ng -v
angular-cli: 1.0.0-beta.11-webpack.2
node: 6.2.1
os: win32 x64
```

> 不同的系统环境、node版本，显示信息可能不一样。

### 初始化项目

angular-cli提供了简单的命令帮我们初始化一个空项目，首先我们切换至项目目录，并执行`ng new hello-world`命令。该命令会在当前文件夹下创建名为`hello-world`的新文件夹，并在该文件夹下面初始化项目。

```bash
$ ng new hello-world
  create .editorconfig
  create README.md
  create src\app\app.component.css
  create src\app\app.component.html
  create src\app\app.component.spec.ts
  create src\app\app.component.ts
  ......
  Installing packages for tooling via npmBinary is fine; exiting.
```

> `ng new`命令会新建子文件夹，并在子文件夹中初始化项目。如果你想在当前文件夹初始化项目，而不是另外建立一个新的子文件夹，可以使用`ng init`命令完成。

下面我们切换到`hello-world`文件夹中看一看刚刚初始化的项目文件目录结构。

```bash
$ cd hello-world
```

## 了解Angular2的文件结构

```bash
$ ng serve
  10% building modules 1/1 modules 0 active
  *
  *
   NG Live Development Server is running on http://localhost:4200.
  *
  20315ms building modules
  24ms sealing
  16ms optimizing
  15ms basic module optimization
  ......
  Version: webpack 2.1.0-beta.18
  Time: 22790ms
                Asset       Size  Chunks             Chunk Names
       main.bundle.js    2.42 MB    0, 2  [emitted]  main
  polyfills.bundle.js     228 kB    1, 2  [emitted]  polyfills
            inline.js    4.96 kB       2  [emitted]  inline
             main.map    2.86 MB    0, 2  [emitted]  main
        polyfills.map     291 kB    1, 2  [emitted]  polyfills
           inline.map    5.13 kB       2  [emitted]  inline
           index.html  483 bytes          [emitted]
  Child html-webpack-plugin for "index.html":
           Asset    Size  Chunks       Chunk Names
      index.html  2.4 kB       0
  webpack: bundle is now VALID.
```