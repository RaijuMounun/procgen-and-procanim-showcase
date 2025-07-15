# Procedural Dungeon & Animation Showcase

## 🎯 Proje Amacı

Bu proje, Unreal Engine 5.5 üzerinde procedural dungeon generation ve procedural animation teknolojilerinin teknik bir gösterimini sunar. Oyun demosu değil, geliştirici ve teknik izleyiciye sistemlerin esnekliğini ve kapasitesini sergilemek için tasarlanmıştır.

---

## 🚀 Hızlı Başlangıç

1. **Gereksinimler:**
   - Unreal Engine 5.5 (veya üstü)
   - Windows 10/11 64-bit
   - 16GB+ RAM önerilir
2. **Projeyi Klonla:**

   ```sh
   git clone https://github.com/raijumounun/procgen-and-procanim-showcase.git
   ```

3. **Projeyi Aç:**
   - `procgenanim.uproject` dosyasını Unreal Engine ile aç.
4. **Gerekirse:**
   - Gerekli plugin ve içeriklerin yüklü olduğundan emin ol.
   - İlk açılışta "Derived Data Cache" ve shader derlemesi zaman alabilir.

---

## 🧱 Klasör Yapısı

```
ProjectRoot/
├── Blueprints/         # Tüm blueprintler (Dungeon, Characters, vb.)
│   ├── Dungeon/
│   ├── Characters/
│   │   ├── Spider/
│   │   └── Human/
├── ControlRigs/        # Control Rig varlıkları
├── Animation/          # IK, Motion Warping, animasyon assetleri
│   ├── IK/
│   └── MotionWarping/
├── UI/                 # Kullanıcı arayüzü blueprintleri ve assetleri
├── DebugTools/         # Debug ve görselleştirme araçları
├── Materials/          # Materyaller ve ilgili assetler
├── Maps/               # Demo ve test haritaları
└── ...
```

---

## 🛠️ Kullanılan Teknolojiler

| Alan         | Teknoloji                                      |
|--------------|------------------------------------------------|
| Oyun Motoru  | Unreal Engine 5.5                              |
| Script Dili  | Blueprint, (opsiyonel) C++                     |
| Animasyon    | Control Rig, FABRIK, Two Bone IK, Motion Warping|
| AI           | EQS (isteğe bağlı awareness için)              |
| Platform     | Windows 64-bit                                 |

---

## 📦 Temel Özellikler

- Procedural dungeon generation (her seferinde farklı harita)
- Çok bacaklı örümcek karakter (Control Rig + Full-body IK)
- İnsan karakter (Animation Blueprint + Motion Warping + IK)
- Gelişmiş debug ve görselleştirme paneli
- UI üzerinden sistemlerin kontrolü

Daha fazla detay için [Features.md](./Features.md) dosyasına bakınız.

---

## 🧠 Notlar

- Proje, teknik gösterim ve eğitim amaçlıdır. Oyun döngüsü veya hikâye içermez.
- Her sistem bağımsız olarak test edilebilir ve debug paneli ile gözlemlenebilir.
- Geliştirici odaklı dökümantasyon ve sunum scriptleri için ilgili .md dosyalarını inceleyin.
