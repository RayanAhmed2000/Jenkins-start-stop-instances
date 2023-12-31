# Jenkins-start-stop-instances
How to start/stop instances or perform others actions on AWS using Jenkins

# Pre requisites
### install EC2 plugin
- Install plugin "Amazon EC2 plugin" 
### Configure Credentials
- Go to Jenkins Credentials
- Add Credential
- Select "AWS credential" from kind drop down
- Paste Access key and Secret Key
### Install AWS CLI on Jenkins Server
- sudo apt install awscli

# Jenkins JOB
### Create a New Freestyle Project
- On the Jenkins dashboard, click on New Item.
- Enter a name for your project, select Freestyle project, and click OK.
### Configure the Project
- In the General section, add a description if needed.
- Add Build Step to Start EC2 Instance
- Scroll down to the Build section.
- Click Add build step and choose Execute shell (for Linux) or Execute Windows batch command (for Windows).
- In the command area, enter the AWS CLI command to start your EC2 instance. For example:
```
aws ec2 start-instances --instance-ids i-0536e7d06b1a96b21 --region ap-south-1
```
- save project and build

# Create scheduler for Job
- Build triggers define cron
- to run every morning at 6AM
```
* 6 * * *
```

### Troubleshooting Job not running on scheduled time
- Set timezone to IST on Jenkins Server
```
sudo timedatectl set-timezone Asia/Kolkata
```
- Check changes
```
timedatectl status
```
- restart Jenkins
```
sudo systemctl restart jenkins
```

 
