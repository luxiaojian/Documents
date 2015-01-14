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
    	
    	
* 组织