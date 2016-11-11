## LAB5: 配置ROS及cartographer
### 安装过程
#### ROS
-1 **Setup your sources.list**  
```  
    $	sudo sh -c 'echo "deb http://packages.ros.org/ros/ubuntu $(lsb_release -sc) main" > /etc/apt/sources.list.d/ros-latest.list'
```  

-2 **Set up your keys**  
```  
    $   sudo apt-key adv --keyserver hkp://ha.pool.sks-keyservers.net:80 --recv-key 0xB01FA116
```  

-3 **Installation**  
```
    $	sudo apt-get update
	$	sudo apt-get install ros-jade-desktop-full
```  

-4 **Initialize rosdep**  
```
    $	sudo rosdep init
    $	rosdep update
```   

-5 **Environment setup**  
```
	$	echo "source /opt/ros/jade/setup.bash" >> ~/.bashrc
	$	source ~/.bashrc
```  

-6 **Getting rosinstall**  
```
	$	sudo apt-get install python-rosinstall
```  

check_ros_package结果：    
![](https://github.com/ybCliff/Screenshot/blob/master/check_ros_package_path.jpg?raw=true)  

#### cartographer  
-1 **Install wstool and rosdep**  
```
	$	sudo apt-get update
	$	sudo apt-get install -y python-wstool python-rosdep ninja-build
```  

-2 **Create a new workspace in 'catkin_ws'**  
```
	$	mkdir catkin_ws
	$	cd catkin_ws
	$	wstool init src
```  

-3 **Install ceres solver**  
```
    $	git clone https://github.com/hitcm/ceres-solver-1.11.0.git
	$	cd ceres-solver-1.11.0/build
	$	cmake ..
	$	make
	$	sudo make install
```  

-4 **Install cartographer**  
```
	$	git clone https://github.com/hitcm/cartographer.git
	$	cd cartographer/build
	$	cmake .. -G Ninja
	$	ninja
	$	ninja test
	$	sudo ninja install 
```  
ninja test结果：
![](https://github.com/ybCliff/Screenshot/blob/master/ninja_test_success.jpg?raw=true)  

-5 **Install cartographer_ros**  
```
	$	cd catkin_ws/src
	$	git clone https://github.com/hitcm/cartographer_ros.git
	$	cd ..
	$	catkin_make
```


2D成功结果如下：  
![](https://github.com/ybCliff/Screenshot/blob/master/2D_result.png?raw=true)
3D没有成功。

### 实验感想
过程很坎坷，到最后也没算完全成功。由于两次实训接触的都是智能小车，所以对于TA在实验课上讲的定位SLAM算法十分感兴趣。在初级实训中我们就只是完成了一些建立在避障基础上的操作；中级实训中就涉及到图像识别，但是由于实训时间持续太短（由于回迁问题），所以Ta也没能传授很多关于Opencv的知识；在暑假的时候也有自学一部分，因此对于这方面还是挺感兴趣的，期待TA关于ROS和cartographer的进一步讲解。
