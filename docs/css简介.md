# CSS

> 层叠样式表(英文全称：Cascading Style Sheets)是一种用来表现[HTML](https://baike.baidu.com/item/HTML)（[标准通用标记语言](https://baike.baidu.com/item/标准通用标记语言/6805073)的一个应用）或[XML](https://baike.baidu.com/item/XML)（标准通用标记语言的一个子集）等文件样式的计算机语言。CSS不仅可以静态地修饰网页，还可以配合各种脚本语言动态地对网页各元素进行格式化。 [1] 
>
> CSS 能够对网页中元素位置的排版进行像素级精确控制，支持几乎所有的字体字号样式，拥有对网页对象和模型样式编辑的能力。
>
> 层叠样式:网页中最终展示的效果,就像透明的色彩卡片一层一层叠加，最终展示的才是给我们的效果。
>
> 页面的图片的宽,高,形状,位置,效果....达到最终的效果。

![img](_media/u=2105690071,2567005152&fm=26&gp=0.jpg)

:kissing_smiling_eyes: 没有使用css的效果

![img](_media/timg.jpg)

:slightly_smiling_face: 使用了css的效果

<img src="_media/image-20201014142652228.png" width="300px">

[css官方地址](https://www.w3.org/TR/)

> **css的组成**:   
>
> + 选择器: 选中页面中的哪一个，或者那些符合条件的元素给添加样式
> + 属性: 给页面中的元素添加那些样式,宽,高,颜色,边框,背景.....
> + 属性的值: 赋给演示需要的值。

> **浏览器读取编译css的顺序:**
>
>浏览器读取css选择器的顺序是从右到左

## 1.Css的基本的使用方式

+ 选择器
+ 声明块
  + 声明
    + 属性
    + 值

![image-20201015094122277](_media/image-20201015094122277.png)

### 1.1 Css的三种使用方式

+ 行内样式表  只能正对当前的元素使用
+ 内部样式表 在页面的head标签内部使用，对页面多个元素的样式进行调整
+ 外部样式表  在外部的css文件中书写，针对于多个页面的样式进行书写规范。

> 行内样式表 : 在开始标签内部使用style属性声明添加样式,在添加样式的属性和赋值 style="color:red;font-size:24px;"属性之间使用分号相隔。

```html
<p style="color: lightcoral; font-size: 20px">
      层叠样式表(英文全称：Cascading Style
      Sheets)是一种用来表现HTML（标准通用标记语言的一个应用）或XML（标准通用标记语言的一个子集）等文件样式的计算机语言。CSS不仅可以静态地修饰网页，还可以配合各种脚本语言动态地对网页各元素进行格式化。
      [1] CSS
      能够对网页中元素位置的排版进行像素级精确控制，支持几乎所有的字体字号样式，拥有对网页对象和模型样式编辑的能力。
      层叠样式:网页中最终展示的效果,就像透明的色彩卡片一层一层叠加，最终展示的才是给我们的效果。
      页面的图片的宽,高,形状,位置,效果....达到最终的效果
    </p>
```

> 内部样式表

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      div {
        width: 600px;
        height: 400px;
        border: 1px solid red;
        margin: 0 auto;
      }
    </style>
  </head>
  <body>
    <div></div>
  </body>
</html>

```

> :smile: 外部样式表:
>
> ​	将css样式表编写到外部的css文件中，在通过link进行引用。
>
> ​	link引入的外部样式表可以在多个页面进行复用，减少开发的时间。
>
> ​	:exclamation: 外部的css样式表，可以使用浏览器的缓存机制，加快网页的加载速度，提升用户的体验。

```html
/*style.css*/
div {
        width: 600px;
        height: 400px;
        border: 1px solid red;
        margin: 0 auto;
      }
```

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
      <!---link  引入外部的连接资源->
      <!--引入外部的css文件 rel声明是层叠样式表  href 引入的资源 可以是本地的 可以使远程的-->
    <link rel="stylesheet" href="style.css">
      <!--link也可以用来引入外部的网页图标-->
      <link rel="icon" href="//www.jd.com/favicon.ico"mce_href="//www.jd.com/favicon.ico" type="image/x-icon"/>
  </head>
  <body>
    <div></div>
  </body>
</html>

```

### 1.2 Css三种使用方式的优先级别

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="style.css" />
    <style>
      div {
        width: 200px;
        height: 300px;
        border: 1px solid green;
      }
    </style>
  </head>
  <body>
    <div style="width: 300px;height: 300px;border: 2px solid pink;"></div>
  </body>
</html>

```

> 我们在页面使用样式表规则:
>
> 1. 先在外部的样式表规定多个页面的相同元素的样式
> 2. 在在页面内使用内部样式表去补充页面的样式
> 3. 针对某一个元素使用行内样式表单独调试
>
> 页面加载代码的顺序是从上而下，从左到右的顺序。所以css优先级根据覆盖的最终效果是:
>
> ​		**行内样式表 > 内部样式表>外部样式表**
>
> :heavy_exclamation_mark: 行内样式表在实际开发中很少使用，修改项目的时候很麻烦。但也是不是绝对的，只是不推荐使用。

## 2.Css选择器

[CSS3选择器规范地址](https://www.w3.org/TR/2011/REC-css3-selectors-20110929/)

[css3最新选择器规范地址](https://www.w3.org/TR/selectors )

### 2.1 Css基本选择器

1. **通配符选择器**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* *代表通配符，body中的所有的元素 */
      * {
        /* color默认代表文字的颜色 */
        color: red;
      }
    </style>
  </head>
  <body>
    <p>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>

    <section>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </section>

    <div>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </div>
  </body>
</html>

```

2. **元素选择器****

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 元素选择器就是根据页面中标签的名称进行选择器，选择到的是页面中所有的选择器名称的标签元素 */
      p {
        color: red;
      }
      section {
        color: green;
      }
    </style>
  </head>
  <body>
    <p>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <p>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>

    <section>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </section>
  </body>
</html>

```

3. **id选择器**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 元素选择器就是根据页面中标签的名称进行选择器，选择到的是页面中所有的选择器名称的标签元素 */
      p {
        color: red;
      }
      /* id选择器：
            在元素的开始标签中通过id=""来对当前的元素进行标识，再通过#+id定义的名称值 进行选择标记的标签进行样式定义
            id的值必须是唯一的，在一个页面中只能有一个。
       */
      #p {
        color: pink;
      }
      section {
        color: green;
      }
    </style>
  </head>
  <body>
    <p>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <p id="p">
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>

    <section>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </section>
    </div>
  </body>
</html>

```

4. **class选择器**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 类选择器可以为多个同名的元素定义相同的样式,这个也是我们在实际开发中使用最多的。
          在元素的开始标签中使用class=""进行命名标记，在使用.+class命名的值 进行样式定义
        同一个元素我们可以定义多个class 可以组合定义这个元素的样式，在后边的学习和框架中我们会经常见到
       */
      .one {
        color: gold;
      }
        .two{
            font-size:24px;
        }
      section {
        color: green;
      }
    </style>
  </head>
  <body>
    <p>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <p id="p">
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <p class="one two">
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <p class="one">
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
      <section class="one">
          Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
      </section>
  </body>
</html>

```

5. **属性选择器**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 属性选择器: 
          element[properties='']{}
          第一种: 没有元素 那就是所有具有哪一个属性的元素会被选中
          第二种: 有元素那就是选择哪一类元素中具有这个属性的元素会被选中
       */
      [name*='s'] {
      }
      /* element[properties='']{}
        等于 所以属性值必须是全写
        元素的属性值是text的元素被选中 
      */
      input[type='text'] {
        background-color: pink;
      }
      /* 
      element[properties^='']{}
        ^ 所以属性值必须是包含属性名称的开始字母 一个或者多个
      元素的属性值以什么开头 */
      input[type^='pas'] {
        background-color: pink;
      }
      /*
      element[properties$='']{}
        $ 所以属性值必须是包含属性名称的结尾的字母 一个或者多个
      */
      input[type$='ord'] {
        background-color: pink;
      }
      /*
      element[properties*='']{}
        * 所以属性值必须是包含属性名称的字母   一个或者多个
      */
      input[type*='ssw'] {
        background-color: pink;
      }
    </style>
  </head>
  <body>
    <span name="myspan">
      Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架。
    </span>
    <input type="text" name="usernamew" /><br />
    <input type="password" name="passord" />
  </body>
</html>

```

### 2.2 CSS分组选择器

1. 交集选择器

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="style.css" />
    <style>
      /* 先选中.one的元素再在p元素中查找所以是两种选择器的交集 */
      p.one {
        color: red;
      }
    </style>
  </head>
  <body>
    <p>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <p class="one">
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
  </body>
</html>

```

2. 并集选择器

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="style.css" />
    <style>
      /* 并集选择器: 各个选择器之间使用逗号隔开,所有的被选中的元素的样式,所以是并集 */
      p.one,
      section {
        color: red;
      }
    </style>
  </head>
  <body>
    <p>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <p class="one">
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </p>
    <section>
      Vue (读音 /vjuː/，类似于 view)
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动。
    </section>
  </body>
</html>

```

### 2.3 css关系选择器

1. 包含选择器 空格隔开
2. 子元素选择器  e > f
3. 相邻元素选择器 e + f
4. 兄弟选择器 e ~ f

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <link rel="stylesheet" href="style.css" />
    <style>
      /*
        祖先元素:
        - 直接或者间接包含后代元素的元素叫做祖先元素
        - 祖先元素可以有一个或者个子元素，孙子元素，孙子的孙子元素...
        父元素:
        - 直接包含子元素的元素叫父元素
        子元素: >
        - 直接被父元素包含的元素是子元素
        后代元素:
        - 直接或者间接被父元素包含的元素是后代元素
        - 子元素也是后代元素
        兄弟元素: e~f
        - e同级父元素中的f元素，后代元素中的f不会被选择
        相邻元素: e+f
        - e父级元素中和e相邻的f元素只能是相邻的第一个f元素

      */
      /* section 是祖先元素也是父元素
        article 是祖先元素也是父元素,也是section的子元素
        p 元素是子元素，也是后代元素
        包含选择器: 包含在section article 中的p元素
      */
      section article p {
        color: red;
      }

      /*
        后代选择器: 
          可以是子元素
          也可以是子孙元素
      */

      section span {
        background-color: lawngreen;
      }
      /*子元素选择器:
        p > span ：
      */

      p > span {
        color: green;
      }
      /*兄弟选择器: 
      .one 后边的 p元素都会被选中
      */
      .one ~ p {
        font-size: 24px;
      }

      /*
        相邻选择器: 
        article 后边紧挨着的第一个aside元素
      */
      article + aside {
        color: green;
        font-size: 28px;
      }
    </style>
  </head>
  <body>
    <section>
      <article>
        <p class="one">
          <span>Vue (读音 /vjuː/，类似于 view)</span>
          是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
          被设计为可以自底向上逐层应用。Vue
          的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
          也完全能够为复杂的单页应用提供驱动
        </p>
        <p>
          我们已经成功创建了第一个 Vue
          应用！看起来这跟渲染一个字符串模板非常类似，但是 Vue
          在背后做了大量工作。现在数据和 DOM
          已经被建立了关联，所有东西都是响应式的。我们要怎么确认呢？打开你的浏览器的
          JavaScript 控制台 (就在这个页面打开)，并修改 app.message
          的值，你将看到上例相应地更新。
        </p>
        <p>
          我们已经成功创建了第一个 Vue
          应用！看起来这跟渲染一个字符串模板非常类似，但是 Vue
          在背后做了大量工作。现在数据和 DOM
          已经被建立了关联，所有东西都是响应式的。我们要怎么确认呢？打开你的浏览器的
          JavaScript 控制台 (就在这个页面打开)，并修改 app.message
          的值，你将看到上例相应地更新。
        </p>
      </article>
      <aside>
        尝试 Vue.js 最简单的方法是使用 Hello World
        例子。你可以在浏览器新标签页中打开它，跟着例子学习一些基础用法。或者你也可以创建一个
        .html 文件
      </aside>
      <aside>
        尝试 Vue.js 最简单的方法是使用 Hello World
        例子。你可以在浏览器新标签页中打开它，跟着例子学习一些基础用法。或者你也可以创建一个
        .html 文件
      </aside>
    </section>
  </body>
</html>

```

![image-20201015115418581](_media/image-20201015115418581.png)

### 2.4 css伪选择器

> **伪类**：同一个标签，根据其**不同的种状态，有不同的样式**。这就叫做“伪类”。伪类用冒号来表示。

#### 2.4.1 伪类选择器

1. 静态伪类选择器

+ :link

+ :visited

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 超链接未被点击之前的样式:  */
      a:link {
        font-size: 20px;
        color: green;
        text-decoration: none;
      }
      /* 改变浏览器默认对超链接显示的颜色 */
      a:-webkit-any-link {
        color: gold;
      }
      /* visited: 访问过url的页面以后 */
      a:visited {
        color: pink;
      }
    </style>
  </head>
  <body>
    <a href="https://www.jd.com">百度一下,你就知道</a>
  </body>
</html>

```

2. 动态伪类选择器

+ :hover  鼠标悬停时的样式
+ :active  设置元素在被用户激活（在鼠标点击与释放之间发生的事件）时的样式。
+ :focus  设置对象在成为输入焦点（该对象的onfocus事件发生）时的样式。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 超链接未被点击之前的样式:  */
      a:link {
        font-size: 20px;
        color: green;
        text-decoration: none;
      }
      /* 改变浏览器默认对超链接显示的颜色 */
      a:-webkit-any-link {
        color: gold;
      }
      /* visited: 访问过url的页面以后 */
      a:visited {
        color: pink;
      }
      /*鼠标放置在元素之上，悬停的状态时定义的样式*/
      a:hover {
        color: brown;
      }
      /* 鼠标左键按下未松开的样式   */
      a:active {
        color: aqua;
      }
      /* 焦点聚集是的状态 */
      input:focus {
        background-color: blue;
      }
    </style>
  </head>
  <body>
    <a href="https://www.jd.com">百度一下,你就知道</a>
    <input type="text" />
  </body>
</html>

```

> :exclamation: **设置超链接a在未被访问前的样式。**
>
> - 如果需要给超链接定义：访问前，鼠标悬停，当前被点击，已访问这4种伪类效果，而又没有按照一致的书写顺序，不同的浏览器可能会有不同的表现 
>
> - 超链接的4种状态，需要有特定的书写顺序才能生效。
>
>   `a:link {} `
>
>   `a:visited {} `
>
>   `a:hover {} `
>
>   `a:active {}`

3. 目标伪类选择器

+ :tartget   
  + URL后面跟锚点#，指向文档内某个具体的元素。这个被链接的元素就是目标元素(target 		element)，:target选择器用于选取当前活动的目标元素。

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
     /* 当点击锚点连接的时候 #one的div会被命中, 那么当前样式就会触发*/
      p:target {
        color: lightgreen;
      }
    </style>
  </head>
  <body>
    <a href="#one">第一章元素</a>
    <p id="one">
      我们已经成功创建了第一个 Vue
      应用！看起来这跟渲染一个字符串模板非常类似，但是 Vue
      在背后做了大量工作。现在数据和 DOM
      已经被建立了关联，所有东西都是响应式的。我们要怎么确认呢？打开你的浏览器的
      JavaScript 控制台 (就在这个页面打开)，并修改 app.message
      的值，你将看到上例相应地更新。
    </p>
    <p class="two">
      我们已经成功创建了第一个 Vue
      应用！看起来这跟渲染一个字符串模板非常类似，但是 Vue
      在背后做了大量工作。现在数据和 DOM
      已经被建立了关联，所有东西都是响应式的。我们要怎么确认呢？打开你的浏览器的
      JavaScript 控制台 (就在这个页面打开)，并修改 app.message
      的值，你将看到上例相应地更新。
    </p>
  </body>
</html>

```

4. 语言伪类选择器

+ :lang   匹配使用特殊语言的元素

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      p:lang(zh-cmn-Hans) {
        color: #f00;
      }
      p:lang(en) {
        color: #090;
      }
    </style>
  </head>
  <body>
    <p lang="zh-cmn-Hans">大段测试文字</p>
    <p lang="en">english</p>
  </body>
</html>

```

![image-20201015151722004](_media/image-20201015151722004.png)

5. 元素状态伪类选择器

+ :checked   已经选中的元素
+ :enable   可用的元素
+ :disable   被禁用的元素

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 被选择中的input元素 */
      input:checked + span {
        background-color: lightcoral;
      }
      /* 可点击有效果的 button元素 */
      button:enabled {
        background-color: lawngreen;
      }
      /* 被禁用的button元素 */
      button:disabled {
        background-color: lightsalmon;
      }
    </style>
  </head>
  <body>
    <input type="checkbox" name="sports" /><span>篮球</span>
    <input type="checkbox" name="sports" checked /><span>羽毛球</span>
    <input type="checkbox" name="sports" /><span>足球</span>
    <hr />
    <button>点击登录</button> <button disabled>点击注册</button>
  </body>
</html>

```

6. 结构伪类选择器

+ :nth-child 
  + odd  奇数
  + even  偶数
+ :nth-last-child
+ :first-letter 第一个字母
+ :first-line第一行
+ :selection表示选中的内容
+ :nth-of-type
+ :nth-last-of-type
+ :first-child   父元素中的第一个子元素,必须包含在一个父元素中
+ :last-child  父元素中的最后一个子元素,必须包含在一个父元素中
+ :only-child  父元素中仅有的一个子元素
+ :first-of-type
+ :last-of-type
+ :root  匹配元素所有在文档的根元素
+ :empty  **匹配没有任何子元素（包括text节点）的元素E**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* e:first-child e元素必须是 */
      li:first-child {
        color: lightcoral;
      }
      li:last-child {
        color: aqua;
      }
      /* 父元素的第n个子元素 n从1开始  */
      li:nth-child(2) {
        color: lightseagreen;
      }
      /*  li:nth-child(odd) {
        color: lightseagreen;
      }
      li:nth-child(even) {
        color: lightseagreen;
      } */
      /*同类型中的兄弟元素的第n个元素 n从零开始*/
      li:nth-last-of-type(3) {
        color: pink;
      }
    </style>
  </head>
  <body>
    <ul>
      <li>Hello World 1</li>
      <li>Hello World 2</li>
      <li>Hello World 3</li>
      <li>Hello World 4</li>
      <li>Hello World 5</li>
      <li>Hello World 6</li>
    </ul>
  </body>
</html>

```

7. 否定伪类选择呢器

+ E:not(F) 匹配所有除F外的E元素

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /* 排除 (选择器)的其余的元素 */
      p:not(:last-child) {
        color: lightcoral;
      }
    </style>
  </head>
  <body>
    <p class="one">
      <span>Vue (读音 /vjuː/，类似于 view)</span>
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动
    </p>
    <p>
      我们已经成功创建了第一个 Vue
      应用！看起来这跟渲染一个字符串模板非常类似，但是 Vue
      在背后做了大量工作。现在数据和 DOM
      已经被建立了关联，所有东西都是响应式的。我们要怎么确认呢？打开你的浏览器的
      JavaScript 控制台 (就在这个页面打开)，并修改 app.message
      的值，你将看到上例相应地更新。
    </p>
  </body>
</html>

```

#### 2.4.2 伪元素选择器

> **设置在对象前（依据对象树的逻辑结构）发生的内容。用来和[content](../../properties/content/content.htm)属性一起使用，并且必须定义content属性**
>
> - CSS3将伪对象选择符(Pseudo-Element Selectors)前面的*单个冒号(:)修改为双冒号(::)*用以区别伪类选择符(Pseudo-Classes  Selectors)，但以前的写法仍然有效。
> - 使用伪元素清除盒子浮动
> - 使用伪元素插入图片,icon

+ ::after
+ ::before

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      span::before {
        content: 'Hello World';
        color: lightcoral;
      }
      span::after {
        content: '------------';
        color: green;
      }
    </style>
  </head>
  <body>
    <span>
      Vue (读音 /vjuː/，类似于 view) 是一套用于构建用户界面的渐进式框架
    </span>
  </body>
</html>

```

###  :imp: 2.5 Css选择器的权重

> 我们可以通过给选择器添加**权值**和**权级**这两个概念的方式来更好的理解选择器的权重
> （注意:“权值”和“权级”的概念是为了更好的理解权重而提出的，并不是真是存在的)

| 选择器         | 表达式或示例                                                 | 说明                                                         | 权重 |
| -------------- | ------------------------------------------------------------ | ------------------------------------------------------------ | ---- |
| ID选择器       | #aaa                                                         |                                                              | 0100 |
| 类选择器       | .aaa                                                         |                                                              | 0010 |
| 标签选择器     | h1                                                           | 元素的tagName                                                | 0001 |
| 属性选择器     | [title]                                                      | [详见这里](http://www.cnblogs.com/rubylouvre/archive/2009/10/27/1590102.html) | 0010 |
| 相邻选择器     | selecter + selecter                                          | 拆分为两个选择器再计算                                       |      |
| 兄长选择器     | selecter ~ selecter                                          | 拆分为两个选择器再计算                                       |      |
| 亲子选择器     | selecter > selecter                                          | 拆分为两个选择器再计算                                       |      |
| 后代选择器     | selecter selecter                                            | 拆分为两个选择器再计算                                       |      |
| 通配符选择器   | *                                                            |                                                              | 0000 |
| 各种伪类选择器 | 如:link， :visited， :hover， :active， :target， :root， :not等 |                                                              | 0010 |
| 各种伪元素     | 如::first-letter,::first-line,::after,::before,::selection   |                                                              | 0001 |
| ！important    |                                                              | `!important` 用来提升优先级，加了这句的样式的优先级是最高的。 |      |

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /*当前选择器的权重运算结果是: 0001 + 0001 = 0010 */
      p span {
        color: red;
      }
      /*当前选择器的权重是: 0001 */
      span {
        color: green;
      }

      /* 虽然我们说浏览器加载代码的顺序是从上到下，从左到右，但是权重大的选择器会被使用 */
    </style>
  </head>
  <body>
    <p class="one">
      <span>Vue (读音 /vjuː/，类似于 view)</span>
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动
    </p>
  </body>
</html>

```



![image-20201015163040597](_media/image-20201015163040597.png)

> 在次添加权重

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Document</title>
    <style>
      /*当前选择器的权重运算结果是: 0001 + 0001 = 0010 */
      p span {
        color: red;
      }
      /*当前选择器的权重是: 0001 + 0010 + 0001 = 0100 */
      p.one span {
        color: pink;
      }
      /*当前选择器的权重是: 0001 */
      span {
        color: green;
      }

      /* 虽然我们说浏览器加载代码的顺序是从上到下，从左到右，但是权重大的选择器会被使用,(分组选择器是单独计算的,不包括在内) */
    </style>
  </head>
  <body>
    <p class="one">
      <span>Vue (读音 /vjuː/，类似于 view)</span>
      是一套用于构建用户界面的渐进式框架。与其它大型框架不同的是，Vue
      被设计为可以自底向上逐层应用。Vue
      的核心库只关注视图层，不仅易于上手，还便于与第三方库或既有项目整合。另一方面，当与现代化的工具链以及各种支持类库结合使用时，Vue
      也完全能够为复杂的单页应用提供驱动
    </p>
  </body>
</html>

```

![image-20201015163347099](_media/image-20201015163347099.png)

### 2.5 样式的继承

> 样式的继承:我们要给一个元素设置样式也同时会应用到他的后代元素上
>
> 继承是发生在祖先和后代元素之间的
>
> 注意:并不是所有的样式都会被继承
>
> + 背景相关
> + 布局相关
> + ....

![image-20201017145852016](_media/image-20201017145852s016.png)

## 3. Css盒子模型

> 所谓盒子模型（Box Model）就是把HTML页面中的元素看作是一个矩形的盒子，也就是一个盛装内容的容器。每个矩形都由元素的**内容(content)、内边距（padding）、边框（border）和外边距（margin）**组成。
>
> 所有的文档元素（标签）都会生成一个矩形框，我们成为元素框（element box），它描述了一个文档元素再网页布局汇总所占的位置大小。因此，**每个盒子除了有自己大小和位置外，还影响着其他盒子的大小和位置。**

![img](_media/dsdsdsdfrr.png)

![img](_media/3247286891&fm=26&gp=0.jpg)

### 3.1 边框(Border)

> border 属性来定义盒子的边框，该属性包含3个子属性：
>
> + border-style(边框样式)
>
> + border-color(边框颜色)
>
> + border-width(边框宽度)
> + border-radius 边框圆角
> + border-imge 边框图片
> + box-shandow 边框阴影

边框分为四边，所以有了:

+ border-bottom 下边框 
+ border-top上边框
+ border-left 做边框
+ border-right 右边框

1. **Border-style**

边框样式定义边框的风格，常用的属性值有:

+ none  没有边框 忽略所有的边框宽度和样式，除非是border-image
+ solid 边框是实线
+ dashed 边框是虚线
+ dotted 边框为点线
+ double 边框是双实线
+ groove  3D凹槽轮廓线
+ outset 3D凸边轮廓

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div {
        width: 300px;
        height: 300px;
        border-style: double;
        border-color: red;
        border-width: 5px;
      }
    </style>
  </head>
  <body>
    <div></div>
  </body>
</html>

```

2. **Border-color**
3. **Border-width**

![image-20201018100546410](_media/image-20201018100546410.png)

4. **Border-radius**(边框圆角)

> boder-radius:左上角 右上角 右下角 左下角
>
> + 取值:
>   + 用长度值设置对象的圆角半径长度。不允许负值 
>   + 用百分比设置对象的圆角半径长度。不允许负值
>
> - 水平半径：如果提供全部四个参数值，将按上左(top-left)、上右(top-right)、下右(bottom-right)、下左(bottom-left)的顺序作用于四个角。 
> - 如果只提供一个，将用于全部的于四个角。 
> - 如果提供两个，第一个用于上左(top-left)、下右(bottom-right)，第二个用于上右(top-right)、下左(bottom-left)。 
> - 如果提供三个，第一个用于上左(top-left)，第二个用于上右(top-right)、下左(bottom-left)，第三个用于下右(bottom-right)。 
> - 垂直半径也遵循以上4点。 

![img](_media/1623059727&fm=26&gp=0.jpg)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div:last-child {
        width: 300px;
        height: 300px;
        border-top: 5px solid green;
        border-left: 5px dashed pink;
        border-right: 5px double gold;
        border-bottom: 10px groove blue;
        border-radius: 10px 15px 20px 30px;
      }
    </style>
  </head>
  <body>
    <div></div>
  </body>
</html>

```

5. **盒子阴影**

> box-shandow: 阴影的水平偏移距离 阴影垂直偏移距离  阴影的模糊程度  阴影的颜色

| 说明       |                                                              |
| :--------- | ------------------------------------------------------------ |
| *h-shadow* | 必需的。水平阴影的位置。允许负值                             |
| *v-shadow* | 必需的。垂直阴影的位置。允许负值                             |
| *blur*     | 可选。模糊距离                                               |
| *spread*   | 可选。阴影的大小                                             |
| *color*    | 可选。阴影的颜色。在[CSS颜色值](https://www.runoob.com/cssref/css_colors_legal.aspx)寻找颜色值的完整列表 |
| inset      | 可选。从外层的阴影（开始时）改变阴影内侧阴影                 |

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div:first-child {
        width: 300px;
        height: 300px;
        background: lawngreen;
        box-shadow: 5px 5px 10px green;
      }
      div:last-child {
        margin-top: 20px;
        width: 300px;
        height: 300px;
        background: lightcoral;
        box-shadow: 0px 0px 10px red inset;
      }
    </style>
  </head>
  <body>
    <div></div>
    <div></div>
  </body>
</html>

```

![image-20201018101744289](_media/image-20201018101744289.png)

### 3.2 内边距(padding)

> 内边距: 边框和内容之间的距离
>
> + 取值:
>   + 长度指定 不允许负值
>   + 百分比指定 参照with进行计算  不允许负值
>
> + 如果提供全部四个参数值，将按上、右、下、左的顺序作用于四边。 
> + 如果只提供一个，将用于全部的四边。 
> + 如果提供两个，第一个用于上、下，第二个用于左、右。 
> + 如果提供三个，第一个用于上，第二个用于左、右，第三个用于下

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div {
        width: 400px;
        height: 300px;
        border: 2px solid red;
        padding: 20px;
      }
      p {
        border: 1px solid green;
      }
    </style>
  </head>
  <body>
    <div>
      <p>
        样式表定义如何显示 HTML 元素，就像 HTML
        中的字体标签和颜色属性所起的作用那样。样式通常保存在外部的 .css
        文件中。我们只需要编辑一个简单的 CSS 文档就可以改变所有页面的布局和外观
      </p>
    </div>
  </body>
</html>

```

![image-20201018102602241](_media/image-20201018102602241.png)

### 3.3 外边距

> margin(外边距)属性定义元素周围的空间。
>
> + margin和padding一样也分为四个方向的空间
>   + margin-top
>   + margin-let
>   + margin-bottm
>   + margin-right
>   + margin: 上 右 下 左  四个方向的外边距值

| 值       | 说明                                        |
| :------- | :------------------------------------------ |
| auto     | 设置浏览器边距。 这样做的结果会依赖于浏览器 |
| *length* | 定义一个固定的margin（使用像素，pt，em等）  |
| *%*      | 定义一个使用百分比的边距                    |

#### 3.3.1 **清除浏览器给元素添加的默认内外边距**

> :exclamation:设置外边距通常会在元素之间进行"留白",留白的空间内通常不能放置其他元素
>
> 浏览器默认的body和窗口之间是有8px的留白距离。
>
> 通常在页面开发的时候我们要取消浏览器给元素添加的默认的外边距和内边距:
>
> *{
>
> margin:0;
>
> padding:0;
>
> }

![image-20201018103434061](_media/image-20201018103434061.png)

#### 3.3.2 **元素居中**

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div {
        width: 400px;
        height: 300px;
        border: 2px solid red;
        padding: 20px;
        margin: 0 auto; /*上下边距为0 左右自适应就会自动居中*/
      }
      p {
        border: 1px solid green;
      }
    </style>
  </head>
  <body>
    <div>
      <p>
        样式表定义如何显示 HTML 元素，就像 HTML
        中的字体标签和颜色属性所起的作用那样。样式通常保存在外部的 .css
        文件中。我们只需要编辑一个简单的 CSS 文档就可以改变所有页面的布局和外观
      </p>
    </div>
  </body>
</html>

```

![image-20201018103849393](_media/image-20201018103849393.png)

#### 3.3.3 **外边距合并**

> 使用margin定义块元素的垂直外边距时，可能会出现外边距的合并

1. **相邻元素垂直方向的外边距合并**

> 当上下相邻的两个块元素相遇时，如果上面的元素有下外边距margin-bottom，下面的元素有上外边距margin-top，则他们之间的垂直间距不是margin-bottom与margin-top之和，而是两者中的较大者。这种现象被称为相邻块元素垂直外边距的合并（也称外边距塌陷）。

![img](_media/klshdahsd.png)

> 解决方案: 可以直接改变其中一个的外边距的值，使之达到想要的效果。(推荐使用)

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div:first-child {
        width: 200px;
        height: 100px;
        border: 2px solid red;
        margin-bottom: 20px;
      }
      div:last-child {
        width: 200px;
        height: 100px;
        border: 1px solid green;
        margin-top: 10px;
      }
    </style>
  </head>
  <body>
    <div></div>
    <div></div>
  </body>
</html>

```

![image-20201018104601138](_media/image-20201018104601138.png)

2. **嵌套块元素垂直外边距的合并**

> 就是垂直方向的margin不但会合并; 当父元素没有设置内边距或边框,以及触发BFC时,如果子元素的值大于父元素时，它会带着父元素一起偏移,此时子元素是相对除了它父级之外的离它最近的元素偏移的：
>
> 通俗讲就是:对于两个嵌套关系的块元素，如果父元素没有上内边距及边框，则父元素的上外边距会与子元素的上外边距发生合并，合并后的外边距为两者中的较大者，即使父元素的上外边距为0，也会发生合并。

![margin1](_media/201212072104421699.gif)



```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div {
        width: 400px;
        height: 300px;
        border-top: none;
        border-left: 2px solid red;
        border-bottom: 2px solid red;
        border-right: 2px solid red;
        margin-top: 20px;
      }
      p {
        margin-top: 30px;
        border: 2px solid green;
      }
    </style>
  </head>
  <body>
    <div>
      <p>
        外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。
        合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者
      </p>
    </div>
  </body>
</html>


```

![image-20201018105900959](_media/image-20201018105900959.png)

> 解决方案:
>
> + 可以通过给父元素添加边框或内边距.(不建议使用,会破坏布局)
>
> + 使用BFC解决: 将父元素的渲染模式改为BFC渲染模式.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div {
        width: 400px;
        height: 300px;
        border-top: none;
        border-left: 2px solid red;
        border-bottom: 2px solid red;
        border-right: 2px solid red;
        margin-top: 20px;
        overflow: hidden;
      }
      p {
        margin-top: 30px;
        border: 2px solid green;
      }
    </style>
  </head>
  <body>
    <div>
      <p>
        外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。
        合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者
      </p>
    </div>
  </body>
</html>

```



![image-20201018105958936](_media/image-20201018105958936.png)

#### 3.3.4 BFC是什么,如何触发BFC

##### FC

Formatting context(格式化上下文)是W3C 规范中的一个概念.
它是页面中的一块渲染区域,并且有一套渲染规则,它决定了其子元素如何定位,以及和其他元素的关系和相互作用.

**BFC**

BFC 即 Block Formatting Contexts (块级格式化上下文)，它属于上述定位方案的普通流。

具有 BFC 特性的元素可以看作是隔离了的独立容器，容器里面的元素不会在布局上影响到外面的元素，并且 BFC 具有普通容器所没有的一些特性。

通俗一点来讲，可以把 BFC 理解为一个封闭的大箱子，箱子内部的元素无论如何翻江倒海，都不会影响到外部。

##### 触发BFC

只要满足以下任意一条件,将会触发BFC.

- body根元素
- 浮动元素：float：除none以为的值
- 绝对定位元素：position：absolute/fixed
- display：inline-block/table-cells/flex
- overflow：除了visible以外的值（hidden/auto/scroll)

### 3.4 内容

> 使用宽度属性width和高度属性height可以对盒子的大小进行控制。
>
> width和height的属性值可以为不同单位的数值或相对于父元素的百分比%，实际工作中最常用的是像素值。
>
> 大多数浏览器，如Firefox、IE6及以上版本都采用了W3C规范，符合CSS规范的盒子模型的总宽度和总高度的计算原则是：
>
> ​	/\*外盒尺寸计算（元素空间尺寸）\*/
>   Element空间高度 = content height + padding + border + margin
>   Element 空间宽度 = content width + padding + border + margin
>   /\*内盒尺寸计算（元素实际大小）\*/
>   Element Height = content height + padding + border （Height为内容高度）
>   Element Width = content width + padding + border （Width为内容宽度）
>
> **注意:**
>
> 1、宽度属性width和高度属性height仅适用于块级元素，对行内元素无效（ img 标签和 input除外）。
>
> 2、计算盒子模型的总高度时，还应考虑上下两个盒子垂直外边距合并的情况。
>
> 3、**如果一个盒子没有给定宽度/高度或者继承父亲的宽度/高度，则padding 不会影响本盒子大小**。

![image-20201018110459759](_media/image-20201018110459759.png)

### 3.5盒子模型布局稳定性

开始学习盒子模型，同学们最大的困惑就是， 分不清内外边距的使用，什么情况下使用内边距，什么情况下使用外边距？

答案是：  其实他们大部分情况下是可以混用的。  就是说，你用内边距也可以，用外边距也可以。 你觉得哪个方便，就用哪个。

但是，总有一个最好用的吧，我们根据稳定性来分，建议如下：

按照 优先使用  宽度 （width）  其次 使用内边距（padding）    再次  外边距（margin）。   

```
  width >  padding  >   margin   
```

原因：

1. margin 会有外边距合并 还有 ie6下面margin 加倍的bug（讨厌）所以最后使用。

2. padding  会影响盒子大小， 需要进行加减计算（麻烦） 其次使用。

3. width   没有问题（嗨皮）我们经常使用宽度剩余法 高度剩余法来做。

### 3.6 Css3的盒子模型

> CSS3中可以通过box-sizing 来指定盒模型，即可指定为content-box、border-box，这样我们计算盒子大小的方式就发生了改变
>
> - content-box： 
>
>   padding和border不被包含在定义的width和height之内。对象的实际宽度等于设置的width值和border、padding之和，即 (  Element width = width + border + padding ) 
>
>   此属性表现为标准模式下的盒模型。 
>
> - border-box： 
>
>   padding和border被包含在定义的width和height之内。对象的实际宽度就等于设置的width值，即使定义有border和padding也不会改变对象的实际宽度，即  ( Element width = width ) 
>
>   此属性表现为怪异模式下的盒模型。 

| content-box | 这是 CSS2.1 指定的宽度和高度的行为。指定元素的宽度和高度（最小/最大属性）适用于box的宽度和高度。元素的填充和边框布局和绘制指定宽度和高度除外 |
| ----------- | ------------------------------------------------------------ |
| border-box  | 指定宽度和高度（最小/最大属性）确定元素边框。也就是说，对元素指定宽度和高度包括了 padding 和 border 。通过从已设定的宽度和高度分别减去边框和内边距才能得到内容的宽度和高度。 |
| inherit     | 指定 box-sizing 属性的值，应该从父元素继承                   |

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div {
        width: 400px;
        height: 300px;
        border-top: none;
        border-left: 2px solid red;
        border-bottom: 2px solid red;
        border-right: 2px solid red;
        margin-top: 20px;
        overflow: hidden; /**/
        /* 盒子大小为 width + padding + border   content-box:此值为其默认值，其让元素维持W3C的标准Box Mode */
        box-sizing: content-box;
          
      }
      p {
        margin-top: 30px;
        border: 2px solid green;
        padding: 5px;
      }
    </style>
  </head>
  <body>
    <div>
      <p>
        外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。
        合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者
      </p>
    </div>
  </body>
</html>

```

![image-20201018111151867](_media/image-20201018111151867.png)

```java
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>盒子模型</title>
    <style>
      div {
        width: 400px;
        height: 300px;
        border-top: none;
        border-left: 2px solid red;
        border-bottom: 2px solid red;
        border-right: 2px solid red;
        margin-top: 20px;
        overflow: hidden; /**/
        /*盒子自身的大小维持不变，里面的内容自动调整*/
        box-sizing: border-box;
      }
      p {
        margin-top: 30px;
        border: 2px solid green;
        padding: 5px;
      }
    </style>
  </head>
  <body>
    <div>
      <p>
        外边距合并指的是，当两个垂直外边距相遇时，它们将形成一个外边距。
        合并后的外边距的高度等于两个发生合并的外边距的高度中的较大者
      </p>
    </div>
  </body>
</html>

```

![image-20201018111300839](_media/image-20201018111300839.png)

### 3.7 盒子模型的水平布局

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta http-equiv="X-UA-Compatible" content="ie=edge">
    <title>Document</title>
    <style>
        .outer{
            width: 800px;
            height: 200px;
            border: 10px red solid;
        }

        .inner{
            /* width: auto;  width的值默认就是auto*/
            width: 200px;
            height: 200px;
            background-color: #bfa;
            margin-right: auto;
            margin-left: auto;
            /* margin-left: 100px;
            margin-right: 400px */
            /* 
                元素的水平方向的布局：
                    元素在其父元素中水平方向的位置由以下几个属性共同决定“
                        margin-left
                        border-left
                        padding-left
                        width
                        padding-right
                        border-right
                        margin-right

                    一个元素在其父元素中，水平布局必须要满足以下的等式
margin-left+border-left+padding-left+width+padding-right+border-right+margin-right = 其父元素内容区的宽度 （必须满足）

                0 + 0 + 0 + 200 + 0 + 0 + 0 = 800
                0 + 0 + 0 + 200 + 0 + 0 + 600 = 800


                100 + 0 + 0 + 200 + 0 + 0 + 400 = 800
                100 + 0 + 0 + 200 + 0 + 0 + 500 = 800
                    - 以上等式必须满足，如果相加结果使等式不成立，则称为过度约束，则等式会自动调整
                        - 调整的情况：
                            - 如果这七个值中没有为 auto 的情况，则浏览器会自动调整margin-right值以使等式满足
                    - 这七个值中有三个值和设置为auto
                        width
                        margin-left
                        maring-right
                        - 如果某个值为auto，则会自动调整为auto的那个值以使等式成立
                            0 + 0 + 0 + auto + 0 + 0 + 0 = 800  auto = 800
                            0 + 0 + 0 + auto + 0 + 0 + 200 = 800  auto = 600
                            200 + 0 + 0 + auto + 0 + 0 + 200 = 800  auto = 400

                            auto + 0 + 0 + 200 + 0 + 0 + 200 = 800  auto = 400


                            auto + 0 + 0 + 200 + 0 + 0 + auto = 800  auto = 300

                        - 如果将一个宽度和一个外边距设置为auto，则宽度会调整到最大，设置为auto的外边距会自动为0
                        - 如果将三个值都设置为auto，则外边距都是0，宽度最大
                        - 如果将两个外边距设置为auto，宽度固定值，则会将外边距设置为相同的值
                            所以我们经常利用这个特点来使一个元素在其父元素中水平居中
                            示例：
                                width:xxxpx;
                                margin:0 auto;



             */
        }
    </style>
</head>
<body>

    <div class="outer">

        <div class="inner"></div>

    </div>
    
</body>
</html>
```

