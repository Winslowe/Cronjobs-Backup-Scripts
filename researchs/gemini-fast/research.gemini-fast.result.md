# Cronjobs-Backup-Scripts Teknik Araştırma Raporu

## 1. Temel Çalışma Prensipleri
Cron, Linux tabanlı sistemlerde iş zamanlaması (scheduling) için kullanılan standart bir servistir. Yedekleme scriptleri ile birleştiğinde şu prensiplerle çalışır:

* **Daemon Süreci:** `crond` servisi her dakika sistem yapılandırmalarını kontrol eder.
* **Otomasyon Akışı:** Scriptler; veriyi paketleme (tar), sıkıştırma (gzip), uzak sunucuya taşıma (rsync/scp) ve eski dosyaları temizleme (rotation) adımlarını sırayla icra eder.



## 2. Benzer Açık Kaynak Projeler ve Rakipler
| Proje | Temel Odak Noktası | Avantajı |
| :--- | :--- | :--- |
| **BorgBackup** | Verimlilik | Mükemmel tekilleştirme (deduplication) yeteneği. |
| **Restic** | Esneklik | Birçok bulut sağlayıcısını yerel olarak destekler. |
| **Duplicati** | Kullanıcı Dostu | Web arayüzü ve blok tabanlı artımlı yedekleme. |
| **Bacula** | Kurumsal | Büyük ölçekli ağ yapıları için gelişmiş yönetim. |

## 3. Kritik Yapılandırma Dosyaları ve Parametreleri
* **/etc/crontab**: Sistem genelindeki görevlerin listesi.
* **/var/spool/cron/crontabs/**: Kullanıcı bazlı görevlerin saklandığı dizin.
* **Parametre Yapısı**: `* * * * *` (Dakika, Saat, Gün, Ay, Haftanın Günü).
* **Rotation Parametresi**: `find /backups -type f -mtime +7 -delete` (7 günden eski yedekleri siler).

## 4. Güvenlik ve Dikkat Edilmesi Gerekenler
* **En Az Yetki (PoLP)**: Yedekleme scripti asla `root` olarak çalıştırılmamalı, sadece yedeği alınacak klasörlere erişimi olan özel bir kullanıcı atanmalıdır.
* **Veri Şifreleme**: Yedekler saklandığı alanda (at-rest) mutlaka AES-256 veya GPG ile şifrelenmelidir.
* **Görünmezlik**: `.my.cnf` gibi dosyalar kullanarak veritabanı şifrelerinin script içinde açık metin (cleartext) kalması önlenmelidir.# Research Result for gemini-fast
