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
		