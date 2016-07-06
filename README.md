# TweenLite

## 简介
TweenLite是一个相当快速、轻量级且小巧的动画库工具，作为GreenSock Animation Platform（GSAP）的一个基础存在。TweenLite实例可以处理任意对象在一段时间内一个或多个属性的缓动。
TweenLite能够依靠极小的文件大小，单独完成绝大多数的动画工作；或者可以和高级序列工具（如：**TimelineLite**、**TimelineMax**）一起使用更简单的去创建复杂任务，与其他类的动画框架相比，为什么考虑GSAP？：

- **速度快** -极大的优化了性能，可以自行查看一些运行速度对比，在如下链接[http://www.greensock.com/js/speed.html](http://www.greensock.com/js/speed.html)
- **少有的丰富的特性设置** 
- **排序 队列 管理功能** 
- **易用性** 
- **兼容性** 
- **可扩展性** 

## 用法
可通过此视频快速构建一个快速入门上手案例[Jump Start tour ](http://greensock.com/jump-start-js).
tween函数最常用的方法是``to()``,该方法允许定义一个最终值：

    var photo = document.getElementById("photo");
	TweenLite.to(photo, 2, {width:"200px", height:"150px"});

上面的代码将缓动一个id为photo的img DOM元素的width和height属性，从当前位置经过2秒钟宽高分别变化为200和150.注意width和height属性被顶一个在一个对象里（花括号之间）。可以放置多个你想放置的属性。相关的animate css属性，你需要使用cssPlugin的css文件。此css文件包含一些系列定义好的样式名。

如果你用字符串写了第一个参数，如（``TweenLite.to("#myID", 1, {left:"100px"})``），那么TweenLite会自动给其添加一个$符号，默认采用jquery那套，如果无法加载到，将默认使用``document.querySelectorAll()``，最后再选择``document.getElementById()``（当使用此方式的时候会自动去除#号前缀），或者也可以自动以自己的选择器引擎，如：``TweenLite.selector = YOUR_SELECTOR_ENGINE;``

所以一旦TweenLite 和 cssPlugin加载之后们可以很容易动画一个元素，如下所示：

    //tween the element with ID of "myID"
	TweenLite.to("#myID", 2, {backgroundColor:"#ff0000", width:"50%", top:"100px", ease:Power2.easeInOut});
	 
	//or if jQuery is loaded, you can do more advanced selecting like all the elements with the class "myClass" like this: 
	TweenLite.to(".myClass", 2, {boxShadow:"0px 0px 20px red", color:"#FC0"});

默认情况下，tween组件会立即执行，你也可以使用``delay``延迟特殊样式或者通过``pasused``去暂停他们的初始运行，如下

    TweenLite.to(logo, 2, {left:"632px", delay:1});

target元素也可以是一个数组对象。例如，下面的缓动实例将让obj1、obj2、obj3的透明度缓动到0.5，角度旋转到45°。

    TweenLite.to([obj1, obj2, obj3], 1, {opacity:0.5, rotation:45});


## 特殊属性, 缓动方式 还有回调函数 (无须其他插件):
之前提供的属性，仅是用于创建缓动某个元素的终止值(to)或者起始值(form),而接下来这些特殊的属性会提供一些其他的功能

- **delay** : 类型 number - 动画开始之前延迟的时间秒数
- **ease** : 缓动类型（函数或者是字符串）- 你可以选择各种缓动类型来控制动画的变化速率，最好使用GreenSock里提供的缓动类型（``Linear, Power0, Power1, Power2, Power3, Power4, Quad, Cubic, Quart, Quint,Strong``）。``.easeIn, .easeOut, 和 .easeInOut``变量在TweenLite里面，你也可以加载EasePack缓动包去获取额外的缓动效果，例如（``Elastic, Back, Bounce, SlowMo, SteppedEase, Circ, Expo, 和 Sine``）
- **paused** : 类型 boolean - 如果为true，将在创建好之后立即停止动画
- **immediateRender** : 类型 boolean - 立即渲染
- **overwrite** : 类型 字符串或者整型 - 覆盖方式 默认为auto
- **onComplete** : 类型 Function - 当动画完成时出发的回调

- **onCompleteParams ** : 类型 Array - 用于传入onComplete的参数数组，例如``TweenLite.to(element, 1, {left:"100px", onComplete:myFunction, onCompleteParams:[element, "param2"]});``，如果是自引用Tween实例本身，可以使用参数``"{self}"``,像这样``onCompleteParams:["{self}", "param2"]``

- **onCompleteScope ** : 类型 Function - 当一个缓动实例从反方向再次回到起点的时候会调用该回调函数。
- **onReverseCompleteParams ** : 类型 Array  - 同onCompleteParams用法一样
- **onReverseCompleteScope ** : 类型 Function - 同onCompleteScope用法一样
- **onStart** : 类型 Function  - 当缓动实例开始的的时候会执行，当时间参数由0变为其他任意时间的时候会执行，在多次重新开始状态下，该函数有可能会被调用多次
- **onStartParams** : 类型 Array  - 同onCompleteParams用法一样
- **onStartScope** : 类型 Function - 同onCompleteScope用法一样

- **onUpdate** : 类型 Function  - 当动画持续进行过程中会一直调用
- **onUpdateParams** : 类型 Array  - 同onCompleteParams用法一样
- **onUpdateScope** : 类型 Function - 同onCompleteScope用法一样

- **useFrames ** : 类型 字符串或者整型 - 覆盖方式 默认为auto
- **lazy ** : 类型 字符串或者整型 - 覆盖方式 默认为auto
- **onOverwrite ** : 当某个元素效果覆盖发生的时候调用
- **autoCSS** : boolean 自动添加css类名，如果为false 将不做检查
- **callbackScope  ** : 该作用域会作用域全体回调函数中（如：onStart, onUpdate, onComplete等等）当设置了这个之后 之前那些作用域属性将被废弃



