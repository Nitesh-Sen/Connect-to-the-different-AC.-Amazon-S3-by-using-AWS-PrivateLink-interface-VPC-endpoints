
# Connect to _Amazon S3_ by using _AWS_ PrivateLink interface _VPC_ endpoints
## Follow these Steps:-
- Take two AWS account:- account A(engineer AC.) and account B(costomer AC.)
> 
- Sign in Account A
	- 
	- [Go to in VPC Service and create a VPC endpoint](https://us-west-1.console.aws.amazon.com/vpc/home?region=us-west-1#Endpoints:)
		- 
		- Click on Create endpoint <br /> 
			<img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image23-34-14_2023-04-14.png"> <br />		
		- Give name tag and choose Service category **AWS Services** <br />
		    <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image23-36-48_2023-04-14.png">  <br />
		- Now scroll the page and here search services **S3**. Then select a specific region **Service Name = com.amazonaws.us-west-1.s3** and select Type **Interface** <br />
		 <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image23-40-36_2023-04-14.png"> <br />
     <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image00-19-00_2023-04-15.png"> <br />
		- Now scroll down select the VPC and only one Subnet in which your instance or you will launch. <br />
		 <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image23-55-16_2023-04-14.png"> <br />
		- In the security group you can take the default security group and will change this security inbound. Give inbound rule **HTTPS  0.0.0.0/0** <br />
		  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image00-01-00_2023-04-15.png"> <br />
		- Last in the policy give **Full access** and click on **Create endpoint** <br />
		  <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image00-02-05_2023-04-15.png"> <br />
		- Enpoint is created now and now change the **Security Group Inbound** and give **Source 0.0.0.0/0**  <br />
		 <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/55722d0819a9e387740f9e73b588bf3d8500d1c1/Images/Image00-23-55_2023-04-15.png"> <br />
     <img alt="coding" width="700" src="https://github.com/Nitesh-Sen/Connect-to-the-different-AC.-Amazon-S3-by-using-AWS-PrivateLink-interface-VPC-endpoints/blob/9cdef7bb15f27ed461dba2e7840e3d35101533cf/Images/Image00-44-11_2023-04-15.png"> <br />
		     > ***VPC endpoint is configured and created.***
