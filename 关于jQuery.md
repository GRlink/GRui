什么是jQuery？

jQuery是一个JavaScript函数库

jQuery是一个轻量级的“写的少，做的多”的JavaScript库

jQuery库包含以下功能：

-  HTML元素选取
-  HTML元素操作
-  CSS操作
-  HTML事件函数
-  JavaScript特效和动画
-  HTML DOM遍历和修改
-  AJAX
-  Utilities

jQuery兼容所有主流浏览器



### 选择器

- **标签选择器**

  ```
  $("p")
  ```

- **id选择器**

  ```
  $("#p1")
  ```

- **.class选择器**

  ```
  $(".p1")
  ```

- **更多方法**

  ```
  $("*")//选取所有元素
  $(this)//选取当前HTML元素
  $("p.test")//选取类名为test的<p>元素
  $("p:first")//选取第一个<p>元素
  $("ul li:first")//选取<ul>元素的第一个<li>元素
  $("ul li:first-child")//选取每个<ul>元素的第一个<li>元素
  $("[href]")//选取有href属性的元素
  $("a[target='_blank']")//选取有target属性值等于"_blank"的<a>标签
  $("a[target!='_blank']")//选取有target属性值不等于"_blank"的<a>标签
  $(":button")//选取所有type="button"的<input>元素和<button>元素
  $("tr:even")/选取偶数位置的<tr>元素
  $("tr:odd")/选取奇数位置的<tr>元素
  ```

  ​


|     方法     |    功能描述     |
| :--------: | :---------: |
|    bind    | 向元素添加事件处理程序 |
|  dblclick  |    双击事件     |
| mouseenter |             |
| mouseleave |             |

