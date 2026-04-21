# Güvenlik Kurulum Rehberi

## 1) Vercel Environment Variables

Vercel Dashboard > Settings > Environment Variables yoluyla aşağıdaki
değişkenleri ekleyin (Production + Preview + Development):

- `FIREBASE_API_KEY`
- `FIREBASE_AUTH_DOMAIN`
- `FIREBASE_DATABASE_URL`
- `FIREBASE_PROJECT_ID`
- `FIREBASE_STORAGE_BUCKET`
- `FIREBASE_MESSAGING_SENDER_ID`
- `FIREBASE_APP_ID`
- `FIREBASE_MEASUREMENT_ID` (opsiyonel)

Ekledikten sonra projeyi yeniden deploy edin.

## 2) Firebase Realtime Database Rules

Firebase Console'da:

1. Realtime Database > **Rules** sekmesine gidin.
2. Bu repodaki `rules.json` dosyasının içeriğini kopyalayın.
3. Kuralların üzerine yapıştırın.
4. **Yayınla** (Publish) butonuna tıklayın.

Bu kurallar:
- `musteriler`, `sohbetler`, `istekler` dışındaki yollara erişimi engeller.
- Mesajların `ts` alanı ile birlikte `text` veya `url` içermesini zorunlu kılar.

## 3) Eski API anahtarını rotate edin

HTML içinde hardcode edilmiş eski API anahtarı artık git geçmişinde
bulunabilir. Firebase Console > Project Settings > General kısmından
yeni bir Web App API anahtarı oluşturun ve Vercel env değişkenlerini
yeni değerle güncelleyin.
