# 用户管理

## 创建IAM用户
1. Service Box中输入IAM，跳转到IAM服务的console

<img width="1245" alt="Screen Shot 2022-04-15 at 8 41 47 PM" src="https://user-images.githubusercontent.com/97269758/163571964-0559407a-5dcf-4dec-89d0-cc6ce5fd721d.png">

2. 创建名为User_John的IAM用户

<img width="1415" alt="Screen Shot 2022-04-15 at 8 48 51 PM" src="https://user-images.githubusercontent.com/97269758/163572660-af9f4fd1-9d9b-4ec2-96b1-e10c02b94c5c.png">

3. 对IAM用户进行命名和设置登录密码

<img width="1048" alt="Screen Shot 2022-04-15 at 8 50 43 PM" src="https://user-images.githubusercontent.com/97269758/163572819-97b69639-318b-47e5-99cd-544054ca92af.png">

## 根据管理需要创建IAM用户组
根据业务的需要对不同的IAM用户进行不同范围的授权，通常通过建立用户组来实现。然后将用户加到对应的用户组中，就实现了对用户的授权管理。
### 根据业务需要创建用户组


2.点击左边栏的User Groups
<img width="1144" alt="Screen Shot 2022-04-15 at 8 43 19 PM" src="https://user-images.githubusercontent.com/97269758/163572083-e2fbc3b8-1c52-49b9-b6d8-1151a3758db1.png">

<img width="1410" alt="Screen Shot 2022-04-15 at 8 44 22 PM" src="https://user-images.githubusercontent.com/97269758/163572196-fd5b122d-b1f6-4868-9e7a-2d08a48db0cf.png">

3. 点击Create Group
创建Group_Analytics,赋给这个User Group对Athena服务的访问控制权限。

<img width="1228" alt="Screen Shot 2022-04-15 at 10 39 07 PM" src="https://user-images.githubusercontent.com/97269758/163584162-6943e8e1-4992-402d-b9c4-f355fbae201f.png">


4. 创建自定义的policy，限制S3访问权限

<img width="1199" alt="Screen Shot 2022-04-15 at 10 40 03 PM" src="https://user-images.githubusercontent.com/97269758/163584353-91f28990-3771-4e76-9ca1-d422be7c1316.png">

Policy的json字符串如下：
```json
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws-cn:s3:::demo-bkt-apr"
            ]
        },
        {
            "Effect": "Allow",
            "Action": [
                "s3:*"
            ],
            "Resource": [
                "arn:aws-cn:s3:::demo-bkt-apr/*"
            ]
        }
    ]
}
```

5. 将demo-bkt-apr-policy策略关联到IAM用户组

<img width="1220" alt="Screen Shot 2022-04-15 at 10 42 25 PM" src="https://user-images.githubusercontent.com/97269758/163584557-030d6cba-a593-4a16-ab78-27e93b3ea1e3.png">



6. 将用户添加到对用的用户组里

<img width="1015" alt="Screen Shot 2022-04-15 at 8 51 14 PM" src="https://user-images.githubusercontent.com/97269758/163572868-de895d43-2125-48ed-a661-6025d72a98e4.png">

<img width="1427" alt="Screen Shot 2022-04-15 at 10 47 43 PM" src="https://user-images.githubusercontent.com/97269758/163585122-cd5d5c41-2a8c-4ff0-bb06-990fb4dff1d7.png">

这样这个Group_Analytics用户组就只具有访问demo-bkt-apr这个桶， 以及使用athena权限。
IAM用户User_John因为在这个组内，所以也只有这些权限。


## Athena表控制

1. service console上输入lake formation

<img width="1229" alt="Screen Shot 2022-04-15 at 10 49 35 PM" src="https://user-images.githubusercontent.com/97269758/163585299-d38cc354-64f9-4a96-b395-1ffd5efff68d.png">

2. 进入lake formation的console，点击左侧Databases，可以看到右侧的Databases的列表

<img width="1259" alt="Screen Shot 2022-04-15 at 10 50 08 PM" src="https://user-images.githubusercontent.com/97269758/163585358-b1eeff90-f6eb-4a74-8346-20b882ceccbe.png">

3. 选中目标Database，然后点击View tables

<img width="1249" alt="Screen Shot 2022-04-15 at 10 51 55 PM" src="https://user-images.githubusercontent.com/97269758/163585560-a9026b61-119c-4167-8f7a-a02c3a790079.png">

4.选中目标表，然后单击Action的Grant

<img width="1261" alt="Screen Shot 2022-04-15 at 10 52 37 PM" src="https://user-images.githubusercontent.com/97269758/163585649-3e130389-e974-4029-ac5a-e214735313e3.png">

5.对目标表的权限进行所需要的操作

<img width="844" alt="Screen Shot 2022-04-15 at 10 53 07 PM" src="https://user-images.githubusercontent.com/97269758/163585711-1f151c99-c8ec-40e0-b79f-cde5f5a67034.png">

