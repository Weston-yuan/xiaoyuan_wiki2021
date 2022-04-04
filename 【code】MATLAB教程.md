### 一、介绍  

* MATLAB是m语言的IDE编译器  
* 文件格式 .m    
* 推荐采用实时脚本编写脚本，用命令行debug   

**基本语法（命令）：**   

```
%注释  
%变量名区分大小写，推荐驼峰命名法   
%look for 找函数   
%help 函数名  
%whos   
```  

数据类型    

```
%matlab是弱语言，不需强制定义数据类型，编译器每次执行前推导   
1、数值阵列（类型）：  
整形(int8/uint8/int16/uint16)      
浮点型（single / double）    
2、字符阵列：字符、字符串  
3、胞体/元祖阵列（重点）   
4、结构体阵列   
5、逻辑阵列（布尔类型）   
6、函数句柄阵列  

*其他：Inf 正无穷、-Inf 负无穷、NaN 非数值量
```

函数  
输入函数：disp / input   
取整函数：floor / ceil / round / fix

ga算法：实时脚本——任务task——优化optimize——GA


