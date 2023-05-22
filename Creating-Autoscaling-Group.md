# How to create an autoscaling group for the sparta app.

Follow the steps below to create an autoscaling group for the Sparta App Page.

## Ground Work before ASG is created

1. Create an EC2 instane for the app titled 'tech230-ahmed-app'

- Go to `instances` and select `launch instance`.
- Name it `tech230-ahmed-app`
- Select Ubuntu Server 18.04 for your Application and OS images
- Select `t2.micro` as your instance type
- Select `tech230` as your key pair (login).
- Select relevant existing security group in the Network Settings section.
- In Advanced details you'll need to add user data. This should be the same as a working version of your app provision script.
- Click `Launch Instance` when ready.

2. Create an AMI for the app titled 'tech230-ahmed-app-AMI'

- On instance summary page, Select `Actions` dropdown and within `Image and Templates`, select `Create Image`.
- Name your AMI as `tech230-ahmed-app-AMI`
- Select `Create Image`

3. Create a template for the app titled 'tech230-ahmed-app-template'

- Go to `Launch Templates` section from the menu shown on the left hand side.
- Select `Create Launch Template`
- Name your template as `tech230-ahmed-app-TMP`
- Select your AMI and instance type (`t2.micro`)
- Select `tech230` as your key pair (login).
- Select relevant existing security group in the Network Settings section.
- In Advanced details you'll need to add user data. This should be the same as a working version of your app provision script.
- Select `Create Launch Template` when ready

## Creating ASG

You can now create your ASG from the EC2 dashboard by clicking `Create Auto Scaling Group`
