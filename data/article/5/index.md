平时做网页的时候，很少会关注到网页元素的边框，最多就是简单设置一下颜色。但是当把一个元素的边框宽度设置为较大宽度之后，就打开了一个新世界。

<!-- more -->

## 容易被忽略的border

通常元素的边框都是`1px`的宽度，或者偶尔设置的宽度比较大的时候，也是四边的颜色都是一致的，看不出什么特别。

我们先来看一下下面这个`div`。其中边框宽度设置为`20px`，并且四边颜色都不同。

<style>.container{text-align: center;}.box1{border-bottom: 20px solid #fc0;border-left: 20px solid #c0f;border-right: 20px solid #0fc;border-top: 20px solid #f0c;display: inline-block;height: 20px;width: 20px;}</style><div class="container"><div class="box1"></div></div>

来看一下这个`div`的代码：

```html
<style>
  .box1 {
    border-bottom: 20px solid #fc0;
    border-left: 20px solid #c0f;
    border-right: 20px solid #0fc;
    border-top: 20px solid #f0c;
    height: 20px;
    width: 20px;
  }
</style>
<div class="box1"></div>
```

哇，神奇了有没有！从前从来没有考虑过`border`的四个边框是如何划分领地的，原来谁都不占谁便宜，45°角平均分隔。

这样就出现了纯天然无添加的CSS几何图形。

## 纯CSS多边形

上面简单的几行代码——只是把边框加宽——就很快出现了一种几何图形：梯形。下面我们来尝试着改变一些宽度高度来画出跟多图形吧。

### 三角形

如果把`div`的宽度（或高度）设置为0，梯形就会变成三角形。

<style>.box2{border-bottom: 20px solid #fc0;border-left: 20px solid #c0f;border-right: 20px solid #0fc;border-top: 20px solid #f0c;display: inline-block;height: 20px;}</style><div class="container"><div class="box2"></div></div>

下面是代码：

```html
<style>
  .box2 {
    border-bottom: 20px solid #fc0;
    border-left: 20px solid #c0f;
    border-right: 20px solid #0fc;
    border-top: 20px solid #f0c;
    height: 20px;
  }
</style>
<div class="box2"></div>
```

但这样还是有四个边，如果想要一个单独的三角形。可以把相邻的边框设置为透明色，来看一下代码。

<style>.box3{border-left: 20px solid transparent;border-right: 20px solid transparent;border-top: 20px solid #f0c;display: inline-block;}</style><div class="container"><div class="box3"></div></div>

```html
<style>
  .box3 {
    border-left: 20px solid transparent;
    border-right: 20px solid transparent;
    border-top: 20px solid #f0c;
  }
</style>
<div class="box3"></div>
```

> 这里因为设置了顶部边框为三角形，所以与底部边框`border-bottom`并没有什么关系。因此可以不设置底部边框`border-bottom`，同时也不用设置`div`的`height`属性。

如果再把边框的透明颜色交换一下，又会出现不同的三角形，比如下面这样：

<style>.box4{border-left: 20px solid #f0c;border-right: 20px solid transparent;border-top: 20px solid transparent;display: inline-block;}</style><div class="container"><div class="box4"></div></div>

```html
<style>
  .box4 {
    border-left: 20px solid #f0c;
    border-right: 20px solid transparent;
    border-top: 20px solid transparent;
  }
</style>
<div class="box4"></div>
```

如果再将不同边框的宽度设置为不一样的值，或者加上旋转属性`transform: rotate(30deg)`，就可以画出其他形状的三角形：

<style>.box5{border-left: 30px solid #f0c;border-top: 50px solid transparent;display: inline-block;}.box6{border-bottom: 80px solid #f0c;border-left: 40px solid transparent;border-right: 110px solid transparent;display: inline-block;margin: 0 20px;}.box7{border-bottom: 90px solid #f0c;border-left: 70px solid transparent;border-right: 110px solid transparent;display: inline-block;transform: rotate(290deg)}</style><div class="container"><div class="box5"></div><div class="box6"></div><div class="box7"></div></div>

> 具体代码大家可以作为练习，或者查看源代码也是可以的哟。

### 四边形

刚刚大家已经见识过纯天然梯形了，使用上面的技巧，比如调整各个边框宽度的比例，透明度，旋转角度等，各种四边形也可以实现。

<style>.box8{border-bottom: 80px solid #f0c;border-left: 0;border-right: 40px solid transparent;display: inline-block;width: 60px;}.box9{border-bottom: 80px solid #f0c;border-left: 30px solid transparent;border-right: 60px solid transparent;display: inline-block;margin: 0 20px;width: 60px;}</style><div class="container"><div class="box8"></div><div class="box9"></div></div>

```html
<style>
  .box8 {
    border-bottom: 80px solid #f0c;
    border-left: 0;
    border-right: 40px solid transparent;
    width: 60px;
  }
  .box9{
    border-bottom: 80px solid #f0c;
    border-left: 30px solid transparent;
    border-right: 60px solid transparent;
    width: 60px;
  }
</style>
<div class="box8"></div>
<div class="box9"></div>
```

通过多个四边形的组合也可以变成平行四边形。

<style>.box10{border-top: 80px solid #f0c;border-right: 0;border-left: 40px solid transparent;display: inline-block;width: 60px;}.box11{border-bottom: 80px solid #f0c;border-left: 0;border-right: 40px solid transparent;display: inline-block;width: 60px;}</style><div class="container"><div class="box10"></div><div class="box11"></div></div>

```html
<style>
  .box10 {
    border-top: 80px solid #f0c;
    border-right: 0;
    border-left: 40px solid transparent;
    width: 60px;
  }
  .box11{
    border-bottom: 80px solid #f0c;
    border-left: 0;
    border-right: 40px solid transparent;
    width: 60px;
  }
</style>
<div class="box10"></div>
<div class="box11"></div>
```

> 当然也可以使用CSS3的`transform: skewX(30deg)`来实现，这种方法只需要一个`div`就可以完成，但却不支持老版本浏览器。更何况通过多个`div`组合的方式，可以实现很多单个`div`不能实现的形状。

### 六边形

六边形需要多个`div`组合后才行出现，比如两个`div`的右边框和左边框可以这样组合：

<style>.box12{border-top: 50px solid transparent;border-right: 87px solid #fc0;border-bottom: 50px solid transparent;display: inline-block;height: 100px;}.box13{border-top: 50px solid transparent;border-left: 87px solid #fc0;border-bottom: 50px solid transparent;display: inline-block;height: 100px;}</style><div class="container"><div class="box12"></div><div class="box13"></div></div>

```html
<style>
  .box12{
    border-top: 50px solid transparent;
    border-right: 87px solid #fc0;
    border-bottom: 50px solid transparent;
    display: inline-block;
    height: 100px;
  }
  .box13{
    border-top: 50px solid transparent;
    border-left: 87px solid #fc0;
    border-bottom: 50px solid transparent;
    display: inline-block;
    height: 100px;
  }
</style>
<div class="box12"></div>
<div class="box13"></div>
```

多个六边形组成的蜂巢就留给大家做练习吧：

<style>.container3 .box14:first-child, .container4 .box14:first-child{border-left-color: transparent;}.container3 .box14:last-child, .container4 .box14:last-child{border-right-color: transparent;}.container4{margin-top: -30px;}.container3, .container4{text-align: center;}.box14{border-top: 25px solid transparent;border-left: 43px solid #fc0;border-right: 43px solid #fc0;border-bottom: 25px solid transparent;display: inline-block;height: 50px;width: 1px;}</style><div class="container3"><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div></div><div class="container4"><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div></div><div class="container4"><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div></div><div class="container4"><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div></div><div class="container4"><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div><div class="box14"></div></div>

### 小练习

让我们来做一个稍微复杂一点的练习，其实并没有什么难度，只是多一些`div`的组合而已。请使用纯CSS写出下面的图形。

> 虽然代码就贴在图形下面，但是请尽量独立完成哦。

<style>.container2{padding-top: 200px;text-align: center;}.box {border-bottom: 200px solid #000;border-left: 200px solid transparent;border-right: 200px solid transparent;display: inline-block;margin-left: -400px;margin-top: -200px;}.box31 {border-bottom-color: rgba(255, 0, 0, 0.15);border-bottom-width: 77px;border-left-width: 15px;border-right-width: 385px;}.box32 {border-bottom-color: rgba(255, 165, 0, 0.15);border-bottom-width: 141px;border-left-width: 59px;border-right-width: 341px;}.box33 {border-bottom-color: rgba(255, 255, 0, 0.15);border-bottom-width: 185px;border-left-width: 123px;border-right-width: 277px;}.box34 {border-bottom-color: rgba(0, 255, 0, 0.15);}.box35 {border-bottom-color: rgba(0, 0, 255, 0.15);border-bottom-width: 185px;border-left-width: 277px;border-right-width: 123px;}.box36 {border-bottom-color: rgba(43, 0, 255, 0.15);border-bottom-width: 141px;border-left-width: 341px;border-right-width: 59px;}.box37 {border-bottom-color: rgba(87, 0, 255, 0.15);border-bottom-width: 77px;border-left-width: 385px;border-right-width: 15px;}.box38 {border-radius: 50%;border: 200px solid rgba(204, 204, 204, 0.2);border-right-color: transparent;border-bottom-color: transparent;transform: rotate(45deg);margin-bottom: -200px;margin-left: 0;}</style><div class="container2"><div class="box box38"></div><div class="box box34"></div><div class="box box33"></div><div class="box box35"></div><div class="box box32"></div><div class="box box36"></div><div class="box box31"></div><div class="box box37"></div></div>

```html
<style>
  .box {
    border-bottom: 200px solid #000;
    border-left: 200px solid transparent;
    border-right: 200px solid transparent;
    display: inline-block;
    margin-left: -400px;
    margin-top: -200px;
  }
  .box31 {
    border-bottom-color: rgba(255, 0, 0, 0.15);    
    border-bottom-width: 77px;
    border-left-width: 15px;
    border-right-width: 385px;
  }
  .box32 {
    border-bottom-color: rgba(255, 165, 0, 0.15);
    border-bottom-width: 141px;
    border-left-width: 59px;
    border-right-width: 341px;
  }
  .box33 {
    border-bottom-color: rgba(255, 255, 0, 0.15);    
    border-bottom-width: 185px;
    border-left-width: 123px;
    border-right-width: 277px;
  }
  .box34 {
    border-bottom-color: rgba(0, 255, 0, 0.15);
  }
  .box35 {
    border-bottom-color: rgba(0, 0, 255, 0.15);
    border-bottom-width: 185px;
    border-left-width: 277px;
    border-right-width: 123px;
  }
  .box36 {
    border-bottom-color: rgba(43, 0, 255, 0.15);
    border-bottom-width: 141px;
    border-left-width: 341px;
    border-right-width: 59px;
  }
  .box37 {
    border-bottom-color: rgba(87, 0, 255, 0.15);
    border-bottom-width: 77px;
    border-left-width: 385px;
    border-right-width: 15px;
  }
  .box38 {
    border: 200px solid rgba(204, 204, 204, 0.2);
    border-bottom-color: transparent;
    border-radius: 50%;
    border-right-color: transparent;
    margin-bottom: -200px;
    margin-left: 0;
    transform: rotate(45deg);
  }
</style>
<div class="box box38"></div>
<div class="box box34"></div>
<div class="box box33"></div>
<div class="box box35"></div>
<div class="box box32"></div>
<div class="box box36"></div>
<div class="box box31"></div>
<div class="box box37"></div>
```

## 纯CSS圆形

### 圆形、扇形、环形

在CSS2.X时代，想要用CSS画出圆形或者圆角，是一项技术活。根据需求的不同还有多种不同的技术，例如使用九宫格贴图或`div`画圆角像素的方式等。

现在我们有了CSS3，可以非常方便的画出圆形和圆角，让我们来享受一下CSS3给我们带来的便利吧。

<style>.circle1 {border: 50px solid #fc0;  border-radius: 50%;  display: inline-block;margin: 0 20px;}.circle2 {  border: 50px solid #fc0;  border-bottom-color: #0cf;  border-left-color: #c0f;  border-radius: 50%;  border-top-color: #ccc;  display: inline-block;margin: 0 20px;}.circle3 {  border: 25px solid #fc0;  border-bottom-color: #0cf;  border-left-color: #c0f;  border-radius: 50%;  border-top-color: #ccc;  display: inline-block;  height: 50px; margin: 0 20px; width: 50px;}</style><div class="container"><div class="circle1"></div><div class="circle2"></div><div class="circle3"></div></div>

简单的几行代码，可以轻松的画出圆形、扇形、环形等。

```html
<style>
.circle1 {
  border: 50px solid #fc0;
  border-radius: 50%;
  display: inline-block;
}
.circle2 {
  border: 50px solid #fc0;
  border-bottom-color: #0cf;
  border-left-color: #c0f;
  border-radius: 50%;
  border-top-color: #ccc;
  display: inline-block;
}
.circle3 {
  border: 25px solid #fc0;
  border-bottom-color: #0cf;
  border-left-color: #c0f;
  border-radius: 50%;
  border-top-color: #ccc;
  display: inline-block;
  height: 50px;
  width: 50px;
}
</style>
<div class="circle1"></div>
<div class="circle2"></div>
<div class="circle3"></div>
```

### 椭圆

当一个`div`的宽度和高度不同的时候，就可以画出椭圆形。比如下面这样

<style>.circle4{border: 30px solid #ccc;border-radius: 50%;display: inline-block;width: 90px;height: 50px;}</style><div class="container"><div class="circle4"></div></div>

```html
<style>
.circle4 {
  border: 30px solid #ccc;
  border-radius: 50%;
  width: 90px;
  height: 50px;
}
</style>
<div class="circle4"></div>
```

下面让我们尝试一下使用`border`来控制椭圆的形状。

<style>.circle5{border: 100px solid #ccc;border-left: none;border-radius: 50%;border-right-color: #fc0;border-top-color: #c0f;display: inline-block;}</style><div class="container"><div class="circle5"></div></div>

当我只是简单地将左边框设置为`none`的时候，神奇的事情又发生了，右边框还算正常，但是上边框和下边框完全变成了奇怪的形状。

```html
<style>
.circle5 {
  border: 100px solid #ccc;
  border-left: none;
  border-radius: 50%;
  border-right-color: #fc0;
  border-top-color: #c0f;
}
</style>
<div class="circle5"></div>
```

这样我们就很方便的得到了椭圆的一部分。

<style>.circle6{border: 100px solid #fff;border-left: none;border-radius: 50%;border-top-color: #c0f;display: inline-block;}</style><div class="container"><div class="circle6"></div></div>

如果把各个边框的宽度都设置为不一样的值，也会得到各种奇葩形状。

<style>.circle7{border-bottom: 20px solid #ccc;border-left: 50px solid #0fc;border-radius: 50%;border-right: 70px solid #f0c;border-top: 100px solid #cf0;}.circle8{border-bottom: 130px solid #ccc;border-left: 50px solid #0fc;border-radius: 50%;border-right: 70px solid #f0c;border-top: 100px solid #cf0;}</style><div class="container"><div class="circle7"></div><div class="circle8"></div></div>

谁能告诉我这尼玛都是些什么鬼  w(ﾟДﾟ)w   。。。