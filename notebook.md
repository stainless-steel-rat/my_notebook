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

