# 用户管理

## 根据管理需要创建IAM用户/用户组
根据业务的需要对不同的IAM用户进行不同范围的授权，通常通过建立用户组来实现。然后将用户加到对应的用户组中，就实现了对用户的授权管理。
### 根据业务需要创建用户组
1. Service Box中输入IAM，跳转到IAM服务的console
<img width="1245" alt="Screen Shot 2022-04-15 at 8 41 47 PM" src="https://user-images.githubusercontent.com/97269758/163571964-0559407a-5dcf-4dec-89d0-cc6ce5fd721d.png">

2.点击左边栏的User Groups
<img width="1144" alt="Screen Shot 2022-04-15 at 8 43 19 PM" src="https://user-images.githubusercontent.com/97269758/163572083-e2fbc3b8-1c52-49b9-b6d8-1151a3758db1.png">

<img width="1410" alt="Screen Shot 2022-04-15 at 8 44 22 PM" src="https://user-images.githubusercontent.com/97269758/163572196-fd5b122d-b1f6-4868-9e7a-2d08a48db0cf.png">

3. 点击Create Group
创建Group_Analytics,赋给这个User Group对两个服务的控制权限。

<img width="1146" alt="Screen Shot 2022-04-15 at 8 48 25 PM" src="https://user-images.githubusercontent.com/97269758/163572627-16b4407f-d99a-4a79-acf4-cf877c511216.png">

4. 添加新的IAM用户

<img width="1415" alt="Screen Shot 2022-04-15 at 8 48 51 PM" src="https://user-images.githubusercontent.com/97269758/163572660-af9f4fd1-9d9b-4ec2-96b1-e10c02b94c5c.png">

5. 对IAM用户进行命名和设置登录密码

<img width="1048" alt="Screen Shot 2022-04-15 at 8 50 43 PM" src="https://user-images.githubusercontent.com/97269758/163572819-97b69639-318b-47e5-99cd-544054ca92af.png">

6. 将用户添加到对用的用户组里

<img width="1015" alt="Screen Shot 2022-04-15 at 8 51 14 PM" src="https://user-images.githubusercontent.com/97269758/163572868-de895d43-2125-48ed-a661-6025d72a98e4.png">

这样一个具有Group_Analytics用户组权限的叫User_John的IAM用户就创建好了。


## IAM用户S3桶访问控制

## IAM用户Athena表访问控制

