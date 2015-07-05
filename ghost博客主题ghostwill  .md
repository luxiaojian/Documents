# ghost博客主题[鬼才晓得]

> 这个主题英文名叫ghostwill,中文名就叫[鬼才晓得]。  

## 主题特性介绍  
### 响应式  
这年头一个网站没有响应式，都不好意思拿出来。[鬼才晓得]才晓得这个主题移动设备进行了优化，对导航栏菜单和文章缩略图用`media query`进行了处理。但交互还需要进一步优化。  

![](http://7qna7i.com1.z0.glb.clouddn.com/screen.png)  
**中屏上显示效果**

![](http://7qna7i.com1.z0.glb.clouddn.com/phone.png)  
**iphone5上显示效果**

![](http://7qna7i.com1.z0.glb.clouddn.com/ipad-vertical.png)  
**ipad竖屏上显示效果**


### 视差滚动效果
![](http://7qna7i.com1.z0.glb.clouddn.com/parallex-background.gif)

这个效果用到一个插件[ Stellar.js](http://markdalgleish.com/projects/stellar.js/),这个插件的效果就是给元素添加视差效果。

```js
/*顶部图片视觉滚差*/
 $(window).stellar();
```

###自定义Cover image

自己过去看了不少国外网站，发现这种大 Banner 、大图片、大字体算是一大趋势。尤其是博客和资讯，大量留白，专注于中部核心内容。[鬼才晓得]支持用户自定义封面照片。

在 Markdown 编辑时，给img图片标签加上cover-image的alt值即可。如果没有自定义图片，会默认抓取文章中的第一张图片，如果文章没有图片，则使用默认图片。

![](http://7qna7i.com1.z0.glb.clouddn.com/cover-image.gif)

**实现代码**

```js
    /*判断cover-image插件*/

    if($('.single-post-inner img').length>0){
        /*如果文章存在图片，首先判断是否有自定义 cover-image*/
        if($('.single-post-inner img[alt="cover-image"]').length>0){
            /*如果有自定义cover，则使用这张*/
            mainImage=$('img[alt="cover-image"]:first');//默认选择第一张 cover-image
            mainImageSource = mainImage.attr('src');
            $('.site-head').css('background-image','url('+mainImageSource+')');
            mainImage.remove();
        }else{
            $('.single-post-inner img:first').attr('alt','cover-image');
            var firstImgWidth=$('.single-post-inner img:first').width();
            console.log(firstImgWidth);
            /*如果没有自定义 cover-image，使用第一章图片*/
                $('.single-post-inner img:first').attr('alt','cover-image');
                mainImage=$('img[alt="cover-image"]');
                mainImageSource = mainImage.attr('src');
                $('.site-head').css('background-image','url('+mainImageSource+')');
                mainImage.remove();
        }

    }
```

### 文章内 url 体验优化  

把文章中一些常用的 url地址自动加上 iconfont，并且对应不同的提示颜色，支持国内外常用社交网站，让读者能快速知道 url 跳转目的地。 


```js
/*给文章中的url添加iconfont方便识别*/
function urlIconlize(url){
    var domain,
        _output;
    var iconMap={/*索引 可在这里添加匹配规则*/
        'twitter':'icon-twitter',
        'qzone':'icon-qzone',
        'weibo':'icon-weibo',
        'facebook':'icon-facebook',
        'github':'icon-github',
        'douban':'icon-douban',
        'google':'icon-google',
        'dribble':'icon-dribble'

    }

    for(var name in iconMap){
        if(typeof iconMap[name] !== 'function'){
            var MapKey=name;
            if(url.indexOf(MapKey)>=0){
                domain=MapKey;
                _output=iconMap[MapKey];
            }
        }
    }

    return _output;
}

$(document).ready(function(){
	/*给博客文章地址url添加ico识别*/
    $('.single-post-inner p a:not(:has(img))').each(function(i){
        var _src=$(this).attr('href');
        var tmp=document.createElement('a');
        tmp.href=_src;
        _selfDomain=tmp.hostname;
        urlIconlize(_selfDomain);
        console.log(_selfDomain);
        //$(this).append(urlIconlize(_selfDomain));
        $(this).prepend('<i class="iconfont '+urlIconlize(_selfDomain)+'"></i>');
        var _selfColor=$(this).find('i').css('color'),
            _originalColor=$(this).css('color');


        /*鼠标悬浮时*/
        $(this).hover(function(){
            $(this).css('color',_selfColor);
            $(this).addClass('animated pulse');
        },function(){
            $(this).css('color',_originalColor);
            $(this).removeClass('animated pulse');
        });

    })
})
```
### 写在最后  
就写这么多功能了，因为这个主题是之前写的，写这个文档的时候只是为了交个作业，就不多扯了，此外这是一个 HTML5 的主题，从一开始我就就没想支持IE8以下的用户，IE的用户就洗洗睡吧。
