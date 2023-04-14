
# Connect to _Amazon S3_ by using _AWS_ PrivateLink interface _VPC_ endpoints
## Follow these Steps:-
- Take two AWS account:- account A and account B
> 
- Sign in Account A
	- 
	- [Go to in VPC Service and create a VPC endpoint](https://us-west-1.console.aws.amazon.com/vpc/home?region=us-west-1#Endpoints:)
		- 
		- Click on Create endpoint <br /> 
			<img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image23-34-14_2023-04-14.png"> <br />		
		- Give **Name tag** and choose Service category **AWS Services** <br />

		- Now scroll the page and here search services **S3**. Then select a specific region **Service Name = com.amazonaws.us-west-1.s3** and select Type **Interface** <br />
		 <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image23-40-36_2023-04-14.png"> <br />
     <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image00-19-00_2023-04-15.png"> <br />
		- Now scroll down select the VPC and only one Subnet in which your instance or you will launch. <br />
		 <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image23-55-16_2023-04-14.png"> <br />
		- In the security group you can take the default security group and will change this security inbound. Give inbound rule only **HTTPS  0.0.0.0/0** <br />
		- Last in the **Policy** give *Full access* and click on **Create endpoint** <br />
		- Enpoint is created now and now change the **Security Group Inbound** and give only **HTTPS     0.0.0.0/0**  <br />
		     > ***VPC endpoint is configured and created.***
		     
		     <br />
	- Launch the *EC2 instance* in Same Region, VPC, Subnet as you configred VPC endpoint.
		-  
		- Here I put the picture <br /> 
		  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/97fe22d681a1c089c6a6507c9464ad12947260bd/Images/Image01-01-28_2023-04-15.png"> 
		  <br /> 

-  Sign in Customer Account
	- 
	- [Go in S3 service and create a bucket](https://s3.console.aws.amazon.com/s3/buckets?region=us-west-1&region=us-west-1) <br /> 
		<img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/e0c70660cb33b9b13a5029c742180538188b889b/CustomerAC_Image/Image02-04-03_2023-04-15.png"> <br /> 
	-  Click on the bucket name and go in the **bucket**
	- In the bucket go in **Permissions** tab.  Then scroll the page and edit the **Bucket policy**. Fill this file content in there.
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Statement1",
            "Effect": "Allow",
            "Principal": {
                "AWS": "arn:aws:iam::CUSTOMER_ACCOUNT_ID:root"
            },
            "Action": "s3:*",
            "Resource": "arn:aws:s3:::mybucket221a"
        },
        {
            "Sid": "Statement2",
            "Effect": "Allow",
            "Principal": {
                "AWS": "ARN_OF_TECHOCLOUDS_INSTANCE_ROLE"
            },
            "Action": "s3:GetObject",
            "Resource": "arn:aws:s3:::mybucket221a/myfolder/*",
            "Condition": {
                "StringEquals": {
                    "aws:SourceVpce": "vpce-<VPC_ENDPOINT_ID>"
                }
            }
        }
    ]
}
```
> *Note:- With this policy you can only download the object. but you cann't list the object in the Customer Bucket. If you want to take all customer-bucket access then change* ``"Action": "s3:GetObject"`` *to* ``"Action": "s3:*"``  *and change this also* ``"Resource": "arn:aws:s3:::mybucket221a/myfolder/*"`` *to* ``"Resource": "arn:aws:s3:::mybucket221a/*"``.
