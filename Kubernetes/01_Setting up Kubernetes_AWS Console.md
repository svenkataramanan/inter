# Setting up Kubernetes from AWS Console
This section talks about the setup of Kubernetes from the AWS Console

## Create Policy, User, Role and Access Key
To access Kubernetes a certain set of permissions are required. To create, go to the AWS console ```https://console.aws.amazon.com/iam/```

### Create Policy
Kubernetes heavily depends on CloudFormation scripts for its creation. So permission is required to access CloudFormation and EKS. Create two policies

EKS-Admin-policy:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "eks:*"
            ],
            "Resource": "*"
        }
    ]
}
```
CloudFormation-Admin-policy:
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Effect": "Allow",
            "Action": [
                "cloudformation:*"
            ],
            "Resource": "*"
        }
    ]
}
```
### Create User
Create a user _EKS-TW-Admin_ and assign the policies. The last 2 policies listed are the custom policies created above
  - AmazonEC2FullAccess
  - IAMFullAccess
  - AmazonVPCFullAccess
  - CloudFormation-Admin-policy
  - EKS-Admin-policy  

### Create IAM role
Create an IAM role _EKS-TW-Role_ which has _EKS_ permission.
- Choose _Roles_ --> _Create role_  
- Choose _EKS_ service followed by _Allows EKS to manage clusters on your behalf_  
- Choose _Next: Permissions_
- Click _Next: Review_
- Enter a *unique* Role name, _EKS-TW-Role_ and click *_Create Role_*

### Create API Access key
For the user _EKS-TW-Admin_  create the Access Key and Secret key
- Choose _Users_ --> _EKS-TW-Admin_ 
- Choose _Security credentials_ tab and click *_Create access key_*
Download the key file and save it securely as it is used latter

### Create Key Pair
Create a new Key Pair which can be used when the instances gets created. To create, go to the AWS console ```https://console.aws.amazon.com/ec2/```
- Choose _Key Pairs_ and click *_Create key pair_*  
- Provide a name for the keypair _EKS-TW-KeyPair_ and click *_Create key pair_*
The key pair file (_EKS-TW-KeyPair.pem_) would automatically download. Save this file for latter use.
