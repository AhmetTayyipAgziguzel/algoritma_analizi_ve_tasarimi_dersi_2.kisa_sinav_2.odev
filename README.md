# algoritma_analizi_ve_tasarimi_dersi_2.kisa_sinav_2.odev

ALGORİTMA ANALİZİ VE TASARIMI DERSİ 2.KISA SINAV 2.ÖDEV


KODUN ÇALIŞTIRILMASI

•	Kodu çalıştırmadan önce görsellerin bulunduğu dosyayı bilgisayarınıza indirip dosya yolunu düzeltmeniz gerekmektedir.


YAZDIĞIMIZ KOD HAKKINDA BİLGİ

•	Kod Python programlama dili ile yazılmıştır ve kullanılan algoritma ve yöntemler aşağıda genel olarak açıklanmıştır.

•	Kodu yazarken https://drive.google.com/drive/folders/1WXM3kbKfKt-k8L87to47WQamYn6oeIym?usp=share_link linkindeki görsel dosyasını bilgisayara indirdik ve kod dosyası ile aynı dizine bu klasörü ekledik. Sonrasında kod içerisinde bu klasör okunarak görseller karşılaştırılmıştır.

•	Kodun çıktısı iki resim arasındaki benzerlik oranını yüzdesel olarak verir ve benzerlik oranını azalan sırada listeler.


OPENCV IMAGE TEMPLATE MATHİNG YÖNTEMİ

OpenCV, bilgisayarlı görü kütüphanesi olup, görüntüleri analiz etmek ve işlemek için bir dizi işlev sunar. OpenCV'nin "Template Matching" (şablon eşleme) işlevi, bir resim içinde belirli bir nesnenin varlığını tespit etmek için kullanılır.
Bir başka deyişle, bu yöntem, bir şablon görüntüyü başka bir büyük görüntüde aramak için kullanılır. Şablon eşleme, genellikle belirli bir nesneyi tanımlamak için basit ve etkili bir yöntemdir. Bununla birlikte, yöntem, şablonun ölçeğini, rotasyonunu veya ışık koşullarını değiştiren durumlarla iyi başa çıkamaz. Bu durumlarda daha sofistike yöntemler (örneğin, özellik tabanlı eşleştirme, makine öğrenme vb.) kullanılabilir.
OpenCV'deki `cv2.matchTemplate()` fonksiyonu, bu işlevi gerçekleştirmek için kullanılır. Bu işlev, giriş görüntüsü ve bir şablon görüntüsü alır ve her bir konumdaki eşleşme sonucunu gösteren bir sonuç görüntüsü döndürür. Bu sonuç görüntüsünde, her piksel, orijinal görüntünün ilgili konumundaki şablonun eşleşmesinin kalitesini temsil eder.
Birkaç farklı eşleştirme yöntemi mevcuttur, bunlar `cv2.TM_CCOEFF`,` cv2.TM_CCOEFF_NORMED`, `cv2.TM_CCORR`,` cv2.TM_CCORR_NORMED`,` cv2.TM_SQDIFF`, ve `cv2.TM_SQDIFF_NORMED` olarak belirtilir. Her biri, eşleşmenin nasıl değerlendirildiğine dair biraz farklı bir yöntem sağlar ve hangi yöntemin kullanılacağı, belirli bir duruma bağlıdır.
Sonuçta, `cv2.minMaxLoc()` fonksiyonunu kullanarak sonuç görüntüsünden en iyi ve en kötü eşleşme konumlarını alabiliriz. Bu fonksiyon, en düşük ve en yüksek yoğunluğa sahip piksellerin koordinatlarını döndürür. Bu koordinatlar, ardından şablonun giriş görüntüsünde nerede bulunduğunu belirlemek için kullanılır.


KODDA KULLANDIĞIMIZ ALGORİTMA VE YÖNTEMLER HAKKINDA BİLGİ

1.	Şablon Eşleştirme (Template Matching): Şablon eşleştirme, bir görüntüdeki belirli bir şablonun diğer görüntülerdeki benzerliklerini bulmaya yönelik bir yöntemdir. Bu yöntemde, şablon görüntüsü, orijinal görüntü üzerinde kaydırılarak karşılaştırılır ve benzerlik skorları hesaplanır. OpenCV'deki `cv2.matchTemplate` fonksiyonu, farklı eşleştirme yöntemlerini kullanarak şablon eşleştirmesini gerçekleştirir. Bu yöntem, bir görüntüden diğerine benzerlik ölçmek için kullanılan temel bir araçtır.

2.	Gri Tonlamalı Görüntü (Grayscale Image): Gri tonlamalı görüntüler, piksellerin sadece parlaklık değerlerini içeren ve renk bilgisini ihmal eden görüntülerdir. Şablon eşleştirme işlemi genellikle gri tonlamalı görüntüler üzerinde gerçekleştirilir, çünkü renk bilgisine ihtiyaç duyulmaz ve işlem daha hızlı ve basit hale gelir. `cv2.IMREAD_GRAYSCALE` parametresi kullanılarak görüntüler gri tonlamalı olarak okunur.

3.	Korelasyon (Correlation): Şablon eşleştirmede, iki görüntü arasındaki benzerlik skoru genellikle korelasyon ölçütüyle belirlenir. Korelasyon, iki görüntü arasındaki ilişkiyi ölçen bir istatistiksel ölçüdür. Benzerlik skoru, korelasyon katsayısının bir fonksiyonu olarak hesaplanır. `cv2.matchTemplate` fonksiyonu, korelasyon yöntemlerinden biri olan TM_CCOEFF_NORMED yöntemini kullanır.

4.	Minimum-Maksimum Normalizasyonu (Min-Max Normalization): Şablon eşleştirme sonucunda elde edilen benzerlik skoru, minimum ve maksimum değerler arasında normalleştirilir. `cv2.minMaxLoc` fonksiyonu, benzerlik skorunun normalleştirilmesini gerçekleştirir ve maksimum benzerlik skoru ile konumunu elde eder.


KARMAŞIKLIK ANALİZİ

1.	`os.listdir(folder_path)`: Bu işlem, belirtilen dizindeki tüm dosyaların bir listesini döndürür. Bu, dosya sayısına (n) bağlıdır, bu yüzden karmaşıklığı O(n) olarak kabul edebiliriz.

2.	İki döngü: Dış döngü n iterasyon yapar ve iç döngü i'nin her bir değeri için n-i iterasyon yapar. Bu, iki döngünün karmaşıklığını O(n^2) yapar.

3.	`cv2.imread()`: Bu işlem, bir resmi okur ve bir matris olarak döndürür. İşlem karmaşıklığı, resmin boyutuna (genişlik x yükseklik) bağlıdır. Ancak bu karmaşıklık, genellikle resimlerin boyutunun sabit olduğu ve bu kod parçacığında döngülerin karmaşıklığının bu işlemi aşacağı düşünülerek ihmal edilir.

4.	`cv2.matchTemplate()`: Bu işlem, iki resmi karşılaştırır ve her bir piksel değeri için bir benzerlik skoru hesaplar. Bu işlem karmaşıklığı, giriş resimlerinin boyutlarına bağlıdır. Ancak bu karmaşıklık, genellikle resimlerin boyutunun sabit olduğu ve bu kod parçacığında döngülerin karmaşıklığının bu işlemi aşacağı düşünülerek ihmal edilir.

5.	`cv2.minMaxLoc()`: Bu işlem, bir matriste en küçük ve en büyük değeri bulur. Bu işlem karmaşıklığı, giriş matrisinin boyutuna bağlıdır. Ancak bu karmaşıklık, genellikle resimlerin boyutunun sabit olduğu ve bu kod parçacığında döngülerin karmaşıklığının bu işlemi aşacağı düşünülerek ihmal edilir.

6.	Benzerlik eşiği kontrolü: Bu, sabit zamanlı bir işlem olan O(1)'dir.

7.	Benzer görüntüler listesine ekleme: Bu, listeye ekleme işlemi olduğundan O(1) karmaşıklığına sahiptir.

8.	Listeyi sıralama: Bu işlem, Python'un timsort algoritması ile gerçekleştirilir ve karmaşıklığı O(n log n)'dir.

Sonuç olarak, kodun genel karmaşıklığı, en büyük karmaşıklığa sahip olan adıma, yani döngülere dayanır ve bu nedenle kodun zaman karmaşıklığı O(n^2) olarak kabul edilir. Bu, kodun her iki görüntüyü karşılaştırmak için tüm görüntü çiftlerini denediği anlamına gelir, bu nedenle karmaşıklık karesel olarak artar.


KAYNAKÇA

•	OpenCV Python: Template Matching

•	Bradski, G., & Kaehler, A. (2008). Learning OpenCV: Computer vision with the OpenCV library. O'Reilly Media, Inc

•	Soleymani, A. (2020). [Practical Python and OpenCV: Learn to build practical

•	OpenCV Resmi Belgeleri: https://docs.opencv.org/

