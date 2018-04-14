I spent a Saturday morning trying to connect to an AWS EC2 desktop after trying to follow the instructions given by AWS on [Connecting to Ubuntu Desktop with Windows](https://aws.amazon.com/premiumsupport/knowledge-center/connect-to-ubuntu-1604-windows/) that completely failed.

The instructions described here are derived from the following <a href="https://www.youtube.com/watch?v=ljvgwmJCUjw">YouTube Video</a>. There were some parts that were not clear/correct so I have clarified and corrected them in this post.

## Configure Ubuntu Desktop Server
* Connect ssh to ec2 instance using PUTTY.
	* See [How to Connect to AWS EC2 using Putty](https://docs.aws.amazon.com/quickstarts/latest/vmlaunch/step-2-connect-to-instance.html). (I used this method and it works just fine)
*  Become the super user by executing the command

```bash
sudo -s
```

* Update the operating system

```bash
sudo apt update && sudo apt upgrade
```

* Type the following commands to install vncserver:

```bash
sudo apt-get install ubuntu-desktop
```

```bash
sudo apt-get install vnc4server
```

```bash
sudo apt-get install gnome-panel
```

* Start the VNCServer.
```bash
vncserver
```
* Remember the password you set. You will need this passcode later when you connect using [tightvnc](http://www.tightvnc.com/) .
* Kill vncserver

```bash
vncserver -kill :1
```

* Modify the VNC startup script

```bash
vi .vnc/xstartup
```

* Add the following lines to the .vnc/xstartup script

```bash
#!/bin/sh
# Uncomment the following two lines for normal desktop:
unset SESSION_MANAGER
# exec /etc/X11/xinit/xinitrc
gnome-session –session=gnome-classic &
gnome-panel&
```

![xstartup script](http://www.sequentropy.com/wp-content/uploads/2018/04/Edit-XStartupScript.jpg)

* Press ESC, followed by <code>:wq</code> (write-quit) to save and exit the file
* Start the VNCServer again
```bash
vncserver
```

## Configure your Windows Box
* Download and install [tightvnc](http://www.tightvnc.com/download.php) to connect remote desktop.
* Run [tightvnc](http://www.tightvnc.com/) viewer

## Configure your EC2 Instance

* Edit your security group.
![Edit your Security Group](http://sequentropy.com/wp-content/uploads/2018/04/SecurityGroup-LaunchWizard.jpg)
* Add  port number <strong>5901</strong> in your ec2 security group
![Add Port 5901 to security group](http://sequentropy.com/wp-content/uploads/2018/04/EditSecurityGroup.jpg)
* Write your public ip number (or DNS name) in remote host text box and port number ```<publicIp>::5901```
![TightVNC](http://sequentropy.com/wp-content/uploads/2018/04/TightVNC-Connect.jpg)
* Your desktop in ec2 instance is ready and execute the command vncserver after every restart.

## FAQ

* `Can I stop my machine and restart it?`: `Yes`. However you will have to re-run the ```vncserver``` command after restarting the server.
