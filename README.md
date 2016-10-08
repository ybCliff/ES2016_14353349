# LAB1: DOL配置
## Description
The distributed operation layer (DOL) is a framework that enables the (semi-) automatic mapping of applications onto the multiprocessor SHAPES architecture platform. The DOL consists of basically three parts:
- DOL Application Programming Interface
- DOL Functional Simulation
- DOL Mapping Optimization

## How to install
+ 1. **安装一些必要的环境（ubuntu为例）：**
```
    $	sudo apt-get update
    $	sudo apt-get install ant
    $ 	sudo apt-get install openjdk-7-jdk
    $	sudo apt-get install unzip
```

+ 2. **直接用命令行下载文件到虚拟机中**
```
    $   sudo wget http://www.accellera.org/images/downloads/standards/systemc/systemc-2.3.1.tgz
    $   sudo wget http://www.tik.ee.ethz.ch/~shapes/downloads/dol_ethz.zip
```

+ 3. **解压文件**
```
    $	mkdir dol                       //新建dol的文件夹
    $	unzip dol_ethz.zip -d dol       //将dolethz.zip解压到 dol文件夹中
    $	tar -zxvf systemc-2.3.1.tgz     //解压systemc
```

+ 4. **编译systemc**
```
    $	cd systemc-2.3.1                //解压后进入systemc-2.3.1的目录下
    $	mkdir objdir                    //新建一个临时文件夹objdir
    $	cd objdir                       //进入该文件夹objdir
    $	../configure CXX=g++ --disable-async-updates    //运行configure(用于编译)
```
&ensp;　　运行configure的结果：  
&ensp;　　![](https://github.com/ybCliff/Screenshot/blob/master/configure_result.jpg?raw=true)

&ensp;　　pwd的结果：  
&ensp;　　![](https://github.com/ybCliff/Screenshot/blob/master/pwd_result.png?raw=true)

+ 5. **编译dol**
```
    $	cd ../dol                       //进入刚刚dol的文件夹
```


&ensp;　　修改build_zip.xml文件, 找到下面这段话，就是说上面编译的systemc位置在哪里，
```    
    <property name="systemc.inc" value="YYY/include"/>
    <property name="systemc.lib" value="YYY/lib-linux/libsystemc.a"/>
```
&ensp;　　把步骤4中pwd的结果替换掉YYY即可  
&ensp;　　然后是编译（语句如下），若成功会显示build successful
```
    $	ant -f build_zip.xml all
```
&ensp;　　编译结果如下：  
&ensp;　　![](https://github.com/ybCliff/Screenshot/blob/master/build_successful.jpg?raw=true)

+ 6. **运行example 1来检验是否配置成功**
```
    $	cd build/bin/main                   //进入build/bin/mian路径下
    $	ant -f runexample.xml -Dnumber=1    //运行第一个例子
```
&ensp;　　成功结果如下：  
&ensp;　　![](https://github.com/ybCliff/Screenshot/blob/master/example_result.jpg?raw=true)

## Experimental experience
&emsp;　这次实验按照Ta所给的PPT流程操作下来，并没有遇到太多的困难，主要是虚拟机一开始是中文系统，所以在最后运行example 1的时候并没有成功。后来将系统转回英文，就可以了。  
&emsp;　这次最大的收获其实是对markdown和github的了解。在本md文件中，由于使用了图片需要加入URL，因此我在github上建立了一个仓库，专门用来存放我的结果截图，然后复制图片链接地址即可得到URL。  
&emsp;　此外，我还学习到了很多markdown的语法。原本markdown就是为了让人不要过于关注排版，所以每一段文本都没有缩进，后来通过查询，发现`&emsp;`代表全空格，`&ensp`代表半空格；当输入法转换成全角输入的时候，按空格也能使得段落缩进，使得整体的布局优美了不少。此外还学会了两种换行方式，其一是软换行，就是在文末+`两个空格`+`ENTER`；另外一种是硬换行，就是文末直接`ENTER`；  
&emsp;　之前没有接触过github和markdown，视野比较狭窄，现在发现这两者如此好用以及方便，实在是感谢Ta的指引。
