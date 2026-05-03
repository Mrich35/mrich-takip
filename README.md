# M.Rich Takip — Fabrika Operasyon Dashboard

> Tek dosyalık, tarayıcıda çalışan, offline-first fabrika operasyon takip uygulaması.

![Dark Mode](https://img.shields.io/badge/Tema-Koyu-0f1117?style=flat-square)
![LocalStorage](https://img.shields.io/badge/Veri-localStorage-10b981?style=flat-square)
![Responsive](https://img.shields.io/badge/Mobil-Uyumlu-3b82f6?style=flat-square)

## Özellikler

| Modül | Açıklama |
|-------|----------|
| **ÖZET** | Daire grafikler (percentage rings) ile anlık dashboard: Aksiyon tamamlanma oranı, Bakım tamamlanma oranı, Geciken aksiyonlar, Genel verimlilik skoru |
| **TOPLANTILAR** | Toplantı ekle, not al, katılımcı kaydet, tarih/saat belirle |
| **AKSİYONLAR** | Kim, ne, ne zaman — durum güncelle (Bekliyor / Devam / Tamam). Gecikenler kırmızı uyarı ile gösterilir |
| **BAKIM** | İş emirleri, ekipman adı, tür (Planlı / Arıza / Kontrol) |

### Temel Özellikler
- **localStorage** ile telefon/bilgisayara kayıt — tarayıcıyı kapatsan da veri silinmez
- **Toplantıdan direkt aksiyon** ekleme (⚡ butonu)
- **Geciken aksiyonlar** otomatik kırmızı uyarı + öncelikli sıralama
- **Filtreleme**: Bekleyen / Devam / Tamam / Geciken / Planlı / Arıza / Kontrol
- **Yüzde halkası (daire grafik)** animasyonlu dashboard
- **JSON yedekleme** — verileri dışa aktar, başka cihaza taşı
- **Mobil uyumlu** — telefonda ve tablette sorunsuz çalışır

## Kullanım

### GitHub Pages ile Online Kullan
1. Bu repo'yu fork'la veya klonla
2. `index.html` dosyasını doğrudan tarayıcıda açabilirsin
3. Veya GitHub Pages aktif et: **Settings → Pages → Source: main branch / root**
4. Link: `https://senin-kullanici-adin.github.io/mrich-takip/`

### Yerel Kullanım
```bash
git clone https://github.com/senin-kullanici-adin/mrich-takip.git
cd mrich-takip
# Doğrudan tarayıcıda index.html aç
```

### Veri Yedekleme
- Header'daki **💾** (disket) butonuna tıkla
- `mrich-takip-yedek-YYYY-MM-DD.json` dosyası indirilecek
- Başka cihazda açmak için: Tarayıcı konsoluna şunu yapıştır:
  ```js
  const data = JSON.parse(`...json içeriği...`);
  localStorage.setItem('mrich_takip_v1', JSON.stringify(data));
  location.reload();
  ```

## Ekran Görüntüleri

| Özet Dashboard | Toplantılar | Aksiyonlar | Bakım |
|---|---|---|---|
| 4 daire grafik + istatistik kartları | Katılımcı, not, tarih | Durum filtre, geciken uyarı | Ekipman, tür, durum |

## Teknolojiler

- **Vanilla HTML5 + CSS3 + JavaScript** (zero dependencies)
- **localStorage API** — persistent client-side storage
- **CSS Grid & Flexbox** — responsive layout
- **SVG stroke-dasharray** — animasyonlu daire grafikler
- **CSS backdrop-filter** — glassmorphism header

## Veri Yapısı (localStorage)

```json
{
  "toplantilar": [
    { "id": "...", "baslik": "...", "tarih": "2026-05-03", "saat": "09:00",
      "katilimcilar": ["Ahmet", "Mehmet"], "notlar": "...", "created": 123456789 }
  ],
  "aksiyonlar": [
    { "id": "...", "tanim": "...", "sorumlu": "...", "bitis": "2026-05-05",
      "durum": "bekliyor|devam|tamam", "toplantiId": "...", "created": 123456789 }
  ],
  "bakimlar": [
    { "id": "...", "baslik": "...", "ekipman": "...", "tur": "planli|ariza|kontrol",
      "tarih": "2026-05-03", "durum": "bekliyor|devam|tamam", "aciklama": "...", "created": 123456789 }
  ]
}
```

## Geliştirici

**M.Rich** — Fabrika Enerji Sistem Teknisyeni

---

> Bu uygulama tamamen client-side çalışır. Hiçbir veri sunucuya gitmez. Tüm veriler tarayıcının localStorage'ında saklanır.
