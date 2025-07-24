#  COVID-19 Makale Metinlerinden Anlamlı Bilgi Çıkarımı

<img width="1101" height="617" alt="image" src="https://github.com/user-attachments/assets/3ff58e79-1a74-4391-a61a-504bc5787b8f" />

Bu proje, COVID-19 hakkında yayımlanmış binlerce bilimsel makaleyi inceleyerek konu modelleme ve metin analizi yöntemleriyle anlamlı bilgiler üretmeyi amaçlamaktadır. Çalışma kapsamında veri temizleme, görselleştirme ve doğal dil işleme (NLP) teknikleri kullanılmıştır.

##  Projenin Amacı

- COVID-19 literatüründe hangi konuların öne çıktığını analiz etmek
- Makalelerin yayımlandığı yılları ve kaynakları görselleştirmek
- Özetlerde geçen kelimelerle tematik analizler yapmak
- Makaleleri konularına göre gruplamak (Topic Modeling)

##  Kullanılan Veri Seti

- **CORD-19**: COVID-19 Open Research Dataset
- `metadata.csv` adlı dosya analiz edilmiştir.
- Ana sütunlar:
  - `title`: Makale başlığı
  - `abstract`: Makale özeti
  - `publish_time`: Yayın tarihi
  - `source_x`: Kaynağı

##  Kullanılan Teknikler ve Adımlar

### 1.  Veri Ön İncelemesi

- Toplam benzersiz makale sayısı
- Yayın yılı dağılımı
- En çok kullanılan kaynaklar (`source_x`)
- Eksik veri analizi (`abstract`, `publish_time`)

### 2.  Veri Temizleme

- Boş `abstract` ve `publish_time` verileri çıkarıldı
- `abstract` sütunundaki metinler küçük harfe çevrildi
- NaN değerler uygun şekilde yönetildi

### 3.  Görselleştirme

- Yıllara göre makale sayısı (özellikle 2019 sonrası)
- En çok kullanılan 10 kaynak
- Özet kelime uzunluğu dağılımı
- `abstract_length` üzerinden histogram

### 4.  Anahtar Kelime Tespiti

- Aşağıdaki anahtar kelimelerle `abstract` içeriği etiketlendi:
  ```python
  ['covid', 'pandemic', 'virus', 'coronavirus', 'sars-cov-2', 'outbreak', 'infection']
