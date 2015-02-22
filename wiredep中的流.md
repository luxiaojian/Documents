#Wiredep中的Stream
**Wiredep**是一个小巧玲珑的`Node`包但却做了一件很棒的事情，根据依赖配置文件中的依赖关系把`Bower`中的成分添加到html或者CSS文件中去。  
你可能以前对`wiredep`从未耳闻，但是很可能你已经在使用它了，因为你以前用过一个很出名的`Grunt`插件`grunt-wiredep`。  
不管那个`node`包还是`Grunt`插件出自一个来自美国密歇根州的小伙之手，这个很友善和才华的小伙叫`Stephen Sawchuk`,我对这位小伙了解并不是很多，甚至他都没有把我添加到他的小组中去管理`Wiredep`,他在`Yeomen`小组创造了`grunt-wiredep`这个插件用在一个编译系统中，这个编译系统在很多`Yeomen`插件中得到应用,并且从中提取了出了我们现在所看到的`wiredep`,同时他把`grunt`插件修改成了一个`wiredep`的包装器。  
总之，介绍就到这里，下面让我们跳转到本文的主旨上。    
#Wiredep,Streams and Gulp ,oh my !  
我将会讨论一下`stream`和它与`Gulp`之间的联系。`stream`非常酷，并且它是让`Gulp`工作的必要部分。  
也许你会问我这里谈得为什么不是`gulp-wiredep`插件，在我回答这个问题之前，让我们一起看一句我从`gulp`网站上摘取的一句`gulp`的原则：  
>通过在结构上精简代码，`gulp`保持让简单的事情更加简单让复杂的工作变得可以控制。   
 
 换句话说就是当你可以在`gulp`编译中直接使用`wiredep`为什么还要专门创造一个`gulp-wiredep`呢？确实，你可以在`gulp`的中任务中直接使用`wiredep`,但是你一旦想尝试更多复杂的事情，你也许会碰到很多问题，因为你不能把`wiredep`和`gulp`中的其他流合并在一起。  
也就是说在最近你知道`wiredep`支持`stream`之前，它没有形成文件。(某种程度上，要感谢我的努力)，我深挖了一下`wiredep`的源码，想尝试发现一些什么，果然我发现一些与`stream`相关的代码，我继续更深的挖掘，确实，`wiredep`通过完美地与`gulp`整合在一起来支持`stream`。（任何人都将可以使用stream）  
例如我曾经想下面这样不用`stream`使用`wiredep`    

	/////////////////////
	// Without Streams //
	/////////////////////

	var gulp    = require('gulp');  
	var wiredep = require('wiredep');

	gulp.task('bower', function () {  
 		 wiredep({
    		src: './src/footer.html',
    		directory: './bower_componets/',
    		bowerJson: require('./bower.json'),
  		});
	});  
	
上边的写法都非常好用知道我遇到另一个`gulp`任务依赖上边的`bower`任务。最简单的方法是返回一个`stream`,很巧的是`wiredep`支持`stream`了。像下面修改上边的代码：  
 
	//////////////////
	// With Streams //
	//////////////////

	var gulp    = require('gulp');  
	// note that we're grabbing the stream function
	var wiredep = require('wiredep').stream;

	gulp.task('bower', function () {  
 	 	gulp.src('./src/footer.html')
    		.pipe(wiredep({
     				 directory: './bower_componets/',
      				bowerJson: require('./bower.json'),
    		}))
    		.pipe(gulp.dest('./dest'));
		});  

就如上边的代码，我们可以整体的使用`gulp`。  
#结论    
当你们中大多人了解`gulp`更进一步就会发现，很多`gulp`的需求的解决方法不是需要`gulp`明确地插件。关于`gulp`最酷的一件事情就是：它仅仅只是代码。  
`wiredep`是其中的一种工具，有你需要的非常好的每一件东西，在这篇文章中使用了很多技术名词，你可以受益如`wiredep`的简单，自动连接，`bower`依赖关系的管理。  
原文地址：https://cameronspear.com/blog/streams-in-wiredep/

