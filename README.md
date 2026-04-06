Linux Yetki Yükseltme Denetim Aracı

Bu betik, Linux sistemlerde kapsamlı yerel güvenlik değerlendirmesi ve yetki yükseltme analizleri yapmak için tasarlanmıştır. Script; sistem bilgileri, dosya izinleri, ağ güvenliği, servis yapılandırmaları, CVE kontrolü ve ML tabanlı anomali analizini aynı anda yürütür.

Önemli Not
Rapor dosyaları script dosyasının bulunduğu dizinde oluşturulur.
İki ayrı dosya üretilir:
sonuclar.txt veya sonuclar_N.txt — ana terminal çıktısı ve tarama sonuçları
yetkiyukseltme_report_TIMESTAMP.txt — detaylı rapor
Raporlar aynı dizinde, farklı isimlerle kaydedilir.
Temel Özellikler
Tam Türkçe arayüz ve açıklamalar
Risk puanlaması (0–100)
ML ve CVE tabanlı analizler
Detaylı sistem ve kullanıcı denetimleri
Dosya sistemi, ağ, servis ve zamanlayıcı incelemeleri
SUID/SGID, yazılabilir dosya ve PATH güvenliği kontrolleri
SSH, sudo, PAM, sysctl, firewall, auditd analizleri
Otomatik düzeltme önerileri ve güvenlik tavsiyeleri
HTML, JSON, Markdown ve SQLite destekli raporlama
En Yeni Eklenen Özellikler
Makine öğrenmesi tabanlı risk tahmini
CVE açıklık taraması
Anomali tespiti (LD_PRELOAD, zombi işlemler, yazılabilir sistem binary’leri)
Akıllı onarım ve sistem güvenlik değerlendirmesi
Tarama sonrası raporun otomatik olarak ekrana yazdırılması
Raporların script dizininde saklanması
Kullanım
./linux-yetki-yukseltme.sh
Seçenekler
-h, --help : Yardım mesajını gösterir
-v : Ayrıntılı çıktı modu
-q : Sessiz mod (yalnızca özet)
-j : JSON çıktısı
-m : Markdown çıktısı
-f : Hızlı tarama
-t : Kapsamlı tarama
-k <anahtar> : Anahtar kelime araması
-e <dizin> : Dışa aktarım dizini
-p : Sudo parolası ister
-r <dosya> : Özel rapor adı
--no-colors : Renkli çıktıyı kapatır
--fix-script : Otomatik düzeltme script’i oluşturur
--html-report : HTML raporu oluşturur
--database : SQLite veritabanı kaydı
--version : Versiyon bilgisi
Örnek Kullanımlar
# Normal tarama
./linux-yetki-yukseltme.sh

# Hızlı tarama ve özet
./linux-yetki-yukseltme.sh -f -q

# JSON çıktısı ile detaylı tarama
./linux-yetki-yukseltme.sh -t -j

# HTML rapor oluşturma
./linux-yetki-yukseltme.sh --html-report

# SQLite kayıt
./linux-yetki-yukseltme.sh --database

# Özel rapor dosyası
./linux-yetki-yukseltme.sh -r ./ozel_rapor.txt
Raporlar

Script çalıştırıldığında en son rapor dosyası otomatik olarak ekrana yazdırılır. Bu sayede kullanıcı hem terminal çıktısını hem de rapor içeriğini aynı anda görüntüleyebilir.

Oluşturulan Dosyalar
sonuclar.txt veya sonuclar_N.txt
yetkiyukseltme_report_TIMESTAMP.txt
security_scans.db (SQLite destekliyse)
Tarama Kapsamı
Sistem Bilgileri
Çekirdek versiyonu
Dağıtım bilgileri
Bellek ve disk kullanımı
İşlemci ve ağ bilgileri
Kullanıcı / Grup Denetimi
Kullanıcı hesapları
Sudo yapılandırması
Parola politikaları
Shadow dosya izinleri
Dosya Sistemi Güvenliği
SUID/SGID dosyaları
Dünya tarafından yazılabilir dosyalar
Yazılabilir sistem binary’leri
Kütüphane enjeksiyonu riskleri
Ağ ve Servis Analizi
SSH, iptables, UFW
Açık portlar
Cron / systemd timer
Servis ve daemon güvenliği
Ek Güvenlik Analizleri
CVE tabanlı sürüm kontrolü
ML tabanlı anomali analizi
Tedarik zinciri riski
Sıfır gün (zero-day) heuristikleri
Auditd hazır durumu
Şifreleme ve TLS kontrolleri
Risk Değerlendirme
Seviyeler
KRİTİK: Acil müdahale gerekli
ÇOK YÜKSEK: Hızlı düzeltme gerekli
YÜKSEK: Kısa sürede iyileştirilmeli
ORTA: Düzenli bakım gerekli
DÜŞÜK: İzlenebilir
Yasal Uyarı

Bu araç yalnızca kendi sisteminizde veya yazılı izin verilen test ortamlarında kullanılmalıdır. Yetkisiz erişim ve testler yasal sorumluluk doğurur.
