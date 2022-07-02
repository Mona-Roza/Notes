### Getting Started
   In this section we'll talk about the key parts, commands and packages when we using server. If you have any idea or feedback about my notes and you can type in issues, you'll help me and the other learners. 


### Create Instance with AWS
If you want to use this service, you should log in your AWS console.

After logging in your console you should follow these tab parts:
> Services->Compute->EC2->Launch instance

In this tab, you can create a new instance/machine. We are using **Ubuntu 18.4**. So what we will talk about in the other sections will be explained through this version of ubuntu. After this explanation we can flow directions:

**!** This directions explain AWS free services. If you need different system requirements, you can change your system elements except the operating system.

1. Firstly choose name for your server:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/names_and_tags.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/names_and_tags.png)

2. Choose your machine's operating system like that:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/machine_image.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/machine_image.png)


3. Choose your instance type like that:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/instance_type.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/instance_type.png)

 
4. We need a key pair because of we can't create password for root user when we are creating our server:


[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/key_pair.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/key_pair.png)


5. When you are creating your key pair, you should be careful about your key's extension. Because you need your_key.pem file. But if you hadn't created your key with .pem extension, don't worry about that. Because, I will explain converting your key file from .ppk to .pem in the other section.

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/create_key_pair.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/create_key_pair.png)


6. If your Summary part like that, we can launch our instance:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/launch_instance.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/launch_instance.png)


#### Converting key pair using PuTTy:
In this section we'll convert our key with .pem extension to key with .ppk extension. But before go on the section, you need PuTTy application. So you should install PuTTy.


1. Start PuTTygen.


2. Open your file with .pem extension with using Load button. After that, you can click Generate button.

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/convert_key.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/convert_key.png)


3. Save public key with Save button. But don't forget where you save.

#### Connect with PuTTy:
In this section we'll access our server with our key pair, remove with accessing key pair, allow accessing with password and create a password for root:


1.  Your ip here: 

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/ip_address.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/ip_address.png)


2. Follow **Connection/SSH/Auth** path and browse directory where you saved your key. And after that Click open button.

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/select_key_file.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/select_key_file.png)


3. You should login as ubuntu where opened command line window:
`login as: ubuntu`


4. Start editing ssh_config file with `sudo nano /etc/ssh/sshd_config  ` command.


5. Find `PasswordAuthentication` permission and change the value to yes. After that append this  permission : `PermitRootLogin yes` 


6. Close and save editing the file with CTRL + X shortcut.


7. Create password for root with this command: `sudo passwd root`


8. We changed permissions so we have to restart sshd service. Use `sudo service sshd restart` or `sudo systemctl restart sshd` command.


9. Update your system with this command: `sudo apt update && sudo apt upgrade -y`
Also run this command whenever you log in your server.


**!** If you want to add user, you can follow next steps.


10. Create a user with `sudo adduser user-name` command.


11. You can change this user's permissons with `sudo usermod -aG sudo user-name` command. This command gives root permissons to your user. 


12. You can create a password for your user with `sudo passwd user-name` command.


With this directions we edited our machine's permissions for accessing with password. After that we can access our server with using any SSH client for Windows machine or with using `ssh root@ip-adsress` command in your machine's command line for Mac or Linux machine.

