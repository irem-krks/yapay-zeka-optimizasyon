# yapay-zeka-optimizasyon
# Altın Oran Arama Algoritması — Savunma Sanayii Uygulamalı Optimizasyon

## Proje Hakkında
Bu proje, türev kullanmadan tek değişkenli fonksiyonları optimize eden **Altın Oran Arama Algoritması**'nın savunma sanayii problemlerine uygulanmasını içermektedir.

## Uygulama Problemi
**ANKA-S İHA Görev Etkinlik Skoru Maksimizasyonu**

Türk Savunma Sanayii Başkanlığı (SSB) bünyesinde yürütülen bir mühendislik senaryosunda, ANKA-S tipi taktik keşif İHA'sının kanat açıklığı parametresi optimize edilmiştir.

- **Karar değişkeni:** Kanat açıklığı x (metre)
- **Arama aralığı:** [3, 7] metre
- **Hassasiyet:** ε = 0.15 m
- **Sonuç:** x* = 3.0689 m, f(x*) = 2.3538

## Kullanılan Yöntem
Altın Oran Arama Algoritması her iterasyonda belirsizlik aralığını sabit r ≈ 0.618 oranıyla küçülterek optimuma yaklaşır. Toplam 7 iterasyonda başlangıç aralığının %96.6'sı elenmiştir.

## Kullanılan Teknolojiler
- Python
- NumPy
- Pandas
- Matplotlib

## Ders
Optimizasyon Teknikleri
