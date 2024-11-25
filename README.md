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

- Select Amazon Linux 2 AMI

- This is a free-tier eligible option

- Comes with common tools pre-installed



### 3. Choose Instance Type

- Select t2.micro for free tier

- Specifications:

  - 1 vCPU

  - 1 GB RAM

  - Variable ECU (Elastic Compute Units)

- Perfect for learning and basic workloads



### 4. Configure Instance Details

- Network: Default VPC

- Subnet: Choose any available

- Auto-assign Public IP: Enable

- Keep other settings as default



### 5. Add Storage

- Default: 8 GB root volume

- Volume type: GP2 (General Purpose SSD)

- Delete on termination: Yes



### 6. Configure Security Group

```

Inbound Rules:

- SSH (Port 22) from My IP

- HTTP (Port 80) from Anywhere

- HTTPS (Port 443) from Anywhere



Outbound Rules:

- All traffic allowed (default)

```



### 7. Review and Launch

- Review all configurations

- Click "Launch"

- Create or select key pair

- Download key pair file (.pem)

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


