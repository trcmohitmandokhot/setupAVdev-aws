# Repository: setupAVdev-aws
Author - Mohit Mandokhot
Version - 0.1.0
Date - 01/22/2021. 

## Why AWS or a Cloud Service? 

## Choosing your instance
### g4dn.xlarge
Please refer to additional documentation (EC2-g4) [https://aws.amazon.com/ec2/instance-types/g4/]
If you are a new AWS customer, you may need to request a limit increase on vCPUs you are able to allocate to the G type instance. 
### t2.xlarge
No GPU, but 4 vCPUs 1 core per thread.
Elastic Interference could be used? Is that true?


## Choosing your AMI
While an Ubuntu 18.04 LTS Server edition can be used as a starter for your EC2 instance, AWS offers you a choice of Linux Machine Images that may be better suited for your cause. 

For example, an Autoware + LGSVL setup requires the use of NVIDIA Drivers and CUDA Support. The use of Deep Learning Base Ubuntu 18.04 AMI may be a better choice for the system. 

A good place to start is to refer to the driver and software requirements for your intended application. For example (Autoware.ai/Requirements) [https://gitlab.com/autowarefoundation/autoware.ai/autoware/-/wikis/Source-Build]

