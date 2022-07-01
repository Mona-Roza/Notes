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


5. When you creating your key pair, you should be careful about your key's extension. Because you need your_key.pem file. But if you didn't create your key with .pem extension, don't worry about that. Because, I will explain the converting your key file to .pem from .ppk in the other section.

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


2.  **Connection/SSH/Auth** sekmesine geçiş yapalım ve keyimizi indirdiğimiz konumu seçelim ardından open ile onaylayalım:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/select_key_file.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/select_key_file.png)


3.  Açılan terminalde aşağıdaki gibi devam edelim:
`login as: ubuntu`

4.  `sudo nano /etc/ssh/sshd_config  `
komutu ile ssh_config dosyasını düzenleme işlemini başlatalım.

5.  Düzenlemeye açılan sshd_config dosyasının 
`PasswordAuthentication yes`
haline getirelim. 
Ardından boş herhangi bir satıra :
`PermitRootLogin yes`
izinini ekleyelim.

6. Ctrl + X ile düzenleme işlemini kaydedelim.

7.  Aşağıdaki komut ile root için şifre oluşturalım:
`sudo passwd root`

8.  İzinleri değiştirdiğimiz için 
`sudo service sshd restart  `
veya 
`sudo systemctl restart sshd`
komutlarınan  bir tanesiyle shh hizmetimizi yeniden başlatıyoruz.

9. Aşağıdaki komutla sistem güncellemelerini indirelim. Ayriyetten bu işlemi her giriş yaptığımızda yapmaya çalışalım:
`sudo apt update && sudo apt upgrade -y`

**!** Buradan sonraki adımlara, kullanıcı eklemek isterseniz devam edebilirsiniz.

10. Aşağıdaki komutla user-name isimli bir user oluşturalım. 
`sudo adduser user-name`

11. Aşağıdaki komutla isterseniz ilgili kullanıcıya root yetkilerini kullanmasına izin verebilirsiniz:
`sudo usermod -aG sudo user-name`

12. Bu komutla user-name adlı kullanıcıya şifre belirleyelim:
`sudo passwd user-name`

Bu adımlar ile şifre ile erişim için makinemizin ayarlarını düzenledik. Artık Windows için herhangi bir SSH clienti kullanarak, Mac veya Linux için kendi konsolunuza  `ssh root@ip-adsress` yazarak bağlantı kurabilirsiniz. 
