# Running Robot Operating (ROS) System on AWS EC2

I spent a Sunday morning figuring out how to run Robot Operating System on AWS EC2. Here are the basic steps and the references to get it working. I've gone through these steps probably about 10 times today and it takes about 5 minutes to set up an instance and configure it.

One of my weekend challenges is to understand how to use Docker better. I might make a "container" or "Docker Image" for ROS. If I do, I will put the reference here.

## Installation
1. Install Ubuntu-16.04 AMI (current stable Ubuntu version)
![Ubuntu AMI](http://www.sequentropy.com/wp-content/uploads/2018/04/EC2-AMI.jpg)
2. Follow the instructions on how to configure your [Ubuntu Instance for Desktop Access](http://brianstankiewicz.com/2018/04/07/tutorial-connecting-to-aws-ec2-ubuntu-desktop/)
2. Install [ROS Kintetic](http://wiki.ros.org/kinetic/Installation/Ubuntu)
  * Do the [ROS Installation](http://wiki.ros.org/kinetic/Installation/Ubuntu) using the remote desktop.
3. Work through [ROS tutorials](http://wiki.ros.org/ROS/Tutorials)
  * Do the [ROS tutorials](http://wiki.ros.org/ROS/Tutorials) using the remote desktop.
  * Here is the first [ROS Tutorial](http://wiki.ros.org/ROS/Tutorials/UnderstandingTopics) in the series that has something that will display.
![ROS on AWS EC2](http://www.sequentropy.com/wp-content/uploads/2018/04/ROS-EC2-DemoRunning.jpg)

## Issues

* I had an issue with ```roscore```. However, I was able to do the rest of the tutorials.
* I tried to install and run the [ROS Turtlebot](http://wiki.ros.org/turtlebot/Tutorials/indigo/Turtlebot%20Installation) but I couldn't get it running. Here is what I found out.
  * Turtlebot requires [ROS Indigo](http://wiki.ros.org/indigo/Installation/Ubuntu)
  * [ROS Indigo](http://wiki.ros.org/indigo/Installation/Ubuntu) requires Ubuntu Tasty. However, I couldn't get Ubuntu-Trusty, ROS-Indigo, and Remote Desktop to all work together.

## Notes

* Installing [ROS with graphics acceleration](https://github.com/yrahal/ec2-setup)
* [Dev environment](https://github.com/yrahal/dev-machine) with graphics acceleration