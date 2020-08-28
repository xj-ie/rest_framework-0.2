# -0.2
美多商城后台



#### 1、项目环境的配置

​	![image-20200826085703466](image\image-20200826085703466.png)

![image-20200827145707398](image/image-20200827145707398.png)

### 1、业务说明

​	验证用户名和密码成功后，为用户签发JWT,前端将签发JWT保存下来。

### 2、后端接口设计 

​	**请求方式**：POST  meiduo_admin/authorizations/

​	**请求参数**：JSON 或者 表单

|  参数名  | 类型 | 是否必须 |  说明  |
| :------: | :--: | :------: | :----: |
| useranme | str  |    是    | 用户名 |
| password | str  |    是    |  密码  |

**返回**：JSON

​	{

​		"useranme":"##",

​		"user_id": ##,

​		"token":"##"

​	}

|  返回值  | 类型 | 是否必须 |    说明    |
| :------: | :--: | :------: | :--------: |
| useranme | str  |    是    |   用户名   |
|    id    | int  |    是    |   用户id   |
|  token   | str  |    是    | 身份证凭证 |



![image-20200827194456131](image\image-20200827194456131.png)



### 1、业务说明

​	通过rest_frame中的GenteAPIView视图类完成统计功能 

### 2、后端接口设计

​	**请求方式**：GET

​	**请求参数**：JSON

| 参数名 | 是否必传 | 类型 |   说明   |
| :----: | :------: | :--: | :------: |
| token  |    是    | str  | 身份凭证 |



​	**返回参数**

{

"user_count": count,

"datetime":time

}

|  返回参数  |   类型   | 是否必传 |   说明    |
| :--------: | :------: | :------: | :-------: |
| user_count |   int    |    是    | 统计个数  |
|  datatime  | datatime |    是    | 统计 时间 |

![image-20200827215021925](image\image-20200827215021925.png)

## 日增用户接口定义

### 1、接口分析

​	**请求方式**：GET /meiduo_admin/statistical/day_increment/

​	**请求参数**： 请求传递token(身份验证参数)

​	**返回参数**：JSON

{

'date'：new_user_date,

"count": day_create_count

}

|  返回参数  |   类型   | 是否必传 |       说明       |
| :--------: | :------: | :------: | :--------------: |
|    date    | datetime |    是    |     今日时间     |
| user_count |   int    |    是    | 今日用户创建个数 |

## 日活用户接口定义

### 1、后端接口设计

​		**请求方式**：GET /meiduo_admin/statistical/day_activate

​		**请求参数**：JWT token（头部传递）

| 请求参数 | 类型 | 是否必传 | 携带部位 |   说明   |
| :------: | :--: | :------: | :------: | :------: |
|  token   | str  |    是    | 请求头部 | 身体验证 |

**返回参数：**

{

"conut"：day_activate_count,

"date": date_day

}

| 返回参数 | 类型 | 是否必需 |      说明      |
| :------: | :--: | :------: | :------------: |
|  count   | int  |    是    | 日活用户总个数 |
|   date   | date |    是    |    当天日期    |

## 下单用户接口

![image-20200828093010828](image\image-20200828093010828.png)

### 1、接口分析

​	**请求方式**：GET

​	**请求参数**：JWT token



| 请求参数 | 类型 | 是否必传 | 携带部位 |   说明   |
| :------: | :--: | :------: | :------: | :------: |
|  token   | str  |    是    | 请求头部 | 身体验证 |

**返回参数：**

{

"conut"：day_activate_count,

"date": date_day

}

| 返回参数 | 类型 | 是否必需 |      说明      |
| :------: | :--: | :------: | :------------: |
|  count   | int  |    是    | 下单用户的个数 |
|   date   | date |    是    |  当天日期下单  |

## 月增用户接口

![image-20200828103012608](image\image-20200828103012608.png)

### 1、接口设计

​	**请求方式**：get /meiduo_admin/statistical/month_increment/

​	**请求参数**：JWT token

| 请求参数 | 类型 | 是否必传 | 携带部位 |   说明   |
| :------: | :--: | :------: | :------: | :------: |
|  token   | str  |    是    | 请求头部 | 身体验证 |

​	**返回结果**：JSON

[

{"count": day_createuser，“date”：day_date},

{"count": day_createuser，“date”：day_date},

......（共三十天）

]

| 返回值 | 类型 | 是否必传 |    说明    |
| :----: | :--: | :------: | :--------: |
| count  | int  |    是    | 日增用户数 |
|  date  | date |    是    |  当天时间  |

