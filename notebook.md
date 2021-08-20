## 2021-8-20
#### **双边滤波:**
  >- **双边滤波主要为了解决高斯滤波作为低通滤波，会在像素值变化比较大的地方做平滑，从而导致图像的模糊，双边滤波在高斯滤波的基础上增加了周围像素值对目标值的影响，从而可以一定程度的保护边缘。**


## 2021-8-19
#### **C++中Atomic的作用:**  
  >- **atomic在头文件`include<atomic>`中，是一个模板类，这是一个原子操作类，用这个类可以实现无锁同步，不需要使用mutex和lock_gaurd等方法**  
  >- **定义一个原子变量`std::atomic<int> xxx`,store()和load()分别定义了原子写和原子读操作，原子类都没有拷贝操作，所以需要使用compare_exhance_weak()和compare_exhange_strong()等方法赋值。**


## 2021-8-9
#### **CMAKE常见语法含义**  
  >1. include(xxx): 载入并执行一个cmake文件或者模块，当指定模块的时候，该命令会在CMAKE_MODULE_PATH目录下寻找对应名字的.cmake文件。  
  >2. file(xx xx xxx): 文件相关操作，包括文件读写，文件删除等，当标志位是GLOB时，表示删选符合要求的文件列表存储到变量中。  
  >3. find_package(xxx): 寻找外部依赖库，先进行Module模式的搜索，主要搜索指定路径下的FindModuleName.cmake文件，如果找不到对应的文件，则进入Config模式，在指定路径下搜索ModuleName-config.cmake文件。一般来说三方库如果使用cmake编译的则会自动生成xxx-config.cmake文件，如果不是cmake编译的则需要自己编写Findxxx.cmake文件。  
  >4. add_definitions(xxx xxx): 在代码编译的时候加入一些宏定义。可以在不修改源码的情况下进行一些测试。  
  >5. set_target_properties(xxx): 了解到的两个作用，一是给对应的库文件对应的版本号等信息，二是将库文件输出为指定的文件名和目录。  
  >6. include_directories(xxx): 添加头文件目录到cmake编译时搜索路径中。  
  >7. add_library(xxx): 利用指定的源文件生成对应的链接文件。  
  >8. target_include_directories(xxx) && target_link_libraries(xxx) && target_compile_options(xxx): 分别表示给对应的目标指定需要包含的头文件，这个命令和include_directories的区别是作用域的不同，include_directories作用于整个目录包括其子目录，target_include_directories只作用于当前目标; target_link_libraries则指定目标需要链接的库；target_compile_options设置目标的编译选项。  
  >9. enable_testing(xxx): 打开编译test的开关。  
  >10. add_subdirectories(xxx): 添加一个子目录，并构建这个子目录，目录中需要包含CMakeLists.txt文件。  
  >11. link_directories(xxx): 添加需要链接的库的路径，这个命令需要在target生成之前运行。  
  >12. add_library(xxx): 根据给定的源文件生成对应的target文件,包括静态库STATIC，动态库SHARED，MODULE三种类型。  
  >13. configure_file(xxx): 复制文件到指定位置。  
  >14. add_custom_target(xx): 设置一个自定义的cmake命令，可以在命令行中执行，例如cmake uninstall。  



## 2021-8-4
#### **C++类模板的编写**
  >- **C++在编译期间会将每个.cpp文件编译成对应的实现，然后在链接阶段去链接这些实现，这就需要.cpp中的实现必须是已知类型的，而类模板的定义是未知类型的，所以如果放到.cpp中则编译出来了无法进行链接。**
  >- **正确的做法是将模板的实现放在.h头文件中，这样会将模板类的特化和实现放到链接阶段，在获得了类具体的类型后编译生成对应的实现。**
  >- **但是这样会导致.h比较冗余，这时可以将实现部分写到一个非.cpp或.h的文件中，例如.tpp文件，在.h中包含这个文件`include <implementation.tpp>`。**


## 2021-08-03
#### **C++编码规范：**  
  >1. 类和public方法的命名使用BigCamel,protected和private方法需要使用smallCamel.  
  >2. 成员变量的命名是小写并使用_分隔  
  >3. 常量和枚举enum使用大写
  >4. *和&修饰符靠近类型名，const修饰符在类型名后面。


## 2021-07-26
#### kalman filter, 原理：
  >- **当前状态的估计 = 上一状态的估计 + 当前测量 的加权和。**  
#### sudo vim .etc/systemd/resolved.conf:  
  >- **修改DNS配置，重启后生效。

## 2021-07-24
#### Git, 删除远程的分支：
  >- `git push origin --delete freature/xxx`  





## 2021-07-18
#### Git, 合并分支的两个方法merge和rebase：
  >- **merge:如果将一个外部分支合并到当前分支，外部分支中的commit将基于时间顺序插入到当前分支的commit中。  
  如果不想混乱当前分支的commit，只能将外部分支的所有后续commit打包加到当前分支的后面  
  `git commit -m "merge other_branch to current_branch."`  
  `git merge --squash master`**  
  >- **rebase: 是重新设置当前分支的分叉点，基于base中最新的commit切出当前分支，当前分支的所有commit基于最新的base commit。  
  `git rebase master`**  
  >- **如果需要强制退回到某个版本：  `git reset commit_id --hard`**



## 2021-07-12
#### Vim, 插入时间：
  >- **xtime 回车.**


## 2021-1-11  
####  Git, 提交代码修改并merge  
  > 1. git checkout hpp_dev_v1   *切换分支*
  > 2. git checkout -b zcw/new_branch    *创建一个新的分支*
  > 3. git add -a    *加入所有的修改*  
  > 4. git commit -m "xxx"    *创建commit*
  > 5. git push     *push 到远程分支*
  > 6. 创建pull request, 将当前分支merge到目标分支。  


## 2021-1-10
##### Ubuntu, 摄像头app: xawtv  

## 2021-1-9
#### C++, "动态绑定"和"静态绑定"：  
   > - **分别用于虚函数和普通函数，当基类的方法是虚函数，利用指针调用派生类的该方法时，指针指的是哪个类型的类对象，调用哪个类对象的方法。**
   >- **当基类的方法是普通函数时，利用指针调用该方法的时候，调用哪个方法的类指针的声明类型，而不取决于指针实际指向的类型。**

#### C++, override:  
   >- **在派生类覆盖基类的虚方法的时候，有可能因为形参列表或者其他细微的区别，导致没有覆盖，这就会违背作者的意愿，在重写的函数后面加上override关键字，就告诉编译器，该方法是一定会覆盖基类中对应方法的，如果没有就报错  
   参考<http://c.biancheng.net/view/1561.html>**

## 2021-1-7
#### 汇编，`mov dword ptr[esp], 10` :  
   >  **将10存储在esp中存储的地址中，以dword(32bit)存储。**
#### C++, volatile关键词：
   > **包括两个主要的特性：**  
   > *1. 如果一个变量被定义成volatile变量，那他将获得“易失性”，通俗的讲就是每次程序修改这个变量都会把对应的值同步到内存中，读取这个变量也会直接从内存中读取，而不是寄存器。*
   > *2. 另一个特性失“不可优化性”，不允许编译器对这个变量做优化，其实也是防止把这个变量优化掉，我觉得和易失性是一个目的。*
#### C++, static关键词：
   > **分为两个大的部分：**  
   > *1. 当独立使用的时候，static类型的变量他是*

## 2021-1-5
#### Linux, ipcs命令:
   > **用于**

