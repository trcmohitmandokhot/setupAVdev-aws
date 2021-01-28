# Repository: setupAVdev-aws
- Author - Mohit Mandokhot
- Version - 0.1.0
- Date - 01/22/2021. 

## Why AWS or a Cloud Service? 

## Choosing your instance
### g4dn.xlarge
Please refer to additional documentation (EC2-g4) [https://aws.amazon.com/ec2/instance-types/g4/]
If you are a new AWS customer, you may need to request a limit increase on vCPUs you are able to allocate to the G type instance.
SSD Storage = 125GB
SSD Root = 96GB
This is going to cost you some $ to provision storage.  
### t2.xlarge
No GPU, but 4 vCPUs 1 core per thread.
Could elastic interference be used?


## Choosing your AMI
While an Ubuntu 18.04 LTS Server edition can be used as a starter for your EC2 instance, AWS offers you a choice of Linux Machine Images that may be better suited for your cause. (Remove these lines ref Ubuntu 18.04)

For example, an Autoware + LGSVL setup requires the use of NVIDIA Drivers and CUDA Support. The use of Deep Learning Base Ubuntu 18.04 AMI may be a better choice for the system. 

For this example use the Amazon Deep Learning AMI (Base or Full Version). It appears that this AMI is supported better, with regular bug-fixes. However, be careful of the right driver versions needed to activate your GPU and run appropriate downstream applications. 

A good place to start is to refer to the driver and software requirements for your intended application. For example [Autoware.ai/Requirements] (https://gitlab.com/autowarefoundation/autoware.ai/autoware/-/wikis/Source-Build)

## Initial checks after launching instance
![Login_Check](/images/system_check1.png)

### Check if all hard-drives are mounted
    $ df -h
It may occur that at this time not all of your NVMe are mounted. <br>

To access NVMe Drives, check if NVMe drivers are [mounted] (https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/nvme-ebs-volumes.html)

    $ modinfo nvme

If no drivers are found try to update drivers from the instructions available. <br> 

The goal here is to mount the provisioned SSD harddrive to the machine and make it available for use. 

Additional links from AWS may help [Make a volume available for use] (https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/ebs-using-volumes.html)

You may want to research on whether to use XFS vs. EXT4 style file system. This is above my current knowledge level. 

## One Route of Action
Something something <br>
### Install a lightweight Ubuntu Desktop Environment

### Install a NOMACHINE Server on the AMS

## Other route of Action X11 Forwarding. Enable running of display tools
BAD IDEA
Remote machine in Ubuntu is the client
Your Windows or Local Machine is the server. 

1. Enable X11 forwarding on remote machine (client) by configuring ssh_config <br>
2. Install XMing on Windows Local Machine (server). Run XMing server. <br>
3. Run PuTTY with X11 forwarding enabled. <br>
4. Log in to the machine. Test my typing xterm or xclock apps on terminal. If it gives an error install x11-apps from apt-get 

## INSTALL ROBOTIC OPERATING SYSTEM
### ROS-Melodic for Ubuntu 18.04
(Installation Guide) [http://wiki.ros.org/melodic/Installation/Ubuntu]

- Install ROS-MELODIC-DESKTOP. This includes ROS, rqt, rviz, and robot-generic libraries
- Make ROS commands available to the current shell
    source /opt/ros/melodic/setup.bash
- Test by finding popular packages such as rospy or roscpp
    rospack find rospy
- Install essential dependiences as stated in the program
    sudo apt install python-rosdep python-rosinstall python-rosinstall-generator python-wstool build-essential

## CAN THIS BE DONE ON A NON-GPU DEVICE? 
