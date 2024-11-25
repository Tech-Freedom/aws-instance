# AWS EC2 Instance Creation Guide

Based on AWS Cloud Quest Learning Experience



## Prerequisites

- AWS Management Console access

- Basic understanding of cloud computing

- Selected AWS Region (Cloud Quest typically uses us-east-1)



## Step-by-Step Instance Creation Process



### 1. Access EC2 Dashboard

- Log into AWS Management Console

- Navigate to EC2 service

- Click "Launch Instance" button



### 2. Choose Amazon Machine Image (AMI)
The AMI provides the information required for launching an instance.

- Select Amazon Linux 2 AMI

- This is a free-tier eligible option

- Comes with common tools pre-installed



### 3. Choose Instance Type
The Instance Type specifies the hardware of the host computer used for this instance. The instance types are grouped based on their compute, memory and storage capabilities.

- Select t2.micro for free tier
![aws1](https://github.com/user-attachments/assets/fba4a698-5c3a-41a0-bad1-38d949b487dd)
- Specifications:

  - 1 vCPU

  - 1 GB RAM

  - Variable ECU (Elastic Compute Units)
    
- Key pair: Proceed without a keypair name (not recommended for irl scenarios, only suitable for lab environment)
  Amazon EC2 uses public key cryptography to encrypt and decrypt login information. Public key cryprography uses a public key to encrypt a piece of data and the recipient uses the private key to decrypt the data. The public and private keys are known as key pair. 
  



### 4. Configure Instance Network Details

- Network: Lab VPC
  A Virtual Private Cloud resides in an AWS Region, but the Subnet resides within a single AZ (Availability Zone)

- Subnet: Choose the one which represents your desired Availability Zone! For this example, we need to choose Subnet 1 for the AZ us-east-1a
  ![awsnetworksettings](https://github.com/user-attachments/assets/e7a287fe-a66d-40e7-b367-5e4bb36e25ad)


- Auto-assign Public IP: Enable

- Keep other settings as default


### 5. Configure a virtual Firewall
  The Firewall settings on AWS are known as Security Groups. The Security Groups control the traffic for one or more instances. Rules can be added to a security group for it to allow traffic from its associated instances.
  ![AWS  Security Group](https://github.com/user-attachments/assets/5787de86-c1ea-4b6e-8970-a1215a8a182e)

  
  - Name the security group
    
  - Specify its characteristics in the description
    
  - Choose security group type (for this lab example, HTTP must be used)


### 6. Add Storage

- Default: 8 GB root volume

- Volume type: GP2 (General Purpose SSD)

- Delete on termination: Yes



### 7. Advanced Details 

- Upload the user data file provided by the quest.
  

### 8. Review and Launch
![awsinstancereview](https://github.com/user-attachments/assets/ade04569-9a79-482e-b598-ce6e227810d5)


- Review all configurations

- Click "Launch"

- Launch instance



### 8. Monitor Instance Status

- Wait for instance state: "Running"

- Check status checks: "2/2 checks passed"

- Note the public IP address



### 9. Connect to Instance

```bash

# Example SSH command

ssh -i "your-key-pair.pem" ec2-user@your-public-ip

```



## Best Practices Learned

1. Always use security groups to control traffic

2. Keep your key pair file secure

3. Use tags to identify resources

4. Monitor instance metrics

5. Stop or terminate instances when not needed



## Common Troubleshooting

1. Cannot connect to instance:

   - Check security group rules

   - Verify key pair permissions

   - Confirm instance is running



2. Instance launch fails:

   - Check service limits

   - Verify AMI availability

   - Review error messages



## Cost Considerations

- Free tier includes:

  - 750 hours per month of t2.micro

  - 30 GB of storage

  - 1 GB of snapshots

- Monitor usage to avoid charges

- Stop instances when not in use



## Key Commands Learned

```bash

# Check instance status

aws ec2 describe-instances



# Stop instance

aws ec2 stop-instances --instance-ids i-1234567890abcdef0



# Start instance

aws ec2 start-instances --instance-ids i-1234567890abcdef0



# Terminate instance

aws ec2 terminate-instances --instance-ids i-1234567890abcdef0

```



## Security Tips

1. Use principle of least privilege

2. Regularly update security groups

3. Use strong key pairs

4. Enable CloudTrail for auditing

5. Monitor AWS Trusted Advisor recommendations



## Next Steps

1. Learn about Auto Scaling

2. Explore Elastic Load Balancing

3. Study AWS networking concepts

4. Practice with different instance types

5. Learn about AWS CLI commands



## Resources

- AWS Documentation

- Cloud Quest game scenarios

- AWS Well-Architected Framework

- AWS Free Tier details



## Notes

This guide is based on the AWS Cloud Quest learning experience and represents a simplified version of AWS instance creation. In production environments, additional security and configuration considerations may be necessary.


