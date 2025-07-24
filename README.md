#  COVID-19 Makale Metinlerinden Anlamlı Bilgi Çıkarımı

<img width="1101" height="617" alt="image" src="https://github.com/user-attachments/assets/3ff58e79-1a74-4391-a61a-504bc5787b8f" />

Bu proje, COVID-19 hakkında yayımlanmış binlerce bilimsel makaleyi inceleyerek konu modelleme ve metin analizi yöntemleriyle anlamlı bilgiler üretmeyi amaçlamaktadır. Çalışma kapsamında veri temizleme, görselleştirme ve doğal dil işleme (NLP) teknikleri kullanılmıştır.

##  Projenin Amacı

- COVID-19 literatüründe hangi konuların öne çıktığını analiz etmek
- Makalelerin yayımlandığı yılları ve kaynakları görselleştirmek
- Özetlerde geçen kelimelerle tematik analizler yapmak
- Makaleleri konularına göre gruplamak (Topic Modeling)

##  Kullanılan Veri Seti

- **CORD-19**: COVID-19 Open Research Dataset : https://www.kaggle.com/datasets/allen-institute-for-ai/CORD-19-research-challenge
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
  covid_related adlı yeni sütun ile sınıflama yapıldı

3# 5.  Konu Modelleme (Topic Modeling)

LDA (Latent Dirichlet Allocation) kullanılarak özetlerden konular çıkarılmıştır:

Metinler:

- Tokenize edildi
- Stop-word’ler çıkarıldı
- Lemmatization uygulandı
- Gensim ile LDA modeli kuruldu
- pyLDAvis ile etkileşimli konu haritası üretildi.

<img width="1917" height="917" alt="image" src="https://github.com/user-attachments/assets/d4b44cae-c454-4658-90a3-e6beab14d261" />

  
## Görsel Örnekler

## Yıllara Göre Makale Sayısı

Yayım yılının dağılımı:

<img width="987" height="590" alt="image" src="https://github.com/user-attachments/assets/ac349fe1-9de0-4339-ac62-8041de9f07c1" />


## En Çok Görülen Kaynaklar

En popüler 10 kaynak:

<img width="747" height="453" alt="image" src="https://github.com/user-attachments/assets/40951365-3a11-4f37-898a-8f26344bfd43" />


## Özet Uzunluğu Dağılımı

Abstract kelime sayısı histogramı:

<img width="545" height="465" alt="image" src="https://github.com/user-attachments/assets/8d4e2154-567f-41bb-ae7e-36d29bc39d69" />

