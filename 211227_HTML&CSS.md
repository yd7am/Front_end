# HTML/CSS
[CSS](https://www.runoob.com/css/css-id-class.html)

***
####选择器
1.ID 选择器（ID selector，IS）：使用 # 标识selector，语法格式：`#S{...}`（S为选择器名）。
2.类选择器（class selector，CS）：使用 . 标识selector，语法格式：`.S{...}`（S为选择器名）。
3.元素选择器（element selector，ES）：又叫标签选择器，使用标签名作为selector名，语法格式：`S{...}`（S为选择器名）。
4.属性选择器（attribute selector，AS）。[AS](https://www.runoob.com/css/css-attribute-selectors.html)
5.包含选择器（package selector，PS）：指定目标选择器必须处在某个选择器对应的元素内部，语法格式：`A B{...}`（A、B为HTML元素/标签，表示对处于A中的B标签有效）。
6.子选择器（sub-selector，SS）：类似于PS，指定目标选择器必须处在某个选择器对应的元素内部，两者区别在于PS允许"子标签"甚至**"孙子标签"**及嵌套更深的标签匹配相应的样式，而SS**强制**指定目标选择器作为 包含选择器对应的标签 内部的标签(**直接子代**)，语法格式：`A>B{...}`（A、B为HTML元素/标签）。
7.兄弟选择器（brother selector，BS）：BS是CSS3.0新增的一个选择器，语法格式：`A~B{...}`（A、B为HTML元素/标签，表示A标签匹配selector的A，B标签匹配selector的B时，B标签匹配样式）
7.1 +选择器：`A+B{...}`如果需要选择**紧接**在另一个元素后的元素，而且二者有相同的父元素，可以使用相邻兄弟选择器。 
8.通用选择器:`*{...}`它的作用是匹配 html 中的所有元素标签。
9.待补充...

>一：#a,b{…………｝ //一个id叫a和一个标签是b的样式
>二：#a b{…………｝  //一个id叫a下面的一个标签是b的样式
>三：#a:b{…………｝  //一个id叫a的伪类b，例如：a:hover
>四：#a.b{…………｝  //一个id叫a的下面的class叫b的样式
>五：p.marked{ }: 为所有 class="marked" 的 p 元素指定一个样式。
>六：.marked p{ }: 为所有 class="marked" 元素内的 p 元素指定一个样式。

####样式优先级
[优先级](https://www.runoob.com/w3cnote/css-style-priority.html)
####块级元素与内联元素
**块级元素(block)特性：**
总是独占一行，表现为另起一行开始，而且其后的元素也必须另起一行显示;
宽度(width)、高度(height)、内边距(padding)和外边距(margin)都可控制;

**内联元素(inline)特性：**
和相邻的内联元素在同一行;
宽度(width)、高度(height)、内边距的top/bottom(padding-top/padding-bottom)和外边距的top/bottom(margin-top/margin-bottom)都不可改变，就是里面文字或图片的大小;

**块级元素主要有：**
 address , blockquote , center , dir , div , dl , fieldset , form , h1 , h2 , h3 , h4 , h5 , h6 , hr , isindex , menu , noframes , noscript , ol , p , pre , table , ul , li
**内联元素主要有：**
a , abbr , acronym , b , bdo , big , br , cite , code , dfn , em , font , i , img , input , kbd , label , q , s , samp , select , small , span , strike , strong , sub , sup ,textarea , tt , u , var
**可变元素(根据上下文关系确定该元素是块元素还是内联元素)：**
applet ,button ,del ,iframe , ins ,map ,object , script

**CSS中块级、内联元素的应用：**
利用CSS我们可以摆脱上面表格里HTML标签归类的限制，自由地在不同标签/元素上应用我们需要的属性。

主要用的CSS样式有以下三个：
display:block  -- 显示为块级元素
display:inline  -- 显示为内联元素
display:inline-block -- 显示为内联块元素，表现为同行显示并可修改宽高内外边距等属性
我们常将所有<li>元素加上display:inline-block样式，原本垂直的列表就可以水平显示了。