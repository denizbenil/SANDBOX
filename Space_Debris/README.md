## GEO Uydu Enkazı Takip Sistemi

Bu proje, Dünya'nın jeosenkron yörüngesindeki (GEO) uydu enkazlarını tespit etmek ve görselleştirmek için geliştirilmiş bir Python uygulamasıdır.
Proje Açıklaması: 
Bu kod, Space-Track.org veritabanından TLE (Two-Line Element) verilerini çekerek GEO yörüngesindeki potansiyel uydu enkazlarını filtreler ve bunların yörüngelerini görselleştirir.

### Nasıl Çalışır?
1. Veri Toplama
Space-Track.org API'sine güvenli oturum açılır
Son 30 gün içinde güncellenmiş TLE verileri çekilir
GEO yörüngesi için spesifik kriterler uygulanır:

Mean Motion (Ortalama Hareket): 0.99 - 1.01 rev/gün
Inclination (Eğiklik): < 10°
Aktif uyduları ve enkazları içerir


2. Enkaz Filtreleme
Kod, üç aşamalı bir filtreleme sistemi kullanır:
Birinci Filtre: Parça Tanımlama

int_designator_piece değerlerine göre filtreleme
"B", "C", "D" parçaları → Roket gövdeleri ve ayrılan parçalar
Ana uyduları ("A" parçası) hariç tutar

İkinci Filtre: Yörünge Karakteristikleri

Inclination > 2° (Gerçek GEO uydularından sapma)
Eccentricity > 0.001 (Yörünge bozukluğu)

Üçüncü Filtre: Yüksek Riskli Enkazlar

Eccentricity > 0.1 (Ciddi yörünge anomalisi)
B-Star drag değeri analizi


3. Görselleştirme
3D Yörünge Görselleştirmesi:

Dünya'nın gerçek texture'ı ile 3D küre modeli
Her enkaz için 24 saatlik yörünge izleri
Renkli kodlama ile obje ayırımı
Başlangıç noktaları işaretli

2D Yer İzi (Ground Track) Haritası:

Dünya haritası üzerinde uydu izleri
Enlem-boylam koordinatlarında gerçek zamanlı pozisyonlar
24 saatlik geçiş rotaları

### 📊 Sonuçlar ve Bulgular
Tespit Edilen Enkaz Kategorileri:

Roket Gövdeleri (B parçaları)

Fırlatma sonrası ayrılan roket üst kademeler
Yüksek eksantrisite değerleri
Kontrol dışı yörünge hareketleri


Ayrılan Parçalar (C, D parçaları)

Uydu ayrılma mekanizmaları
Koruyucu kapaklar ve adaptörler
Uydu parçalanma enkazları



### Önemli Parametreler:

Mean Motion: GEO yörüngesi için teorik değer 1.0027 rev/gün
Dünya'nın Sidereal Günü: 86164 saniye
GEO Yörünge Yüksekliği: ~35,786 km (deniz seviyesinden)


### Grafiklerden Çıkarılabilecek Bilgiler:
✅ 3D Yörünge Grafiği:

Enkaz objelerinin uzaysal dağılımı
Yörünge düzlemleri ve eğimleri
Dünya ile olan mesafe ilişkisi

✅ Ground Track Haritası:

Hangi coğrafi bölgeler üzerinden geçtikleri
Yörünge periyotları
Kapsama alanları


### 🛠️ Teknik Gereksinimler
python# Gerekli kütüphaneler
requests          # HTTP istekleri için
skyfield          # Uydu yörünge hesaplamaları
matplotlib        # Görselleştirme
numpy             # Sayısal hesaplamalar
scipy             # Görüntü işleme (texture için)


### 🔑 Kullanım
Space-Track.org'da ücretsiz hesap oluşturun
Kullanıcı adı ve şifrenizi kodda güncelleyin
Kodu çalıştırın

pythonpython tle_geo_debris_tracker.py


### ⚠️ Önemli Notlar
Güvenlik: Kodda kimlik bilgileri bulunmaktadır. Gerçek kullanımda bunlar çevre değişkenlerine taşınmalıdır.
Veri Güncelliği: TLE verileri son 30 güne ait filtrelenmektedir
API Limitleri: Space-Track.org API kullanım limitlerine tabidir


### 🎓 Eğitsel Değer
Bu kod aşağıdaki konuları öğrenmek isteyenler için mükemmel bir örnektir:

Uzay enkazı takibi
TLE formatı ve uydu yörünge mekaniği
API entegrasyonu ve oturum yönetimi
3D bilimsel görselleştirme
Veri filtreleme ve analiz teknikleri


### 📈 Potansiyel Geliştirmeler ?? Gelecek Günlerde Bunları Deneyebilirim

Veritabanı entegrasyonu
Otomatik raporlama sistemi
Gerçek zamanlı uyarı mekanizması
Çarpışma riski analizi
Zaman serisi animasyonları 
