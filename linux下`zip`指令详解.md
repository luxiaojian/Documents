#linux下`zip`指令详解  
###`zip`的基本用法是：`zip [参数] [打包后的文件夹名] [打包目录的路径]`

###参数  
* `-q`:安静模式，在压缩时不显示指令执行过程。
* `-r`:将目录下所有的子目录文件一起处理。  
  
###一些例子  
* `zip -q -r es.nuist.edu.zip ./es.nuist.edu.cn/`:当前目录下`es.nuist.edu.cn`这个目录下的所有文件进行打包压缩成文件`es.nuist.edu.cn.zip`

###`unzip`的基本用法:`unzip [参数] 压缩文件名.zip`
* `-t` 测试文件有无损坏，但不解压。
* `-q` 执行时不显示任何信息。
* `-d<目录>` 指定文件解压缩后所要存储的目录。  

###例子  
* `unzip huankekepu.zip`:解压`huankekepu.zip`到当前目录。
* `unzip huankekepu.zip -d /root`:解压`huankekepu.zip`到`root`目录。