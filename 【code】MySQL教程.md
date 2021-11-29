### 一、概念

常见数据库类型  
<img src="https://i.loli.net/2021/11/13/1emonKNuWPI6JZF.png" width="40%">  

通过DBMS操作数据库   
<img src="https://i.loli.net/2021/11/13/fDOEt9plkWyZi53.png" width="40%">    

MySQL数据结构-表结构  
红色为表的主键，主键是该表行的唯一标识     
<img src="https://i.loli.net/2021/11/13/z6uNtqoYPrSAIwf.png" width="40%">   
外键是用来连接表与表之间的关系   
<img src="https://i.loli.net/2021/11/13/8WktjdJwabYgH36.png" width="60%">  

eg. 一个完整的表结构   
<img src="https://i.loli.net/2021/11/13/lsQ1tFda5SKGJq6.png" width="60%">  


### 二、本地MySQL数据库   

1、下载安装   

* 下载MySQL community  

<img src="https://i.loli.net/2021/11/13/O4aV53LS2lMD7Pm.png" width="60%">    

* 安装，设定整个数据库的管理员密码  

<img src="https://i.loli.net/2021/11/13/KRZiy3QLzwmXbc1.png" width="60%">  

* 下载MySQL workbench  数据库可视化操作界面  

<img src="https://i.loli.net/2021/11/13/zWfXQGuVHZp7waB.png" width="60%">   

* 安装完成，在workbench界面进行操作  

<img src="https://i.loli.net/2021/11/13/8WJVawPDRMBETxp.png" width="60%">  

_* 注意：版本兼容问题【Mac os10.15.7 + MySQL community sever8.0.22 + MySQL workbench8.0.22】_  


2、对数据库的基本操作（创建、增删改查、删除)   

* 创建数据库  

<img src="https://i.loli.net/2021/11/13/zOkTmSaEQLI7Wcb.png" width="40%">  

<img src="https://i.loli.net/2021/11/13/fF7hKOzEtSdx3ZN.png" width="40%">  
SQL支持的数据类型   

* 创建表，删除表  

<img src="https://i.loli.net/2021/11/13/wcxH5TlpUkKNC9S.png" width="40%">  




### 三、Python连接数据库   

**安装包mysql-connector-python**   

`pip install mysql-connector-python  `   


**示例1：create_db.py用py创建数据库**  

```python
import mysql.connector

#无目标database时，连接
connection= mysql.connector.connect(host='localhost',
                                    port='3306',
                                    user='root',
                                    password='yuan1991')

cursor = connection.cursor()

#创建database
#cursor.execute("CREATE DATABASE `qq`;")

#获取所有数据库名称show database,fetchall()获取所有回传的资料
# cursor.execute("SHOW DATABASES;")
# records = cursor.fetchall()
# for r in records:
#   print(r)

#使用数据库
# cursor.execute("USE `qq`;")

#创建表格
# cursor.execute("CREATE TABLE `qq_user`(qq INT);")


#关闭连接
cursor.close()
connection.close()


#成功连接！！！
```   

**示例2：select_data.py查询表数据**  

```python
import mysql.connector

#无目标database时，连接
connection= mysql.connector.connect(host='localhost',
                                    port='3306',
                                    user='root',
                                    password='yuan1991',
                                    database='qq')

cursor = connection.cursor()

#获取表内所有资料，查
# cursor.execute("SELECT * FROM `branch`;")

# records = cursor.fetchall()
# for r in records:
#   print(r)

#关闭连接
cursor.close()
connection.close()
```  

**示例3：** update_data.py增删改-数据    

```python
import mysql.connector

#无目标database时，连接
connection= mysql.connector.connect(host='localhost',
                                    port='3306',
                                    user='root',
                                    password='yuan1991',
                                    database='qq')

cursor = connection.cursor()

#增
# cursor.execute("INSERT INTO `branch` VALUES(s, 'qq', NULL)")

#删
cursor.execute("DELETE FROM `branch` WHERE `branch_id` = 5;")

#改
cursor.execute("UPDATE `branch` SET `manager_id` = NULL WHERE `branch_id` = 4;")

#查

#关闭连接
cursor.close()
#增删改数据都必须commit()
connection.commit()
connection.close()
```  

**示例4：** mysql.connector获取变量值的sql语句     

```
#mysql.connector连接数据库

#用此语法写入SQL语句，可获得变量的value
a = 7
b = 8
c = 9
sql = "INSERT INTO `qq_user_1` VALUES('%s', '%s', '%s')"
val = (a, b, c)

cursor.execute(sql, val)

#增删改数据都必须commit()
connection.commit()
#关闭连接
```  

### 四、face_database的实例   

1、本地创建MySQL数据库   

创建包含json类型字段的表，主键id自动生成   

<img src="https://i.loli.net/2021/11/23/q3MuYejOSGILaEK.png" width="60%">   

2、人脸检测代码中，插入数据上送MySQL的模块    

关于json:  
* json.dumps()：接收python类型的数据作为参数，返回了一个str对象的encodedjson（从python数据转换为json）   
* json.loads()：接收json字符串，返回python类型的数据（从json字符串转换为python数据）


```python
######### 测试数据库face_database——face_json_test ###########这个if开始向MySQL灌入所有 img-face 点[id,x,y]
        if len(face)!= 0:
            #这是整个face[]打印的
            # print(face)

            #这是一个个[id,x,y]打印的
            # for a in face:
            #     print(a)

####———————————————————— 可作为TCP传输的点data ——————————————————————
            # print(face[1][2])
            # print(face[1])

            face_json = json.dumps(face, ensure_ascii=False) 
            ######   在这里插入上传函数,(1)令一个face打包为一条json；（2）上传此条json至MySQL；
            #连接到数据库
            connection= mysql.connector.connect(host='localhost',
                                                port='3306',
                                                user='root',
                                                password='yuan1991',
                                                database='face_database')
            cursor = connection.cursor()

            sql = "INSERT INTO `face_json_test`(face_json) VALUES('%s')" % (face_json)
            # val = (null, json.dumps(face))
            #debug 数据类型不对！！！！！！！！ null不对！！！
            cursor.execute(sql)

            #增删改数据都必须commit()
            connection.commit()
            #关闭连接
            cursor.close()
            connection.close()
########## 测试数据库face_database——face_json_test  ########灌一轮数据结束，收集到一张img，一张face的468个点[id,x,y]            
```

3、查询数据表/清空数据表











