# AWS Auto Scaling CLI Practice (Sept 7, 2026)

## Create Launch Template
```bash
aws ec2 create-launch-template \
  --launch-template-name MamotorsTemplate \
  --version-description "v1" \
  --launch-template-data '{
    "ImageId":"ami-xxxxxxxx0",
    "InstanceType":"t2.micro",
    "KeyName":"mudasir-key",
    "SecurityGroupIds":["sg-xxxxxx"],
    "SubnetId":"subnet-xxxxxx"
  }'  
Create Auto Scaling Groupaws autoscaling create-auto-scaling-group \
  --auto-scaling-group-name MamotorsASG \
  --launch-template LaunchTemplateName=MamotorsTemplate,Version=1 \
  --min-size 1 \
  --max-size 3 \
  --desired-capacity 2 \
  --vpc-zone-identifier "subnet-xxxxxx" \
  --health-check-type EC2 \
  --health-check-grace-period 190
Update Auto Scaling Group
cat << 'EOF' > autoscaling-cli.md
# AWS Auto Scaling CLI Practice (Sept 7, 2026)

## Create Launch Template
```bash
aws ec2 create-launch-template \
  --launch-template-name MamotorsTemplate \
  --version-description "v1" \
  --launch-template-data '{
    "ImageId":"ami-xxxxxxxx0",
    "InstanceType":"t2.micro",
    "KeyName":"mudasir-key",
    "SecurityGroupIds":["sg-xxxxxx"],
    "SubnetId":"subnet-xxxxxx"
  }'  
Create Auto Scaling Groupaws autoscaling 
  --auto-scaling-group-name MamotorsASG \
  --launch-template LaunchTemplateName=MamotorsTemplate,Version=1 \
  --min-size 1 \
  --max-size 3 \
  --desired-capacity 2 \
  --vpc-zone-identifier "subnet-xxxxxx" \
  --health-check-type EC2 \
  --health-check-grace-period 190
Update Auto Scaling Group

Update Auto Scaling Group
aws autoscaling update-auto-scaling-group \
  --auto-scaling-group-name MamotorsASG \
  --desired-capacity 3 \
  --vpc-zone-identifier "subnet-xxxxxxxx"

Scaling Policies
aws autoscaling put-scaling-policy \
  --auto-scaling-group-name MamotorsASG \
  --policy-name ScaleOut \
  --adjustment-type ChangeInCapacity \
  --scaling-adjustment 1
