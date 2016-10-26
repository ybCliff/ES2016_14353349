# LAB3: DOL实例分析&编程  
### 修改完后结果  
#### Example 1  
running result:  
![](https://github.com/ybCliff/Screenshot/blob/master/ex1_run_result.jpg?raw=true)  
dot result:  
![](https://github.com/ybCliff/Screenshot/blob/master/ex1_dot.jpg?raw=true)  
#### Example 2  
running result:  
![](https://github.com/ybCliff/Screenshot/blob/master/ex2_run_result.jpg?raw=true)  
dot result:  
![](https://github.com/ybCliff/Screenshot/blob/master/ex2_dot.jpg?raw=true) 
### 修改步骤  
#### Example 1  
1. **添加实现立方的代码文件**  
![](https://github.com/ybCliff/Screenshot/blob/master/ex1_add_file.png?raw=true)  
我并没有在原有square文件上进行修改，而是保留了squre新增cubic。届时具体用哪份代码由xml决定。  

2. **cubic.h内容**  
![](https://github.com/ybCliff/Screenshot/blob/master/ex1_cubic_h.jpg?raw=true)  

3. **cubic.c内容**  
![](https://github.com/ybCliff/Screenshot/blob/master/ex1_cubic_c.jpg?raw=true)  
注意到红框内容就是实现立方的关键代码，在suqre.c中是`i = i * i`  

4. **修改xml**  
![](https://github.com/ybCliff/Screenshot/blob/master/ex1_altxml.jpg?raw=true)  
注意修改代码运行文件以及connections间的名字即可。至此，完成example 1的修改  

#### Example 2  
1. **修改最大迭代次数**  
![](https://github.com/ybCliff/Screenshot/blob/master/ex2_change_iteration_times.jpg?raw=true)  
原本是经过了3次的平方操作，最后得到6次方。而现在我们需要4次方，所以只需要迭代2次。  
至此，example 2修改完毕。

### 实验感想
&emsp;　了解了生产者、运算执行模块、消费者。  
&emsp;　生产者由generator文件描述，其中：  
- `generator_init`是初始化函数——用以初始化变量or指针指向等；
- `generator_fire`是信号产生函数，执行n次（n是自己设定的）,然后销毁   

&emsp;　消费者由comsumer文件描述，其中：  
- `comsumer_init`含义同`generator_init`
- `comsumer_fire`是信号消费函数，执行n次（n是自己设定的）,然后销毁   

&emsp;　运算执行模块则是由我们人为灵活定义。  
&emsp;　上面所提及的三部分都只是“个体”，如果要连成整体（系统架构、模块链接定义），就需要xml来定义  
&emsp;　xml主要由3部分组成：`进程定义`，`通道定义`，`连线定义`；

