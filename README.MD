# 🛡️ Cron-Backup Master: Otomatik Yedekleme ve Zamanlama Sistemi

[![Cron](https://img.shields.io/badge/Service-Cron-orange?style=for-the-badge&logo=linux)](https://en.wikipedia.org/wiki/Cron)
[![Backup](https://img.shields.io/badge/Task-Backup_Automation-blue?style=for-the-badge)](https://github.com/)
[![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)](https://opensource.org/licenses/MIT)

Bu proje, Linux sistemlerin vazgeçilmez zamanlayıcısı olan **Cron** mekanizmasını kullanarak, kritik verilerin insan müdahalesi olmadan nasıl yedekleneceğini, yönetileceğini ve korunacağını ele alan teknik bir rehberdir.

---

## ⚙️ Cron Nedir ve Nasıl Çalışır?

**Cron**, Unix benzeri işletim sistemlerinde komutları veya scriptleri önceden belirlenmiş zamanlarda çalıştırmak için kullanılan zaman tabanlı bir iş zamanlayıcıdır.

### Çalışma Mekanizması:
1. **Daemon Süreci:** Arka planda sürekli çalışan `crond` servisi, her dakikanın başında uyanır.
2. **Tablo Kontrolü:** `/etc/crontab` ve kullanıcıya özel `crontab` dosyalarını tarar.
3. **Zaman Eşleşmesi:** Belirlenen tarih/saat verisi o an ile eşleşiyorsa, atanmış görevi (yedekleme scripti vb.) sistem yetkileriyle başlatır.

---

## 📝 Crontab Sözdizimi (Syntax)

Cron görevleri 5 temel sütundan ve çalıştırılacak komuttan oluşur:

```text
 .---------------- dakika (0 - 59)
 |  .------------- saat (0 - 23)
 |  |  .---------- ayın günü (1 - 31)
 |  |  |  .------- ay (1 - 12)
 |  |  |  |  .---- haftanın günü (0 - 6) (Pazar=0 veya 7)
 |  |  |  |  |
 * * * * * /yol/komut_veya_script.sh
