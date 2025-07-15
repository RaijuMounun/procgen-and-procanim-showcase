# Teknik Tasarım Dokümanı – Procedural Dungeon & Animation Showcase

Bu doküman, projenin teknik ve görsel tasarım kararlarını, ana algoritmaları, sistem şemalarını ve mimari prensipleri detaylandırır.

---

## 1. Genel Mimari

Proje, modüler ve genişletilebilir olacak şekilde, aşağıdaki ana sistemlerden oluşur:

- **Dungeon Generation** (Procedural)
- **SpiderCharacter Animation System**
- **HumanCharacter Animation System**
- **Showcase UI & Debug Panel**

Her sistem bağımsız olarak test edilebilir ve debug paneli ile gözlemlenebilir.

---

## 2. Dungeon Generation Tasarımı

### 2.1. Yüksek Seviyede Akış

1. Grid oluşturulur (ör. 2D dizi veya tile array)
2. Oda yerleşimi algoritması (BSP veya Room Graph) ile odalar grid’e yerleştirilir
3. Odalar arasında bağlantı (corridor) algoritması çalışır
4. NavMesh otomatik olarak güncellenir
5. Debug overlay ve görselleştirme yapılır

### 2.2. Veri Yapıları

- **GridCell**: Tür (boş, oda, koridor), koordinat, bağlantılar
- **Room**: Başlangıç/bitis koordinatları, boyut, bağlı odalar
- **Corridor**: Başlangıç/bitis noktası, yol üzerindeki hücreler

### 2.3. Algoritma Notları

- **BSP (Binary Space Partitioning):**
  - Grid, rastgele şekilde alt parçalara bölünür
  - Her parça bir oda olarak atanır
  - Komşu odalar arasında koridorlar açılır
- **Room Graph:**
  - Rastgele oda noktaları seçilir
  - Minimum Spanning Tree veya benzeri algoritma ile bağlantı kurulur

### 2.4. Genişletilebilirlik

- Oda tipleri (boss, loot, spawn) eklenebilir
- Farklı corridor algoritmaları denenebilir
- Grid boyutu ve parametreleri UI’dan değiştirilebilir

---

## 3. SpiderCharacter Animation System

### 3.1. Rig ve Control Rig

- Her bacak için ayrı IK zinciri (FABRIK veya Two Bone IK)
- Gövde için ana kontrol noktası

### 3.2. Bacak Hedefleme

- Her frame’de, bacak world forward + offset ile ileri pozisyon belirler
- O noktaya raycast yapılır, yüzeye göre hedef pozisyon atanır
- Bacaklar sıralı ve offset’li şekilde hareket eder (örümcek yürüyüşü)

### 3.3. Gövde Adaptasyonu

- Tüm bacak raycast’lerinin ortalaması ile gövde yüksekliği ve eğimi ayarlanır
- Duvarda/yüzeyde yürüme için normal vektörüne göre gövde rotasyonu

### 3.4. Debug

- Raycast çizgileri, bacak hedef noktaları ve IK zincirleri debug panelde gösterilir

---

## 4. HumanCharacter Animation System

### 4.1. Animation Blueprint

- Temel yürüme/koşma animasyonları
- State machine ile hareket geçişleri

### 4.2. Çevresel Etkileşimler

- Eller ve ayaklar için raycast ile çevre kontrolü
- Duvara yakınsa el hedefi, engel varsa ayak hedefi belirlenir

### 4.3. IK ve Motion Warping

- Two Bone IK ile el/ayak hedef pozisyonlaması
- Motion Warping ile animasyonların hedeflere adapte edilmesi

### 4.4. Postür ve Blending

- Eğime göre postür düzeltme
- Çevresel blending (ör. idle animasyonunun ışığa göre değişmesi)

### 4.5. Debug

- Raycast’ler, IK hedefleri ve blending durumları debug panelde gösterilir

---

## 5. Showcase UI & Debug Panel Tasarımı

### 5.1. UI Panel

- Dungeon oluşturma/resetleme butonu
- Karakter animasyon layer’larını aç/kapatma
- Debug modlarını toggle etme (ör. raycast debug, bacak hedefleri)

### 5.2. Debug Görselleştirme

- Raycast çizgileri, IK hedef noktaları, animasyon blending durumları
- Anlık teknik veri gösterimi (ör. FPS, aktif sistemler)

### 5.3. Kamera ve Sunum

- Farklı sistemleri gösterecek kamera açıları ve geçişler
- İzleyiciye net gösterim için sahne düzeni

---

## 6. Genişletilebilirlik ve Modülerlik

- Her sistem bağımsız modül olarak tasarlanır
- Yeni karakter veya dungeon algoritması kolayca eklenebilir
- UI ve debug paneli yeni sistemlere kolayca entegre edilebilir

---

## 7. Önemli Teknik Kararlar & Alternatifler

- **Blueprint vs C++:** Prototip ve hızlı iterasyon için Blueprint, performans kritik kısımlar için C++
- **IK Solver Seçimi:** FABRIK hızlı ve stabil, Two Bone IK daha basit durumlar için
- **NavMesh:** Unreal’ın yerleşik NavMesh sistemi kullanılacak
- **Debug:** Tüm sistemler için anlık debug ve görselleştirme zorunlu

---

## 8. (Opsiyonel) Sistem Şeması (Metinle)

```
[Dungeon Generator] ---> [Grid/Room Data] ---> [NavMesh]
                                   |
                                   v
[SpiderCharacter] <--- [Surface Data (Raycast)]
[HumanCharacter]  <--- [Surface Data (Raycast)]
                                   |
                                   v
                            [Debug Panel]
                                   |
                                   v
                                [UI Panel]
```

---

## 9. Notlar

- Tüm sistemler, teknik gösterim ve eğitim amaçlıdır
- Geliştirici odaklı dökümantasyon ve sunum scriptleri için ilgili .md dosyalarını inceleyin
