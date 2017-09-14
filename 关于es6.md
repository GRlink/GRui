### var

JavaScript中，我们通常说的作用域是函数作用域，使用var声明的变量，无论是在代码的哪个地方声明的，都会提升到当前作用域的最顶部，这种行为叫做**变量提升**

也就是说，如果在函数内部声明的变量，都会被提升到该函数开头，而在全局声明的变量，就会提升到全局作用域的顶部。

### let

let和const都能够声明块级作用域，用法和var是类似的，let的特点是不会变量提升，只会作用在当前所在块级作用域中。

### const

声明常量，一旦声明，不可更改，而且常量必须初始化赋值。

const虽然是常量，不允许修改默认赋值，但如果定义的是对象Object，那么可以修改对象内部的属性值。

```
const和let的异同点
相同点：const和let都是在当前块内有效，执行到块外会被销毁，也不存在变量提升（TDZ），不能重复声明。
不同点：const不能再赋值，let声明的变量可以重复赋值。
```

```
在实际开发中，我们选择使用var、let还是const，取决于我们的变量是不是需要更新，通常我们希望变量保证不被恶意修改，而使用大量的const，在react中，props传递的对象是不可更改的，所以使用const声明，声明一个对象的时候，也推荐使用const，当你需要修改声明的变量值时，使用let，var能用的场景都可以使用let替代。
```



### 变量提升

在javascript中，函数及变量的声明都会被提升到函数的最顶部。也就是说，变量可以在使用后声明。
var let const中，var的声明会被提升到该作用于的顶部，但是被赋的值不会提升。let和const被赋予了一个“暂存性死区”的概念

### 暂存死区

暂存死区的意思是在当前作用域的块内，在声明变量前的区域叫做暂存死区。

### 块级作用域

在for循环中，使用var声明循环变量，会跳出循环体污染当前的函数

### 在全局作用域声明

如果在全局作用域使用let或者const声明，当声明的变量本身就是全局属性，比如closed。只会覆盖该全局变量，而不会替换它。

```
    window.closed = false
    let closed = true
    
    closed // true
    window.closed // false
```









### 函数的默认参数

在ES5中，我们给函数传参数，然后在函数体内设置默认值，如下面这种方式。

```
    function a(num, callback) {
      num = num || 6
      callback = callback || function (data) {console.log('ES5: ', data)}
      callback(num * num)
    }
    a() //ES5: 36，不传参输出默认值
    
    //你还可以这样使用callback
    a(10, function(data) {
      console.log(data * 10) // 1000， 传参输出新数值
    })
```

**而在ES6中，我们使用新的默认值写法。**

```
    function a(num = 6, callback = function (data) {console.log('ES6: ', data)}) {
      callback(num * num)
    }
    
    a() //ES6: 36， 不传参输出默认值
    
    a(10, function(data) {
      console.log(data * 10) // 1000，传参输出新数值
    })
```

**使用ES6的默认值写法可以让函数体内部的代码更加简洁优雅**

**默认值对arguments对象的影响**

我们先要了解arguments对象是什么？准确一点来说它是一个类数组对象，它存在函数内部，它将当前函数的所有参数组成了一个类数组对象。

```
    function a(num, b){
      console.log(arguments) // {"0": 6, "1": 10}
      console.log(arguments.length) // 2
    }
    
    a(6, 10) 
```

上面的输出结果看起来很正常，那么，如果我们加上参数默认值会怎样呢？

```
    function a(num = 1, b = 1){
      console.log(arguments)
    }
    a() // {} 默认值不能被arguments识别。
    a(6, 10) // {"0":6,"1":10}
```

下面我们看一下修改参数默认值对arguments的影响。

1、在ES5的非严格模式下，一开始输入的参数是1，那么可以获取到arguments[0]（表示第一个参数）全等于num，修改num = 2之后，arguments[0]也能更新到2。

```
    function a(num){
      console.log(num === arguments[0]) //true
      num = 2 //修改参数默认值
      console.log(num === arguments[0]) //true
    }
    a(1)
```

2、在ES5的严格模式下，arguments就不能在函数内修改默认值后跟随着跟新了。

```
    "use strict"; //严格模式   
    function a(num) {
      console.log(num === arguments[0]); // true
      num = 2;
      console.log(num === arguments[0]); // false
    }
    a(1);
```

**在ES6环境下，默认值对arguments的影响和ES5严格模式是同样的标准。**

**默认参数表达式**

参数不仅可以设置默认值为字符串，数字，数组或者对象，还可以是一个函数。

```
    function add() {
      return 10
    }
    function a(num = add()){
      console.log(num)
    }
    a() // 10
```

**默认参数的临时死区**

第一章我们提到了let和const什么变量的暂存死区（TDZ），默认参数既然是参数，那么也同样有暂存死区，函数的作用域是独立的，a函数不能共享b函数的作用域参数。

```
    //当初始化a时，b还没有声明，所以第一个参数对b来说就是临时死区。
    function add(a = b, b){
      console.log(a + b)
    }
    add(undefined, 2) // b is not define
```

### 无命名参数

上面说的参数都是命名参数，而无命名参数也是函数传参时经常用到的。当传入的参数是一个对象，不是一个具体的参数名，则是无命名参数。

```
    function add(object){
      console.log(object.a + object.b)
    }
    let obj = {
      a: 1,
      b: 2
    }
    add(obj) // 3
```

**不定参数的使用：**使用...（展开运算符）的参数就是不定参数，它表示一个数组。

```
    function add(...arr){
      console.log(a + b)
    }
    let a = 1,b = 2
    add(a, b) // 3
```

**不定参数的使用限制：**必须放在所有参数的末尾，不能用于对象字面量setter中。

```
    //错误的写法1
    function add(...arr, c){
      console.log(a + b)
    }
    let a = 1,b = 2,c = 3
    add(a, b, c)
    
    //错误的写法2
    let obj = {
      set add(...arr) {
      
      }
    }
```

**ES6中的构造函数Function新增了支持默认参数和不定参数。**

### 展开运算符（...）

展开运算符的作用是解构数组，然后将每个数组元素作为函数参数。

有了展开运算符，我们操作数组的时候，就可以不再使用apply来指定上下文环境了。

```
    //ES5的写法
    let arr = [10, 20, 50, 40, 30]
    let a = Math.max.apply(null, arr)
    console.log(a) // 50
    
    //ES6的写法
    let arr = [10, 20, 50, 40, 30]
    let a = Math.max(...arr)
    console.log(a) // 50
```

### 块级函数

**严格模式下：**在ES6中，你可以在块级作用域内声明函数，该函数的作用域只限于当前块，不能在块的外部访问。

```
    "use strict";
    if(true) {
      const a = function(){
      
      }
    } 
```

**非严格模式：**即使在ES6中，非严格模式下的块级函数，他的作用域也会被提升到父级函数的顶部。所以大家写代码尽量使用严格模式，避免这些奇葩情况。

### 箭头函数（=>）

```
    const arr = [5, 10]
    const s = arr.reduce((sum, item) => sum + item)
    console.log(s) // 15
    //es5会解释成
    const s = arr.reduce(function(sum,item){
      return sum+item;
    })
```

**箭头函数和普通函数的区别是：**

1、箭头函数没有this，函数内部的this来自于父级最近的非箭头函数，并且不能改变this的指向。

2、箭头函数没有super

3、箭头函数没有arguments

4、箭头函数没有new.target绑定。

5、不能使用new

6、没有原型

7、不支持重复的命名参数。

**箭头函数的简单理解**

1、箭头函数的左边表示输入的参数，右边表示输出的结果。

```
    const s = a => a
    console.log(s(2)) // 2
```

2、箭头函数中，最重要的this报错将不再成为你每天都担心的bug。

3、箭头函数还可以输出对象，在react的action中就推荐这种写法。

```
    const action = (type, a) => ({
      type: "TYPE",
      a
    })
```

4、支持立即执行函数表达式写法

```
    const test = ((id) => {
      return {
        getId() {
          console.log(id)
        }
      }
    })(18)
    test.getId() // 18
```

5、箭头函数给数组排序

```
    const arr = [10, 50, 30, 40, 20]
    const s = arr.sort((a, b) => a - b)
    console.log(s) // [10,20,30,40,50]
```

### 尾调用优化

尾调用是什么鬼？

尾调用是指在函数return的时候调用一个新的函数，由于尾调用的实现需要存储到内存中，在一个循环体中，如果存在函数的尾调用，你的内存可能爆满或溢出。

ES6中，引擎会帮你做好尾调用的优化工作，你不需要自己优化，但需要满足下面3个要求：

1、函数不是闭包

2、尾调用是函数最后一条语句

3、尾调用结果作为函数返回

**一个满足以上要求的函数如下所示：**

```
    "use strict";   
    function a() {
      return b();
    }
```

**下面的都是不满足的写法：**

```
    //没有return不优化
    "use strict";
    function a() {
      b();
    }
    
    //不是直接返回函数不优化
    "use strict";
    function a() {
      return 1 + b();
    }
    
    //尾调用是函数不是最后一条语句不优化
    "use strict";
    function a() {
      const s = b();
      return s
    }
    
    //闭包不优化
    "use strict";
    function a() {
      const num = 1
      function b() {
        return num
      }
      return b
    }
```

**尾调用实际用途——递归函数优化**

在ES5时代，我们不推荐使用递归，因为递归会影响性能。

但是有了尾调用优化之后，递归函数的性能有了提升。

```
    //新型尾优化写法
    "use strict";  
    function a(n, p = 1) {
      if(n <= 1) {
        return 1 * p
      }
      let s = n * p
      return a(n - 1, s)
    }
    //求 1 x 2 x 3的阶乘
    let sum = a(3)
    console.log(sum) // 6
```

s



