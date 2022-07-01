#### Başlarken
   Bu bölümde server kullanırken ihtiyaç duyabileceğimiz püf noktalar, komut satırları ve uygulamalar hakkında konuşacağız. Görüş ve geri bildirimlerinizi  issues kısmından bildirirseniz, bana ve öğrenmek isteyenlere yardımcı olabilirsiniz.

#### AWS Hizmeti İle Instance Oluşturma
Bu hizmeti kullanabilmek için öncelikle AWS konsolunuza giriş yapmalısınız. 

Konsolunuza giriş yaptıktan sonra **Services** sekmesinin altından** Compute** sekmesine ve Compute sekmesi altından **EC2** sekmesine giriyoruz. Bu sekmenin içerisinden **Launch instance** sekmesine geçiş yapıyoruz. Yani yolumuz şu şekilde:
> Services->Compute->EC2->Launch instance

Artık bu sekme üzerinden kendimize bir instance yani bir makine oluşturabiliriz.  Burada oluşturulması gösterilen makine **Ubuntu 18.4** içermekte ve ilerleyen safhalarda Ubuntu'nun bu sürümüne yönelik yönergeler yer almaktadır. Şimdi aşağıdaki adımları izleyelim:

**!** Buradaki adımlar, AWS'nin ücretsiz sağladığı hizmetler çerçevesinde şekillenmiştir.  İşletim sistemi dışındaki seçenekler ihtiyaca göre şekillendirilebilir.

1. Öncelikle isimlendirmemizi yapıyoruz:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/names_and_tags.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/names_and_tags.png)


2.  Makinemizin işletim sistemini seçiyoruz:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/machine_image.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/machine_image.png)


3. Instance typemızı seçiyoruz:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/instance_type.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/instance_type.png)


4. AWS üzerinde root kullanıcımız için direkt şifre oluşturamıyoruz, bu nedenle makinemize bağlabilmek için bir key pair almamız gerekiyor:


[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/key_pair.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/key_pair.png)


5. Key pairi oluştururken dikkat etmemiz gereken noktalardan bir tanesi .pem uzantılı şekilde oluşturmaktır. Eğer key pairinizi .pem uzantılı oluşturmadıysanız bir sonraki bölümde .ppk uzantısından .pem uzantısına dönüşüm için gerekli adımlar belirtilecektir.

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/create_key_pair.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/create_key_pair.png)


6. Eğer Summary bölümünüz aşağıda bulunan resimdeki gibiyse artık instancemizi başlatabiliriz:

[![](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/launch_instance.png)](https://github.com/Mona-Roza/Notes/blob/main/About%20Server%20%26%20About%20Linux/images/launch_instance.png)
