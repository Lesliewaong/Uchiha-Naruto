# 纯HTML/CSS项目——“宇智波•鸣人”

## 项目展示

[展示地址](https://lesliewaong.top/item/Naruto/)

> 展示动图

[![HWV49x.gif](https://s4.ax1x.com/2022/02/15/HWV49x.gif)](https://imgtu.com/i/HWV49x)

注意：

* 对移动端进行了自适应。
* 鼠标移入三勾玉或轮回圈部分有动画。
* 在苹果的设备上会有展示bug， `drop-shadow()`在轮回眼上无法生效。
* Web端无法使用缩放功能。

## 背景渐变

### 线性渐变（linear-gradient）

基础用法：

```css
background:linear-gradient(angle,start-color,soft-line,end-color);
```

* **angle**是渐变角度，不写则默认从上到下，也就是`to bottom`，当然其他类似的直角方向还有`to right`,`to top`,`to left`。其他的对角方向包括`to left top`,`to right top`,`to bottom right`,`to bottom left`。需要注意的是：对角线角度的单词顺序**不讲究顺序**，`to bottom right`和`to right bottom`是一样的意思。

* **start-color && end-color**表示起始色标和终止色标，支持16进制颜色（如"`#85e96c`"），h5示例颜色（如"`aqua`"），rgb（如"`rgb(133, 233, 108)`"），rgba（"`rgba(133, 233, 108,.5)`"）、`transparent`。

* **soft-line**:柔性分界。不写则默认50%。表示两种颜色过渡的柔和边界，不是硬性边界。

* 如果想写一条硬线，也就是所谓的`hard line`来进行无渐变分割，则在两个色标尾部紧接着写上50%，注意，除了50%其他都不能完全消除渐变效果。这是一个去渐变的硬线分割写法。

  ```css
  background:linear-gradient(#fc4a09 50%,#f7d1ab  50%);
  ```

### 径向渐变（radial-gradient）

基础语法：

```css
background:radial-gradient(shape,start-color, soft-line,end-color );
```

* **shape**即渐变的形状，不写则为默认的`ellipse椭圆`，可以改为`circle正圆`。

* 其他参数的含义（`start-color`,`end-color`,`soft-line`），包括硬线的实现代码，配合背景图使用的写法，**都与线性渐变的几个同名参数或同名操作完全相同**。

## 自适应布局单位vw,vh

### 视口单位(Viewport units)

> 什么是视口？ 

视口 (viewport) 代表当前可见的计算机图形区域。在 **Web 浏览器**术语中，**通常与浏览器窗口相同**，但不包括浏览器的UI， 菜单栏等——即指你正在浏览的文档的那一部分。

文档，比如这篇文章，可能会非常长。你的viewport 就是你现在所能见到的所有事物。值得注意的是“什么是视口区域”这个问题，页面中的一些导航菜单也包括在其中。**Viewport 的大小取决于屏幕的大小，无论浏览器是否处于全屏模式，是否被用户缩放了。**Viewport 外的区域，比如这个文档的See Also部分，可能需要滚动到其所在的区域才会出现在屏幕上。

- 在尺寸较大的设备中，在这些设备上，**应用显示区域不一定是全屏的，viewport 是浏览器窗口的大小**。
- 在大多数移动设备中，**浏览器是全屏的**，**viewport 是整个屏幕的大小**。
- 在全屏模式下，viewport 是设备屏幕的范围，窗口是浏览器窗口，浏览器窗口大小小于或等于视口的大小，并且文档是这个网站，文档的大小可比 viewport 长或宽。

概括地说，**viewport 基本上是当前文档的可见部分**。

Web 浏览器包含两个 viewport，**布局视口 (layout viewport)** 和**视觉视口 (visual viewport)**。visual viewport 指当前浏览器中可见的部分，并且可以变化。当使用触屏双指缩放，当动态键盘在手机上弹出的时候，或者之前隐藏的地址栏变得可见的时候，visual viewport 缩小了，但是 layout viewport 却保持不变。

在上面描述的布局视口 (layout viewport) 和视觉视口 (visual viewport) 不是您将遇到的唯一视口。 在布局视口中完全或部分显示的任何子视口都被视为可视视口。

我们通常认为宽度和高度的媒体查询是相对于浏览器窗口的宽度和高度而言的。 **它们实际上是相对于视口的**，即**主文档（document）中的窗口（window对象）**，但它也是**嵌套浏览上下文（如对象，iframe和SVG）中元素父级的本身的大小**。 在CSS中，我们也有基于视口大小的长度单位。 `1vh` 单位是 `1%` 布局视口的高度，`vw` 单位与此类似。

对于一个 `iframe` 来说，视觉视口是其内部高度和宽度的大小而不是其父文档的大小。你可以为其高度和宽度设置任意数值，但过大的值可能会使 `iframe` 部分内容超出视口导致超出部分不可见。

视口单位主要包括以下4个：

* **vw**：1vw等于视口宽度的1%。
* **vh**：1vh等于视口高度的1%。
* **vmin**：选取vw和vh中最小的那个。
* **vmax**：选取vw和vh中最大的那个。

### vh/vw与%区别

 **vh and vw：相对于视口的高度和宽度，而不是父元素的**（**CSS百分比是相对于包含它的最近的父元素的高度和宽度**）。

### 兼容性问题

在移动端 iOS 8 以上以及 Android 4.4 以上获得支持，并且在微信 x5 内核中也得到完美的全面支持。

### 缺点

用户失去了放缩任何使用`vw`单位的元素的能力。

## border

一个用于设置各种单独的边界属性的简写属性。

`border`可以用于设置一个或多个以下属性的值: `border-width`, `border-style`, `border-color`

### 利用border画三角形

本质还是利用了盒模型，**每个边框都是梯形**，当**内容区宽高为0**时就成三角形。

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>CSS三角形</title>
    <style>
        body{
            background-color: rgb(77, 80, 79);
        }
        .div1{
            width: 0;
            height: 0;
            border: 125px solid transparent;
            border-left-color: aqua;
            display: inline-block;
        }
        .div2{
            width: 0;
            height: 0;
            border-top: 125px solid transparent;
            border-bottom: 125px solid rgb(36, 15, 153);
            border-left: 125px solid transparent;
            border-right: 125px solid transparent;
            display: inline-block;
        }
        .div3{
            width: 0;
            height: 0;
            border-top: 125px solid transparent;
            border-bottom: 125px solid rgb(153, 15, 45);
            border-left: 125px solid transparent;
            /* border-right: 125px solid transparent; */
            display: inline-block;
        }
        .div4{
            width: 0;
            height: 0;
            border-top: 250px solid rgb(15, 153, 61);
            border-left: 125px solid transparent;
            border-right: 125px solid transparent;
            display: inline-block;
        }
        .div5{
            width: 600px;
            height: 80px;
            background-color: white;
            margin: 100px;
            position: relative;
        }
        .div5::after{
            content: '';
            position: absolute;
            right: 50%;
            top: 100%;
            transform: translateX(50%);
            border: 20px solid transparent;
            border-top-color:  white;
        }
    </style>
</head>
<body>
    <div class="div1"></div>
    <div class="div2"></div>
    <div class="div3"></div>
    <div class="div4"></div>
    <div class="div5"></div>
</body>
</html>
```

效果图：

[![7m1wcj.png](https://s4.ax1x.com/2022/01/11/7m1wcj.png)](https://imgtu.com/i/7m1wcj)

## border-radius 

`border-radius`允许你设置元素的外边框圆角当使用**一个半径时确定一个圆形**,当使用**两个半径时确定一个椭圆**

这个(椭)圆与边框的交集形成圆角效果。

该属性是一个简写属性,是为了将这四个属性 `border-top-left-radius` 、`border-top-right-radius` 、`border-bottom-right-radius`和 `border-bottom-left-radius` 简写为一个属性。

即使元素**没有边框**,圆角也可以用到 `background` 上面,具体效果受 `background-clip` 影响。

```css
/* 右上和左下设置圆角*/
border-radius: 0 12vmin 0 12vmin;
/* 圆形*/
width: 60vmin;
height: 60vmin;
border-radius: 50%;
```

## box-shadow

用于在元素的框架上添加阴影效果。你可以在同一个元素上设置多个阴影效果，并用逗号将他们分隔开。该属性可设置的值包括`阴影的X轴偏移量`、`Y轴偏移量`、`模糊半径`、`扩散半径`和`颜色`。

你几乎可以在任何元素上使用`box-shadow`来添加阴影效果。如果元素同时设置了 [`border-radius`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/border-radius)属性 ，那么阴影也会有圆角效果。

如果没有指定`inset`，默认阴影在边框外，即阴影向外扩散。

使用 `inset` 关键字会使得阴影落在盒子内部，这样看起来就像是内容被压低了。 此时阴影会在边框之内 (即使是透明边框）、背景之上、内容之下。

```css
box-shadow: inset 0 0 1vmin rgba(17, 17, 17, 0.8);
```

**注意**

ios中`box-shadow`容易出现bug，一种方式是设置`border: none;`，使用`box-shadow`和`border-radius`可以获得类似**边框**的效果。

## filter

将模糊或颜色偏移等图形效果应用于元素。滤镜通常用于调整图像，背景和边框的渲染。

CSS 标准里包含了一些已实现预定义效果的函数。你也可以参考一个 SVG 滤镜，通过一个 URL 链接到 SVG 滤镜元素。

```css
filter: drop-shadow( -0.8vmin -0.5vmin 0.3vmin  rgb(216, 59, 59));
```

### drop-shadow()

为输入图像添加投影效果。投影实际上是输入图像的alpha蒙版的一个模糊的、偏移的版本，用特定的颜色绘制并合成在图像下面。

**注意:** 这个函数有点类似于 [`box-shadow`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/box-shadow) 属性. `box-shadow` 属性在元素的整个框后面创建一个矩形阴影, 而 `drop-shadow()` 过滤器则是创建一个符合图像本身形状(alpha通道)的阴影。

```css
drop-shadow(offset-x offset-y blur-radius spread-radius color)
```

**注意**

`drop-shadow()`在ios中也会出现bug，但在一些地方又能正常显示，因此尚未找到原因和解决方法。

## position

### static

该关键字指定元素使用正常的布局行为，即元素在文档常规流中当前的布局位置。

此时 `top`, `right`, `bottom`, `left` 和 `z-index `属性无效。

### relative

该关键字下，元素先放置在未添加定位时的位置，再在不改变页面布局的前提下调整元素位置（因此会在此元素未添加定位时所在位置留下空白）。

`position:relative` 对 `table-*-group`, `table-row`, `table-column`, `table-cell`, `table-caption` 元素无效。

### absolute

元素会**被移出正常文档流**，并不为元素预留空间，通过指定元素相对于**最近的非 static 定位祖先元素的偏移**，来确定元素位置。绝对定位的元素可以设置外边距（margins），且**不会与其他边距合并**。

### fixed

元素会**被移出正常文档流**，并不为元素预留空间，而是通过指定元素相对于**屏幕视口（viewport）**的位置来指定元素位置。元素的位置在屏幕滚动时不会改变。打印时，元素会出现在的**每页的固定位置**。`fixed` 属性会创建**新的层叠上下文**。当元素祖先的 `transform`, `perspective` 或 `filter` 属性非 `none` 时，容器由视口改为该祖先。

### sticky

根据文档的正常流程定位元素，然后根据`top`、`right`、`bottom`和`left`的值相对于最**近的滚动祖先和包含块(最近的块级祖先)进行偏移**，包括与表相关的元素。该偏移量不会影响任何其他元素的位置。

此值始终创建新的堆叠上下文。请注意，它到其具有“滚动机制”的最近祖先的粘性元素“粘贴”（当该祖先的`overflow` 是 `hidden`, `scroll`, `auto`, 或 `overlay`时），即使该祖先不是最近的实际滚动祖先。这有效地抑制了任何“粘性”行为

## CSS动画

### transform

**`transform`**属性允许你旋转，缩放，倾斜或平移给定元素。这是通过修改CSS视觉格式化模型的坐标空间来实现的。

**`transform-origin`** 属性让你更改一个元素变形的原点。（默认的转换原点是 `center`)

#### rotate()

定义一个旋转属性，将元素在不变形的情况下旋转到不动点周围(如 [`transform-origin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/transform-origin) 属性所指定) 。 移动量由指定角度定义;如果为**正值**，则运动将为**顺时针**，如果为负值，则为逆时针 。 180°的旋转称为点反射 (*point reflection*)。

`rotate(a)`

*a* 该参数表示`angle`代表旋转的角度。正角表示顺时针旋转，负角表示逆时针旋转。

#### scale()

可改变元素的大小。 它可以增大或减小元素的大小，并且缩放量由矢量定义，并且它可以使在一个方向上比另一个方向更多。

这种变换的特点是矢量的坐标可定义在每个不同方向上各子完成一定比例缩放。如果矢量的两个坐标相等，则缩放是均匀的或各向同性的，并且元素的形状被保留。在这种情况下，缩放函数定义了一个同调变换。

当超出 `[-1, 1]`范围外时，缩放将在坐标方向上放大元素；当在该范围内时，它在该方向收缩元素。当等于1时，它什么也不做，当它为负时，它执行点反射和大小修改。

#### translate()

用于移动元素在平面上的位置。这种变换的特点是矢量的坐标定义了它在每个方向上的移动量。

```CSS
/* 父元素相对定位，子元素absolute+transform实现绝对居中 */
.forehead {
    height: 8vmin;
    background-color: #4D4747;
    position: relative;
}
.forehead .plate {
    width: 30vmin;
    height: 6.5vmin;
    background-color: #cecece;
    padding: 0.3vmin 0 0 0;
    border-radius: 1vmin;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
}
/* 水平方向平移v */
transform: translateX(-50%);
```

#### transform对定位元素的影响

当给一个元素加上`transform`属性的时候，这个元素就会具有`relative`的特性,所以**若一个元素的父元素拥有tranform属性，那么子元素在使用定位属性的时候要注意。**

### animation

animation属性是 `animation-name`,`animation-duration`, `animation-timing-function`,`animation-delay`,`animation-iteration-count`,`animation-direction`,`animation-fill-mode` 和 `animation-play-state` 属性的一个简写属性形式。

##### animation-name

指定应用的一系列动画,每个名称代表一个由`@keyframes`定义的动画序列。

##### @keyframes

关键帧 **`@keyframes`** at-rule 规则通过在动画序列中定义关键帧（或waypoints）的样式来控制CSS动画序列中的中间步骤。和 `过渡transition` 相比，关键帧 `keyframes` 可以控制动画序列的中间步骤。

如果一个关键帧规则没有指定动画的开始或结束状态（也就是，`0%`/`from` 和`100%`/`to`，浏览器将使用元素的现有样式作为起始/结束状态。这可以用来从初始状态开始元素动画，最终返回初始状态。

如果在关键帧的样式中使用了不能用作动画的属性，那么这些属性会被忽略掉，支持动画的属性仍然是有效的，不受波及。

如果一个关键帧中没有出现其他关键帧中的属性，那么这个属性将使用插值（不能使用插值的属性除外，这些属性会被忽略掉）。

关键帧中出现的 `!important` 将会被忽略。

##### animation-duration

指定一个动画周期的时长。

默认值为0s，表示无动画。

##### animation-timing-function

定义CSS动画在每一动画周期中执行的节奏 可能值为一或多个 `<timing-function>` 。 

对于关键帧动画来说,`timing function`作用于**一个关键帧周期**而非整个动画周期,即从关键帧开始开始,到关键帧结束结束。

定义于一个关键帧区块的缓动函数(animation timing function)应用到该关键帧;另外,若该关键帧没有定义缓动函数,则使用定义于整个动画的缓动函数。

##### animation-delay

定义动画于何时开始，即**从动画应用在元素上到动画开始的这段时间的长度**。

`0s`是该属性的默认值，代表动画在应用到元素上后立即开始执行。否则，该属性的值代表动画样式应用到元素上后到开始执行前的时间长度；

定义一个**负值**会让动画立即开始。但是动画会从它的动画序列中某位置开始。例如，如果设定值为-1s，动画会从它的动画序列的第1秒位置处立即开始。

如果为动画延迟指定了一个负值，但起始值是隐藏的，则从动画应用于元素的那一刻起就获取起始值。

##### animation-iteration-count 

定义动画在结束前运行的**次数** 

可以是1次/无限循环`infinite`. 如果指定了多个值,每次播放动画时,将使用列表中的下一个值,在使用最后一个值后循环回第一个值。

动画播放的次数；默认值为`1`。可以用小数定义循环，来播放动画周期的一部分：例如，`0.5` 将播放到动画周期的一半。不可为负值。

##### animation-direction 

指示动画是否反向播放

`normal` 每个循环内动画向前循环，换言之，**每个动画循环结束，动画重置到起点重新开始**，这是默认属性。

`alternate` **动画交替反向运行，反向运行时，动画按步后退，同时，带时间功能的函数也反向**，比如，`ease-in` 在反向时成为 `ease-out`。计数取决于开始时是奇数迭代还是偶数迭代

`reverse` 反向运行动画，每周期结束动画由尾到头运行。

`alternate-reverse`反向交替， 反向开始交替。动画**第一次运行时是反向的，然后下一次是正向**，后面依次循环。决定奇数次或偶数次的计数从1开始。

##### animation-fill-mode 

设置CSS动画在执行之前和之后如何将样式应用于其目标

`none` 当动画未执行时，动画将不会将任何样式应用于目标，而是已经赋予给该元素的 CSS 规则来显示该元素。这是默认值。

`forwards` 目标将保留由执行期间遇到的**最后一个关键帧计算值**。 最后一个关键帧取决于`animation-direction`和`animation-iteration-count`的值。

`backwards` 动画将在应用于目标时**立即应用第一个关键帧中定义的值**，并在`animation-delay`期间保留此值。 第一个关键帧取决于`animation-direction`的值。

`both` 动画将遵循`forwards`和`backwards`的规则，从而在两个方向上扩展动画属性。

##### animation-play-state 

定义一个动画是否运行或者暂停。 

可以通过查询它来确定动画是否正在运行。

另外,它的值可以被设置为暂停和恢复的动画的重放。

恢复一个已暂停的动画,将从它开始暂停的时候,而不是从动画序列的起点开始在动画

`running` 当前动画正在运行。

`paused` 当前动画已被停止。

### transition

**`transition`** 属性是 `transition-property`，`transition-duration`，`transition-timing-function`和 `transition-delay` 的一个简写属性。

过渡可以为一个元素**在不同状态之间切换的时候定义不同的过渡效果**。不同的状态可以使用**伪类**定义，比如`:hover`或`:active`，或者使用`JavaScript`动态设置。

## var()

**`var()`**函数可以代替元素中任何属性中的值的任何部分。**`var()`**函数不能作为属性名、选择器或者其他除了属性值之外的值。（这样做通常会产生无效的语法或者一个没有关联到变量的值。）

**如果一个属性值在多处被使用，该方法就很有用。**

方法的第一个参数是要替换的自定义属性的名称。函数的可选第二个参数用作回退值。如果第一个参数引用的自定义属性无效，则该函数将使用第二个值。

`var( <custom-property-name> , <declaration-value>? )`

* `<custom-property-name>` 自定义属性名

  在实际应用中它被定义为以**两个破折号**（`--`）开始的任何有效标识符。 自定义属性仅供作者和用户使用; CSS 将永远不会给他们超出这里表达的意义。

* `<declaration-value>` 声明值（后备值）

  回退值被用来在自定义属性值无效的情况下保证函数有值。回退值可以包含任何字符，但是部分有特殊含义的字符除外。

## 伪类/伪元素

### 伪类

**伪类**是选择器的一种，它用于选择处于**特定状态**的元素，比如当它们是**这一类型的第一个元素**时，或者是**当鼠标指针悬浮在元素上面**的时候。它们表现得会像是你向你的文档的某个部分应用了一个类一样，**帮你在你的标记文本中减少多余的类，让你的代码更灵活、更易于维护**。

伪类就是开头为`冒号:`的关键字。

#### 简单的伪类

`:first-child` 第一个子元素，`:last-child`，最后一个子元素 `:nth-child()` 选中第n个子元素。

#### 用户动作伪类

一些伪类仅适用于用户以某种方式与文档交互。这些用户动作伪类，有时称为动态伪类，就像用户在与之交互时添加到元素中的类一样。例子包括：

`:hover`- 这仅适用于用户在元素上**移动鼠标**，通常是**链接**。

`:focus` - 仅在用户通过**单击或使用键盘控件**来适用元素。

### 伪元素

伪元素的行为方式类似。但是，它们的行为就像您在标记中添加了一个全新的 HTML 元素，而不是将类应用于现有元素。伪元素以双冒号开头`::`。

注意：**一些早期的伪元素使用单冒号语法**，因此您有时可能会在代码或示例中看到这一点。现代浏览器支持具有单冒号或双冒号语法的早期伪元素，**以实现向后兼容性**。

在 CSS 中，使用`::before`和`::after`伪元素以及`content`属性被称为“生成的内容”，您经常会看到这种技术被用于各种任务。

**`::before`**/`::after`用来创建一个伪元素，作为已选中元素的**第一个**/**最后一个子元素**。通常会配合[`content`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/content)属性来为该元素添加装饰内容。这个虚拟元素**默认是行内元素**。

**`::before`**/`::after`表示法是在**CSS 3**中引入的，`::`符号是用来区分**伪类**和伪元素的。支持CSS3的浏览器同时也都支持CSS2中引入的表示法`:before`/`:after`。

**注:** IE8仅支持`:before`/`:after`。

## 层叠上下文

元素提升为一个比较特殊的图层，在三维空间中 **(z轴)** 高出普通元素一等。

- 触发条件
  - 根层叠上下文(`html`)
  - `position`
  - css3属性
    - `flex`
    - `transform`
    - `opacity`
    - `filter`
    - `will-change`
    - `-webkit-overflow-scrolling`
- 层叠等级：层叠上下文在z轴上的排序
  - 在同一层叠上下文中，层叠等级才有意义
  - `z-index`的优先级最高

[![o3dDRs.png](https://z3.ax1x.com/2021/11/30/o3dDRs.png)](https://imgtu.com/i/o3dDRs)

> 示例

[![HyTAQs.png](https://s4.ax1x.com/2022/02/14/HyTAQs.png)](https://imgtu.com/i/HyTAQs)

在这个例子中，每个被定位的元素都创建了独自的层叠上下文，因为他们被指定了定位属性和 `z-index` 值。我们把层叠上下文的层级列在下面：

- Root
  - DIV #1
  - DIV #2
  - DIV #3
    - DIV #4
    - DIV #5
    - DIV #6

请一定要注意 `DIV #4`，`DIV #5` 和 `DIV #6` 是 `DIV #3` 的子元素，所以它们的层叠完全在 `DIV #3` 中被处理。一旦 `DIV #3` 中的层叠和渲染处理完成，`DIV #3` 元素**就被作为一个整体传递与兄弟元素的 DIV 在 root（根）元素进行层叠。**