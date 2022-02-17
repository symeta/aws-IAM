# aws IAM
 aws IAM related topic
## table of contents
- [achieve temporary authorization to a certain IAM user leveraging on STS assume role](#achieve-temporary-authorization-to-a-certain-IAM-user-leveraging-on-STS-assume-role)
- [cloud9 visits s3 without ak/sk](#cloud9-visits-s3-without-ak/sk)

## achieve temporary authorization to a certain IAM user leveraging on STS assume role
large enterprise has complicated organization structure. different level staff should have different level of authorization of cloud resources. however, there are cases that certain staff needs to have authorization of cloud resources that are without their everyday scope. in order to achieve temporary authorization of cloud services, aws introduces the STS assume role mechanism to build a temporary mapping raltionship (trust relationship) between roles and IAM user. after accomplishing the specific job, the relationship could be de-attached, and thus the authorization of cloud services to the IAM user is cancelled.
the trust relationship is built by configing the json @ role configuration console.

the snapshot of the role configuration console is as below:
![Screen Shot 2022-01-30 at 1 34 16 PM](https://user-images.githubusercontent.com/97269758/151688063-8c283758-1e78-4b5e-8f97-5ac6c4acb860.png)

the trust relationship is built by configuring the following json:
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::<account id>:user/dev_user"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```
the trust relationship cannot be de-attached by deleting the json.

## cloud9 visits s3 without ak/sk
