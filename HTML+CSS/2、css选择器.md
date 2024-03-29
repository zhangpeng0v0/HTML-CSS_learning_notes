#    CSS

## 1 CSS介绍

**CSS** ，即Cascading Style Sheets（层叠样式表）。可以用来为HTML或者XML添加样式（主要是HTML）。 
**元素是能够指定样式的最小单位，狭义上元素指标签，广义上元素还包括伪元素。** 

CSS注释方法：`/*注释内容*/ `

### 1.1 HTML语言与CSS的联系：

**HTML和CSS之间的关系**:

- HTML：构建页面（人）；CSS：构建HTML元素的样式（化妆师）
- HTML是页面的内容组成，CSS是页面的表现。

仅仅通过HTML语言来改变标签显示样式的话，只能通过HTML属性进行，这有着很多限制和困难：
1. HTML标签提供的有关样式的属性较少。
2. 相似的样式在不同的标签里可能通过不同的属性进行定义，较难记忆。
3. 属性的取值不够严谨规范，浏览器表现差异明显。
4. 需要为每个标签都进行属性指定，标签较多时实现繁琐。

使用CSS就可以解决以上的问题，更加自由和方便的定义标签样式。
1. CSS作用：用于控制网页的外观，修饰和美化html标签的,实现了结构和形式的分离。
2. 使用CSS+DIV的优点 采用CSS+DIV进行网页重构相对与传统的TABLE网页布局而具有以下3个显著优点：**1：表现和内容相分离 2：提高页面浏览速度 3：易于维护和改版**

## 2 CSS的样式表

使用CSS之前，必须先书写一些HTML标签，因为CSS是给HTML标签来赋予样式。
CSS样式表分类：**行内样式表，内嵌样式表，外部样式表**。

### 2.1 行内（内联）样式表：style属性

每个标签都可以添加**style**属性，可以通过这个属性为当前标签添加样式。 `<p style="color:#f00;"></p>`

**书写方便，权重高，但没有实现样式和结构的分离，使用情况较少，只能控制一个标签（少）。**

### 2.2 内嵌样式表：style标签

将CSS代码集中写在HTML文档的head头部标签中，并用style标签定义；语法中，style标签一般位于head标签中title标签之后，也可以把他放在HTML文档的任何地方。

```html
<head>
    <style>
        选择器{
            font-size:24px;
            color:red;
            font-family:"楷体","KaiTi";
        }
    </style>
</head>
```

**部分结构和样式相分离，但没有彻底分离，使用情况较多，可以控制一个页面（中）。**

### 2.3 外部样式表（.css文件与`<link>`）

语法中，link标签需要放在head头部标签中，并且必须指定link标签的三个属性，具体如下：

- href：定义所链接外部样式表文件的url，相对路径或者绝对路径。
- type：定义所链接文档的类型，在这里需要指定为"text/CSS"，表示被链接的外部文件为CSS样式表。
- rel：定义当前文档与被链接文档之间的关系，在这里需要指定为"stylesheet"，表示被链接的文档是一个样式表文件。

**完全实现结构和样式相分离，不过需要引入，使用最多，可以控制整个站点（多）。**

建立一个以css为扩展名的文本文件，在里面键入以下内容： 

```css
选择器{
    font-size:24px;
    color:red;
    font-family:"楷体","KaiTi";
}
```

然后就可以使用`<link>`标签引入到HTML的head标签内 。

```html
<head>
    <link rel="stylesheet" href="css文件路径">
</head>
```



###2.4 导入样式表（不建议直接在HTML中使用） 

导入样式和链接样式比较相似，采用@import样式导入CSS样式表，在HTML初始化时，会被导入导HTML或者CSS文件中，成为文件的一部分，类似内嵌样式。不过在加载文HTML档后再加载样式，所以有时会出现没有样式的情况（很短暂），然后就有样式了。

```html
在HTML中使用：
<style type="text/css">
@import url(style.css);
</style>
在CSS中使用：
@import url(style.css);
```

> 如果需要引入多个CSS文件链接式则需要多写几句，也可以写成一个总的CSS，在里面用导入式导入其他的CSS，然后再用链接式在HTML中链接总的CSS。

### 2.5 样式表的优先级

```html
<!--css样式引入方式：
			-1.行内样式
			-2.内联样式，内嵌样式。style标签 可使用
			-3.外链样式。link 推荐使用  
			-4.外部导入 。。。@import 
			开发：html css js  解耦合
			
			几种引入方式优先级？ 就近原则
			行内样式 优先级最高的 -->
<style>
			div {
				color: red;
				/*字体大小*/
				font-size: 30px;
			}
			
		</style>
		<link rel="stylesheet" type="text/css" href="css/style.css"/>
	</head>
	<body>
		<div class="my-div" id="my_div">
引入方式：1.行内样式 2，内联样式 3.外链样式
		</div>
<!--当前两类样式表中操作的元素，是同一个元素时同一个样式，看权重-->
			
<!--1.同一选择器，样式表引入有无影响？就近 覆盖
	2.同一选择器，样式表引入出现覆盖 就近原则，必须操作的为同一个样式；如果样式不一样，那各自都起效果。
	3.选择器不同的时候，同一样式按权重走，如果不同样式，同上。-->
	4.在标签内定义的优先级最高，其次是<head>中<style>定义的，其次是外部的；<head>标签中如果外部引入在<style>在标签之前引入，那么<style>标签将会覆盖外部引入相同的部分，反之亦然。	
```

### 2.6 CSS的样式设置和规则

**样式设置**：width 宽度 ， height 高度，单位为 px；em，rem，%等；
 background-color 背景颜色 颜色表示三种方式（单词表示法，16进制，rgb(0,0,0)）。

*详细介绍看后面的文本属性*

**样式规则**：

1、选择器用于指定CSS样式作用的HTML对象，花括号内是对该对象设置的具体样式。
2、属性和属性值以"键值对"的形式出现。（声明=属性+属性值，一个选择器中可以有多个声明）
3、属性是对指定的对象设置的样式属性，例如字体大小、文本颜色等。
4、属性和属性值之间用英文“:”连接。
5、多个“键值对”之间用英文";"进行区分。

## 3 选择器（重点）

选择种类包含：
基本选择器（标签选择器，类选择器，ID选择器），
关系选择器（后代选择器，子代选择器，并集选择器，交集选择器），
伪类选择器，伪元素选择器，属性选择器等 。

**通用选择器**：匹配页面中所有元素
语法：*｛属性：值｝
使用场合：定义当前页面中最基本的显示样式，如：字体，大小……

**属性与值**

- 允许出现多个***属性：值***对，每对之间用***;***隔开
- 特点：只作用于在所定义的标签内，其它标签不受影响。

### 3.1 标签选择器

**语法：标签名** 
按照标签的标签名进行选择，可一次选择多个，把某一类表情哦爱你全部选择出来。
**能快速为页面中同类型的标签统一样式，同时这也是它的缺点，不能设置差异化样式。**

```html
<style>
    div{
        color:red;
    }
</style>

<div>第1个div</div><!-- 红色的 -->
<div>第2个div</div><!-- 红色的 -->
<span>第1个div</span>
<span>第2个span</span>
<div>第3个div</div><!-- 红色的 -->
```

### 3.2 id选择器

**语法：#id** 
按照标签的id属性进行选择，该语法中，id名即为HTML元素的id属性值，大多数的HTML元素都可以定义id属性，元素的id值是唯一的，只能对应文档中某一个具体的元素，用法基本和类选择器相同。 

id选择器与类选择器的区别在于使用次数。类选择器（class）好比人的名字，可以多个人重复使用；id选择器好比人的身份证号码，是唯一的，不能重复使用。

```html
<style>
    #div1{
        color:red;
    }
</style>

<div id="div1">id为div1的div</div><!-- 红色的 -->
<div id="div2">id为div2的div</div>
<div id="div3">id为div3的div</div>
```

### 3.3 类选择器

**语法：.class** 
按照标签的class属性进行选择，可一次选择多个。 
- 标签的class属性可以写多个，用空格分隔。
- 一个页面中可以有多个相同的类名, 一个标签也可以设置多个类名,空格隔开即可。

**类选择器最大的优势是可以为元素对象定义单独或相同的样式，可以选择一个或多个标签。**

> 1、长名称或词组可以使用中横线来为选择器命名。
> 2、不建议使用"_"下划线来命名选择器。（输入的时候少按一个shift键；浏览器兼容问题；JS变量命名是用"_"，能良好区分JavaScript变量命名）
>
> 3、不要以纯数字、中文等命名，尽量使用英文字母来表示。

```html
<style>
    .t1{
        color:red;
    }
</style>

<div class="t1">class为t1的div</div><!-- 红色的 -->
<div class="t2">class为t2的div</div>
<span class="t1">class为t1的span</div><!-- 红色的 -->
```

### 3.4 多类名选择器

给标签指定多个类名，达到更多的选择目的。

多类名选择器在后期布局比较复杂的情况下使用较多。

**注意**：

> 1、样式显示效果跟HTML元素中的类名先后顺序没有关系与CSS样式书写的上下顺序有关。
>
> 2、各个类名中间用空格隔开。

### 3.5 通配符选择器（全选择器）

通配符选择器用"*"号表示，它是所有选择器中作用范围最广的，能匹配页面所有的元素。

基本语法：*｛属性1：属性值1；属性2：属性值2；｝

```html
<!--使用通配符选择器定义CSS样式，清除所有HTML标记的默认边距-->
*{
margin:0;
padding:0;
}
```

### 3.6 子元素选择器（javaScript中详细说明）

:nth-child(index) 匹配其父元素下的第n个子（从1开始）

:eq(index) 匹配一个子元素（从0开始）

## 4 复合选择器（关系选择器）

两个或多个基本选择器，通过不同方式连接而成的选择器。

### 4.1 后代选择器

找到指定的标签的所有后代，然后设置属性。
**语法：选择器1 选择器2…… **（父 子 孙）
先找到选择器1，然后在选择器1下找到所有选择器2，最后设置属性。

注意点：

- **后代选择器必须用空格隔开。**
- 后代不一定是儿子，也可以是孙子

### 4.2 子代选择器

子代选择器是两个及以上的选择器同时作用的结果，符合前一个选择器的直接子标签中所有符合后一个选择器的标签被选中，可以一次选择多个。（选中指定父元素的指定子元素）

**语法：选择器1>选择器2** （父>子）

注意点：
1、**子选择器用大于号隔开**

2、子元素选择器在IE6浏览器中不支持

 ### 4.3 并集选择器

并集选择器是两个及以上的基本选择器同时作用的结果，任何形式的选择器都可以，并集选择器是多个选择器通过逗号连接而成的。

**通常用于集体声明。**

 **语法：选择器1,选择器2** ……

```html
h1,h2,h3{color:red;font-size:23px;}
```

### 4.4 交集选择器

交集选择器是由两个选择器直接连接构成，其结果是选中二者各自元素范围的交集，**其中第一必须是标签选择器，第二个必须是类选择器或者id选择器，两个选择器之间不能有空格，必须连续书写。**

**语法：选择器1选择器2 （中间没有空格）** 

```html
h3.class(color:red;font-size:13px;)
```

##5 伪类选择器

###5.1 伪类选择器

伪类选择器是指当一些标签符合某些条件时会被选中的选择器，相当于这些标签有了这些class，但是程序员不必在标签上 手动添加这个（些）class，伪类选择器必须配合其他选择器使用。 **伪类主要有以下几种：**

1. :focus 选中焦点所在的标签（主要是表单元素）。

2. :hover 选中鼠标悬浮上去的标签。

3. :visited 选中被浏览过的超链接。

4. :nth-child(n) 匹配当前元素的父元素中的第n个子元素（从1开始）。

   ```html
   <style>
       li:nth-child(1){
           color:red;
       }
   </style>
   
   <ul>
       <li></li> <!-- 变红 -->
       <li></li>
       <li></li>
   </ul>
   ```

   

5. :last-child 匹配父元素中的最后一个子元素。

6. :first-child 匹配父元素中的第一个子元素。

> 注意写的时候，他们的顺序尽量不要颠倒 按照 lvha 的顺序。 

**提示：chrome的开发者工具可以强行给元素加上伪类，方便调试**

```css
a {   /* a是标签选择器  所有的链接 */
            font-weight: 700;
            font-size: 16px;
            color: gray;
        }
a:hover {   /* :hover 是链接伪类选择器 鼠标经过 */
            color: red; /*  鼠标经过的时候，由原来的 灰色 变成了红色 */
}
```

### 5.2 伪元素选择器（了解）

**和伪类选择器的区别： **
1.伪类选择器依赖现有的元素，伪元素选择器会创建元素。
2.伪类选择器与其他选择器只能使用:分隔，伪元素选择器可以使用::分隔。

**伪元素主要有以下几种（不再重复写出::分隔符）：**

1. :first-letter 将其选择器选出的元素内的第一个文字创建为伪元素，进而可以添加样式。
2. :first-line 将其他选择器选出的元素内的第一行文字创建为伪元素，进而可以添加样式。
3. :before 在其他选择器选出的元素前面创建一个伪元素，内容由content属性指定，进而可以添加样式。
4. :after 在其他选择器选出的元素后面创建一个伪元素，内容由content属性指定，进而可以添加样式。常见最多的是就是清除浮动。

## >sublime快捷方式

sublime可以快速提高我们代码的书写方式

1. 生成标签 直接输入标签名 按tab键即可 比如 div 然后tab 键， 就可以生成；
2. 如果想要生成多个相同标签 加上 * 就可以了 比如 div*3 就可以快速生成3个div；
3. 如果有父子级关系的标签，可以用 > 比如 ul > li就可以了；
4. 如果有兄弟关系的标签，用 + 就可以了 比如 div+p；
5. 如果生成带有类名或者id名字的， 直接写 .demo 或者 #two tab 键就可以了。

##>CSS书写规范

开始就形成良好的书写规范，是专业化的开始。 

###空格规范

【强制】 选择器 与 { 之间必须包含空格。 

示例： .selector { } 

【强制】 属性名与之后的 : 之间不允许包含空格， :与属性值之间必须包含空格。

示例：font-size: 12px;

### 选择器规范

【强制】 当一个 rule 包含多个 selector 时，每个选择器声明必须独占一行。 

示例：

```css
/* good */
.post,
.page,
.comment {
    line-height: 1.5;
}

/* bad */
.post, .page, .comment {
    line-height: 1.5;
}
```

【建议】 选择器的嵌套层级应不大于 3 级，位置靠后的限定条件应尽可能精确。

示例：

```css
/* good */
#username input {}
.comment .avatar {}

/* bad */
.page .header .login #username input {}
.comment div * {}
```

### 属性规范

【强制】 属性定义必须另起一行。

示例：

```css
/* good */
.selector {
    margin: 0;
    padding: 0;
}

/* bad */
.selector { margin: 0; padding: 0; }
```

【强制】 属性定义后必须以分号结尾。

示例：

```css
/* good */
.selector {
    margin: 0;
}

/* bad */
.selector {
    margin: 0
}
```

## >CSS三大特性

层叠、继承、优先级是学习CSS必须掌握的三大特性。

### CSS层叠性
所谓层叠性是指多种CSS样式的叠加。 是浏览器处理冲突的一个能力,如果一个属性通过两个相同选择器设置到同一个元素上，那么这个时候一个属性就会将另一个属性层叠掉 。
一般情况下，如果出现样式冲突，则会按照CSS书写的顺序，以最后的样式为准。
1. 样式冲突，遵循的原则是就近原则。 那个样式离着结构近，就执行那个样式。
2. 样式不冲突，不会层叠。

### CSS继承性（重点） 
所谓继承性是指书写CSS样式表时，子标签会继承父标签的某些样式，如文本颜色和字号。想要设置一个可继承的属性，只需将它应用于父元素即可。 
恰当地使用继承可以简化代码，降低CSS样式的复杂性。子元素可以继承父元素的样式（text-，font-，line-这些元素开头的都可以继承，以及color属性） 

### CSS优先性
定义CSS样式时，经常出现两个或更多规则应用在同一元素上，这时就会出现优先级的问题。 
考虑权重时：
```
1、继承样式的权重为0。即在嵌套结构中，不管父元素样式的权重多大，被子元素继承时，他的权重都为0，也就是说子元素定义的样式会覆盖继承来的样式。
2、行内样式优先。应用style属性的元素，其行内样式的权重非常高，可以理解为远大于100。总之，他拥有比上面提高的选择器都大的优先级。
3、权重相同时，CSS遵循就近原则。也就是说靠近元素的样式具有最大的优先级，或者说排在最后的样式优先级最大。
4、CSS定义了一个!important命令，该命令被赋予最大的优先级。也就是说不管权重如何以及样式位置的远近，!important都具有最大优先级。
```

###CSS特殊性（Specificity）

关于CSS权重，我们需要一套计算公式来去计算，这个就是 CSS Specificity，我们称为CSS 特性或称非凡性，它是一个衡量CSS值优先级的一个标准 具体规范入如下：

specificity用一个四位的数 字串(CSS2是三位)来表示，更像四个级别，值从左到右，左面的最大，一级大于一级，数位之间没有进制，级别之间不可超越。

| 继承或者* 的贡献值       | 0,0,0,0  |
| ------------------------ | -------- |
| 每个元素（标签）贡献值为 | 0,0,0,1  |
| 每个类，伪类贡献值为     | 0,0,1,0  |
| 每个ID贡献值为           | 0,1,0,0  |
| 每个行内样式贡献值       | 1,0,0,0  |
| 每个!important贡献值     | ∞ 无穷大 |

 **权重是可以叠加的** 

```
div ul  li   ------>      0,0,0,3

.nav ul li   ------>      0,0,1,2

a:hover      -----—>      0,0,1,1

.nav a       ------>      0,0,1,1   

#nav p       ----->       0,1,0,1
```

 **注意**：
	1、数位之间没有进制 比如说： 0,0,0,5 + 0,0,0,5 =0,0,0,10 而不是 0,0, 1, 0， 所以不会存在10个div能赶上一个类选择器的情况。
	2、继承的权重是 0。

总结优先级：
1. 使用了 !important声明的规则。
2. 内嵌在 HTML 元素的 style属性里面的声明。
3. 使用了 ID 选择器的规则。
4. 使用了类选择器、属性选择器、伪元素和伪类选择器的规则。
5. 使用了元素选择器的规则。
6. 只包含一个通用选择器的规则。
7. 同一类选择器则遵循就近原则。

**总结**：权重是优先级的算法，层叠是优先级的表现 

####！important 的使用

!important写法：(实际应用很少) 

```html
<style>
    div{
        font-size:20px;
        color:red !important;
    }
</style>
<div style="color:blue;">第一个div中的测试文字</div><!-- 变红 -->
<div style="font-size:28px;color:blue;">第二个div中的测试文字</div><!-- 变红，字体变大 -->
```

#### 权值

1.id选择器>类选择器>标签选择器
2.选择器权值：行内1000，id选择器100，类选择器10，标签选择器1，*0,继承样式最低
3.多个选择器选中同一个元素时，看权值；权值相同时，就近原则。
4.使用在属性值后面加一个 !important,增加选择器的权重 可以强制优先级最高，都带有!important时继续按照上述规则 
5.任何由程序员指定的样式优先级都大于浏览器默认样式

**多个选择器选中同一个元素时，看权值**

简单记法：  **!important > style属性 > id > class > 标签 > \* > 浏览器** 

## 6 文本的基本属性

文字颜色：color; font-size 字号；font-family 字体；  font-weight 字体加粗 bold;/正常normal;font-style字体样式 normal/italic 。

**基本语法格式**（综合样式设置）：

选择器{font:font-style font-weight font-size/line-height font-family;}

<!--文字：样式（倾斜） 加粗 字体大小/行高 字体-->

- 使用font属性时，必须按上面语法格式中的顺序来写，不能更换顺序，各个属性以空格隔开。
- 注意：其中不需要设置的属性可以省略（取默认值），但必须保留font-size和font-family属性，否则font属性将不起作用。

###6.1 文字颜色color

使用属性**color**来指定文字颜色，其属性取值是CSS颜色。 

**CSS颜色表（RGB分别代表红绿蓝，a代表alpha不透明度）** 

| 表示形式 | 说明                                                         | 举例                                                         |
| -------- | ------------------------------------------------------------ | ------------------------------------------------------------ |
| 颜色名称 | 通过英文单词指定颜色                                         | red、green、blue                                             |
| HEX      | 通过#RRGGBB或者#RGB的形式用十六进制（#0-9a-f）表示颜色       | f0000（同#f00）、#00ff00（同#0f0）、#0000ff（同#00f）        |
| RGB      | 通过rgb(r,g,b)的形式用三个0-255的数字表示颜色                | rgb(255,0,0),rgb(0,255,0),rgb(0,0,255);或者rgb(100%,0%,0%),百分号不能省，0也不能省百分号 |
| RGBA     | RGB形式的扩展，第四个字母alpha（不透明度）取值范围0~1,不可为负数，表示透明度，0表示完全透明 | rgba(0,0,0,0.6)表示半透明黑色                                |

### 6.2 文字大小font-size

使用属性**font-size**来指定文字大小，其属性取值是数字加CSS单位。 

**CSS单位表** 

| 单位 | 描述（作为文字大小单位）                            | 备注（作为长度单位）                       |
| ---- | --------------------------------------------------- | ------------------------------------------ |
| px   | 像素（最常用的绝对单位，中文偶数，英文奇数）        | 最常用的绝对单位                           |
| in   | 英寸                                                | 不常用                                     |
| cm   | 厘米                                                | 不常用                                     |
| em   | 最常用的相对单位，取父标签font-size的倍数           | 以当前标签的font-size为基准值取倍数        |
| rem  | 最近比较流行的相对单位，取html标签的font-size的倍数 | 移动端布局，不常用                         |
| %    | 以百分比形式取父标签font-size的倍数（不常用）       | 最常用的相对单位，取父元素对应长度的百分比 |

如果使用rem作为文字单位，就可以在用户改变当前浏览器字体时，更加智能的对字体大小进行控制，并且在桌面端和手机端表现良好。 

### 6.3 文字字体font-family

使用属性**font-family**来指定文字字体，属性取值一般是多个引号引起来的字体名称用逗号进行分隔，浏览器会从第一个字体开始尝试，如果不支持第一个字体则会自动向后查找。 

- 可以通过escape()来测试属于什么字体。
- 为了照顾不同电脑的字体安装问题，尽量只是用宋体和微软雅黑中文字体。

~~~html
font-family:"楷体","KaiTi","仿宋","FangSong";
~~~

**常见字体中英文名称对照表（了解即可，不用记）** 

| 中文名称   | 英文名称（推荐使用） | 文字示例                |
| ---------- | -------------------- | ----------------------- |
| 宋体       | SimSun               | 中文 English 123 ，。； |
| 黑体       | SimHei               | 中文 English 123 ，。； |
| 微软雅黑   | Microsoft YaHei      | 中文 English 123 ，。； |
| 微软正黑体 | Microsoft JhengHei   | 中文 English 123 ，。； |
| 楷体       | KaiTi                | 中文 English 123 ，。； |
| 仿宋       | FangSong             | 中文 English 123        |

### 6.4 文字粗细font-weight

| 属性值                         | 说明                                |
| ------------------------------ | ----------------------------------- |
| normal（常用）                 | 常规，默认值                        |
| bold（常用）                   | 加粗，常用                          |
| bolder                         | IE5+， 特粗体                       |
| lighter                        | IE5+，细体                          |
| number（100~900）(100的整数倍) | IE5+ ，数字400=normal;数字700=bold; |

> 1、在HTML中将对象直接加粗,可以用<b>或<strong>对其加粗。
>
> 2、使用CSS加粗对象可以使用font-weight:bold即可实现加粗。

###6.5 文字样式font-style

| 属性值  | 说明         |
| ------- | ------------ |
| normal  | 常规，默认值 |
| italic  | 斜体，常用   |
| oblique | 倾斜         |

## 7 段落属性

### 7.1 行间距(文本行高)line-height

line-height属性用于设置行间距，就是行与行之间的距离，即字符的垂直间距，一般称为行高。

line-height常用的属性单位有三种，分别是像素px、相对值em（字符倍数）、百分比%，实际工作中使用最多的是像素px。

一般情况下，行距比字号大7.8像素左右。

### 7.2 水平对齐方式text-align

用于设置文本内容的水平对齐方式，相当于html中的align对齐属性。**只有对块级元素（block）设定才会生效，并且可继承。**

text-align:排列值

属性值：left左对齐（默认）；   right右对齐 ；  center居中对齐（是让盒子里的内容水平居中，而不是让盒子居中对齐）；justify两端对齐，可以让大段的文本看起来比较整齐，不过两端对齐的表现可能会因浏览器的不同而有所不同。

> 块级元素水平居中：margin:0 auto;

### 7.3 垂直对齐方式vertical-align

设置文字的垂直对齐方式。语法：vertical-align:排列取值

| 排列取值    | 说明                           |
| ----------- | ------------------------------ |
| baseline    | 浏览器默认的垂直对齐方式       |
| sub         | 文字的下标                     |
| super       | 文字的上标                     |
| top         | 垂直靠上对齐                   |
| text-top    | 使元素和上级元素的字体向上对齐 |
| middle      | 垂直居中对齐                   |
| text-bottom | 使元素和上级元素的字体向下对齐 |

> line-height（行高）：子元素的行高与父元素的行高相等，垂直居中。

### 7.4 首行缩进text-indent

text-indent属性用于设置首行文本的缩进，浏览器默认不缩进，其属性值可为字符宽度的倍数em，也可为相对于浏览器窗口的百分比%，允许使用负值。建议使用em作为设置单位。

1em就是一个字的宽度，若是汉字的段落，1em就是一个汉字的宽度。

### 7.5 文本的修饰text-decoration

text-decoration通常用于给链接修改装饰效果。

| 值           | 描述                                                   |
| ------------ | ------------------------------------------------------ |
| none         | 默认。定义标准的文本                                   |
| underline    | 下划线，定义文本下的一条线，下划线也是我们链接自带的。 |
| overline     | 上划线，定义文本上的一条线                             |
| line-through | 中划线（删除线），定义穿过文本下的一条线               |
| blink        | 文字闪烁效果                                           |

### 7.6 文字阴影text-shaow（CSS3）

**text-shadow** 决定文字的阴影，部分浏览器不支持
**text-transform**:文字大小写转换。 none默认，capitalize单词以大写字母开头， uppercase全大写，lowercase全小写。
**white-space**:规定段落中的文本是否换行。normal默认处理方式（换行）；nowrap 强制在同一行内显示所有文本（不换行）

比较简单的文字阴影由四个属性值组成： 

~~~html
text-shadow:水平偏移（必写） 垂直偏移（必写） 模糊距离 阴影颜色
~~~

###7.7 单词间隔word-spacing 

指的是单词间的最小，最大和最佳间隙 或者说单词之间空格的大小。

语法：word-spacing:normal（正常的间隔）/in/长度值（可以是负值）+单位

### 7.8 字符间隔letter-spacing

指的是字符间的最小，最大和最佳间隙。

语法：letter-spacing:normal/inherit/initial

### 7.9 文本转换text-transform

文字大小写转换。语法：text-transform:转换值

 none默认原始值，capitalize单词以大写字母开头， uppercase全大写，lowercase全小写。

###7.10 



## 8 背景属性

###8.1 background-color（背景颜色）

指定背景颜色；属性值是CSS颜色

###8.2 background-size（背景大小）

更改背景图片大小；例如：background-size: 200px 210px; 

###8.3 background-image（背景图片）

指定背景图片；属性值是none（默认的无背景图片）/url （背景图片地址） 。提倡背景图片后面的地址，url不要加引号。 

> 若图片不重复的话，图片覆盖不到的地方会被背景颜色填充；若图片平铺，则会覆盖背景颜色。
>
> 属性允许指定一个图片展示在背景中（只有CSS3才可以多背景）可以和 background-color 连用。 

例如：url(/i/eg_bg_04.gif)        （url不要加引号）

###8.4 background-repeat（背景重复）

指定背景图片是否重复，以及哪个方向重复或者是否平铺

**属性值**：
repeat：背景图像在纵向和横向上平铺（默认的）
repeat-x：背景图片在横向上平铺
repeat-y：背景图片在纵向上平铺
no-repeat ：背景图像不平铺

> 设置背景图片是，默认把图片在水平和垂直方向平铺以铺满整个元素。

例如：background-image: url(/i/eg_bg_03.gif); background-repeat: repeat-y; 

###8.5 background-position（背景位置）

指定背景图片在背景中的位置 

**属性值**：

- position：center（背景图片居中对齐，用的最多）,left,right,top,bottom等方位值，通常对成对出现。
- length：百分比数值（%），由浮点数字和单位标识符组成的长度值（浮点数字px）。

> 1、设置或检索对象的背景图像位置，必须现指定background-image属性，默认值为：（0% 0%）。
>
> 2、若指定了一个值，则该值用于横坐标，纵坐标默认为50%；若有两个值，则第一个值用于横坐标，第二个值用于纵坐标。
>
> 3、position后面是横坐标和纵坐标，可以使用方位名词或者精确单位。
>
> 4、若精确单位和方位名词混合使用，则必须横坐标在前，纵坐标在后。（background-position:15px top;其中15px是横坐标，top是纵坐标。）

例如：background-image:url('/i/eg_bg_03.gif'); background-repeat:no-repeat; background-position:center; 

###8.6 background-attachment（背景附着） 

设置或检索背景图像是随对象内容滚动还是固定的

语法：background-attachment : scroll | fixed  

**属性值**：

- scroll：背景图像是随着对象内容滚动。
- fixed：背景图像固定

###8.7 背景透明（CSS3）

background：rgba(0,0,0,0.3);

最后一个参数是alpha透明度，取值范围0~1之间。

> 背景半透明是指盒子背景半透明，盒子里面的内容不受影响。

###8.8 背景简写

background属性的值的书写顺序官方没有强制标准。不过为了增加可读性，可以写成如下格式：

background:背景颜色 背景图片地址 背景平铺 背景滚动 背景位置

例如：background:transparent url(image.jpg) repeat-y scroll 50% 0; 

## 9 列表中的符号设置（重要）

list-style分解版：list-style-type项目符号类型；list-style-image项目符号图像；list-style-position项目符号位置。

可以指定列表中每一项的标志样式，既可以通过ul或者ol指定其中所有项的样式，又可以通过li单独制定每一项的样式。 

简写综合方式：list-style:square url()  inside 

**注意：list-style-type在使用时不考虑是ul还是ol** 

/*list-style-type: circle;*/
/*list-style-type: afar;*/
/*list-style-type: square;*/`

| list-style-position | 列表标记位置                                                 |
| ------------------- | ------------------------------------------------------------ |
| inside              | 列表项目标记放置在文本中，且环绕文本以标记为中心对齐。       |
| outside             | 默认值。保持标记位于文本的左侧。列表项目标记放置在文本以外，且环绕文本不以标记为中心对齐。 |
| inherit             | 规定应该从父元素继承list-style-position属性的值。            |

| list-style-type      | 无序列表标记类型   | 有序列表标记类型                          |
| -------------------- | ------------------ | ----------------------------------------- |
| none                 | 无标记             |                                           |
| disc                 | 默认。标记是实心圆 |                                           |
| circle               | 标记是空心圆       |                                           |
| square               | 标记是实心方块     |                                           |
| decimal              |                    | 有序数字，ol默认，标记是数字（1，2，3……） |
| decimal-leading-zero |                    | 以0开头的数字标记（01，02，03……）         |
| lower-roman          |                    | 小写罗马数字（）                          |
| upper-roman          |                    | 大写罗马数字：Ⅰ，Ⅱ，Ⅲ，Ⅳ，Ⅴ，Ⅵ，Ⅶ，Ⅷ，Ⅸ   |
| lower-alpha          |                    | 有序小写英文字母                          |
| upper-alpha          |                    | 有序大写英文字母                          |

| 有序列表的其他属性（type） | 作用                                                         |
| -------------------------- | ------------------------------------------------------------ |
| start                      | 定义开始的序号（<ol type="3">，即从3开始标记3，4，5……）      |
| value                      | 在某一列重新开始定义列序号（<li value="4"></li>,不管前面的序号，从这一列开始以4开头定义） |

##10 导航栏案例

使用技巧：在一行内的盒子内，设定行高等于盒子的高度，就可以是文字垂直居中。

```html
<head>
        <meta charset="utf-8">
        <style> 
        body {
            background-color: #000;
        }
        a {
            width: 200px;
            height: 50px;
            /* background-color: orange; */
            display: inline-block;  /* 把a 行内元素转换为行内块元素 */
            text-align: center;  /* 文字水平居中 */
            line-height: 50px;  /* 我们设定行高等于盒子的高度，就可以使文字垂直居中 */
            color: #fff;
            font-size: 22px;
            text-decoration: none;  /* 取消下划线 文本装饰 */
        }
        a:hover {  /* 鼠标经过 给我们的链接添加背景图片*/
            background: url(images/h.png) no-repeat; 
        }
        </style>
    </head>
    <body>
    <a href="#">专区说明</a>
    <a href="#">申请资格</a>
    <a href="#">兑换奖励</a>
    <a href="#">下载游戏</a>
    </body>
```



##11 简易盒子类型

CSS就三个大模块： 盒子模型 、 浮动 、 定位，其余的都是细节。要求这三部分，无论如何也要学的非常精通。 

所谓盒子模型就是把HTML页面中的标签（元素）看作是一个矩形的盒子，也就是一个盛装内容的容器。每个矩形都由元素的内容、内边距（padding）、边框（border）和外边距（margin）组成。 

![Alt text](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/B1MkJpFAxtIAAAAASUVORK5CYII=) 

### 11.1 盒子大小box-sizing

####手动指定宽度和高度的计算方式

| 属性值      | 说明                     |
| ----------- | ------------------------ |
| content-box | 宽高是内容区的宽高，默认 |
| border-box  | 宽高从边框开始计算，常用 |

指定最小宽度、最小高度、最大宽度、最大高度，常配合取相对值的宽度和高度使用。

#### content的width和height

用于指定宽度和高度，一般是操作内容区的宽度和高度，计算元素实际占用空间时需要考虑内边距和边框。width和height的属性值可以为不同单位的数值或相对于父元素的百分比%，实际工作中最常用的是像素值。 

大多数浏览器，如Firefox、IE6及以上版本都采用了W3C规范，符合CSS规范的盒子模型的总宽度和总高度的计算原则是： 

```html
 /*外盒尺寸计算（元素空间尺寸）*/
  Element空间高度 = content height + padding + border + margin
  Element空间宽度 = content width + padding + border + margin
  /*内盒尺寸计算（元素实际大小）*/
  Element Height = content height + padding + border （Height为内容高度）
  Element Width = content width + padding + border （Width为内容宽度）
```

**注意**：

*1、宽度属性width和高度属性height仅适用于块级元素，对行内元素无效（ img 标签和 input除外）。*

2、*计算盒子模型的总高度时，还应考虑上下两个盒子垂直外边距合并的情况*。*

3、*如果一个盒子没有给定宽度/高度或者继承父亲的宽度/高度，则padding 不会影响本盒子大*小

###11.2 边框border

border-width（宽度）:上边 [右边 下边 左边]; `
border-style（类型）:上边 [右边 下边 左边]; 
border-color（颜色）:上边 [右边 下边 左边]; 

综合写法：border: 宽度 类型 颜色`

border-top:（上边框）宽度 类型 颜色;` 
border-bottom:（下边框）宽度 类型 颜色;` 
border-left:（左边框）宽度 类型 颜色;` 
border-right:（右边框）宽度 类型 颜色;`

| 类型取值 | 说明                                     |
| -------- | ---------------------------------------- |
| none     | 没有边框，即忽略所有边框的宽度（默认值） |
| solid    | 单实线，最常用                           |
| dotted   | 点线，可能显示为实线                     |
| dashed   | 虚线，可能显示为实线                     |
| double   | 双实线，宽度表现不统一                   |

####表格的细线边框

以前学过的html表格边框很粗，这里只需要CSS一句话就可以美观起来。 让我们真的相信，CSS就是我们的白马王子（白雪公主）。

table{ border-collapse:collapse; } collapse 单词是合并的意思

border-collapse:collapse; 表示边框合并在一起。

####圆角边框(CSS3)

radius 半径（距离）

语法格式：                                

```
border-radius: 左上角  右上角  右下角  左下角;
```

border-radius（边框圆角）:指定四个角度圆角半径，取值超过短边的50%时相当于50%。

常见用法：

1. 制作圆角矩形，此时取值不要达到或超过短边的50%。
2. 制作圆形或椭圆形（用户头像常见），取值为短边的50%。

###11.3 内边距（内补白）padding

内容与边框之间的距离 

`padding-top:上边距`  `padding-bottom:下边距`  `padding-left:左边距`  `padding-right:右边距` 

简写方式如下：

`padding:四边边距` （一个值）
`padding:上下边距 左右边距`（两个值） 
`padding:上边距 左右边距 下边距` （三个值）
`padding:上边距 右边距 下边距 左边距`（四个值）（上右下左，从上边开始按顺时针旋转）

###11.4 外边距（外补白）margin

外边距：元素与元素之间的距离 。设置外边距会在元素之间创建“空白”， 这段空白通常不能放置其他内容。 

~~~html
margin-top:上边距 
margin-bottom:下边距 
margin-left:左边距 
margin-right:右边距

简写方式如下：
margin:四边边距 
margin:上下边距 左右边距 
margin:上边距 左右边距 下边距 
margin:上边距 右边距 下边距 左边距（上右下左，从上边开始按顺时针旋转）
~~~

注意：
1、盒子水平居中：margin: 0 auto 
	条件：必须是块级元素；盒子必须指定宽度（width）
	方法：给左右的外边距设置为auto

> margin：

2、父子关系中设置子元素margin时要慎重，可以使用padding。
给子元素设置margin-top,实际是给父元素设置了，解决方法：使用padding。
3、图片下方有空隙产生（父元素加边框出现的空隙）：img{vertical-align:middle;} vertical-align:top/bottom/middle 或img{display:block;}
4、各个浏览器下img有空隙 img{float:left;} 两个块元素，竖向的margin值不增加，会重叠，其间距为最大margin值 。
5、IE6横向margin加倍（产生因素：块属性、float、有横向margin ） 解决方法：display：inline；
6、制作网页时清除元素的默认内外边距，是为了更方便的控制网页中的元素：
*{
  padding:0;/*清除内边框*/
  margin:0;/*清除外边框*/
}

> 行内元素只有左右外边距，没有上下外边距。

> 上下内边距在ie6等低版本浏览器中会问题，尽量不用。

7、外边距合并：使用margin定义块元素的垂直外边距时，可能会出现外边距的合并。
8、嵌套块元素垂直外边距的合并：
	问题：对于两个嵌套关系的块元素，如果父元素没有上内边距及边框，则父元素的上外边距会与子元素的上外边距发生合并，合并后的外边距为两者中的较大者，即使父元素的上外边距为0，也会发生合并。![嵌套块元素垂直外边距的合并](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/嵌套块元素垂直外边距的合并.png)
	
解决办法：为父元素定义1像素的上边框或上内边距；为父元素添加overflow:hidden。
9、相邻块元素垂直外边距的合并：
当上下相邻的两个块元素相遇时，如果上面的元素有下外边距margin-bottom，下面的元素有上外边距margin-top，则他们之间的垂直间距不是margin-bottom与margin-top之和，而是两者中的较大者。这种现象被称为相邻块元素垂直外边距的合并（也称外边距塌陷）。

![相邻块元素垂直外边距的合并](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/相邻块元素垂直外边距的合并.png)

解决办法：避免这种情况即可。

  ### 11.5 盒子模型布局稳定性

根据稳定性来分，建议优先使用宽度（width）其次使用内边距（padding） 再次外边距（margin）。 

理由：
1、margin 会有外边距合并 还有 ie6下面margin 加倍的bug（讨厌）所以最后使用。
2、padding 会影响盒子大小， 需要进行加减计算（麻烦） 其次使用。
3、width 没有问题（嗨皮）我们经常使用宽度剩余法 、高度剩余法来做。

### 11.6 盒子阴影

语法：
	box-shadow:水平阴影 垂直阴影 模糊距离 阴影尺寸 阴影颜色  内/外阴影； 

| 值       | 描述                                     |
| -------- | ---------------------------------------- |
| h-shadow | 必写。水平阴影的位置，允许负值。         |
| v-shadow | 必写。垂直阴影的位置，允许负值           |
| blur     | 可选。模糊距离。                         |
| spread   | 可选。阴影的尺寸                         |
| color    | 可选。阴影的颜色。参阅CSS颜色值          |
| inset    | 可选。将外部阴影（outset）改为内部阴影。 |
1、前两个属性是必须写的。其余的可以省略。
2、外阴影 (outset) 但是不能写，默认；  想要内阴影 inset

```css
div {
            width: 200px;
            height: 200px;
            border: 10px solid red;
            /* box-shadow: 5px 5px 3px 4px rgba(0, 0, 0, .4);  */
            /* box-shadow:水平位置 垂直位置 模糊距离 阴影尺寸（影子大小） 阴影颜色  内/外阴影； */
            box-shadow: 0 15px 30px  rgba(0, 0, 0, .4);
}
```



### 11.7 文字与盒子居中时，图片和背景的区别
文字水平居中是 text-align: center
盒子水平居中是将左右margin改为auto
```css
text-align: center; /* 文字居中水平 */ 
margin: 10px auto; /* 盒子水平居中 左右margin 改为 auto 就阔以了 */ 
```
插入图片 我们用的最多 比如产品展示类
背景图片我们一般用于小图标背景 或者 超大背景图片
```css
section img {  
        width: 200px;/* 插入图片更改大小 width 和 height */
        height: 210px;
        margin-top: 30px;  /* 插入图片更改位置 可以用margin 或padding  盒模型 */
        margin-left: 50px; /* 插入当图片也是一个盒子 */
    }

aside {
        width: 400px;
        height: 400px;
        border: 1px solid purple;
        background: #fff url(images/sun.jpg) no-repeat;

        background-size: 200px 210px; /*  背景图片更改大小只能用 background-size */
        background-position: 30px 50px; /* 背景图片更该位置 我用 background-position */
    }
```

> 页面流（normal flow）

> 页面上的元素被解析后的一种渲染方式，类似于水流的方式。页面自上而下解析，遇到块级元素就让它占据一个新行，遇到行内元素就按照父元素的text-align属性按照一定的方向进行流动，如此循环进行页面渲染。
>
> 普通文档流：元素从上到下排列的顺序
>
> 脱离文档流：元素从正常的排列顺序被抽离（浮动，定位）
>
> CSS的3种定位机制：普通流（标准流）、浮动和定位。 

##12 浮动float

###12.1 浮动

将元素从正常排列顺序抽离出，排列在父元素的最左侧/最右侧（按照我们的意愿进行排列），若浮动元素超出当前行宽度，超出元素自动挤到下行。它允许周围其他文字和行内元素围绕自己进行布局。
浮动的目的就是为了让多个块级元素在同一行上显示。
在CSS中，通过float属性来定义浮动，其基本语法格式如下： 选择器{float:属性值;}

| 属性值 | 说明               |
| ------ | ------------------ |
| none   | 元素不浮动，默认值 |
| left   | 元素向左浮动       |
| right  | 元素向右浮动       |

- 当一个盒子浮动时（float不为none时），脱离页面流，漂浮在其他的标准流盒子上面，**将不再占据块级元素的空间**。

- 当一个**行内元素**浮动后，就**可以为其指定宽高**了。

- 浮动的盒子需要和标准流的父级搭配使用 ，元素添加浮动后，元素会具有行内块元素的特性。元素的大小完全取决于定义的大小或者默认的内容多少，浮动根据元素书写的位置来显示相应的浮动。 

- 浮动首先创建包含块的概念（包裹）。浮动的元素总是找离它最近的父级元素对齐。但是不会超出内边距（padding）的范围。

  ![浮动找最近的父类盒子对齐](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/浮动找最近的父类盒子对齐.jpg)

- 浮动的元素排列位置，跟上一个元素（块级）有关系。如果上一个元素有浮动，则A元素顶部会和上一个元素的顶部对齐；如果上一个元素是标准流，则A元素的顶部会和上一个元素的底部对齐。   

![浮动的两个子盒子](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/浮动的两个子盒子.jpg)



### 12.2 清除浮动

> 图文混排：给一个盒子里的图片作浮动，下方的图片会占领上方图片之前的位置，被覆盖
>
> 

清除浮动后造成的影响。本质上是为了解决父级元素因为子级元素浮动引起内部高度为0的问题。

浮动应用：页面布局中  多栏布局，两端对齐布局，导航栏。

![正常标准盒子](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/正常标准盒子.jpg)

![子盒子浮动](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/子盒子浮动.jpg)

方法一：父元素设置宽高（高是必须的）border padding  margin   #当高度不能固定的时候就不适用了
方法二：父元素触发BFC的方式，设置 overflow:hidden|auto|scroll

方法三：给需要清除浮动的元素设置clear:left/right/both，清除在该元素之上其他元素浮动造成的影响。

>代码简洁，但内容增多容易造成不会自动换行，导致内容被隐藏掉，无法显示需要溢出的元素。
方法三：属性clear——可以让一个元素主动向下移动来保持自己和其他浮动元素和自己不在同一行。
基本语法格式：选择器{clear:属性值;}
存在问题：给该元素设置margin时没有效果，使影响元素的margin失效 

| 属性值 | 说明                 |
| ------ | -------------------- |
| none   | 不清除浮动，默认值   |
| left   | 清除左边的浮动       |
| right  | 清除右边的浮动       |
| both   | 清除左右的浮动，常用 |
 方法四：使用after伪元素清除浮动-实际应用（综合最优的方法——万能法）

在需要清除自身里面的浮动对其他盒子影响的盒子里，设置:after；或者在需要清除上方盒子内的浮动对当前盒子的影响时，在当前盒子设置:before

:after 方式是空元素的升级版，好处是不用单独加标签

```css
.clearfix:after {  
    content: "."; 
    display: block; 
    height: 0; 
    clear: both; 
    visibility: hidden;  
}  

.clearfix {*zoom: 1;}   /* IE6、7 专有 */
```

> 注意： content:”.” 里面尽量跟一个小点，或者其他，尽量不要为空，否则再firefox 7.0前的版本会有生成空格。 
符合闭合浮动思想 结构语义化正确 ,但是由于IE6-7不支持:after，使用 zoom:1触发 hasLayout。 
方法五：使用before和after双伪元素清除浮动

```css
.clearfix:before,.clearfix:after { 
  content:"";
  display:table;  /* 这句话可以触发BFC BFC可以清除浮动,BFC我们后面讲 */
}
.clearfix:after {
 clear:both;
}
.clearfix {
  *zoom:1;
}
```
代码更简洁 ,但是由于IE6-7不支持:after，使用 zoom:1触发 hasLayout。 

## 13 定位position

指定元素的定位方式，默认为**static**，根据页面流进行定位。当一个元素定位不为**static**时，可以用（边偏移属性）**top**、**left**、**right**、**bottom**和**z-index**来操作元素的位置。 

语法格式：选择器{position:属性值;}

| 属性值   | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| static   | 静态定位：各个元素在HTML页面流中默认的位置。不可用边偏移     |
| relative | 相对定位-相对元素的原来位置进行偏移，结合方位进行位置确定，但元素在页面流中的位置依然保留 |
| absolute | 绝对定位-相对于具有定位的父元素位置进行偏移；元素模式（无论是块级元素还是行内元素）转换为行内块模式（若是行内元素）。 |
| fixed    | 固定定位-相对于浏览器窗口进行的固定位；元素模式（无论是块级元素还是行内元素）转换为行内块模式。 |

### 13.1 相对定位relative

position:relative——指定元素为相对定位，元素以在页面中原来占据的位置为原点，根据（top、left、right和bottom）的取值进行偏移，每次移动的位置，是以自己的左上角为基点移动（相对于自己来移动位置） 。但在偏移后，原位置任然占据空间。 相对定位的盒子仍在标准流中，它后面的盒子仍以标准流方式对待它。（相对定位不脱标） 。多用于子绝互相，单独应用很少。

### 13.2 绝对定位absolute

position:absolute——指定元素为绝对定位，元素不再占据任何页面空间（完全脱标）。此时会根据其最近的第一个**不是static定位**（绝对、相对、固定定位）的父元素结合（top、left、right和bottom）进行定位。**若找不到这种父元素，则根据整个页面进行定位**。 

**绝对定位的盒子水平/垂直居中：**
普通的盒子是左右margin 改为 auto就可， 但是对于绝对定位就无效了

定位的盒子也可以水平或者垂直居中，有一个算法。
	1、首先left50%父盒子的一半大小
	2、然后走自己外边距负的一半值就可以了 margin-left。

### 13.3 子绝父相（外相对，内绝对）

子绝父相：因为子级是绝对定位，不会占有位置， 可以放到父盒子里面的任何一个地方。父盒子布局时，需要占有位置，因此父亲只能是相对定位。
一种在处理某些定位问题时较为常见的书写方式。当我们想让一个子元素相对于其某个父元素位置确定，我们就可以设置这个父元素为相对定位，并把这个子元素设置后绝对定位后结合（top、left、right和bottom）进行处理。
定位位置，不受父元素padding的影响。
可配合使用z-index来设置元素的层叠顺序。
属性值为：整数。默认值是0。z-index值越大越靠上。

### 13.4 固定定位fixed（常用于打广告） 

position:fixed——指定元素为固定定位，元素将脱离页面流的控制，不再占据任何页面空间（完全脱标）。元素会相对于整个视口（用户可以看到的页面部分，即可视窗口）进行定位，当页面滚动时，该元素保持固定不动。

### 13.5 叠放次序（z-index）

当对多个元素同时设置定位时，定位元素之间有可能会发生重叠。 在CSS中，要想调整重叠定位元素的堆叠顺序，可以对定位元素应用z-index层叠等级属性，其取值可为正整数、负整数和0。 例如：z-index:2;

**注意**： 

1. z-index的默认属性值是0，取值越大，定位元素在层叠元素中越居上。
2. 如果取值相同，则根据书写顺序，后来居上。
3. 后面数字一定不能加单位。
4. 只有相对定位，绝对定位，固定定位有此属性，其余标准流，浮动，静态定位都无此属性，亦不可指定此属性。

###13.6 定位模式转换

跟浮动一样，元素添加了绝对定位和固定定位之后，元素模式也会发生转换，都转换为行内块模式， 比如**行内元素**如果添加了绝对定位或者固定定位后浮动后，可以不用转换模式，直接给高度和宽度。

### 13.7 四种定位总结

| 定位模式         | 是否脱标占有位置     | 是否可以使用边偏移 | 移动位置基准                     |
| ---------------- | -------------------- | ------------------ | -------------------------------- |
| 静态static       | 不脱标，正常模式     | 不可以             | 正常模式                         |
| 相对定位relative | 不脱标，占有位置     | 可以               | 相对自身位置移动（自恋型）       |
| 绝对定位absolute | 完全脱标，不占有位置 | 可以               | 相对于定位父级移动位置（拼爹型） |
| 固定定位fixed    | 完全脱标，不占有位置 | 可以               | 相对于浏览器移动位置（认死理型） |

## 14 元素的显示与隐藏

在CSS中有三个显示和隐藏的单词比较常见，我们要区分开，他们分别是 display ，visibility 和 overflow。 
他们的主要目的是让一个元素在页面中消失，但是不在文档源码中删除。 最常见的是网站广告，当我们点击类似关闭不见了，但是我们重新刷新页面，它们又会出现和你玩躲猫猫！！ 

###14.1 display 显示

作用：display属性用于设置或检索元素是否显示和显示方式。
特点：隐藏之后，不再保留位置。

| 属性值               | 说明                                   |
| -------------------- | -------------------------------------- |
| display:block        | 对象转换为块级元素，也有显示元素的意思 |
| display:inline       | 行内元素                               |
| display:none         | 隐藏显示                               |
| display:inline-block | 行内块元素，可以被指定宽高的类行内元素 |

### 14.2 visibility 可见性
作用：用于设置或检索是否显示对象
特点：隐藏之后，继续保留原有位置。

visibility:visible 对象可视

visibility:hidden 对象隐藏

**元素不显示的两种形式：visibility:hidden占空间；display:none不占空间。**

###14.3 overflow 溢出
作用：检索或设置当对象的内容超过其指定高度及宽度时如何管理内容。

visible : 不剪切内容也不添加滚动条。
auto :  超出自动显示滚动条，不超出不显示滚动条
hidden : 不显示超过对象尺寸的内容，超出的部分隐藏掉
scroll : 不管超出内容否，总是显示滚动条

- 行内元素与块级元素的比较

|          | 块级元素                                 | 行内元素                     |
| -------- | ---------------------------------------- | ---------------------------- |
| 占据空间 | 总是占据一个新行                         | 可以和其他行内元素占同一行   |
| 内部内容 | 可以有文字和其他任意元素                 | 只能有其他行内元素和文字     |
| 边距     | 可以自由指定外边距和内边距（行内块也是） | 竖直方向上的内外边距不起作用 |

 ### 14.4 元素可以被指定宽高的情况
当元素满足以下任一条件时，可以被手动指定宽高。 

1. 是块级元素。
2. 是img或input。
3. 是行内块元素。
4. 是float不为none的元素。
5. 是定位方式不为static或relative的元素。

###14.5 background详解与CSS精灵

- **background详解**

  1.仅仅指定背景色： 
  ​    background:CSS颜色; 相当于 background-color:CSS颜色; 
  2.仅仅指定背景图片： 
  ​    background:url(图片路径); 相当于 background-image:url(图片路径); 
  ​    background:url(图片路径) no-repeat; 相当于 background-image:url(图片路径) no-repeat; 
  ​    （no-repeat用于让背景图片不重复） 
  3.同时指定背景色和背景图片： 
  ​    background:CSS颜色 url(图片路径); 
  4.指定背景图片的位置： 
  ​    background:url(图片路径) no-repeat 水平偏移 垂直偏移

- **雪碧图和CSS精灵**

  像下面这样，由许多小图拼接成的一大张图像就可以叫做一个雪碧图。因为其需要配合CSS精灵使用，所以有时候也被叫做精灵图。 
  CSS精灵（CSS Sprite）是一种使用CSS属性background来从雪碧图上取图片的技术。

  - **使用CSS精灵的好处**

  我们知道，当我们访问一个网页时会向服务器发送一次请求。如果这个网页中，引入了其他文件（比如CSS、图片），那么同样需要向服务器发送请求。

  服务器接收到请求后，会根据请求的地址去寻找对应文件，并将它发送给客户端，这是一个比较耗时耗力的操作。

  如果使用CSS精灵，那我们从同一张雪碧图上取多次图片只需要向服务器发送一次请求。

  因此，合理使用CSS精灵技术，能够减少请求次数，从而

  > **1. 减轻服务器压力** 
  > **2. 减少用户的等待时间** **3. 图片不易丢失** **4.后期维护简单**

  ![Alt text](https://github.com/DeerKing007/HTML-CSS_learning_notes/blob/master/HTML%2BCSS/picture/h8W2Tk2Yl5f0gAAAABJRU5ErkJggg==) 

## 15 CSS高级技巧

### 15.1 CSS用户界面样式

所谓的界面样式， 就是更改一些用户操作样式， 比如 更改用户的鼠标样式， 表单轮廓等。但是比如滚动条的样式改动受到了很多浏览器的抵制，因此我们就放弃了 ，防止表单域拖拽 。

####鼠标样式cursor

设置或检索在对象上移动的鼠标指针采用何种系统预定义的光标形状。 

| 属性值(可使用鼠标指向测试) | 说明                                    |
| -------------------------- | --------------------------------------- |
| auto                       | 自动根据当前位置判断，默认值            |
| default                    | 系统默认光标，通常是箭头                |
| pointer                    | 系统指示光标，通常是手形                |
| text                       | 系统文本光标，通常类似于细高的大写字母I |
| wait                       | 系统等待光标，通常是转动的彩色圆圈      |
| help                       | 系统帮助光标，通常是箭头加一个问号      |

#### vertical-align 垂直对齐
让带有宽度的块级元素居中对齐，是margin: 0 auto;
让文字居中对齐，是 text-align: center;
vertical-align 垂直对齐， 这个看上去很美好的一个属性， 实际有着不可捉摸的脾气。
```
vertical-align:baseline(默认)||top||middle||bottom
```
vertical-align 不影响块级元素中的内容对齐，它只针对于行内元素或者行内块元素，特别是行内块元素， **通常用来控制图片、表单与文字的对齐。** 默认的图片会和文字基线对齐。 

#### 去除图片底侧空白缝隙
 图片或者表单等行内块元素，他的底线会和父级盒子的基线对齐。这样会造成一个问题，就是图片底侧会有一个空白缝隙。 
解决的方法就是：
1、给img 添加vertical-align:middle | top等。 让图片不要和基线对齐。
2、给img 添加display：block; 转换为块级元素就不会存在问题了。 

#### 轮廓 outline

是绘制于元素周围的一条线，位于边框边缘的外围，可起到突出元素的作用。 

```css
outline:outline-color||outline-style||outline-width
```

但是我们都不关心可以设置多少，我们平时都是去掉的。

最直接的写法是 ： outline: 0; 或者 outline: none;

```html
<input type="text" style="outline:0;"/>
```

### 15.2 溢出的文字隐藏

#### word-break：自动换行

normal：使用浏览器默认的换行规则。
break-all：允许在单词内换行。
keep-all：只能在半角空格或连字符处换行。
主要处理英文单词

####white-space

white-space设置或检索对象内文本显示方式。通常我们使用于强制一行显示内容
normal：默认处理方式 
nowrap：强制在同一行内显示所有文本，直到文本结束或者遭遇br标签对象才换行。
可以处理中文

#### text-overflow：文字溢出

ext-overflow : clip | ellipsis

设置或检索是否使用一个省略标记（…）标示对象内文本的溢出

clip：不显示省略标记（…），而是简单的裁切

ellipsis：当对象内文本溢出时显示省略标记（…）

注意一定要首先强制一行内显示，再次和overflow属性 搭配使用

### 15.3 核心技术

核心技术就是利用CSS精灵（主要是背景位置）和盒子padding撑开宽度, 以便能适应不同字数的导航栏。
一般的经典布局都是这样的：
```
<li>
  <a href="#">
    <span>导航栏内容</span>
  </a>
</li>
```
总结：
1. a 设置 背景左侧，padding撑开合适宽度。
2. span 设置背景右侧， padding撑开合适宽度 剩下由文字继续撑开宽度。
3. 之所以a包含span就是因为 整个导航都是可以点击的。

##16 其他补充

###16.1 BFC(块级格式化上下文)

BFC(Block formatting context)

直译为”块级格式化上下文”。

**那些元素会具有BFC的条件**

不是所有的元素模式都能产生BFC，w3c 规范：
display 属性为 block, list-item, table 的元素，会产生BFC.
大家有么有发现这个三个都是用来布局最为合理的元素，因为他们就是用来可视化布局。
注意其他的display属性，比如 line 等等，他们创建的是 IFC ，我们暂且不研究。

**什么情况下可以让元素产生BFC**

## 

