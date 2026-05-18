# LibraryHub - Dijital Kütüphane Yönetim Sistemi

Kitap envanterlerinin dijital olarak takip edilebildiği, üye kayıtlarının tutulabildiği ve emanet/ödünç kitap süreçlerinin dinamik olarak yönetilebildiği modern ve minimalist bir masaüstü kütüphane otomasyonudur. PyQt5 altyapısı üzerinde kurumsal tasarım yönergeleri ve Nesne Yönelimli Programlama (OOP) prensipleri kullanılarak, güvenli katmanlı mimari (Frontend/Backend) modeliyle geliştirilmiştir.

---

### 🚀 Teknolojiler

* **Python 3** - Temel programlama dili
* [cite_start]**PyQt5 (>=5.15.0)** - Masaüstü GUI (Grafik Kullanıcı Arayüzü) framework'ü [cite: 1]
* **JSON** - Veri kalıcılığı ve yerel ilişkisel veritabanı yönetimi
* **Fusion Style** - Modern ve platformlar arası tutarlı arayüz stili

---

### 📂 Proje Yapısı

```text
library_hub/
├── main.py                          # Uygulamanın ana giriş noktası ve başlatıcı
[cite_start]├── requirements.txt                 # Üçüncü parti kütüphane bağımlılıkları [cite: 1]
├── data/                            # JSON formatında yerel veritabanı dosyaları (Otomatik oluşturulur)
│   └── kullanicilar.json            # Sistem yetkilileri ve kimlik doğrulama verileri
├── backend/
│   ├── __init__.py
│   ├── veri_yoneticisi.py           # Kütüphane iş mantığı, CRUD işlemleri ve ilişkisel arama motoru
│   ├── auth.py                      # Kullanıcı oturum yönetimi ve yetkilendirme modülü
│   └── seed.py                      # Veritabanı boşsa devreye giren örnek veri (kitap/üye) yükleyici
└── frontend/
    ├── __init__.py
    ├── ana_pencere.py               # Ana kontrol paneli, kitap/üye tabloları ve navigasyon
    ├── login.py                     # Yetkili personel giriş ekranı (QDialog)
    └── tema.py                      # Kurumsal renk paleti ve UI stil şablonları (ANA_STIL)

🧠 Ana Yapı ve İş Mantığı Katmanları
🔐 Kimlik Doğrulama Yönetimi (backend/auth.py -> AuthYoneticisi)

    Özellikler: kullanicilar.json dosya yolu.

    Metodlar: kullanici_var_mi(), varsayilan_kullanici_olustur(), kullanici_dogrula(ad, sifre).

⚙️ Kütüphane Veri Merkezi (backend/veri_yoneticisi.py -> VeriYoneticisi)

    Özellikler: veri_klasoru referansı, kitap, üye ve ödünç takip veri kümeleri.

    Metodlar: tum_kitaplar(), tum_uyeler(), tum_oduncler().

🎨 Grafik Arayüz Yönetimi (frontend/)

    LoginPenceresi (login.py): Uygulama güvenliğini sağlayan, ana pencere öncesi çalışan ve personeli doğrulayan modal giriş ekranı.

    AnaPencere (ana_pencere.py): High DPI ölçeklendirme destekli, kitap teslim durumlarını ve üye hareketlerini listeleyen ana dashboard ekranı.

✨ Temel Özellikler

    Merkezi Kütüphane Paneli (Dashboard): Kitapların müsaitlik durumunu, aktif ödünç verilen eserleri ve üye özetlerini tek bir ekranda yöneten bütünleşik arayüz.

    Katmanlı Güvenlik Kapısı (Auth Gate): Sistem geçerli bir personel oturumu (aktif_kullanici) doğrulamadan ana ekranın açılmasını kesin olarak engelleyen güvenli mimari yapısı.

    Akıllı Veri Besleyici (Auto-Seed): Sistem ilk kez çalıştırıldığında veya yerel veri klasörü boş olduğunda otomatik olarak kütüphane envanterine örnek kitapları, üyeleri ve ödünç kayıtlarını senkronize eden akıllı test mekanizması.

    Yüksek Çözünürlük (DPI) Desteği: Modern ve yüksek yoğunluklu ekranlarda grafiklerin, ikonların ve yazı tiplerinin bulanıklaşmasını önleyen AA_EnableHighDpiScaling ve AA_UseHighDpiPixmaps entegrasyonu.

    Kurumsal Tasarım Dili: Segoe UI tipografik hiyerarşisine sahip, temiz, göz yormayan ve modern "Fusion" arayüz giydirmesi (ANA_STIL).

🛠️ Kurulum ve Çalıştırma

Gerekli bağımlılıkları yüklemek ve kütüphane otomasyonunu başlatmak için terminalinizde sırasıyla şu komutları çalıştırın:
Bash

pip install -r requirements.txt
python main.py

🔒 Varsayılan Giriş Bilgileri

Sistem ilk kez çalıştırıldığında yetkili personel hesabı otomatik olarak arka planda oluşturulur:

    Kullanıcı Adı: admin

    Şifre: admin123

🌱 Otomatik Yüklenen Örnek Veriler (Seed)

Eğer yerel data/ klasörünüz boşsa, sistem ilk açılışta kütüphane süreçlerinin simüle edilebilmesi için veri tabanını otomatik olarak popüle eder ve şu istatistikleri konsola raporlar:

    Örnek Kitap Envanteri

    Örnek Kayıtlı Üyeler

    Aktif ve Geçmiş Ödünç / Emanet Kayıtları
