image.png

Based on the Image above.

I wrote a CloudFormation Script to Automate the Deployment of the Network Infrastructure.

In the script I:
- Created a VPC

- Created and attached an Internet Gateway to the VPC

- Created Two Subnets within the VPC with Name Tags to call them “Public” and “Private”
    - These will also need input parameters for their ranges, just like the VPC.
    - The Subnet called “Public” needs to have a NAT Gateway deployed in it
    - This will require you to allocate an Elastic IP that you can then use to assign it to the   NAT Gateway.
    - The Public Subnet needs to have the MapPublicIpOnLaunch property set to true. Use this reference for help.
    - The Private Subnet needs to have the MapPublicIpOnLaunch property set to false.

- Assign the Public and Private Subnets to their corresponding Routing table
- Created a Route in the Public Route Table to send default traffic ( 0.0.0.0/0 ) to the Internet Gateway you created
- Created a Route in the Private Route Table to send default traffic ( 0.0.0.0/0 ) to the NAT Gateway.

Finally, once I executed this CloudFormation script, I am  able to delete it and create it again, over and over in a predictable and repeatable manner, this is the true verification of working Infrastructure-as-Code.