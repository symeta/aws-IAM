# aws IAM
 aws IAM related topic

## achieve temporary authorization to a certain IAM user leveraging on STS assume role
large enterprise has complicated organization structure. different level staff should have different level of authorization of cloud resources. however, there are cases that certain staff needs to have authorization of cloud resources that are without their everyday scope. in order to achieve temporary authorization of cloud services, aws introduces the STS assume role mechanism to build a temporary mapping raltionship (trust relationship) between roles and IAM user. after accomplishing the specific job, the relationship could be de-attached, and thus the authorization of cloud services to the IAM user is cancelled.
the trust relationship is built by configing the json @ role configuration console.

the snapshot of the role configuration console is as below:


