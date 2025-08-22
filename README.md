# Deniz Kaynak Arama ve Sondaj Platformu 🛳️

---

## Özet
Bu proje, denizlerde doğal kaynakları arayan bir şirketin karı maksimize etmek amacıyla geliştirilmiştir. Amaç, arama bölgelerini en doğru sayıda ve uygun boyutlarda karelere bölmek, bu alanlar üzerinde platformlar kurmak ve sondaj faaliyetlerini gerçekleştirmektir. Yazılım, her bölgenin rezerv değerini hesaplar, bölümleme yapar, platform ve sondaj sayısını belirler, maliyetleri ve kar miktarını kullanıcıya sunar.  

---

## Giriş
Denizlerde kaynak arayan bir şirketin maksimum kar elde edebilmesi için:  
- Kaynak bölgelerinin belirlenmesi  
- Bu bölgelerin optimum alanlara bölünmesi gerekir  

Bölünen karelerin boyutları 1x1, 2x2, 4x4, 8x8 veya 16x16 olarak belirlenir. Yazılım, bölümlenen karelere platform kurar, kalan alanlarda sondaj yapar ve maliyetleri hesaplar. Kar miktarı, toplam rezerv ile toplam maliyet arasındaki fark olarak hesaplanır.  

---

## Yöntem
1. **GLUT ve OpenGL Başlatma**  
   - Tek pencere, çift tampon, RGB ayarı  
   - Pencere boyutu ve başlığı belirlenir  

2. **Veri Okuma ve İşleme**  
   - Dosyadan veya URL’den alınan koordinatlar `receivedData` dizisine aktarılır  
   - Karekök koordinatları işlenir ve yedek matrise kaydedilir  
   - Duplicate kontrolü yapılır, kenar sayıları belirlenir  

3. **Alan ve Rezerv Hesaplama**  
   - yardım alınan matematiksel formül : https://math.stackexchange.com/questions/2138051/how-many-squares-are-crossed-by-the-diagonal-of-a-rectangle-splitted-into-n-ti
     ```  

4. **Platform ve Sondaj Hesaplama**  
   - Her bölgeye kurulacak platform ve sondaj sayısı belirlenir  
   - Toplam platform ve sondaj maliyeti hesaplanır:  
     ```text
     Toplam maliyet = (Toplam platform * Platform fiyatı) + (Toplam sondaj * Birim değer)
     ```  
   - Kar miktarı:  
     ```text
     Kar = Toplam rezerv - Toplam maliyet
     ```  

5. **Çizim ve Görselleştirme**  
   - Her bölge OpenGL ile çizilir:  
     - 1. Bölge: Kırmızı  
     - 2. Bölge: Yeşil  
     - 3. Bölge: Mavi  
   - Grid çizgileri eklenir ve pencereye tüm veriler çizilir  

---

## Deney Sonuçları
- Program, kullanıcı tarafından girilen fiyat ve değerlerle birlikte platform sayısı, sondaj sayısı, rezerv değeri, toplam maliyet ve kar miktarını ekrana gösterir  
- Her bölge için birim kare sayısı ve alan bilgisi görüntülenir  

---
<img width="610" height="204" alt="Ekran Resmi 2025-08-22 12 30 23" src="https://github.com/user-attachments/assets/360a8008-3298-4ef2-b2dc-29c4f9587302" />

<img width="888" height="804" alt="Ekran Resmi 2025-08-22 12 45 45" src="https://github.com/user-attachments/assets/202d618e-0a76-4948-bc62-2c0094175819" />


## Kurulum ve Çalıştırma
1. Depoyu klonlayın:  
```bash
git clone https://github.com/zeynepplbyk/deniz-arsiv-sondaj.git
