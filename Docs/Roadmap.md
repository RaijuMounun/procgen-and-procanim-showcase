# Yol Haritası – Procedural Dungeon & Animation Showcase

Bu dosya, projenin geliştirme sürecini fazlara ve adımlara bölerek detaylı bir yol haritası sunar. Her faz, teknik hedefler, yapılacak işler ve önerilen zaman çizelgesiyle birlikte açıklanmıştır.

---

## 🚦 Genel Geliştirme Akışı

1. **Altyapı & Hazırlık** (tamamlandı)
2. **Procedural Dungeon Sistemi** (in progress)
3. **SpiderCharacter (Çok Bacaklı Karakter)**
4. **HumanCharacter (İnsan Karakter)**
5. **Showcase UI & Debug Panel**
6. **Genişletme & İyileştirme**

---

## 📅 Gantt Benzeri Zaman Çizelgesi (Öneri)

| Faz \ Hafta         | 1 | 2 | 3 | 4 | 5 | 6 | 7 | 8 |
|---------------------|---|---|---|---|---|---|---|---|
| Altyapı & Hazırlık  |✔️ |   |   |   |   |   |   |   |
| Dungeon Sistemi     |   |███|███|   |   |   |   |   |
| SpiderCharacter     |   |   |███|███|   |   |   |   |
| HumanCharacter      |   |   |   |███|███|   |   |   |
| UI & Debug Panel    |   |   |   |   |███|███|   |   |
| Genişletme          |   |   |   |   |   |   |███|███|

> **Not:** Zaman çizelgesi örnektir, ekibin hızına ve önceliklerine göre değiştirilebilir.

---

## Faz 1 – Altyapı & Hazırlık (tamamlandı)

### Hedefler

- Proje klasör yapısının oluşturulması
- Temel Unreal Engine ayarları ve input mapping
- Geliştirici debug paneli için temel UI altyapısı

### Yapılacaklar

- [x] Proje başlat, klasörleri oluştur
- [x] Gerekli plugin ve starter content’i ekle
- [x] Temel input ve kamera sistemi kur
- [x] Basit bir debug paneli oluştur (örnek butonlar, log gösterimi)

---

## Faz 2 – Procedural Dungeon Sistemi (in progress)

### Hedefler

- Grid tabanlı harita ve oda sistemi
- Oda yerleşimi ve bağlantı algoritması (BSP/RoomGraph)
- NavMesh entegrasyonu
- Dungeon debug overlay ve UI’dan kontrol

### Yapılacaklar

- [ ] Grid ve room class’larını oluştur
- [ ] Oda yerleşimi algoritmasını uygula
- [ ] Oda ve koridor bağlantılarını kur
- [ ] NavMesh otomatik üretimini entegre et
- [ ] Dungeon parametrelerini UI’dan değiştirilebilir yap
- [ ] Oda, grid ve bağlantı overlay’lerini debug için çizdir
- [ ] Dungeon oluşturma/resetleme butonu ekle

---

## Faz 3 – SpiderCharacter (Çok Bacaklı Karakter)

### Hedefler

- Spider karakterin rig ve Control Rig kurulumu
- Bacak hedefleme ve raycast sistemi
- Bacak IK ve hareket sıralaması
- Gövde yüksekliği ve eğim adaptasyonu
- Debug görselleştirme

### Yapılacaklar

- [ ] Spider karakterin skeletal mesh ve rig’ini hazırla
- [ ] Control Rig ile bacak IK zincirlerini kur
- [ ] Her bacak için raycast ile hedef pozisyon belirleme sistemi yaz
- [ ] Bacakların sıralı ve offset’li hareket etmesini sağla
- [ ] Gövde yüksekliğini ve eğimini raycast sonuçlarına göre ayarla
- [ ] Raycast’leri, bacak hedeflerini ve IK zincirlerini debug panelde göster

---

## Faz 4 – HumanCharacter (İnsan Karakter)

### Hedefler

- Temel yürüme/koşma animasyonları
- El ve ayak için çevresel raycast sistemleri
- IK hedef pozisyonlama ve motion warping
- Postür düzeltme ve çevresel blending
- Debug görselleştirme

### Yapılacaklar

- [ ] İnsan karakter için Animation Blueprint oluştur
- [ ] Temel yürüme/koşma animasyonlarını entegre et
- [ ] Eller ve ayaklar için raycast ile çevre kontrolü ekle
- [ ] Duvara yakınken ellerin otomatik yaslanmasını sağla
- [ ] Ayağın önünde engel varsa, ayağı oraya yerleştir
- [ ] Two Bone IK ile el/ayak hedef pozisyonlaması uygula
- [ ] Motion Warping ile animasyonları hedeflere adapte et
- [ ] Eğime göre postür düzeltme ve çevresel blending sistemleri ekle
- [ ] Raycast’leri, IK hedeflerini ve blending durumlarını debug panelde göster

---

## Faz 5 – Showcase UI & Debug Panel

### Hedefler

- Tüm sistemlerin UI üzerinden kontrolü
- Teknik detayların ve debug verilerinin görselleştirilmesi
- Sunum ve gösterim için kamera açıları

### Yapılacaklar

- [ ] UI panelde dungeon oluşturma, karakter animasyon layer’larını aç/kapatma, debug modlarını toggle etme butonları ekle
- [ ] Raycast, IK hedefi, animasyon blending gibi teknik detayları anlık göster
- [ ] Farklı sistemleri gösterecek kamera açıları ve geçişler ekle
- [ ] Her sistemin çalışmasını izleyiciye net gösterecek şekilde sahne düzenle

---

## Faz 6 – Genişletme & İyileştirme

### Hedefler

- Ekstra animasyon ve sistemler
- Sunum ve dökümantasyonun tamamlanması

### Yapılacaklar

- [ ] Tavan yürüyüşü (örümcek için)
- [ ] Farklı yüzey türleri ve tepki animasyonları
- [ ] Player input’a bağlı procedural combat hareketleri
- [ ] Environment awareness (ışık, ses, vs.)
- [ ] Her sistem için kısa teknik açıklamalar ve kullanım notları ekle
- [ ] Geliştirici veya izleyici için rehber doküman hazırla

---

## 📝 Notlar & İpuçları

- Her fazı bitirdikçe, showcase UI ve debug panelini güncelle.
- Teknik gösterim için, her sistemin "neden ilginç" olduğunu vurgulayan kısa açıklamalar ekle.
- Blueprint ile başla, ihtiyaç olursa C++ ile optimize et.
- Her sistemin bağımsız çalışabilir ve gösterilebilir olmasına dikkat et.
