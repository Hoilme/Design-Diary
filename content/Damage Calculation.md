
LoL'de ve benzer oyunlarda hasar hesaplaması hemen hemen aynıdır, alınan her Direnç(Zırh-Büyü Direnci) oyuncunun can havuzunu ilgili hasar türüne karşı %1 arttırır. Direnç miktarı arttıkça hasar azaltma miktarı için gereken direnç miktarı arttığından dolayı azalan getiri(Diminishing Returns) olduğu yanılsamasına düşmek çok normaldir fakat formüller böyle bir şey olmadığını açıklıyor.

Tüm fiziksel ve büyü hasarı hedefin efektif direncine(R) göre ölçeklenir. Gerçek hasar bunu tamamen baypas eder, azaltılamaz.



$$\text{Hasar Çarpanı} = \frac{100}{100 + R}$$
$$\text{Hasar Azaltma(\%)} = \text{1 - Hasar Çarpanı}$$

$$\text{Azaltılmış Hasar(Post-Mitigation Damage)} = \text{Hasar}\times \text{Hasar Çarpanı}$$

Bu formüllerdeki "Hasar Çarpanı" bize dirençlerin azalttığı hasarı verir, 100 dirence(R) sahip bir hedef $\frac{100}{100+100} = \%50$ daha az hasar alır. Canı 1000 olan bir hedefe yapılan ve 1000 hasar vuran bir saldırıdan hedef sadece 500 hasar alır. Çıkan bu sonuca baktığımız zaman alınan direnç hedefin can değerini dolaylı yoldan %100 arttırmış olur, bu değere "Efektif Can(EHP)" diyoruz. 

$$\text{Efektif Can(EHP)} = Can(HP) \times \left(1 + \frac{R}{100}\right) = HP \times \frac{100+R}{100}$$
Bu formülleri kullanarak daha önce bahsettiğim azaltılmış getirinin sadece bir yanılsama olduğunun yanısıra bir sonuca daha varıyoruz; hedefe sadece direnç(R) veya sadece can(HP) eklemenin getirdiği verim ikisini dengede tutacak şekilde paylaştırılarak eklendiğinde getirdiği verimden daha düşüktür. Bunu bir çift değişkenli fonksiyon olarak düşünüp kısmi türev alarak her statın marjinal getirisini ölçebiliriz.

$$f(\text{HP}, R) = \text{EHP} = \text{HP} \cdot \left(1 + \frac{R}{100}\right) = \text{HP} + \frac{\text{HP} \cdot R}{100}$$

Bu fonksiyonda:

* HP : Hedefin toplam can havuzu
* R : Hedefin ilgili hasar türüne karşı direnci
* $\frac{HP\times R}{100}$ : Bu terim ise çarpımsal etkileşimin yani HP ve R değerlerinin birbirlerini yukarı çektiği yerdir.
  
  Şimdi marjinal değerleri görmek için kısmi türev alalım:

#### A. Direncin Marjinal Değeri: $\frac{\partial \text{EHP}}{\partial R}$

Canı(HP) bir sabit kabul edip fonksiyondan R'ye göre türev alalım:

$$\frac{\partial \text{EHP}}{\partial R} = \frac{\partial}{\partial R} \left( \text{HP} + \frac{\text{HP}}{100} \cdot R \right) = \frac{\text{HP}}{100}$$

Buradan çıkan sonuç:
* Türevin sonucunda R değişkeni yoktur. Yani direncin sağladığı marjinal EHP getirisi sahip olunan dirence bağlı değildir. Direnç 0'ken de 300'ken de getirisi sabittir. Toplam HP'nin %1'i.
* 1000 HP'ye sahipken alınan 1 direnç +10 EHP verirken 4000 HP'ye sahipken alınan 1 direnç +40 EHP sağlar.
* Direnç kendi içinde azalan getiriye sahip değildir fakat HP ne kadar yüksekse getirisi o kadar artar.

#### B. Canın Marjinal Değeri: $\frac{\partial \text{EHP}}{\partial \text{HP}}$

Bu kez direnci(R) sabit kabul edip fonksiyondan HP'ye göre türev alalım:

$$\frac{\partial \text{EHP}}{\partial \text{HP}} = \frac{\partial}{\partial \text{HP}} \left( \text{HP} \cdot \left(1 + \frac{R}{100}\right) \right) = 1 + \frac{R}{100}$$

Buradan çıkan sonuç ise :
* Eklenen her +1 HP hedefin efektif can değerine +1 değil, 1 + $\frac{R}{100}$ ekler.
* Direnç 0'ken alınan HP +1 EHP sağlarken direnç 200'ken alınan HP +3 EHP sağlar.
* Direnç ne kadar yüksekse alınan HP değeri de bir o kadar yüksektir.


