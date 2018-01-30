---
title: emmet 用法，超级方面，值得收藏
date: 2018-01-30 22:58:27
tags:
---
# 一、简写语法

Emmet 用和 CSS 选择器相似的语法来描述元素的嵌套层级关系和属性，实现 HTML/XML/CSS 等代码的智能自动补全。

其通过文件名后缀识别文件类型，从而使用对应的自动补全语法。默认自动补全快捷键为制表符（Tab）。

下文中的“自动补全”均指“按下快捷键后自动补全”。

注意：Emmet 语法中的空格表示结束解析，所以书写语句中不能出现空格。

# 1、元素

在编辑器中输入元素名称，即可自动补全生成 HTML 标签，即使不是标准的 HTML 标签。

```// before
div
foo

// after
<div></div>
<foo></foo>

输入 ! 或者 html:5 可以自动补全为 HTML5 基本结构。想要输出 HTML4 文本类型申明可以输入 html:4s 或者 html:4t 。

// before
! (或html:5)

// after
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Document</title>
</head>
<body>
    
</body>
</html>


2、嵌套操作

1）child：使用 “>” 生成子元素

// before
div>ul>li

// after
<div>
    <ul>
        <li></li>
    </ul>
</div>


2) Sibling: 使用符号 “+” 生成兄弟元素


// before
div+p+bq

// after
<div></div>
<p></p>
<blockquote></blockquote>

3) Climb-up:使用 “^” 生成父元素，与 “>” 相反


// before
div+div>p>span+em^bq

// after
<div></div>
<div>
    <p><span></span><em></em></p>
    <blockquote></blockquote>
</div>

你甚至可以使用多个 “^”。


// before
div+div>p>span+em^^^bq

// after
<div></div>
<div>
    <p><span></span><em></em></p>
</div>
<blockquote></blockquote>

4) Multiplication:使用 “*” 操作符生成多个元素

复制代码
// before
div>ul>li*5

// after
<div>
    <ul>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
        <li></li>
    </ul>
</div>

5) Grouping:使用 “()” 操作符将元素分组，实现更复杂的简写任务


// before
// "+" 后面的元素与括号中的第一个元素属于兄弟关系
div>(header>ul>li*2)+footer>p

//after
<div>
    <header>
        <ul>
            <li></li>
            <li></li>
        </ul>
    </header>
    <footer>
        <p></p>
    </footer>
</div>

3. 属性操作

在简写时就可以为元素设置属性。

1) id 与 class

简写时，元素与 id 属性值之间用 “#” 分隔，与 class 属性值之间用 “.” 分隔。


// before
div#header+div.page+div#footer.class1.class2.class3

// after
<div id="header"></div>
<div class="page"></div>
<div id="footer" class="class1 class2 class3"></div>

2) 其他属性

使用 [attr] 标记添加其他属性。

// before
td[title='hello' colspan=3]

// after
<td title="hello" colspan="3"></td>
注意：

方括号中可添加任意数量的属性
不给定属性值，则属性值为""。td[colspan title]将得到 <td colspan="" title=""></td>
属性值可用单引号或双引号，输出统一为双引号
如果属性值中没有空格，则引号可省略
3) 为条目编号

使用 “*” 符号生成的多个元素，可用 “$” 操作符实现从1到 N 自动编号。

// before
li.item$*3

// after
<li class="item1"></li>
<li class="item2"></li>
<li class="item3"></li>

可在 “$” 后添加 “@n” 修改编号的起始值为n。

复制代码
// before
li.item$@3*3

// after
<li class="item3"></li>
<li class="item4"></li>
<li class="item5"></li>


可在 “$” 后添加 “@-” 修改编号的方向。


// before
li.item$@-3*3

// after
<li class="item5"></li>
<li class="item4"></li>
<li class="item3"></li>

## 4. 添加文本

使用花括号 “{}” 操作符为元素添加文本节点。

// before
a[href=me.htm]{click me}

// after
<a href="me.htm">click me</a>
因为文本也是节点，所以 a[href=me.htm]{click me} 与 a[href=me.htm]>{click me} 等价。

但有多个元素时则要注意。

// before
a[href=me.htm]{click me}+p{ok}
a[href=me.htm]>{click me}+p{ok}

// after
<a href="me.htm">click me</a>
<p>ok</p>

<a href="me.htm">click me
    <p>ok</p>
</a>
