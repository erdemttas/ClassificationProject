# ClassificationProject
![roadmap](https://github.com/user-attachments/assets/c585fb22-dc50-425f-825d-f573a6b863ea)


## Proje Hakkında
Bu proje, 22 farklı kategoriye ait metinlerin sınıflandırılması amacıyla gerçekleştirilmiştir. Staj süresi boyunca çeşitli makine öğrenmesi ve derin öğrenme algoritmaları denenmiş, veri seti oluşturulmuş, modeller eğitilmiş ve sonuçlar analiz edilmiştir. Bu süreçte karşılaşılan sorunlara çözümler aranmış ve deneysel testlerle ilerleme kaydedilmiştir.

## Genel Sonuç
Projede farklı makine öğrenmesi algoritmaları denedim(XGboost, lstm, svm gibi) farklı embedding modelleri denedim (BERT, all-MiniLM-L6-v2), 220bin adet veri kullandım bazı algoritmalarda aşırı öğrenmeye düştü model, bazı algoritmalarda hiç öğrenemedi, bazısında öğrendi ama istenilen derece iyi öğrenemedi, nasıl daha başarılı bir sonuç ortaya koyulur üzerine çeşitli araştırmalar yaptım, nihayetinde xgboost adlı model en başarılısı oldu başarıs seviyesi %90 civarında ama test verisiyle bu civarda kendim manuel veri girdiğimde birçok kez hata yaptı. bu süreçte sıfırdan veri üretip model eğitmeye gayret gösterdim, sonuç ne kadar tatmin etmesede gerçek hayat problemlerinde yaşanabilecek sorunları gözlemlemiş oldum, bana olumlu bir katkısı olduğundan bahsedebilirim.

---

## Gelişim Süreci

### **04.07.2025 – Proje Yol Haritası ve Hazırlık**
Proje boyunca nasıl bir yol izleyeceğimi belirlemek için araştırmalar yaptım. Hangi algoritmaları kullanmalıyım, veri setini nasıl oluşturmalıyım gibi temel sorulara yanıtlar aradım. Teknik planlama yaptım.

---

### **07.07.2025 – Veri Seti Oluşturma**
Toplam 22 kategori için Claude AI yardımıyla sentetik veri ürettim. Her sınıf için 10.000 örnek olmak üzere toplam 220.000 adet veri oluşturuldu. İlk etapta bu veriler modeli eğitmek için kullanılacak.

---

### **08.07.2025 – XGBoost ile Model Eğitimi**
XGBoost algoritmasını kullanarak eğitim işlemini gerçekleştirdim. Başarı oranı (`accuracy`) %92 civarında. Ancak model, dışarıdan girilen verilerde zaman zaman yanlış sınıflandırmalar yapıyor.

![xgboost-gorsel](https://github.com/user-attachments/assets/103b769b-9bf7-464a-8805-6a5a0007ac9a)

---

### **09.07.2025 – Modelin Gerçek Performansı**
Modelin eğitim başarımı yüksek görünmesine rağmen gerçek dünya verileriyle test edildiğinde başarı oranı yaklaşık %60 civarında. Bu durumun sebebini araştırmaya başladım. Ağırlıklı olarak veri kalitesine ve overfitting’e odaklandım.

---

### **10.07.2025 – Veri Kalitesi Sorunları**
Yapay zeka tarafından üretilen verilerin tekrar eden yapılar içerdiğini gözlemledim. "Şalterde arıza var", "elektrik panosunda arıza var" gibi cümleler, sadece anahtar kelime değişerek tekrar ediyordu. Bu da modelin öğrenmesini olumsuz etkiliyor.

---

### **11.07.2025 – XGBoost Hiperparametre Denemeleri**
XGBoost modelinin parametrelerini değiştirerek farklı konfigürasyonlar denedim. Ancak sonuç olarak modelin `accuracy` değeri %99’a ulaşsa da, bu başarı tamamen ezberlemeden (overfitting) kaynaklıydı.

---

### **14.07.2025 – LSTM ile Derin Öğrenmeye Geçiş**
Klasik makine öğrenmesi yöntemlerinin yetersiz kaldığı yerlerde derin öğrenmeye geçme kararı aldım. LSTM modelini 5 epoch ile denedim ve ilk sonuçları analiz ettim.

![LSTM İlk Sonuç](https://github.com/user-attachments/assets/a526cc36-d06b-4925-a284-71e696c86ddc)

---

### **16.07.2025 – LSTM Eğitiminin Devamı**
Eğitim süresini uzatmak amacıyla epoch sayısını 100 olarak ayarladım. Ancak Google Colab oturum süresi kısıtlaması nedeniyle sadece 14 epoch tamamlanabildi. Bu sürede de model performansında ciddi bir iyileşme gözlemlenmedi.

![LSTM Devam](https://github.com/user-attachments/assets/6c102a33-0c9e-425b-89f2-d753a58aec22)

---

### **17.07.2025 – Yeni Embedding Modeli Araştırmaları**
Modelin başarısını artırmak amacıyla embedding modelini değiştirme kararı aldım. Bu kapsamda açık kaynaklı modelleri araştırıp küçük denemeler gerçekleştirdim.

---

### **20.07.2025 – MiniLM + LightGBM Denemesi**
Yeni embedding modeli olan `all-MiniLM-L6-v2` ile birlikte LightGBM algoritmasını kullandım. İlk başta yüksek doğruluk elde edilse de bu modelin de ezberleme yaptığı sonucuna ulaştım.

![LightGBM Sonuç](https://github.com/user-attachments/assets/26110777-5773-493e-b8bc-3270901e0119)

---

### **22.07.2025 – Doğal Veri Toplama Denemeleri**
Veri setinin doğallığını artırmak için internet forumları, teknik destek platformları gibi kaynaklardan gerçek kullanıcı metinleri toplamaya çalıştım. Ancak uygun ve etik veri toplamak zor olduğu için sınırlı miktarda veri elde edebildim.

---

### **25.07.2025 – SVM ile Alternatif Model Denemesi**
Support Vector Machines (SVM) algoritmasıyla modeli yeniden eğiterek alternatif sonuçlar elde ettim. Accuracy XGBoost’tan düşük olsa da, overfitting riski daha düşüktü. Bu yönüyle değerlendirmeye alınabilir.

---

### **27.07.2025 – Model Karşılaştırma ve Sonuç Analizi**
XGBoost, LightGBM, LSTM ve SVM modellerini karşılaştırdım. Aşırı öğrenme, doğruluk oranı, inference hızı gibi kriterlerle tablo çıkardım.  
SVM gerçek veri üzerindeki başarısıyla öne çıkarken, LSTM ise zaman ve kaynak açısından maliyetli kaldı.

---

### **29.07.2025 
Eğittiğim modellerin nasıl dağıtılacağı üzerine düşündüm. Kullanıcıdan gelen metni sınıflandıran basit bir Flask API tasarladım. all-MiniLM-L6-v2 embedding modeliyle metni vektöre çevirip, SVM modeline vererek sınıf tahmini yapan bir yapı kurdum. Modelin gerçek dünyada nasıl kullanılabileceğini test etmiş oldum.


---

### **30.07.2025  

Son testlerimi yaptım. BERT ve MiniLM gibi farklı embedding modellerini karşılaştırdım. Özellikle kısa metinlerde hangi yapının daha başarılı olduğunu analiz ettim. Ayrıca modellerin metin uzunluğuna göre performans değişimini inceledim.


---

### **01.08.2025
Projeyi genel olarak değerlendirdiğimde çok şey öğrendiğim bir süreç olduğunu söyleyebilirim. Gerçek hayatta karşılaşılabilecek veri problemleri, model seçimi, overfitting, eğitim süresi, embedding gibi birçok konuda deneyim kazandım.

---

### **04.08.2025 – Kapanış ve Sonuç**
Bugün githuba hesabımı güncelledim ve projeyi sonlandırdım,
