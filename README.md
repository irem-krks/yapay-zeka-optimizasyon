# Altın Oran Arama Algoritması — İHA Kanat Açıklığı Optimizasyonu

Optimizasyon Teknikleri dersi kapsamında, türev kullanmadan tek değişkenli fonksiyonları optimize eden **Altın Oran Arama (Golden Section Search)** algoritması Python'da sıfırdan yazıldı ve ANKA-S tipi bir taktik keşif İHA'sından esinlenen **varsayımsal** bir mühendislik senaryosuna uygulandı.

📓 Kod ve iterasyon tablosu: [altin_oran_arama.ipynb](altin_oran_arama.ipynb)

## Senaryo (varsayımsal)

Senaryo ders için kurgulanmıştır; gerçek bir kurum projesi, ölçümü ya da verisi değildir. Amaç, İHA kanat açıklığının (x, metre) bir "görev etkinlik skoru" üzerindeki etkisini modelleyip skoru en yüksek yapan değeri algoritmayla aramaktır.

- **Karar değişkeni:** kanat açıklığı x (m)
- **Arama aralığı:** [3, 7] m (alt sınır radar kısıtı, üst sınır hangar kısıtı olarak kurgulanmıştır)
- **Hassasiyet:** ε = 0.15 m
- **Skor fonksiyonu (kurgusal):** f(x) = x·sin(x) + 2·cos(x/2) − 0.1·x² + 3 — menzil-dayanıklılık, yakıt verimliliği ve ağırlık cezası bileşenlerini temsil edecek şekilde seçilmiş analitik bir fonksiyon

## Yöntem

Her iterasyonda belirsizlik aralığı sabit r = (√5 − 1) / 2 ≈ 0.618 oranıyla küçülür: iki iç nokta hesaplanır ve maksimizasyonda fonksiyon değeri düşük olan taraf elenir. L_k = r^k · (b − a) < ε olduğunda durulur. Bu problem için gerekli iterasyon sayısı k = 7'dir.

## Sonuçlar

| Alan | Değer |
|------|-------|
| Son belirsizlik aralığı | [3.0000, 3.1378] |
| Aralık uzunluğu (L) | 0.1378 m |
| Algoritmanın verdiği nokta (x*, son aralığın orta noktası) | 3.0689 m |
| Skor f(x*) | 2.3538 |
| İterasyon sayısı | 7 |

7 iterasyonda başlangıç aralığının yaklaşık %96.6'sı elenmiştir.

## Sınırlılıklar

- Skor fonksiyonu gerçek bir uçuş modeli değildir; algoritmayı göstermek için kurgulanmış analitik bir fonksiyondur. Aralıktaki sayısal değerler gerçek bir tasarım önerisi olarak kullanılamaz.
- Altın Oran Arama, aralıkta **tek tepeli (unimodal)** bir fonksiyon varsayar. Bu fonksiyon [3, 7] aralığında tek tepeli değildir: yaklaşık x = 5.2'de bir minimumu vardır ve 7'ye doğru yeniden artar.
- Aralıkta en yüksek değer alt sınırdadır (x = 3, f ≈ 2.665). Bu yüzden algoritma alt sınıra yakın bir noktaya yakınsamıştır; döndürülen x* son aralığın orta noktası olduğundan (f ≈ 2.354) sınırdaki maksimumdan biraz düşüktür. Sonuç bir sınır çözümüdür, iç bir optimum değildir.
- Tek değişkenli ve tek amaçlı bir problemdir; çok değişkenli ya da çok amaçlı problemler için ayrı yöntemler gerekir.

## Kullanılan Teknolojiler

Python · NumPy · Pandas · Matplotlib · Jupyter Notebook

## Çalıştırma

```bash
pip install -r requirements.txt
jupyter notebook altin_oran_arama.ipynb
```
