# 利用wordpress搭建一个学院网站  

## wordpress主题构成文件  

### 主页

home.php
index.php
### 文章页

single-{post_type}.php – 如果文章类型是videos（即视频），WordPress就会去查找single-videos.php（WordPress 3.0及以上版本支持）
single.php
index.php
### 页面

自定义模板 – 在WordPress后台创建页面的地方，右侧边栏可以选择页面的自定义模板
page-{slug}.php – 如果页面的缩略名是news，WordPress将会查找 page-news.php（WordPress 2.9及以上版本支持）
page-{id}.php – 如果页面ID是6，WordPress将会查找page-6.php
page.php
index.php

## 开始制作主题  
### HTML静态模板制作  
首页：index.html
存档页：archive.html
页面：page.html
文章页：single.html
联系页：contact.html
图片：/images/
样式表：style.css
缩略图：screenshot.png

### 设计稿  
![](http://7qna7i.com1.z0.glb.clouddn.com/huanke.png)  
**首页**  

![](http://7qna7i.com1.z0.glb.clouddn.com/category.png)  
**分类页**  

![](http://7qna7i.com1.z0.glb.clouddn.com/page.png)  
**详情页** 

### 变html demo为php文件  
#### header.php和footer.php
把html文档中公用的头部文件和尾部文件抽出，放到header.php和footer.php文件中，让后在其他文件中引入即可

```php
<?php get_header(); ?>
```

#### category.php,page.php,index.php
下面几个模板都是直接中html静态文件直接切过来的，只是把html中的一些参数换成wordpress提供的参数接口，加上一些php的循环。  

```php
 <?php query_posts('cat=2&showposts=8'); ?>
                            <?php while (have_posts()) : the_post(); ?>
                            <li><a href="<?php the_permalink(); ?>" class="c-title"><?php the_title(); ?></a>
                            <p class="gray rfloat"><?php  the_modified_time('Y/n/j');?></p>
                            </li>
                            <?php endwhile; wp_reset_query(); ?>
```

**wordpress的一些参数接口**  
is_home() ： 是否为主页，首页使用的是 index.php
is_front_page() ：是否为指定的首页，如果首页不是默认的index.php，比如你在后台 - 设置 - 阅读，指定了首页，就要用这个来判断
is_single() ： 是否为内容页（Post）
is_page() ： 是否为内容页（Page）
is_attachment() ：是否为附件页
<?php the_title(); ?> ： 内容页（Post/Page）标题
<?php the_permalink() ?> ： 内容页（Post/Page） Url
<?php the_category(', ') ?> ： 特定内容页（Post/Page）所属Category
<?php the_author(); ?> ： 作者（只显示作者名字，没有链接）
<?php the_author_posts_link(); ?> ：作者（显示作者，并且包含链接到作者文章目录的链接）
<?php the_time('Y-m-d') ?> ：显示时间，时间格式由“字符串”参数决定，具体参考PHP手册
<?php echo get_post_meta(); ?> : 获取保存在 post_meta 这个表中的数据，比如输出某个 自定义字段 的内容
<?php the_ID(); ?> ： 特定内容页（Post/Page） ID
<?php the_tags('关键字: ', ', ', ''); ?> ：显示文章的关键字tag
<?php the_excerpt(); ?> ：Post/Page 的摘要，输入文章发布页面中的摘要面板的内容
<?php the_content('more'); ?> ：Post/Page 的摘要，配合 <!–more–> 来使用
<?php the_content(); ?>  ： 显示内容（Post/Page） 全文
<?php wp_list_pages(); ?> ： 显示Page列表，常用于显示单篇文章的分页，配合 <!–next page-> 来使用
<?php edit_post_link(); ?> ： 如果用户已登录并具有权限，显示编辑链接
<?php posts_nav_link(); ?> ： 显示上一页/下一页的链接，通常用在索引页、分类页和文章存档页

### 主题的一些特性  
#### 在网页中需要使用icon的地方使用webfont和css sprite  
在图标是纯色的icon时候使用webfont，我在页面中使用的图片来自阿里的[iconfont](http://www.iconfont.cn/),在这个网站上我可以在选择需要的图标，然后一起下载下来成webfont,在网页中使用即可。  

![](http://7qna7i.com1.z0.glb.clouddn.com/webfont.png)

css sprite这里就不详细介绍了，其实就是background属性。  

### 使用html5的video代替flash在网页中播放视频

```html
<video controls width="310" height="193" poster="<?php bloginfo('template_url') ?>/images/video_poster.jpg">
                        <source src="<?php bloginfo('template_url') ?>/video.mp4" type="video/mp4">
                        <source src="<?php bloginfo('template_url') ?>/video.ogv" type="video/ogv">
                        <source src="<?php bloginfo('template_url') ?>/video.webm" type="video/webm">
                    </video>
```
