# Alexa-RaspberryPi
Run Amazon's Alexa on the RasoberryPi3 
### Amazon Alexa’ yı Raspberry Pi 3 de Çalıştırmak
### Motivasyon

Bursa/IO olarak geliştirici ve girişimcilerden oluşan ekipte 14 Hafta süren IoT Atölyesi düzenledik. IoT’ nin her aşamasını ele aldığımız bu süreç içerisindeki konulardan biri de Amazon Alexa’ yı kendi Raspberry Pi üzerine entegre etmekti. Amacımız ise atölye içerisinde katılımcıların aldıkları bilgiler ile Alexa’ yı birleştirmelerini sağlayarak kendi donanımlarını veya yapmak istedikleri işlemleri Alexa ile sesli olarak kontrol etmek. 

İzlenilecek adımlar:<br/>

•	İhtiyacımız olan malzemeler<br/>
•	Amazon developer hesabı açmak<br/>
•	Developer hesabımızda Alexa için gerekli düzenlemeleri yapmak <br/>
•	Alexa’ yı Raspberry Pi 3 üzerine kurmak <br/>
•	Alexa’yı çalıştırmak <br/>

### Neye İhtiyacımız Var 

Alexa arkasında yapay zeka olan sesli ev asistanı olarak geçmektedir. Bunu Raspberry Pi üzerinde  istenilen şekilde çalıştırmak için : <br/>
•	Raspberry Pi 3 <br/> 
•	USB Girişli Mikrofon ( Mikrafonlu Web Cam kullanılabilir) <br/>
•	Jack girişli Hoparlör veya HDMI üzerinden de ses alabilirsiniz <br/>

### Amazon Developer Hesabı 
Amazon developer hesabı açmadaki amacımız, Alexa’ yı kullanmak adına onun ses servisinden yararlanmak ve bize özel oluşturduğu ID ve alt yapıyı kullanabilmek.
*https://developer.amazon.com/* adresine giriyoruz. Burada eğer Amazon hesabımız yok ise Amazon hesabı açmamız gerekecek. **Önemli** bir nokta ise kayıt olurken ya Amerika ya da İrlanda üzerinden adres göstermeniz. Çünkü Amazon diğerlerine geliştirme yapmak için bazı fonksiyonlarını açmıyor. Bunun içinde projenizde beklemediğiniz hatalar ile karşılaşabilirsiniz. Herhangi bir adres göstermeniz yeterli. Telefon numaranız kendinizin olsun, size kayıt esnasında doğrulama kodu gönderilecek.
Evet şimdi hesabımızı da açtıktan sonra *https://developer.amazon.com*  adresinden girişimizi yapıyoruz.  Developer Console > Alexa Voice Service > Create Product  adımlarını takip ediyoruz.

![Developer Ekranı](https://github.com/BahadirGLCK/Alexa-RaspberryPi/blob/master/images/1.jpg)

### Alexa’ yı Oluşturmak 

Alexa’ yı kendimize özel hale getirmek ve belirli bir şekilde Amazon ile bağlantı kurabilmesini sağlamak adına bu düzenlemelere ihtiyaç duymaktayız. Ürünü bilgileri sayfasında aşağıda bulunan görseldeki gibi kendinize yönelik doldurabilirsiniz. 

![Yeni](https://github.com/BahadirGLCK/Alexa-RaspberryPi/blob/master/images/2.jpg)

Burada **Product ID** önemli not almanızda fayda var. Alexa’ yı indirdiğimizde burada yazdığımız ID yi gireceğiz. 
Şimdi gelelim cihazımızın güvenlik kısmını oluşturmaya. Burada 2. Sayfaya geçtiğimizde CREATE NEW PROFILE' ı tıklayarak yeni profil oluşturuyoruz.

![Güvenik Ekranı](https://github.com/BahadirGLCK/Alexa-RaspberryPi/blob/master/images/3.jpg)

Bir sonraki sayfaya geç dediğimizde ise bize Web/ Android/IOS gibi araçların hangisinde bu güvenik kısmını oluşturmak istiyorsun şekline seçenekleri veriyor. 

![Web Güvenlik Profili](https://github.com/BahadirGLCK/Alexa-RaspberryPi/blob/master/images/4.jpg)

Burada kırmızı kutu içine aldığım kısımlar bizim ekleyeceğimiz kısımlar. Allowed orgins = *https://localhost:3000*  Allowed Return URLs kısmına = *https://localhost:3000/authresponse*.  Yazıyoruz ve ADD e tıklamayı unutmayın. 
**Client ID , Client Secret ve Security Profıle ID leri de kopyalayp bir yerde tutun.** Çünkü bu kodlar bize kurulum esnasında eşleme yapmak için sorulacak. 
FINISH deyip buradaki süreci bitiriyoruz.

### Alexa’ yı Raspberry Pi 3 e Yüklemek ve Çalıştırmak 

![Rasp İlk Terminal](https://github.com/BahadirGLCK/Alexa-RaspberryPi/blob/master/images/5.jpg)

•	Yeni bir terminal açarak    “cd Desktop” <br/>
•	“git clone https://github.com/alexa/alexa-avs-sample-app.git” enter <br/>
•	Masaüstünde alexa-avs-sample-app klasörü oluştu <br/>
•	Yine komut ekranından  “cd ~/Desktop/alexa-avs-sample-app” enter <br/>
•	nano automated_install.sh  dediğimizde yukarıda resimde gördüğümüz panel geldi. Bu panelde Product ID ,
Client ID ve Client Secret kısmına ise üst aşamada not aldığımız kısımları yazdık. Ctrl+x deyip kaydettikten sonra enter ile bu ekrandan çıktık. <br/>
•	“cd ~/Desktop/alexa-avs-sample-app”  enter <br/>
•	Devamında  “ . automated_install.sh” diyerek Alexa ev asistanını Raspberry Pi üzerine kurmuş oluyoruz. Kuruluma geçmeden önce kullanım esnasında özelleştirmek veya genel olarak kalmasını istediğiniz özellikler hakkında soruları yönelttikten sonra kuruluma geçildi. En fazla 20 dk. lık bir kurulumdan sonra çalıştırma kısmına geldi. <br/>

### Alexa’yı Çalıştırmak 
Burada sıra ile diğerini kapatmadan 3 adet terminal ekranı açacağız. Bu aşamaları gerçekleştirirken çıkışınız olacak kulaklık veya hoparlör ve girişiniz olacak USB li mikrofonunuzu bağlayın.
İlk terminal ekranımızda aşağıdaki şekilde bulunan kodları yazdık. 

![İlk Terminal](https://github.com/BahadirGLCK/Alexa-RaspberryPi/blob/master/images/6.jpg)

Burada  port 3000 i dinleme işlemi gerçekleştriyoruz ve bundan sonraki terminal ekranında bunu kapatmadan şu işlemi gerçekleştiriyoruz:

![İkinci Çalıştırma Teminali](https://github.com/BahadirGLCK/Alexa-RaspberryPi/blob/master/images/7.jpg)

Burada Localhost a bağlanma işlemi gerçekleştiriyor ve amacımız token alabilmek. Burada atlanılmaması gereken bir nokta öncelikle java paneli üzerinde çıkan ilk pencereyi onayladıktantan sonra bekleyin ve browserdan sayfa açılıp local hosttan “token is ready” yazısını gördükten sonra OK a tıklayıp onay penceresini kapatabilirsiniz. 
3. Aşama ise Alexa’ nın üzerinde algılama ve cevap oranını daha kaliteli hale getirmek için kit yüklüyoruz. <br/>
•	cd ~/Desktop/alexa-avs-sample-app/samples  enter <br/>
•	cd wakeWordAgent/src && ./wakeWordAgent -e kitt_ai <br/>
Bu aşamaları gerçekleştirdik ve şu an Alexa temel işlemleri yapabilmekte.

Evet şimdi Alexa ile istediğiniz şekilde konuşabilir ona internet üzerinden arama yapabileceği tüm bilgileri sorabilirsiniz. Eğer Alexa ya kendinizin istediği size özel bir işlemi gerçekleştirmek istiyorsanız ise Amazon developer hesabınızdan Alexa Skill Kit üzerinden aşamaları takip ederek gerçekleştirebilirsiniz. 
