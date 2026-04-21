# CHANGELOG

## Güvenlik Düzeltmeleri

### Firebase Config HTML'den kaldırıldı
- `api/config.js` eklendi — Vercel env değişkenlerinden Firebase config döner.
- `vercel.json` içine `/api/config` rewrite eklendi.
- `admin.html`, `kullanıcı.html`, `müşteri.html` içindeki hardcoded
  `FIREBASE_CONFIG` kaldırıldı; sayfa yüklenirken `/api/config` üzerinden
  senkron olarak çekilir. Hata durumunda Türkçe hata ekranı gösterilir.

### Kullanıcı ID güvenliği
- `kullanıcı.html` içinde `Math.random()` tabanlı ID üretimi
  `crypto.getRandomValues()` ile değiştirildi (18 haneli hex).

### Rate limiting
- `kullanıcı.html` mesaj gönderimine 3 saniyede en fazla 5 mesaj
  sınırı eklendi (`canSendMessage()`). Sınır aşılırsa Türkçe uyarı.

### Firebase Security Rules
- `rules.json` oluşturuldu. Kurulum adımları `SECURITY.md` içinde.
- Bilinmeyen kök yollar varsayılan olarak kilitli (`$other` = false).

### Dokunulmayanlar
- `admin.html` içindeki `genCode()` (zaten `crypto.getRandomValues`).
- Mevcut UI, animasyonlar, renk paleti.
- Türkçe karakterli dosya isimleri.

## Uyarı
Git geçmişinde açıkta kalan eski API anahtarı **rotate edilmelidir**.
Detay: `SECURITY.md`.
