#使用Emment进行html标签简写 
>Emment是一个编辑器插件,我是在`sublime text`中使用的,使用方法也很简单，每次按照语法规则写完后，按一下`tab`就可以实现自动补全。  
 
##语法规则（Syntax）  
* 子元素选择符`>`  
   `div>ul>li`  
	
		<div>
    		<ul>
    			<li></li>
    		</ul>
    	</div>  
    	
* 兄弟元素选择符号`+`

	`div+div`  
	
		<div></div>
    	<div></div>  
    	
* 上级元素选择符号`^`  

	`div+div>p>span>em^bq`    
	
		<div> </div>
      	<div>
    	  	<p>
    			<span><em></em></span>
    			<blockquote></blockquote>
    	 	</p>
      	</div>  
       
       
    `div+div>p>em^^bq`  
     
    	<div></div>
    	<div>
    		<p><em></em></p>
    	</div>  
    	

* 乘法计算符`*`

	`div>ul>li*2`
	
		<div>
			<ul>
				<li></li>
				<li></li>
			</ul>
		</div>  	
* 组织元素符号（） 

	`div>(header>ul>li*2)+footer>p`
		
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
	
	`(div>dl>(dt+dd)*3)+footer>p` 
	
		<div>
			<dl>
				<dt></dt>
				<dd></dd>
				<dt></dt>
				<dd></dd>
				<dt></dt>
				<dd></dd>
			</dl>
		</div>
		<footer>
			<p></p>
		</footer>

* 元素属性符号`[]`

	`h1[title=header]`
	
		<h1 title="header"></h1>
		
* 内容符号`{}`  

	`a{click me}`   
	 
		<a href="">click me</a>

		
* 元素自动递增符号`$`  

	`div>ul>li.item$*4`	  
	
		<ul>
			<li class="item1"></li>
			<li class="item2"></li>
			<li class="item3"></li>
			<li class="item4"></li>
		</ul>

	`h$[title=item$]{header $}*3`
	
		<h1 title="item1">header 1</h1>
		<h2 title="item2">header 2</h2>
		<h3 title="item3">header 3</h3>
	
	`div>ul>li.item$$$*3`  
	
		<div>
			<ul>
				<li class="item001"></li>
				<li class="item002"></li>
				<li class="item003"></li>
			</ul>
		</div>
	
	`div>ul>li.item$@-*5`逆序排布  
	
		<div>
			<ul>
				<li class="item5"></li>
				<li class="item4"></li>
				<li class="item3"></li>
				<li class="item2"></li>
				<li class="item1"></li>
			</ul>
		</div>
	`div>ul>li.item$@3*5`从序号3开始计算，往下排5个。  
	
		<div>
			<ul>
				<li class="item3"></li>
				<li class="item4"></li>
				<li class="item5"></li>
				<li class="item6"></li>
				<li class="item7"></li>
			</ul>
		</div>  

##HTML中的简写语法
* `!`或者`html:5`  
  
		<!DOCTYPE html>
		<html lang="en">
		<head>
			<meta charset="UTF-8">
			<title>Document</title>
		</head>
		<body>
	
		</body>
		</html>   
* `meta:utf`  

		<meta http-equiv="Content-Type" content="text/html;charset=UTF-8">  

* `link:css`  

		<link rel="stylesheet" href="style.css">  
		
* `link:favicon`

		<link rel="shortcut icon" type="image/x-icon" href="favicon.ico">  
		
* `link:touch`

		<link rel="apple-touch-icon" href="favicon.png">  
* `style`  

		<style></style>  
		
* `script:src`

		<script src=""></script>
		
##css中的简写语法  

* 快速创建`font-face`  

	* `@f`
	
			@font-face {
				font-family:;
				src:url();
			}
		
	* `f+`  
	
			@font-face {
				font-family: 'FontName';
				src: url('FileName.eot');
				src: url('FileName.eot?#iefix') format('embedded-opentype'),
				 	url('FileName.woff') format('woff'),
				 	url('FileName.ttf') format('truetype'),
				 	url('FileName.svg#FontName') format('svg');
				font-style: normal;
				font-weight: normal;
			}	
			
* 补足浏览器私有前缀  
	* 私有前缀说明 `w` -`-webkit-` `m`-`-moz-` `s`-`-ms-` `o`-`-o-`
     比如在输入`-wm-trf`
     
     		-webkit-transform: ;
			-moz-transform: ;[link](http://)
			transform: ;	

###一些关于Emmet的文档  
* [Emmet Documentation](http://docs.emmet.io/cheat-sheet/)
* [Emmet文档](http://docs.emmet.io/abbreviations/syntax/)



