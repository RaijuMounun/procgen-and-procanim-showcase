# Geliştirici Notları – Procedural Dungeon & Animation Showcase

Bu dosya, projede çalışan geliştiriciler için pratik ipuçları, Blueprint/C++ notları, sık karşılaşılan hatalar ve çözümler ile geliştirme sırasında alınan önemli kararları içerir.

---

## 1. Blueprint ve C++ Notları

- **Prototipleme için Blueprint:**
  - Hızlı iterasyon ve görsel debugging için ana sistemler önce Blueprint ile prototiplenmeli.
  - Performans kritik veya karmaşık algoritmalar C++’a taşınabilir.
- **Blueprint’te Fonksiyonlar:**
  - Fonksiyonları mümkün olduğunca saf (pure) ve yan etkisiz yaz.
  - Event Graph’ı sade tut, karmaşık mantığı fonksiyonlara böl.
- **C++ ile Entegrasyon:**
  - Blueprint fonksiyonlarını `BlueprintCallable` veya `BlueprintPure` ile expose et.
  - C++ class’larını Blueprint’te miras alarak kullanmak esneklik sağlar.

---

## 2. Asset ve Klasör Yönetimi

- **Klasör Yapısı:**
  - Her ana sistem için ayrı klasör (Blueprints/Dungeon, Blueprints/Characters/Spider, vb.)
  - Asset isimlendirmede önek kullan (ör. BP_, SK_, MAT_, UI_)
- **Referans Döngülerinden Kaçın:**
  - Özellikle Blueprint’lerde circular dependency oluşmamasına dikkat et.

---

## 3. Sık Karşılaşılan Hatalar & Çözümler

- **NavMesh Güncellenmiyor:**
  - Dungeon oluşturulduktan sonra `Rebuild Navigation` fonksiyonunu tetikle.
- **IK Hedefleri Yanlış Pozisyonda:**
  - Raycast’lerin world space’te yapıldığından ve doğru collision channel kullandığından emin ol.
- **Animasyon Blending Sorunları:**
  - State machine’de blend ayarlarını ve transition kurallarını gözden geçir.
- **Blueprint Compile Errors:**
  - Fonksiyon parametre tiplerini ve dönüş değerlerini kontrol et.
  - Circular reference olup olmadığını denetle.
- **Shader Derleme Uzun Sürüyor:**
  - İlk açılışta normaldir, asset sayısı arttıkça süre uzayabilir.

---

## 4. Debugging ve Test İpuçları

- **Debug Panelini Kullanın:**
  - Raycast, IK hedefi, animasyon blending gibi teknik verileri anlık gözlemleyin.
- **Print String ve Breakpoint:**
  - Blueprint’te hızlı test için `Print String` ve breakpoint kullanın.
- **Profiling:**
  - Karmaşık sistemlerde Unreal’ın Profiler ve Stat komutlarını kullanın (`stat unit`, `stat fps`, `stat anim`)

---

## 5. Geliştirme Kararları & Notlar

- **Modülerlik:**
  - Her sistemin bağımsız çalışabilir ve test edilebilir olmasına özen gösterildi.
- **Debug Zorunluluğu:**
  - Tüm ana sistemlerde debug görselleştirme ve UI entegrasyonu zorunlu tutuldu.
- **Blueprint Önceliği:**
  - Hızlı prototipleme için öncelik Blueprint, optimize gerekirse C++
- **Dökümantasyon:**
  - Her karmaşık Blueprint veya C++ class’ı için kısa açıklama eklenmeli.

---

## 6. Faydalı Kaynaklar

- [Unreal Engine Documentation](https://docs.unrealengine.com/5.0/en-US/)
- [Blueprint Visual Scripting](https://docs.unrealengine.com/5.0/en-US/blueprint-visual-scripting-in-unreal-engine/)
- [Animation and IK](https://docs.unrealengine.com/5.0/en-US/animation-in-unreal-engine/)
- [Control Rig](https://docs.unrealengine.com/5.0/en-US/control-rig-in-unreal-engine/)
- [Unreal C++ API](https://docs.unrealengine.com/5.0/en-US/API/)

---

## 7. Notlar

- Bu dosya, ekip içinde güncel tutulmalı ve yeni ipuçları/hatalar eklendikçe güncellenmelidir.
- Sık karşılaşılan sorunlar ve çözümler burada paylaşılmalıdır.
