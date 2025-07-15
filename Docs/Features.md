# Özellikler – Procedural Dungeon & Animation Showcase

## 🎯 Proje Hedefi

Bu proje, Unreal Engine 5.5 üzerinde procedural dungeon generation ve procedural animation teknolojilerinin teknik bir gösterimini sunar. Oyun demosu değil, geliştirici ve teknik izleyiciye sistemlerin esnekliğini ve kapasitesini sergilemek için tasarlanmıştır.

---

## 🧩 Modül Listesi ve Teknik Özellikler

### 1. Procedural Dungeon Generator

- **Teknik Yöntem:** BSP (Binary Space Partitioning) veya Room Graph bağlantılı tile-based sistem
- **Öne Çıkanlar:**
  - Her seferinde farklı, rastgele dungeon üretimi
  - NavMesh ile tam uyumlu
  - Oda bağlantı görselleştirmesi ve debug overlay’leri
  - Modüler, yeniden kullanılabilir yapı

### 2. SpiderCharacter (Çok Bacaklı Varlık)

- **Animasyon Sistemi:** Control Rig + Full-body IK
- **Öne Çıkanlar:**
  - Her bacak için raycast ile hedef pozisyon belirleme
  - Duvarda, eğimli yüzeyde veya köşede yürüyebilme
  - Bacaklar senkronize ama offset'li hareket eder (örümcek gibi)
  - Gövde konumu yüzeye göre pozisyonlanır ve eğilir

### 3. HumanCharacter (İnsan Karakter)

- **Animasyon Sistemi:** Animation Blueprint + Motion Warping + IK
- **Öne Çıkanlar:**
  - Duvarlara yakınken ellerin otomatik olarak duvara yaslanması
  - Ayağın önünde bir yükselti varsa ayağını oraya koyma
  - Eğime göre postür düzeltme
  - Çevresel faktörlere duyarlı animasyon blending

### 4. Showcase UI

- **Özellikler:**
  - Dungeon oluşturma butonu
  - Karakter animasyon layer’larını aktif/pasif etme
  - Hedef gösterim modlarını toggle etme (örneğin raycast debug, bacak hedefleri)

### 5. Debug Display

- **Özellikler:**
  - Tüm raycast'lerin görselleştirilmesi
  - IK hedef pozisyonlarının gösterimi
  - Procedural sistemlerin anlık çıktısı (örneğin ray collision noktaları)

---

## 🕹️ Teknik Sistemler

### Procedural Dungeon Generation

- **Yöntem:** BSP/RoomGraph ile grid tabanlı random layout
- **Bağlantı:** Tile'lar üzerinde odaların bağlantılarını pathfinding veya corridor algoritması ile bağlama
- **NavMesh:** Otomatik NavMesh generation
- **Modülerlik:** Dungeon Generator sınıfı reusable olacak

### Procedural Animation – Spider

- **Bacak Hedefleme:** Her frame’de bacak için ileri pozisyon belirlenir, raycast yapılır, hedef pozisyon atanır
- **IK:** FABRIK solver ile bacak hedefe yönlendirilir
- **Gövde Adaptasyonu:** Gövde raycast’lere göre yüksekliğe ayarlanır
- **Hareket Sırası:** Bacaklar sıralı ve kontrollü offset’lerle hareket eder

### Procedural Animation – Human

- **Çevre Algısı:** Line Trace ile ellerin ve ayakların yakın çevresi kontrol edilir
- **El/Ayak Hedefleme:** Duvara yakınsa el hedefi, engel varsa ayak hedefi belirlenir
- **Motion Warping:** Hareket animasyonları hedeflere adapte edilir
- **Postür:** Eğime göre postür düzeltme ve çevresel blending
- **Opsiyonel:** EQS ile çevresel awareness sistemleri entegre edilebilir

---

## 🧪 Geliştirme Aşamaları (Task Breakdown)

### Faz 1 – Temel Dungeon Sistemi

- [ ] Grid ve room sistemi kur
- [ ] Room yerleşimi ve bağlantılar
- [ ] NavMesh otomatik üretimi
- [ ] UI üzerinden dungeon oluşturma butonu

### Faz 2 – Örümcek Karakter

- [ ] Rig + Control Rig ayarı
- [ ] Bacak hedef pozisyonlama (raycast)
- [ ] Bacak IK kontrolü
- [ ] Gövde yüksekliği adaptasyonu

### Faz 3 – İnsan Karakter

- [ ] Temel yürüme animasyonu
- [ ] El ve ayak raycast sistemleri
- [ ] IK hedef pozisyonlaması
- [ ] Postür düzeltme
- [ ] Motion Warping entegrasyonu

### Faz 4 – UI ve Debug

- [ ] Hedef debug sistemleri
- [ ] Raycast ve IK hedeflerinin çizimi
- [ ] UI panelden tüm sistemlerin kontrolü

---

## 🎮 Genişletme Fikirleri

- [ ] Tavan yürüyüşü (örümcek için)
- [ ] Farklı yüzey türleri ve tepki animasyonları
- [ ] Player input'a bağlı procedural combat hareketleri
- [ ] Environment awareness: ışığa göre idle değişimi, vs.
- [ ] Web deploy veya ekran kayıtları için gösterim modları

---

## 📦 Kullanılacak Teknolojiler

| Alan         | Teknoloji                                      |
|--------------|------------------------------------------------|
| Motor        | Unreal Engine 5.5                              |
| Script Dili  | Blueprint + Opsiyonel C++                      |
| AI           | EQS (isteğe bağlı awareness için)              |
| Animasyon    | Control Rig, FABRIK, Two Bone IK, Animation Blueprint, Motion Warping |
| Platform     | Windows 64-bit                                 |

---

## 📁 Proje Yapısı (Klasörler)

```
ProjectRoot/
├── Blueprints/
│   ├── Dungeon/
│   ├── Characters/
│   │   ├── Spider/
│   │   └── Human/
├── ControlRigs/
├── Animation/
│   ├── IK/
│   └── MotionWarping/
├── UI/
├── DebugTools/
├── Materials/
└── Maps/
```

---

## 🧠 Notlar

- Proje baştan sona **geliştirici showcase** mantığında olacak, oyuncu odaklı değil.
- Her sistemin çalışmasını gösterecek bir debug panel ve kameralar olacak.
- Sistemin bölümlerini parça parça gösterebilecek bir sistem tasarımı yapılmalı.
