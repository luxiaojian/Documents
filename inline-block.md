#解决Inline Block元素之间的空隙  
最近我看到这个问题这个问题好几次在`twitter`上被提及和关于这个问题的Dabblet上[一个有趣的代码片段](http://dabblet.com/gist/2422174)  ,所以在这篇文章中我会好好讨论一下这个问题。  
描述问题:如果你按正常的格式来排版一系列`inline-block`元素，那么它们之间就会出现间隙。  
也就是说:   
 
```html  
<nav>
  <a href="#">One</a>
  <a href="#">Two</a>
  <a href="#">Three</a>
</nav>  
```
```css
nav a {
  display: inline-block;
  padding: 5px;
  background: red;
}
```
浏览器里显示结果是  
![](spaces.png)
我们希望元素能够紧凑的排列，所以我在这个导航的例子中，需要去掉不可以点击的部分。  
我不认为这是一个bug,这仅仅是因为行内的设置对元素起作用了。文字间的间隙可以通过向右键入一个空格来实现。同样块之间的间隙就像文字之间的间隙一样。  
下面总结了一些可以消除间隙让inline block元素紧凑排列方法。   
 
###Remove the spaces  
HTML标签之间的空隙(换行符和制表符都算空隙，需要清除)，使用下面技巧中的其中一个来压缩HTML就可以解决这个问题。

```html
<ul>
  <li>
   one</li><li>
   two</li><li>
   three</li>
</ul>
```  
或者  

```html
<ul>
  <li>one</li
  ><li>two</li
  ><li>three</li>
</ul>
```

或者通过加注释  

```html
<ul>
  <li>one</li><!--
  --><li>two</li><!--
  --><li>three</li>
</ul>
```
这些解决方法都很受欢迎，但是它们都是小戏法。  

###Negative margin
通过`-4px`的margin（可以根据父元素字体大小来调整移动距离）可以移动元素回原位。好像在IE6和IE7上有点问题，但是忽略IE6和IE7却可以换来代码的整洁。  

```css
nav a {
  display: inline-block;
  margin-right: -4px;
}
```

###Skip the closing tag  
HTML5不要求标签的闭合，但是必须承认，这让人感觉怪怪的。

```html
<ul>
  <li>one
  <li>two
  <li>three
</ul>
```
###Set the font size to zero  
字体的宽度设置为0，空隙也就变为0。  

```css
nav {
  font-size: 0;
}
nav a {
  font-size: 16px;
}
```  
###Just float them instead  
也许根本就不需要使用inline-block,使用浮动或者其他方式。这样允许设置它们的宽，高，以及padding