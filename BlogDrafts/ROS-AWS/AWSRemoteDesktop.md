# Running Robot Operating (ROS) System on AWS

## Tutorials

1. [YouTube Tutorial](https://www.youtube.com/watch?v=9U6GDonGFHw)

## AWS

### Setting up a UI
1. [Connect to AWS EC2 using PUTTY](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/putty.html?icmpid=docs_ec2_console)


1. [Ubuntu Desktop AWS Windows](https://aws.amazon.com/premiumsupport/knowledge-center/connect-to-ubuntu-1604-windows/)

[YouTub Video](https://www.youtube.com/watch?v=ljvgwmJCUjw)

1. Connect ssh to ec2 instance.

2. Become the super user after executing the command sudo -s

3. Type the following commands to install vncserver:
  * sudo apt-get install ubuntu-desktop
  * sudo apt-get install vnc4server
  * sudo apt-get install gnome-panel

4. Type the command vncserver once.

5. Remember the password you use for accessing the vncserver. Kill vncserver by typing the command vncserver -kill :1

6. Type vi .vnc/xstartup and modify the file

```bash
#!/bin/sh
# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
gnome-session –session=gnome-classic &
gnome-panel&
```

7. Press ESC, followed by :wq to save and exit the file

8. Type vncserver again to start vncserver.

9. Download and install [tightvnc](ttp://www.tightvnc.com/download.php) to connect remote desktop.

10. Now run tightvnc viewer

11. Add the port no 5901 in your ec2 security group

12. Write your public ip in remote host text box and port no. <publicIp>::5901

13. Your desktop in ec2 instance is ready and execute the command vncserver after every restart.
