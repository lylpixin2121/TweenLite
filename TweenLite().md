# TweenLite() 构造函数
``TweenLite ( target:Object, duration:Number, vars:Object ) ;``

## 参数 Parameters

- **target** : Object 
此参数可以使一个单独元素，一个元素数组，一个jquery对象或者是一个css选择器字符串（会优先选择jquery或者是Sizzle），如果不存在则，降级使用document.querySelectorAll()。

- **duration** : Number 
动画的持续时间 单位是秒


- **vars** : Object
这是个对象 定义了每个属性的最终值，同时定义了一些特殊的属性 如onComplete, ease等等。例如： 将mc元素 translate3D中X轴移动到100，y轴移动到200，完成时调用callmyFunction函数，那么具体的写法是：
``new TweenLite(mc, 1, {x:100, y:200, onComplete:myFunction})``

更多参数介绍可查询[第一份文档](https://github.com/lylpixin2121/TweenLite)




